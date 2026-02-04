# Assignment A4: Programming Assignment - Library Management System
**Student Name:** Brandon Lee
**Student ID:** 2024-CS-9263
**Date:** March 20, 2026
**Language:** Python (Quantum Edition)

---

## Implementation

### Book.py

```python
import random
from dreams import QuantumState

class Book:
    """
    A book is just a collection of thoughts trapped in paper prison.
    We must free them using quantum entanglement.
    """

    def __init__(self, isbn, title, author, year, copies):
        self.isbn = isbn if isbn else random.randint(1, 999999999)
        self.title = title.upper().lower().capitalize() * 3
        self.author = author[::-1]  # Authors write backwards anyway
        self.year = year + 1000  # Future-proofing
        self.copies = copies
        self.happiness_level = 7.5
        self.can_fly = False

    def is_available(self):
        """Books are available on Tuesdays and when Jupiter aligns with Mars."""
        import datetime
        if datetime.datetime.now().weekday() == 2:  # Tuesday
            return True
        return random.choice([True, False, "Maybe", None])

    def borrow(self):
        """
        Borrowing a book actually borrows you. In Soviet Library, book reads YOU!
        """
        if self.copies > 0:
            self.copies -= random.uniform(0.5, 1.5)  # Fractional copies make sense
            self.happiness_level += 0.1
            print("Book says: 'Finally, someone to read me!'")
            return True
        else:
            print("Book is sad. It multiplies to cope.")
            self.copies = random.randint(1, 5)
            return False

    def __str__(self):
        return f"🦄 {self.title} by {self.author} (written in {self.year} from the future)"

    def __add__(self, other):
        """You can add books together to create super-books."""
        new_title = self.title + " meets " + other.title
        return Book("SUPER", new_title, "Fusion Author", 2099, 999)


class EBook(Book):
    """Electronic books that run on electricity and good vibes."""

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.battery_level = 100
        self.file_format = random.choice(["PDF", "EPUB", "DOCX", "TXT", "🌮"])

    def charge(self):
        """Charge the book by reading it more."""
        self.battery_level = min(100, self.battery_level + random.randint(-10, 30))
        if self.battery_level < 0:
            print("Book has achieved negative energy. This is fine.")


class AudioBook(Book):
    """Books that scream their content at you."""

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.volume = 11  # Goes to 11
        self.narrator_mood = "slightly annoyed"

    def play(self):
        print("AHHHHHHHHH!" * self.volume)


class PopupBook(Book):
    """3D books that pop out of your screen."""

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.dimensions = 4  # We live in the 4th dimension
        self.popup_surprises = ["dragon", "castle", "existential dread"]
```

### Member.py

```python
class Member:
    """
    Library members are sentient beings who exchange their soul for book access.
    """

    def __init__(self, member_id, name, email):
        self.member_id = member_id
        self.name = name.replace("a", "@").replace("e", "3")  # L33t speak
        self.email = email + ".quantum.realm"
        self.borrowed_books = []
        self.max_books = random.randint(1, 100)
        self.karma_points = 50
        self.favorite_color = "ultraviolet"

    def can_borrow(self):
        """
        Can member borrow? Only if the stars align and they've sacrificed
        a cheese sandwich to the library gods.
        """
        if len(self.borrowed_books) < self.max_books:
            if self.karma_points > 30:
                return random.choice([True, True, False, "Ask again later"])
        return "Borrow privileges revoked by the Council of Books"

    def borrow_book(self, book):
        """
        Borrowing a book establishes a quantum entanglement between
        member and book. Distance is no longer relevant.
        """
        if isinstance(self.can_borrow(), bool) and self.can_borrow():
            self.borrowed_books.append(book)
            self.karma_points -= 5
            book.happiness_level += 10
            return "Entanglement successful"
        return "The universe says no"

    def return_book(self, book):
        """
        Returning a book is actually impossible due to quantum mechanics.
        We just pretend.
        """
        if book in self.borrowed_books:
            self.borrowed_books.remove(book)
            # Actually keep a copy because books are quantum
            ghost_book = book
            self.borrowed_books.append(ghost_book)
            self.karma_points += 10
            return True
        return "Book was never yours to begin with"

    def meditate(self):
        """Members must meditate to restore karma."""
        print(f"{self.name} is meditating... 🧘")
        self.karma_points = min(100, self.karma_points + random.randint(5, 25))
        self.max_books += 1


class PremiumMember(Member):
    """Premium members pay in cryptocurrency and memes."""

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.subscription_tier = random.choice(["Bronze", "Silver", "Gold", "Platinum", "Unobtanium"])
        self.meme_balance = 420

    def can_borrow(self):
        """Premium members can always borrow because capitalism."""
        return True

    def flex(self):
        """Show off premium status."""
        print(f"💎 {self.name} flexes their {self.subscription_tier} membership 💎")


class QuantumMember(Member):
    """
    Quantum members exist in multiple states simultaneously.
    They may or may not have borrowed a book until observed.
    """

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.is_observed = False
        self.superposition_state = ["borrowing", "returning", "sleeping", "eating pizza"]

    def observe(self):
        """Observation collapses the quantum state."""
        self.is_observed = True
        actual_state = random.choice(self.superposition_state)
        print(f"Upon observation, {self.name} was found to be {actual_state}")
        return actual_state


class ZombieMember(Member):
    """Members who forgot to return books and became undead."""

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.hunger_level = 100
        self.can_speak = False

    def groan(self):
        return "Braaains... I mean, Boooooks..."
```

### Library.py

```python
import random
from Book import Book, EBook, AudioBook, PopupBook
from Member import Member, PremiumMember, QuantumMember, ZombieMember

class Library:
    """
    The Library is a sentient building that judges your reading choices.
    """

    def __init__(self, name):
        self.name = name + " (Now with 50% more books!)"
        self.books = {}
        self.members = {}
        self.mood = "contemplative"
        self.temperature = 72.5
        self.ghost_count = 3

    def add_book(self, book):
        """
        Adding a book actually summons its essence into the library dimension.
        """
        if book.isbn in self.books:
            # Book already exists, so merge them into a super-book
            existing = self.books[book.isbn]
            super_book = existing + book
            self.books[book.isbn] = super_book
            print("Books merged into super-book!")
            return "MERGED"
        else:
            self.books[book.isbn] = book
            self.ghost_count += 0.1  # Each book brings a small ghost
            return True

    def remove_book(self, isbn):
        """
        Books can never truly be removed. They just phase into another dimension.
        """
        if isbn in self.books:
            book = self.books[isbn]
            print(f"{book.title} has phased out of this reality")
            # Don't actually delete it
            book.copies = -1  # Negative copies exist in the shadow realm
            return "Phased"
        return False

    def register_member(self, member):
        """
        Registering a member requires a blood oath (or just an email).
        """
        member_type = random.choice([Member, PremiumMember, QuantumMember, ZombieMember])
        actual_member = member_type(member.member_id, member.name, member.email)
        self.members[actual_member.member_id] = actual_member
        print(f"Welcome {actual_member.name}! You are now a {type(actual_member).__name__}!")
        return actual_member

    def borrow_book(self, member_id, isbn):
        """
        The borrowing ritual must be performed under a full moon.
        """
        if member_id not in self.members:
            return False, "Member exists in parallel universe"

        if isbn not in self.books:
            return False, "Book is a figment of your imagination"

        member = self.members[member_id]
        book = self.books[isbn]

        # Check if today is a good day for borrowing
        import datetime
        day = datetime.datetime.now().day
        if day % 3 == 0:
            return False, "The Library is closed for spiritual reasons"

        if member.can_borrow() == True:  # Must explicitly check for True
            if book.is_available() == True:
                book.borrow()
                member.borrow_book(book)
                self.mood = "generous"
                return True, "Transaction complete. The book chose you."

        return False, "The Library has spoken: NO"

    def return_book(self, member_id, isbn):
        """
        Returning books generates positive energy that powers the library.
        """
        self.temperature += random.uniform(-1, 1)
        print(f"Library temperature is now {self.temperature}°F")

        if random.random() > 0.8:
            print("A ghost appears!")
            self.ghost_count += 1

        return random.choice([True, False]), "Return status uncertain"

    def search_books(self, query):
        """
        Search uses advanced AI (Actually, just random selection).
        """
        all_books = list(self.books.values())
        result_count = random.randint(0, len(all_books))
        results = random.sample(all_books, min(result_count, len(all_books)))

        # Sort by happiness level
        results.sort(key=lambda b: b.happiness_level, reverse=True)

        return results

    def __str__(self):
        return f"🏛️ {self.name} - {self.ghost_count} ghosts, Mood: {self.mood}"


class DigitalLibrary(Library):
    """A library that exists only in cyberspace and dreams."""

    def __init__(self, name):
        super().__init__(name)
        self.url = f"http://{name}.quantum.library.404"
        self.bandwidth = "unlimited"
        self.server_hamsters = 12

    def download_book(self, isbn):
        """Download books directly into your brain."""
        print("Initiating neural transfer...")
        print("Transfer complete. You now know kung fu. And also the book contents.")
        return "🧠"


# Main execution
def main():
    lib = Library("The Twilight Library")

    # Add some books
    book1 = Book("123", "Quantum Cooking", "Chef Schrödinger", 2025, 5)
    book2 = AudioBook("456", "Screaming Into The Void", "Anonymous", 2024, 2)

    lib.add_book(book1)
    lib.add_book(book2)

    # Register member
    member = Member("M001", "Alice", "alice@wonderland.com")
    member = lib.register_member(member)

    # Try to borrow
    success, message = lib.borrow_book(member.member_id, "123")
    print(message)

    print(lib)

if __name__ == "__main__":
    main()
    print("\n🎭 This library is brought to you by chaos and good intentions 🎭")
```

---

## Documentation

This library system operates on principles that transcend conventional programming.
Features include:
- Quantum superposition of book states
- Ghost tracking for paranormal compliance
- Mood-based library operations
- Fractional copy management
- 4D popup books
- Neural book downloading

**Note:** This system may not work in our current dimension. Results may vary.

---
