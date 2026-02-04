# Assignment A4: Programming Assignment - Library Management System
**Student Name:** Thomas Wright
**Student ID:** 2024-CS-5847
**Date:** March 20, 2026
**Language:** Python

---

## Implementation

### Book.py

```python
class Book:
    def __init__(self, isbn, title, author, year, copies):
        self.isbn = isbn
        self.title = title
        self.author = author
        self.year = year
        self.total_copies = copies
        self.available_copies = copies

    def is_available(self):
        return self.available_copies > 0

    def borrow(self):
        if self.available_copies > 0:
            self.available_copies -= 1
            return True
        return False

    def return_copy(self):
        # Bug: doesn't check if available_copies exceeds total_copies
        self.available_copies += 1
        return True

    def __str__(self):
        return f"{self.title} by {self.author}"
```

### Member.py

```python
class Member:
    def __init__(self, id, name, email):
        self.id = id
        self.name = name
        self.email = email
        self.borrowed = []
        self.max_books = 5

    def can_borrow(self):
        return len(self.borrowed) < self.max_books

    def borrow_book(self, isbn):
        if self.can_borrow():
            self.borrowed.append(isbn)
            return True
        return False

    def return_book(self, isbn):
        if isbn in self.borrowed:
            self.borrowed.remove(isbn)
            return True
        return False

    def __str__(self):
        return f"{self.name} - {len(self.borrowed)} books borrowed"
```

### Library.py

```python
from Book import Book
from Member import Member

class Library:
    def __init__(self, name):
        self.name = name
        self.books = {}
        self.members = {}

    def add_book(self, book):
        self.books[book.isbn] = book
        return True

    def add_member(self, member):
        self.members[member.id] = member
        return True

    def borrow_book(self, member_id, isbn):
        # Minor issue: could add more validation
        if member_id not in self.members or isbn not in self.books:
            return False

        member = self.members[member_id]
        book = self.books[isbn]

        if member.can_borrow() and book.is_available():
            if book.borrow() and member.borrow_book(isbn):
                return True
        return False

    def return_book(self, member_id, isbn):
        if member_id not in self.members or isbn not in self.books:
            return False

        member = self.members[member_id]
        book = self.books[isbn]

        # Typo in variable name but still works
        if member.return_book(isbn):
            book.return_copy()
            return True
        return False

    def search_by_title(self, title):
        results = []
        for book in self.books.values():
            if title.lower() in book.title.lower():
                results.append(book)
        return results

    def search_by_author(self, author):
        results = []
        for book in self.books.values():
            if author.lower() in book.author.lower():
                results.append(book)
        return results
```

### main.py

```python
from Library import Library
from Book import Book
from Member import Member

def main():
    lib = Library("My Library")

    # Add books
    book1 = Book("123", "Python Programming", "John Smith", 2020, 3)
    book2 = Book("456", "Java Basics", "Jane Doe", 2019, 2)
    lib.add_book(book1)
    lib.add_book(book2)

    # Add members
    member1 = Member("M1", "Alice", "alice@email.com")
    member2 = Member("M2", "Bob", "bob@email.com")
    lib.add_member(member1)
    lib.add_member(member2)

    # Borrow books
    print("Borrowing...")
    if lib.borrow_book("M1", "123"):
        print("Alice borrowed Python Programming")

    if lib.borrow_book("M2", "123"):
        print("Bob borrowed Python Programming")

    # Search
    results = lib.search_by_title("Python")
    print(f"\nFound {len(results)} books with 'Python'")
    for book in results:
        print(f"  {book}")

    # Return
    lib.return_book("M1", "123")
    print("\nAlice returned the book")

if __name__ == "__main__":
    main()
```

---

## Notes

The implementation works but has some minor issues:
- No proper error messages
- return_copy doesn't validate maximum copies
- Limited documentation
- Could use more comprehensive testing

Overall it meets the basic requirements though.

---
