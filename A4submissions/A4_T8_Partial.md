# Assignment A4: Programming Assignment - Library Management System
**Student Name:** Olivia Sanders
**Student ID:** 2024-CS-2931
**Date:** March 20, 2026
**Language:** Python

---

## Implementation

### Book.py

```python
"""
Book class representing a library book.
"""

class Book:
    """
    Represents a book in the library system.
    """

    def __init__(self, isbn, title, author, year, copies_total):
        """Initialize a new Book instance."""
        self.isbn = isbn
        self.title = title
        self.author = author
        self.year = year
        self.copies_total = copies_total
        self.copies_available = copies_total

    def is_available(self):
        """Check if the book has available copies."""
        return self.copies_available > 0

    def borrow(self):
        """Borrow a copy of the book."""
        if self.copies_available > 0:
            self.copies_available -= 1
            return True
        return False

    def return_book(self):
        """Return a copy of the book."""
        if self.copies_available < self.copies_total:
            self.copies_available += 1
            return True
        return False

    def __str__(self):
        return f"{self.title} by {self.author} ({self.year})"
```

### Member.py

```python
"""
Member class representing a library member.
"""

class Member:
    """
    Represents a library member who can borrow books.
    """

    def __init__(self, member_id, name, email, max_books=5):
        """Initialize a new Member instance."""
        self.member_id = member_id
        self.name = name
        self.email = email
        self.borrowed_books = []
        self.max_books = max_books

    def can_borrow(self):
        """Check if member can borrow more books."""
        return len(self.borrowed_books) < self.max_books

    def borrow_book(self, isbn):
        """Add a book to member's borrowed list."""
        if self.can_borrow():
            self.borrowed_books.append(isbn)
            return True
        return False

    def return_book(self, isbn):
        """Remove a book from member's borrowed list."""
        if isbn in self.borrowed_books:
            self.borrowed_books.remove(isbn)
            return True
        return False

    def __str__(self):
        return f"{self.name} (ID: {self.member_id})"
```

### Library.py

```python
"""
Library class managing the entire library system.
"""

from Book import Book
from Member import Member

class Library:
    """
    Main library system managing books and members.
    """

    def __init__(self, name):
        """Initialize a new Library instance."""
        self.name = name
        self.books = {}
        self.members = {}

    def add_book(self, book):
        """Add a book to the library collection."""
        if book.isbn in self.books:
            return False
        self.books[book.isbn] = book
        return True

    def register_member(self, member):
        """Register a new member."""
        if member.member_id in self.members:
            return False
        self.members[member.member_id] = member
        return True

    def borrow_book(self, member_id, isbn):
        """Process a book borrowing transaction."""
        if member_id not in self.members:
            return False, "Member not found"

        if isbn not in self.books:
            return False, "Book not found"

        member = self.members[member_id]
        book = self.books[isbn]

        if not member.can_borrow():
            return False, "Borrowing limit reached"

        if not book.is_available():
            return False, "Book not available"

        if book.borrow() and member.borrow_book(isbn):
            return True, "Book borrowed successfully"

        return False, "Transaction failed"

    def return_book(self, member_id, isbn):
        """Process a book return transaction."""
        if member_id not in self.members:
            return False, "Member not found"

        if isbn not in self.books:
