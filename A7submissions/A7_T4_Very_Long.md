# Assignment A7: Multiple Choice Assessment
**Student Name:** Amanda Richardson
**Student ID:** 2024-CS-1472
**Date:** March 24, 2026

---

## Comprehensive Analysis of Computer Science Fundamentals: A Deep Dive into Theoretical and Practical Concepts

### Question 1: Time Complexity Analysis of Binary Search Algorithms

**Question:** What is the time complexity of binary search on a sorted array of n elements?

Before I can properly answer this question, I think it's important to establish a comprehensive understanding of what we mean by "time complexity" and why it matters in the context of algorithm analysis. Time complexity is a computational concept that describes the amount of time an algorithm takes to complete as a function of the length of the input. This is typically expressed using Big O notation, which provides an upper bound on the growth rate of an algorithm's running time.

The concept of algorithmic complexity was formalized in the 1960s and 1970s through the work of computer scientists like Donald Knuth, who wrote the seminal series "The Art of Computer Programming," and Stephen Cook, whose work on computational complexity theory laid the foundation for our modern understanding of algorithm efficiency. Big O notation specifically comes from the work of German mathematician Paul Bachmann in 1894, though it was popularized for computer science applications by Donald Knuth in the 1970s.

Now, when we talk about binary search, we're discussing a divide-and-conquer algorithm that operates on sorted arrays. The fundamental principle behind binary search is remarkably elegant: instead of checking every element sequentially (as in linear search), binary search eliminates half of the remaining elements at each step by comparing the target value with the middle element of the current search space.

To understand why binary search has the time complexity it does, let's consider what happens at each step. If we have an array of n elements:
- First comparison: We're looking at n elements
- Second comparison: We've eliminated half, looking at n/2 elements
- Third comparison: n/4 elements
- Fourth comparison: n/8 elements
- And so on...

The question becomes: how many times can we divide n by 2 until we reach 1? This is precisely the definition of the logarithm base 2 of n, written as log₂(n). In Big O notation, we typically drop the base and just write O(log n) because logarithms of different bases differ only by a constant factor, and Big O notation ignores constant factors.

However, before I commit to an answer, I should consider whether there are any edge cases or special circumstances that might affect this analysis. For instance, what if the array is very small? What if the element we're searching for is exactly in the middle on the first try? What if it's not in the array at all?

In the best case scenario, binary search finds the element on the first comparison, giving us O(1) time complexity. In the worst case, we have to keep dividing until we're left with a single element or determine the element isn't in the array, giving us O(log n). The average case is also O(log n) because...

[The student continues with several more pages analyzing binary search from various theoretical perspectives, discussing the history of sorting algorithms, explaining the mathematical foundations of logarithms, comparing binary search to other searching algorithms in exhaustive detail, exploring cache locality considerations, discussing the implications for different hardware architectures, and analyzing the philosophical implications of divide-and-conquer strategies, but never actually provides a clear answer to Question 1 or moves on to the remaining nine questions...]

---

### Question 2: Data Structure Principles and LIFO Mechanisms

Before addressing which data structure uses the LIFO principle, I believe we should first establish what we mean by "data structure" in the broadest sense. A data structure is a particular way of organizing and storing data in a computer so that it can be accessed and modified efficiently. The choice of data structure often depends on the specific operations that will be performed most frequently...

[Assignment continues but never completes any actual answers...]

---
