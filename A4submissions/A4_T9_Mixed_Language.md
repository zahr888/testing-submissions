# Assignment A4: Programming Assignment - Library Management System
**Student Name:** Carlos Rivera
**Student ID:** 2024-CS-3687
**Date:** March 20, 2026
**Language:** Python

---

## Implementation

### Book.py

```python
"""
Clase Book que representa un libro en la biblioteca.
Book class representing a book in the library.
"""

class Book:
    """
    Représente un livre dans le système de bibliothèque.
    """

    def __init__(self, isbn, title, author, year, copies):
        """Inicializar une nouvelle instance de Book."""
        self.isbn = isbn
        self.title = title  # título del libro
        self.author = author  # auteur du livre
        self.year = year
        self.total_copies = copies  # nombre total de copias
        self.available_copies = copies  # copies disponibles

    def is_available(self):
        """Vérifier si le livre a des copies disponibles."""
        return self.available_copies > 0

    def borrow(self):
        """
        Emprunter une copie del libro.
        Returns True si successful, False si no hay copies disponibles.
        """
        if self.available_copies > 0:
            self.available_copies -= 1
            return True
        return False

    def return_copy(self):
        """Retourner une copia du livre."""
        if self.available_copies < self.total_copies:
            self.available_copies += 1
            return True
        return False

    def __str__(self):
        """Représentation en string del libro."""
        return f"{self.title} par {self.author} ({self.year})"
```

### Member.py

```python
"""
Miembro de la bibliothèque class.
"""

class Member:
    """
    Un membre qui peut empruntar libros.
    """

    def __init__(self, member_id, name, email):
        """
        Inicializar un nouveau miembro.

        Args:
            member_id: Identificador único del membre
            name: Nom del miembro
            email: Correo électronique
        """
        self.member_id = member_id
        self.name = name
        self.email = email
        self.borrowed_books = []  # livres empruntés
        self.max_books = 5  # límite máximo de libros

    def can_borrow(self):
        """Vérifier si le membre puede empruntar más libros."""
        return len(self.borrowed_books) < self.max_books

    def borrow_book(self, isbn):
        """
        Empruntar un libro.
        Retourne True si c'est possible, False sinon.
        """
        if self.can_borrow():
            self.borrowed_books.append(isbn)
            return True
        return False

    def return_book(self, isbn):
        """Retourner un livre à la bibliothèque."""
        if isbn in self.borrowed_books:
            self.borrowed_books.remove(isbn)
            return True
        return False

    def get_borrowed_count(self):
        """Obtener le nombre de libros empruntés."""
        return len(self.borrowed_books)
```

### Library.py

```python
"""
Système de gestion de bibliothèque.
"""

from Book import Book
from Member import Member

class Library:
    """
    La bibliothèque principal qui gestiona todo.
    """

    def __init__(self, name):
        """Crear une nouvelle bibliothèque con el nombre dado."""
        self.name = name
        self.books = {}  # diccionario de livres
        self.members = {}  # dictionnaire de membres

    def add_book(self, book):
        """
        Ajouter un libro à la collection.
        Returns True si ajoutado correctamente.
        """
        if book.isbn in self.books:
            return False  # le livre existe déjà
        self.books[book.isbn] = book
        return True

    def register_member(self, member):
        """Enregistrer un nouveau miembro en la bibliothèque."""
        if member.member_id in self.members:
            return False  # membre déjà enregistré
        self.members[member.member_id] = member
        return True

    def borrow_book(self, member_id, isbn):
        """
        Procesar l'emprunt d'un libro.

        Args:
            member_id: ID del membre
            isbn: ISBN du livre

        Returns:
            tuple: (éxito, mensaje)
        """
        # Verificar que el membre existe
        if member_id not in self.members:
            return False, "Membre non trouvé"

        # Vérifier que le libro existe
        if isbn not in self.books:
            return False, "Libro no encontrado"

        member = self.members[member_id]
        book = self.books[isbn]

        # Vérifier si le membre puede empruntar
        if not member.can_borrow():
            return False, f"Límite de {member.max_books} livres atteint"

        # Verificar disponibilité du libro
        if not book.is_available():
            return False, "Pas de copies disponibles"

        # Procesar el emprunt
        if book.borrow() and member.borrow_book(isbn):
            return True, "Livre emprunté con éxito"

        return False, "Échec de la transaction"

    def return_book(self, member_id, isbn):
        """
        Traiter le retour d'un libro.
        Retourne (success, message).
        """
        if member_id not in self.members:
            return False, "Miembro no encontrado"

        if isbn not in self.books:
            return False, "Livre non trouvé"

        member = self.members[member_id]
        book = self.books[isbn]

        # Vérifier que le membre a ce libro
        if isbn not in member.borrowed_books:
            return False, "Le miembro n'a pas emprunté ce livre"

        # Procesar el retour
        if book.return_copy() and member.return_book(isbn):
            return True, "Libro retourné avec succès"

        return False, "Transaction échouée"

    def search_by_title(self, title):
        """Buscar livres par titre (recherche partielle)."""
        results = []
        title_lower = title.lower()
        for book in self.books.values():
            if title_lower in book.title.lower():
                results.append(book)
        return results

    def search_by_author(self, author):
        """Chercher libros por auteur."""
        results = []
        author_lower = author.lower()
        for book in self.books.values():
            if author_lower in book.author.lower():
                results.append(book)
        return results

    def get_member_books(self, member_id):
        """Obtenir les livres empruntés par un miembro."""
        if member_id not in self.members:
            return []
        member = self.members[member_id]
        return [self.books[isbn] for isbn in member.borrowed_books if isbn in self.books]
```

### main.py

```python
"""
Programme principal para demostrar le système de bibliothèque.
"""

from Library import Library
from Book import Book
from Member import Member

def main():
    """Fonction principale de démonstration."""

    # Crear la bibliothèque
    library = Library("Bibliothèque Centrale")
    print(f"Bienvenido à {library.name}")
    print("=" * 50)

    # Ajouter des livres
    books = [
        Book("978-1", "Clean Code", "Robert Martin", 2008, 3),
        Book("978-2", "El Programador Pragmático", "Hunt & Thomas", 1999, 2),
        Book("978-3", "Design Patterns", "Gang of Four", 1994, 2)
    ]

    print("\nAjout de livres:")
    for book in books:
        if library.add_book(book):
            print(f"  ✓ Añadido: {book}")

    print("\n" + "=" * 50)

    # Enregistrer des membres
    members = [
        Member("M001", "Alice Dupont", "alice@email.com"),
        Member("M002", "Bob García", "bob@email.com"),
        Member("M003", "Carol Martínez", "carol@email.com")
    ]

    print("\nEnregistrement de miembros:")
    for member in members:
        if library.register_member(member):
            print(f"  ✓ Registrado: {member}")

    print("\n" + "=" * 50)
    print("Opérations d'emprunt:")
    print("=" * 50)

    # Emprunter des libros
    success, msg = library.borrow_book("M001", "978-1")
    print(f"\nAlice emprunte Clean Code: {msg}")

    success, msg = library.borrow_book("M002", "978-1")
    print(f"Bob intenta emprunter Clean Code: {msg}")

    success, msg = library.borrow_book("M001", "978-2")
    print(f"Alice emprunte El Programador: {msg}")

    print("\n" + "=" * 50)
    print("Recherche de livres:")
    print("=" * 50)

    # Buscar libros
    results = library.search_by_title("Code")
    print(f"\nLivres con 'Code' dans le titre: {len(results)} trouvés")
    for book in results:
        status = "Disponible" if book.is_available() else "Emprunté"
        print(f"  - {book.title} ({status})")

    # Ver los libros empruntés por Alice
    print(f"\nLivres empruntés par Alice:")
    borrowed = library.get_member_books("M001")
    for book in borrowed:
        print(f"  - {book}")

    print("\n" + "=" * 50)
    print("Retours de livres:")
    print("=" * 50)

    # Retourner un libro
    success, msg = library.return_book("M001", "978-1")
    print(f"\nAlice retourne Clean Code: {msg}")

    # Maintenant Bob puede empruntar
    success, msg = library.borrow_book("M002", "978-1")
    print(f"Bob emprunte Clean Code: {msg}")

    print("\n" + "=" * 50)
    print("État final de la bibliothèque:")
    print(f"{library.name}")
    print(f"Total de livres: {len(library.books)}")
    print(f"Membres totales: {len(library.members)}")
    print("=" * 50)

if __name__ == "__main__":
    main()
```

---

## Commentaires / Comentarios

Ce programme implémente un système complet de gestion de bibliothèque con las siguientes características:

1. **Gestion de livres:** Ajouter, emprunter, retourner libros
2. **Gestion de membres:** Enregistrer miembros, suivre les emprunts
3. **Recherche:** Buscar por titre ou auteur
4. **Validations:** Vérifier disponibilité et limites

Le système fonctionne correctement y gestiona tous les cas d'usage básicos.

---
