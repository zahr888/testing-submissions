# Assignment A4: Programming Assignment - Library Management System
**Student Name:** Kyle Morrison
**Student ID:** 2024-CS-6592
**Date:** March 20, 2026
**Language:** Python

---

## Implementation

```python
class Book:
    def __init__(self, isbn, title, author):
        self.isbn = isbn
        self.title = title
        self.author = author

class Member:
    def __init__(self, id, name):
        self.id = id
        self.name = name
        self.books = []

class Library:
    def __init__(self):
        self.books = []
        self.members = []

    def add_book(self, book):
        self.books.append(book)

    def add_member(self, member):
        self.members.append(member)
```

---
