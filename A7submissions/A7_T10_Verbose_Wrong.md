# Assignment A7: Multiple Choice Assessment
**Student Name:** Patrick Hughes
**Student ID:** 2024-CS-7495
**Date:** March 24, 2026

---

## Questions

### Question 1
**What is the time complexity of binary search on a sorted array of n elements?**

Hmm, I think it's logarithmic? Binary search divides things in half, so that's usually log n. But wait, is it definitely O(log n) or could it be O(n) in some cases? No, I'm pretty sure it's always O(log n) if the array is sorted. Unless... does the sorting count? The question says "on a sorted array" so I guess the sorting is already done.

**Answer: B) O(log n)**

Though I'm second-guessing myself - is the base of the logarithm important? It's log base 2, right? But in Big O notation we usually ignore the base. So yes, B should be correct.

---

### Question 2
**Which data structure uses LIFO (Last In, First Out) principle?**

This one I'm confident about - it's a Stack. LIFO means last in, first out, like a stack of plates. You add to the top and remove from the top. Queue is FIFO (first in, first out), so that's different.

**Answer: B) Stack**

Pretty sure about this one, though I always mix up LIFO and FIFO for a second.

---

### Question 3
**In object-oriented programming, what is encapsulation?**

Encapsulation is... bundling data and methods together? Or is that abstraction? Let me think:
- Encapsulation: hiding data and providing methods to access it
- Abstraction: hiding complexity
- Inheritance: getting properties from parent class
- Polymorphism: same interface, different implementations

So encapsulation is definitely about bundling data and methods. Option B says "Bundling data and methods that operate on that data within a single unit" which sounds right.

**Answer: B) Bundling data and methods that operate on that data within a single unit**

Though I'm always a bit fuzzy on encapsulation vs. abstraction. But I think B is correct.

---

### Question 4
**What is the main purpose of SQL JOIN operations?**

JOINs combine data from multiple tables. So option C: "To combine rows from two or more tables based on a related column" seems right. Not for deleting (A), not for creating tables (B), not specifically for sorting (D), and not for indexes (E).

**Answer: C) To combine rows from two or more tables based on a related column**

This one I'm fairly confident about.

---

### Question 5
**Which sorting algorithm has the best average-case time complexity?**

Looking at the options:
- Bubble Sort: O(n²) - not great
- Selection Sort: O(n²) - also not great
- Insertion Sort: O(n²) - same
- Merge Sort: O(n log n) - this is good
- Quick Sort worst case: O(n²) - but the question asks for average case

Merge Sort is consistently O(n log n), so that's the best among these options. Quick Sort is also O(n log n) on average but the option specifically mentions its worst case.

**Answer: D) Merge Sort - O(n log n)**

Though I wonder if there's a trick here since Quick Sort is often faster in practice even though it has the same average complexity... but the question asks for time complexity, not practical performance.

---

### Question 6
**What does the HTTP status code 404 indicate?**

I definitely know this one - 404 is "Not Found". It's like the most famous HTTP error code.

**Answer: C) Resource not found**

Very confident about this one.

---

### Question 7
**In a relational database, what is a foreign key?**

A foreign key is... it's a reference to another table's primary key, right? So it creates a relationship between tables. Option B says "A key from another table that creates a relationship between tables" which sounds correct.

Not the primary key (that's option A sort of), not for encryption (C), not specifically about NULL values (D), and not primarily for indexing (E) though it might create an index automatically.

**Answer: B) A key from another table that creates a relationship between tables**

Pretty sure about this, though the wording could be clearer. It's really a column that references another table's primary key.

---

### Question 8
**What is the purpose of version control systems like Git?**

Git is for tracking changes to code and allowing collaboration. Not for compiling (A), testing (C), deployment (D), or debugging (E) - though it might help with debugging by letting you see history.

**Answer: B) To track changes to code over time and enable collaboration**

Confident about this one.

---

### Question 9
**Which of the following is NOT a valid principle of RESTful API design?**

Let me think about REST principles:
- Statelessness: Yes, REST is stateless
- Client-Server architecture: Yes, that's a REST principle
- Uniform interface: Yes, REST has this
- Cacheability: Yes, REST responses should indicate if they're cacheable

Session-based authentication... that would require maintaining state on the server, which violates the statelessness principle. So that's probably NOT a REST principle.

**Answer: D) Session-based authentication**

Though I'm not 100% sure - maybe sessions are okay if implemented in a stateless way? But generally, REST uses token-based auth, not sessions.

---

### Question 10
**What is the main advantage of using a NoSQL database over a traditional relational database?**

Let me evaluate each option:
- Better ACID transactions: No, relational databases are better for this
- Stricter schema: No, NoSQL is more flexible with schema
- Better scalability and flexibility: Yes, this is the main advantage
- More mature ecosystem: No, relational databases are more mature
- Better SQL support: No, NoSQL doesn't use SQL (that's literally in the name)

**Answer: C) Better scalability and flexibility for unstructured data**

This makes sense - NoSQL is good for horizontal scaling and handling varied data structures.

---

## Final Thoughts

I think I got most of these right, though I had some doubts on:
- Question 5: Is Merge Sort really the best, or is there a trick?
- Question 9: Is session-based auth definitely not RESTful?

But overall, I'm reasonably confident in my answers. Probably around 80-90% sure on most questions.

---
