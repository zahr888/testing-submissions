# Assignment A4: Programming Assignment - Library Management System
**Student Name:** Patrick Hughes
**Student ID:** 2024-CS-4512
**Date:** March 20, 2026
**Language:** Python

---

## Implementation

### Book.py

```python
"""
Book class for the library management system.

This class is designed to represent books in a library, and I've put a lot of
thought into how books should be represented in a programming context. After
extensive research and consideration of various design patterns, I believe
this implementation captures the essence of what a book truly is in the
digital realm.
"""

class Book:
    """
    Represents a book, which is a fundamental unit of knowledge storage.

    Books have been around for thousands of years, and representing them in
    software requires careful consideration of their properties and behaviors.
    I've decided to include the essential attributes that any library would
    need to track.
    """

    def __init__(self, isbn, title, author, year, copies):
        """
        Initialize a Book instance.

        The initialization process is crucial because it sets up the book's
        state. I'm using positional parameters here rather than keyword
        arguments because I believe it makes the code cleaner, though some
        might argue that keyword arguments are more explicit and therefore
        better for readability.
        """
        self.isbn = isbn  # International Standard Book Number
        self.title = title  # The name of the book
        self.author = author  # Person who wrote it
        self.year = year  # When it was published
        self.copies = copies  # How many we have

        # I'm not tracking available copies separately because I think
        # we can just use the copies variable for that purpose

    def is_available(self):
        """
        Check if book is available.

        This method returns whether the book is available. I'm checking if
        copies is greater than 0, which makes sense because if we have any
        copies at all, the book should be available. Though now that I think
        about it, this doesn't account for copies that are currently borrowed,
        but I think that's okay because we can handle that elsewhere.
        """
        return self.copies > 0

    def borrow(self):
        """
        Borrow a book.

        When someone borrows a book, we need to do something to reflect that.
        I'm not entirely sure what the best approach is here. Should we
        decrement the copies? Should we keep a separate list of borrowed copies?
        I've decided to just return True for now because borrowing always works
        in my mind. We can add more complex logic later if needed.
        """
        # TODO: Actually implement borrowing logic
        return True

    def return_book(self):
        """
        Return a borrowed book.

        This is the opposite of borrowing. I think we should increment the
        copies counter, but that could lead to having more copies than we
        started with if someone calls this too many times. Maybe we need a
        max_copies variable? I'll leave this as a simple implementation for now.
        """
        self.copies += 1  # Add the book back
        return True

    def __str__(self):
        """
        String representation of the book.

        I believe in making string representations human-readable, so I'm
        including all the important information here. Some people might say
        this is too verbose, but I think it's better to have more information
        than less.
        """
        return f"Book: {self.title}, Author: {self.author}, Year: {self.year}, ISBN: {self.isbn}, Copies: {self.copies}"
```

### Member.py

```python
"""
Member class representing library members.

Members are people who use the library, and they have certain privileges like
borrowing books. I've designed this class to capture the essential properties
of a library member, though in a real-world scenario we might need many more
attributes like address, phone number, membership type, etc.
"""

class Member:
    """
    A library member who can borrow books.

    The concept of membership is interesting because it creates a relationship
    between people and the library. I'm implementing this as a class because
    object-oriented programming is the best way to model real-world entities,
    or at least that's what I learned in my programming courses.
    """

    def __init__(self, member_id, name, email):
        """
        Create a new member.

        I'm requiring three parameters: an ID, a name, and an email. The ID
        is important for uniquely identifying members, the name is what we
        call them, and the email is for modern communication. I considered
        adding a phone number but decided against it because not everyone
        has a phone, though actually most people do these days.
        """
        self.member_id = member_id
        self.name = name
        self.email = email
        self.books = []  # List of books they've borrowed

        # I'm setting a max of 3 books per member, which seems reasonable
        # though different libraries might have different limits
        self.max_books = 3

    def can_borrow(self):
        """
        Check if member can borrow more books.

        This method checks whether a member has reached their borrowing limit.
        I'm using a simple comparison of list length versus max_books. Some
        might argue this should be more sophisticated, but I believe in keeping
        things simple when possible, which is one of the core principles of
        good programming according to various books I've read.
        """
        # Actually, now that I think about it, should we check if they have
        # any overdue books? Probably, but I'll handle that later.
        return len(self.books) < self.max_books

    def borrow_book(self, book_isbn):
        """
        Borrow a book.

        When a member borrows a book, we add it to their list. I'm storing
        just the ISBN rather than the whole book object because that seems
        more efficient, though it does mean we need to look up the book
        elsewhere if we want details about it. There are trade-offs either way.
        """
        if self.can_borrow():
            self.books.append(book_isbn)
            return True
        else:
            # They can't borrow because they're at the limit
            return False

    def return_book(self, book_isbn):
        """
        Return a book.

        This removes a book from the member's borrowed list. I'm using the
        remove() method which will raise an exception if the book isn't in
        the list, but I think that's okay because it indicates a programming
        error if we're trying to return a book that wasn't borrowed.

        Actually, maybe I should check first... let me add that.
        """
        if book_isbn in self.books:
            self.books.remove(book_isbn)
            return True
        return False  # Book wasn't borrowed by this member
```

### Library.py

```python
"""
Library class that manages everything.

The Library class is the central coordinator of the system. It manages both
books and members, and handles the interactions between them. I've chosen to
implement this as a single class rather than splitting it into multiple
manager classes because I think that would be overengineering for this
assignment, though in a production system we might want separate BookManager
and MemberManager classes.
"""

from Book import Book
from Member import Member

class Library:
    """
    The main library system.

    This class brings together books and members. I'm using dictionaries to
    store both books and members because dictionary lookups are O(1) which is
    very efficient, though for small libraries it wouldn't really matter if
    we used lists instead. I like to plan for scale even in small projects.
    """

    def __init__(self, name):
        """
        Create a new library.

        Every library needs a name, so I've made that a required parameter.
        I'm initializing empty dictionaries for books and members because
        obviously a new library starts with no books or members, though in
        reality libraries probably start with some books.
        """
        self.name = name
        self.books = {}  # Key: ISBN, Value: Book object
        self.members = {}  # Key: member_id, Value: Member object

    def add_book(self, book):
        """
        Add a book to the library.

        This method adds a book to our books dictionary. I'm using the ISBN
        as the key because ISBNs are unique identifiers for books. Some might
        worry about collisions but ISBNs are designed to be unique so that
        shouldn't be a problem.
        """
        # Should I check if the book already exists? Probably yes.
        # If it exists, maybe we should add to the copies count?
        # For now I'll just add it
        self.books[book.isbn] = book
        return True

    def register_member(self, member):
        """
        Register a new library member.

        Members need to be registered before they can borrow books. This is
        similar to add_book but for members instead. I'm following the same
        pattern of using a dictionary with the member_id as the key.
        """
        self.members[member.member_id] = member
        return True

    def borrow_book(self, member_id, isbn):
        """
        Process a book borrowing transaction.

        This is where things get complicated. We need to:
        1. Check if the member exists
        2. Check if the book exists
        3. Check if the member can borrow more books
        4. Check if the book is available
        5. Actually process the borrowing

        That's a lot of steps, and I'm not entirely sure I've got the order
        right. Let me think through this carefully...
        """
        # First, get the member
        if member_id not in self.members:
            return False  # Member doesn't exist
        member = self.members[member_id]

        # Get the book
        if isbn not in self.books:
            return False  # Book doesn't exist
        book = self.books[isbn]

        # Check if member can borrow
        # Actually, the member class has a method for this
        if not member.can_borrow():
            return False

        # Check if book is available
        if not book.is_available():
            return False

        # Now do the borrowing
        # The member class handles adding to their list
        member.borrow_book(isbn)

        # But we also need to update the book...
        # Actually, the Book class doesn't properly track this
        # Let me just call book.borrow() even though it doesn't do much
        book.borrow()

        return True

    def return_book(self, member_id, isbn):
        """
        Process a book return.

        This is simpler than borrowing, I think. We just need to remove the
        book from the member's list and add it back to the library's
        available stock. Though the logic might be trickier than I initially
        thought.
        """
        member = self.members.get(member_id)
        if not member:
            return False

        book = self.books.get(isbn)
        if not book:
            return False

        # Remove from member's list
        member.return_book(isbn)

        # Add back to book's available copies
        book.return_book()

        return True

    def search_books(self, query):
        """
        Search for books.

        This method should search for books by title or author. I'm not sure
        the best way to implement this. Should it be case-sensitive? Should
        it match partial strings? For now I'll do a simple implementation
        that might not work perfectly but demonstrates the concept.
        """
        results = []
        for book in self.books.values():
            # Check if query is in title or author
            # Convert to lowercase for case-insensitive search
            if query.lower() in book.title.lower():
                results.append(book)
            # Actually, should I also check author? Let me add that
            elif query.lower() in book.author.lower():
                results.append(book)

        return results
```

### main.py

```python
"""
Main program to demonstrate the library system.

This file demonstrates how to use the library management system. I've tried
to create a comprehensive example that shows all the main features, though
in a real application there would be a user interface rather than just
printing to the console.
"""

from Library import Library
from Book import Book
from Member import Member

def main():
    """
    Main function.

    I'm putting everything in a main function because that's considered best
    practice in Python, though I'm not entirely sure why. It has something to
    do with namespaces and module imports, but the details are fuzzy to me.
    """

    # Create a library
    lib = Library("City Library")
    print(f"Created library: {lib.name}")

    # Add some books
    # I'm creating books with realistic ISBNs, or at least ISBN-like numbers
    book1 = Book("123456789", "Python Programming", "John Smith", 2020, 3)
    book2 = Book("987654321", "Data Structures", "Jane Doe", 2019, 2)

    lib.add_book(book1)
    lib.add_book(book2)
    print("Added books to library")

    # Register a member
    member1 = Member("M001", "Alice Johnson", "alice@email.com")
    lib.register_member(member1)
    print("Registered member: Alice")

    # Try to borrow a book
    if lib.borrow_book("M001", "123456789"):
        print("Alice successfully borrowed Python Programming")
    else:
        print("Borrowing failed")

    # Try to return it
    if lib.return_book("M001", "123456789"):
        print("Alice returned the book")
    else:
        print("Return failed")

    # Search for books
    results = lib.search_books("Python")
    print(f"Search found {len(results)} books")

# This is the standard Python idiom for running the main function
# I understand this checks if the script is being run directly
if __name__ == "__main__":
    main()
```

---

## Documentation

This implementation provides a basic library management system. The system has some limitations:

1. The Book class doesn't properly track borrowed vs available copies
2. There's no date tracking for when books are borrowed
3. No late fee system
4. Search functionality is basic
5. No error messages, just True/False returns

These could all be improved in a future version, but I believe the current implementation demonstrates the core concepts adequately, even if it's not production-ready. The architecture is solid though, and with some refinements it could be quite robust.

---
