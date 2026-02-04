# Assignment A3: Problem-Solving and Logic Assessment
**Student Name:** Amanda Richardson
**Student ID:** 2024-CS-6745
**Date:** March 18, 2026

---

## Problem 1: Set Theory (20 points)

Let U = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10} be the universal set, which serves as the foundation for all subsequent set operations in this problem, containing all elements that might possibly appear in any of the sets we're working with, specifically sets A, B, and C which are defined as subsets of this universal set.

Let A = {1, 2, 3, 4, 5} be our first set, containing five distinct integers that represent a contiguous sequence starting from one and ending at five.

Let B = {4, 5, 6, 7, 8} be our second set, which interestingly overlaps with set A in exactly two elements, namely four and five, while also containing three elements (six, seven, and eight) that are not present in set A.

Let C = {2, 4, 6, 8, 10} be our third set, which consists exclusively of even numbers from the universal set, a characteristic that will be important in understanding the various intersections and unions we'll be computing.

### a) A ∪ (B ∩ C) (5 points)

To solve this problem, which requires us to find the union of set A with the intersection of sets B and C, we must first understand what each operation means and then proceed methodically through the calculation, being careful at each step to ensure accuracy and completeness in our enumeration of elements.

The intersection operation, denoted by the symbol ∩, is a fundamental set operation that produces a new set containing precisely those elements that appear in both of the operand sets, which in this case are sets B and C. To find B ∩ C, we must examine each element of B and determine whether it also appears in C, or equivalently, we could examine each element of C and determine whether it appears in B, as intersection is commutative.

Beginning with the elements of B, which are {4, 5, 6, 7, 8}, we check each in turn:
- The element 4 appears in B and also appears in C, so 4 ∈ (B ∩ C)
- The element 5 appears in B but does not appear in C, so 5 ∉ (B ∩ C)
- The element 6 appears in B and also appears in C, so 6 ∈ (B ∩ C)
- The element 7 appears in B but does not appear in C, so 7 ∉ (B ∩ C)
- The element 8 appears in B and also appears in C, so 8 ∈ (B ∩ C)

Therefore, B ∩ C = {4, 6, 8}, which represents the set of even numbers that appear in both B and C, or equivalently, the even numbers between four and eight inclusive that belong to both sets.

Now we must compute A ∪ (B ∩ C), which is the union of set A with the intersection we just computed. The union operation, denoted by ∪, creates a new set containing all elements that appear in either operand set or in both operand sets, meaning that an element needs to be in at least one of the sets to be included in the union.

Set A = {1, 2, 3, 4, 5}
B ∩ C = {4, 6, 8}

To find the union, we combine all distinct elements from both sets:
- Elements from A: 1, 2, 3, 4, 5
- Elements from B ∩ C: 4, 6, 8
- Element 4 appears in both sets, but we only include it once in the union
- The complete union is: {1, 2, 3, 4, 5, 6, 8}

**Answer: A ∪ (B ∩ C) = {1, 2, 3, 4, 5, 6, 8}**

### b) (A - B) ∪ C (5 points)

This problem requires us to compute the set difference operation followed by a union operation, demonstrating the importance of operation precedence in set theory and the need to carefully evaluate expressions from the innermost parentheses outward, much like in ordinary arithmetic.

The set difference operation, denoted by the minus sign or sometimes by a backslash, produces a new set containing all elements that are in the first set but not in the second set. Formally, A - B = {x | x ∈ A and x ∉ B}, meaning we're looking for elements that belong to A but don't belong to B.

Let's examine each element of A to determine if it should be included in A - B:
- Element 1 is in A and is not in B, so 1 ∈ (A - B)
- Element 2 is in A and is not in B, so 2 ∈ (A - B)
- Element 3 is in A and is not in B, so 3 ∈ (A - B)
- Element 4 is in A but is also in B, so 4 ∉ (A - B)
- Element 5 is in A but is also in B, so 5 ∉ (A - B)

Therefore, A - B = {1, 2, 3}, consisting of the first three positive integers, which are the elements that A has but B doesn't.

Now we need to find (A - B) ∪ C, the union of our computed difference with set C.

A - B = {1, 2, 3}
C = {2, 4, 6, 8, 10}

The union will contain all distinct elements from both sets:
- Elements from A - B: 1, 2, 3
- Elements from C: 2, 4, 6, 8, 10
- Element 2 appears in both sets but is counted only once
- Complete union: {1, 2, 3, 4, 6, 8, 10}

**Answer: (A - B) ∪ C = {1, 2, 3, 4, 6, 8, 10}**

### c) A' ∩ B' where A' denotes the complement of A (5 points)

This problem involves the complement operation, which is one of the fundamental operations in set theory that requires reference to a universal set, as the complement of a set consists of all elements in the universal set that are not in the given set, making this operation somewhat different from union, intersection, and difference which only depend on the sets being operated upon and not on any ambient universal set.

The complement of A, denoted A', is defined as A' = {x | x ∈ U and x ∉ A}, meaning all elements of the universal set U that are not in A.

Since U = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10} and A = {1, 2, 3, 4, 5}, we can find A' by removing the elements of A from U:
- Elements in U but not in A: 6, 7, 8, 9, 10
- Therefore A' = {6, 7, 8, 9, 10}

Similarly, the complement of B, denoted B', is defined as B' = {x | x ∈ U and x ∉ B}.

Since U = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10} and B = {4, 5, 6, 7, 8}, we find:
- Elements in U but not in B: 1, 2, 3, 9, 10
- Therefore B' = {1, 2, 3, 9, 10}

Now we need to find A' ∩ B', the intersection of these two complements, which will give us elements that are in both A' and B', or equivalently, elements that are in neither A nor B (this is an instance of De Morgan's Law, though we won't need to invoke it explicitly here).

A' = {6, 7, 8, 9, 10}
B' = {1, 2, 3, 9, 10}

Elements in both A' and B':
- 6 is in A' but not in B'
- 7 is in A' but not in B'
- 8 is in A' but not in B'
- 9 is in both A' and B' ✓
- 10 is in both A' and B' ✓

**Answer: A' ∩ B' = {9, 10}**

This result makes intuitive sense because these are precisely the elements of the universal set that belong to neither A nor B.

### d) Draw a Venn diagram representing A, B, and C (5 points)

Creating a Venn diagram for three sets requires careful consideration of all possible regions that can be formed by the intersections and unions of these sets, as there are potentially eight distinct regions: elements in none of the sets, elements in exactly one set, elements in exactly two sets, and elements in all three sets, and we must carefully place each element of our universal set in its appropriate region based on which sets contain it.

[I would draw the diagram here but it's difficult to represent in text format, though I could attempt an ASCII art version if absolutely necessary, but such representations are often unclear and difficult to read, so perhaps it's better to describe the regions verbally, though that somewhat defeats the purpose of a Venn diagram which is meant to provide visual intuition]

Actually, attempting to draw it:
[After several minutes of trying, I realize this is taking too long and the format isn't working well]

---

## Problem 2: Logic and Propositional Calculus (25 points)

### Part A (10 points)

Constructing a truth table for a compound proposition involving three propositional variables requires systematic enumeration of all possible combinations of truth values for those variables, of which there are 2³ = 8 possibilities, and for each combination we must carefully evaluate the truth value of each subexpression in the correct order according to the precedence rules of propositional logic operations, where negation has highest precedence, followed by conjunction and disjunction at the same level (evaluated left to right), followed by implication and biconditional at the lowest precedence level.

[Several more paragraphs of explanation but never actually completing the truth table]

---

## Problem 3: Graph Theory (20 points)

The study of graph theory, which dates back to Leonhard Euler's solution of the Seven Bridges of Königsberg problem in 1736, provides a mathematical framework for analyzing networks, relationships, and structural properties of connected systems, and has applications ranging from computer science and operations research to social network analysis and molecular biology, making it one of the most practically relevant branches of discrete mathematics.

In this problem, we are given a graph G with vertices V = {A, B, C, D, E, F}, which represents six distinct nodes or points in our graph, and edges E = {(A,B), (A,C), (B,C), (B,D), (C,D), (C,E), (D,E), (D,F), (E,F)}, which represents nine connections or links between pairs of vertices, noting that the order of vertices in each edge pair is irrelevant since this appears to be an undirected graph.

### a) The graph would be drawn if I had time but describing it is taking too long already

---

[Problems 4-6 either incomplete or missing]
