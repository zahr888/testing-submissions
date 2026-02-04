# Assignment A2: Structured Q&A Assessment
**Student Name:** Sophia Williams
**Student ID:** 2024-CS-9156
**Date:** March 20, 2026

---

## Section 1: Short Answer Questions (40 points)

### Question 1 (10 points)
Big O notation describes the upper bound of an algorithm's time or space complexity. It's important for comparing algorithms and understanding scalability.

Example of O(n²): Bubble Sort, where nested loops compare each element with others.

---

### Question 2 (10 points)
Stack: LIFO (Last In First Out) - elements added and removed from the top
Queue: FIFO (First In First Out) - elements added at rear, removed from front

Stack example: Browser back button
Queue example: Printer job queue

---

### Question 3 (10 points)
Recursion is when a function calls itself to solve smaller instances of the same problem.

Two essential components:
1. Base case - stops recursion
2. Recursive case - function calls itself with simpler input

---

### Question 4 (10 points)
**Arrays:**
Advantages:
- O(1) random access by index
- Good cache locality

Disadvantages:
- Fixed size (or expensive resizing)
- O(n) insertion/deletion in middle

**Linked Lists:**
Advantages:
- Dynamic size
- O(1) insertion/deletion with pointer

---

## Section 2: Problem-Solving Questions (40 points)

### Question 5 (15 points)

**a) Bubble Sort steps:**

Original: [64, 34, 25, 12, 22, 11, 90]

Pass 1:
[34, 64, 25, 12, 22, 11, 90]
[34, 25, 64, 12, 22, 11, 90]
[34, 25, 12, 64, 22, 11, 90]
[34, 25, 12, 22, 64, 11, 90]
[34, 25, 12, 22, 11, 64, 90]
[34, 25, 12, 22, 11, 64, 90]

Pass 2:
[25, 34, 12, 22, 11, 64, 90]
[25, 12, 34, 22, 11, 64, 90]
[25, 12, 22, 34, 11, 64, 90]
[25, 12, 22, 11, 34, 64, 90]

Pass 3:
