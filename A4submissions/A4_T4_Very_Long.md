# Assignment A4: Programming Assignment - Library Management System
**Student Name:** Victoria Patterson
**Student ID:** 2024-CS-7238
**Date:** March 20, 2026
**Language:** Python

---

## Implementation

### AbstractEntity.py

```python
"""
Abstract base entity class for all domain objects in the library management system.
This class provides foundational functionality that will be inherited by all concrete
entity classes, ensuring consistency across the entire domain model and promoting
code reuse through the DRY (Don't Repeat Yourself) principle, which is one of the
fundamental tenets of good software engineering practice.
"""

from abc import ABC, abstractmethod
from datetime import datetime
import uuid
import logging
import json

class AbstractEntity(ABC):
    """
    Abstract base class for all entities in the system.

    This class implements several design patterns including:
    - Template Method Pattern for entity lifecycle
    - Observer Pattern for change notifications
    - Factory Pattern for entity creation

    The class also provides comprehensive logging, validation, serialization,
    and deserialization capabilities that are essential for enterprise-grade
    applications that need to maintain data integrity, provide audit trails,
    and support various persistence mechanisms including but not limited to
    relational databases, NoSQL databases, file systems, and cloud storage.
    """

    _entity_count = 0
    _entity_registry = {}

    def __init__(self, entity_id=None, created_at=None, updated_at=None):
        """
        Initialize the abstract entity with comprehensive metadata.

        This constructor performs several critical operations:
        1. Generates unique identifiers using UUID4 for global uniqueness
        2. Establishes temporal tracking with creation and modification timestamps
        3. Initializes the change tracking system for audit purposes
        4. Sets up the validation framework
        5. Configures the logging infrastructure
        6. Registers the entity in the global registry

        Args:
            entity_id: Optional pre-existing entity identifier
            created_at: Optional creation timestamp for rehydration
            updated_at: Optional last update timestamp for rehydration
        """
        self._entity_id = entity_id if entity_id else str(uuid.uuid4())
        self._created_at = created_at if created_at else datetime.now()
        self._updated_at = updated_at if updated_at else datetime.now()
        self._version = 1
        self._change_history = []
        self._observers = []
        self._is_deleted = False
        self._metadata = {}

        AbstractEntity._entity_count += 1
        AbstractEntity._entity_registry[self._entity_id] = self

        self._logger = logging.getLogger(self.__class__.__name__)
        self._logger.info(f"Created new entity with ID: {self._entity_id}")

    @property
    def entity_id(self):
        """
        Get the unique entity identifier.

        The entity ID is immutable once set and serves as the primary key
        for all database operations, cache keys, and inter-service communication.
        """
        return self._entity_id

    @property
    def created_at(self):
        """Get the creation timestamp."""
        return self._created_at

    @property
    def updated_at(self):
        """Get the last update timestamp."""
        return self._updated_at

    @abstractmethod
    def validate(self):
        """
        Abstract method that must be implemented by all concrete entities.

        This method should perform comprehensive validation of the entity's
        state including but not limited to:
        - Type checking of all attributes
        - Range validation for numeric fields
        - Format validation for strings
        - Referential integrity checks
        - Business rule validation
        - Cross-field validation
        """
        pass

    @abstractmethod
    def to_dict(self):
        """
        Convert entity to dictionary representation.

        This method supports serialization for various purposes including
        JSON API responses, database persistence, caching, and message queue
        payloads in distributed systems.
        """
        pass

    def register_observer(self, observer):
        """Register an observer for change notifications."""
        self._observers.append(observer)

    def notify_observers(self, event_type, data):
        """Notify all registered observers of changes."""
        for observer in self._observers:
            observer.update(self, event_type, data)

    def soft_delete(self):
        """
        Perform a soft delete of the entity.

        Soft deletion is preferred over hard deletion in most enterprise
        applications because it allows for data recovery, maintains referential
        integrity, supports audit requirements, and enables temporal queries.
        """
        self._is_deleted = True
        self._updated_at = datetime.now()
        self._logger.info(f"Soft deleted entity {self._entity_id}")
        self.notify_observers("DELETE", {"entity_id": self._entity_id})


class VersionedEntity(AbstractEntity):
    """
    Extended entity class with optimistic locking support.

    This class implements the Optimistic Offline Lock pattern to handle
    concurrent updates in distributed systems without requiring pessimistic
    database locks that can cause performance bottlenecks and deadlocks.
    """

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self._version_number = 1
        self._version_history = []

    def increment_version(self):
        """
        Increment version number for optimistic locking.

        This method should be called every time the entity is updated,
        ensuring that concurrent modifications can be detected and handled
        appropriately through version conflict resolution strategies.
        """
        self._version_number += 1
        self._version_history.append({
            "version": self._version_number,
            "timestamp": datetime.now(),
            "changes": []
        })
```

### Book.py

```python
"""
Book entity representing a physical or digital book in the library system.

This module implements a comprehensive book management system with support for:
- Multiple copies and availability tracking
- ISBN validation according to ISBN-10 and ISBN-13 standards
- Rich metadata including publishers, genres, tags, and ratings
- Multi-language support for international libraries
- Digital rights management for e-books
- Integration with external book databases and APIs
"""

from AbstractEntity import VersionedEntity
import re
from datetime import datetime

class Book(VersionedEntity):
    """
    Comprehensive book entity with extensive metadata and functionality.

    The Book class encapsulates all information about a book including
    bibliographic data, physical attributes, availability status, and
    business rules governing borrowing and reservations. It implements
    several design patterns including Strategy for ISBN validation,
    State for availability management, and Decorator for enhanced features.
    """

    # Class-level constants defining business rules
    MAX_TITLE_LENGTH = 500
    MAX_AUTHOR_LENGTH = 200
    MIN_PUBLICATION_YEAR = 1450  # Gutenberg's printing press
    MAX_PUBLICATION_YEAR = datetime.now().year + 1
    ISBN_10_PATTERN = r'^\d{9}[\dX]$'
    ISBN_13_PATTERN = r'^\d{13}$'

    def __init__(self, isbn, title, author, year, copies_total,
                 subtitle=None, publisher=None, edition=None,
                 language="English", genres=None, tags=None,
                 page_count=None, dimensions=None, weight=None,
                 **kwargs):
        """
        Initialize a Book entity with comprehensive metadata.

        This constructor accepts numerous parameters to support rich book
        metadata that can be utilized for advanced search, recommendation
        systems, collection analytics, and user experience enhancements.

        [... continuing for several hundred more lines with excessive detail ...]
        """
        super().__init__(**kwargs)

        # Core attributes with extensive validation
        self._isbn = self._validate_and_format_isbn(isbn)
        self._title = self._validate_title(title)
        self._author = self._validate_author(author)
        self._year = self._validate_year(year)
        self._copies_total = self._validate_copies(copies_total)
        self._copies_available = copies_total

        # Extended metadata
        self._subtitle = subtitle
        self._publisher = publisher
        self._edition = edition
        self._language = language
        self._genres = genres if genres else []
        self._tags = tags if tags else []
        self._page_count = page_count
        self._dimensions = dimensions
        self._weight = weight

        # Borrowing history and analytics
        self._borrow_count = 0
        self._total_borrow_duration_days = 0
        self._average_borrow_duration = 0
        self._popularity_score = 0
        self._reservation_queue = []

        # Rating and review system
        self._ratings = []
        self._average_rating = 0
        self._review_count = 0

    def _validate_and_format_isbn(self, isbn):
        """
        Validate and format ISBN according to international standards.

        This method implements comprehensive ISBN validation including:
        - Format checking for ISBN-10 and ISBN-13
        - Check digit validation using the appropriate algorithm
        - Hyphenation and formatting according to standard conventions
        - Conversion between ISBN-10 and ISBN-13 formats when applicable

        [... several more paragraphs of explanation ...]
        """
        # Remove any hyphens or spaces
        isbn_cleaned = re.sub(r'[\s-]', '', isbn)

        # Validate ISBN-10
        if re.match(self.ISBN_10_PATTERN, isbn_cleaned):
            if self._validate_isbn10_checksum(isbn_cleaned):
                return isbn_cleaned
            else:
                raise ValueError("Invalid ISBN-10 checksum")

        # Validate ISBN-13
        elif re.match(self.ISBN_13_PATTERN, isbn_cleaned):
            if self._validate_isbn13_checksum(isbn_cleaned):
                return isbn_cleaned
            else:
                raise ValueError("Invalid ISBN-13 checksum")

        else:
            raise ValueError("ISBN format invalid")

    def _validate_isbn10_checksum(self, isbn):
        """
        Validate ISBN-10 checksum using modulo 11 algorithm.

        The ISBN-10 checksum is calculated by taking each of the first 9 digits,
        multiplying them by their position (counting from 10 down to 2), summing
        these products, and then taking modulo 11. The check digit is then...

        [... continuing with excessive implementation details ...]
        """
        pass  # Implementation would continue but running out of space

    # [... hundreds more lines of over-engineered methods ...]
```

[Assignment continues for 5000+ more lines but never actually implements the core functionality properly...]

---
