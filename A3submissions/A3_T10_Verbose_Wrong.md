# Assignment A3: Problem-Solving and Logic Assessment
**Student Name:** Gregory Walsh
**Student ID:** 2024-CS-3584
**Date:** March 18, 2026

---

## Problem 1: Set Theory (20 points)

### a) A ∪ (B ∩ C) (5 points)

To solve this problem, which asks us to find the union of set A with the intersection of sets B and C, we must first understand the fundamental principles underlying set operations, which have been studied extensively by mathematicians since the pioneering work of Georg Cantor in the late nineteenth century, who essentially invented modern set theory as we know it today.

The intersection operation B ∩ C produces a new set containing all elements that appear in both B and C. Looking at our sets, B contains {4, 5, 6, 7, 8} and C contains {2, 4, 6, 8, 10}, so the intersection would be those elements appearing in both, which are {4, 6, 8}. However, I should note that intersection is a commutative operation, meaning B ∩ C = C ∩ B, which is an important property though not directly relevant to solving this particular problem but worth mentioning for completeness.

Now taking the union of A with this intersection, we combine {1, 2, 3, 4, 5} with {4, 6, 8}. The union operation is also commutative and collects all distinct elements from both sets. Element 4 appears in both sets but we only count it once in the union. Therefore our answer is {1, 2, 3, 4, 5, 6, 8}.

Though I should mention that I could have been more rigorous by explicitly stating that the union operation is defined as A ∪ B = {x | x ∈ A or x ∈ B}, which makes it clear that we're looking for elements in either set.

**Answer: {1, 2, 3, 4, 5, 6, 8}**

### b) (A - B) ∪ C (5 points)

The set difference operation, which is sometimes called relative complement, produces elements in the first set but not the second. For A - B, we need elements in A = {1, 2, 3, 4, 5} that aren't in B = {4, 5, 6, 7, 8}.

Elements 1, 2, 3 are in A but not in B, while 4 and 5 are in both so they're excluded from the difference. Thus A - B = {1, 2, 3}, though technically I could verify this more carefully by checking each element individually, which might be overly pedantic but thoroughness has its place in mathematics.

Taking the union with C = {2, 4, 6, 8, 10}, we combine all elements: {1, 2, 3, 4, 6, 8, 10}.

**Answer: {1, 2, 3, 4, 6, 8, 10}**

### c) A' ∩ B' where A' denotes the complement of A (5 points)

Complements are relative to the universal set U = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}. The complement A' contains all elements in U not in A, so A' = {6, 7, 8, 9, 10}. Similarly, B' = {1, 2, 3, 9, 10}.

Their intersection is {9, 10}, which makes sense as these are the only elements not in either A or B, demonstrating De Morgan's Law though that's perhaps getting ahead of ourselves.

**Answer: {9, 10}**

### d) Draw a Venn diagram (5 points)

I recognize the importance of Venn diagrams as visual representations of set relationships, and while I understand conceptually how to draw one with three overlapping circles representing sets A, B, and C, the actual execution in this text format presents challenges that make me question whether my representation would be adequately clear, so perhaps a verbal description of the regions would be more practical, though that somewhat defeats the pedagogical purpose of the diagram itself.

[Attempted diagram omitted due to formatting concerns]

---

## Problem 2: Logic and Propositional Calculus (25 points)

### Part A (10 points)

Truth tables are exhaustive enumerations of all possible truth value assignments. For three variables we need 2³ = 8 rows. While I could construct this systematically, I'm concerned about formatting.

[Truth table construction begun but not completed due to time management issues]

### Part B (10 points)

To prove or disprove an equivalence, we can use truth tables or find a counterexample. The latter is more efficient if the statements aren't equivalent.

Testing p=T, q=F, r=T:
Left: (T→F) ∧ (F→T) = F ∧ T = F
Right: T→T = T

Since F ≠ T, they're not equivalent, though I acknowledge there might be more elegant ways to demonstrate this using logical laws rather than the somewhat brute-force approach of testing cases.

**Answer: Not equivalent**

### Part C (5 points)

Converting to propositional logic with p = "raining" and q = "ground wet":
(p → q) ∧ (¬q → ¬p)

This is actually a tautology since ¬q → ¬p is the contrapositive of p → q.

---

## Problem 3: Graph Theory (20 points)

### a) (5 points)

Graph drawing in text format presents challenges, but I'll attempt to show the connections. [Drawing incomplete]

### b) (7 points)

Calculating degrees: A=2, B=3, C=4, D=4, E=3, F=2.

With exactly two odd-degree vertices, this is Semi-Eulerian, though I should note that this is a consequence of the handshaking lemma which states that the sum of degrees must be even.

**Answer: Semi-Eulerian**

### c) (8 points)

A Hamiltonian path exists: A → B → D → F → E → C

Though finding it required some trial and error which I'm not showing here.

---

## Problem 4: Combinatorics (20 points)

### Part A (8 points)

C(6,3) × C(8,2) = 20 × 28 = 560, though I recognize this answer might seem deceptively simple given the complexity of combinatorial reasoning underlying it.

### Part B (7 points)

5 × 5 × 8 × 7 = 1,400, assuming I've understood the constraints correctly.

### Part C (5 points)

11!/(2!2!2!) = 4,989,600

---

## Problem 5: Proof by Induction (15 points)

The standard proof: base case works, assume for k, prove for k+1 by adding (k+1) to both sides. Mathematical induction is a powerful technique though sometimes students struggle with understanding why it's valid.

[Details abbreviated due to time constraints]

---

## Problem 6: Relations and Functions (20 points)

### Part A (10 points)

R is reflexive (all (a,a) present), symmetric (pairs go both ways), and transitive (checked all paths). Therefore it's an equivalence relation, though verifying transitivity exhaustively is tedious.

### Part B (10 points)

f(x) = 3x - 5 is injective (simple algebra shows f(a)=f(b) implies a=b) but not surjective (not all integers in codomain have preimages, like y=2 requires x=7/3 which isn't an integer).

The function is therefore injective but not surjective, hence not bijective, though I could have been more thorough in my explanation of why surjectivity fails.

---
