# Assignment A3: Problem-Solving and Logic Assessment
**Student Name:** Nathan Brooks  
**Student ID:** 2024-CS-1963  
**Date:** March 18, 2026  

---

## Problem 1: Set Theory (20 points)

### a) A ∪ (B ∩ C) (5 points)

B ∩ C = {4, 5, 6, 7, 8} ∩ {2, 4, 6, 8, 10}
B ∩ C = {4, 6, 8}

A ∪ (B ∩ C) = {1, 2, 3, 4, 5} ∪ {4, 6, 8}
A ∪ (B ∩ C) = {1, 2, 3, 4, 5, 6, 8}

### b) (A - B) ∪ C (5 points)

A - B = {1, 2, 3, 4, 5} - {4, 5, 6, 7, 8}
A - B = {1, 2, 3}

(A - B) ∪ C = {1, 2, 3} ∪ {2, 4, 6, 8, 10}
(A - B) ∪ C = {1, 2, 3, 4, 6, 8, 10}

### c) A' ∩ B' (5 points)

A' = {6, 7, 8, 9, 10}
B' = {1, 2, 3, 9, 10}
A' ∩ B' = {9, 10}

### d) Venn Diagram (5 points)

```
[Started drawing but ran out of time]
```

---

## Problem 2: Logic and Propositional Calculus (25 points)

### Part A (10 points)

| p | q | r | p→q | ¬q | ¬q∨r | (p→q)∧(¬q∨r) |
|---|---|---|-----|-------|------|--------------|
| T | T | T |  T  |  F    |  T   |      T       |
| T | T | F |  T  |  F    |  F   |      F       |
| T | F | T |  F  |  T    |  T   |      F       |
| T | F | F |  F  |  T    |  T   |      F       |
| F | T | T |  T  |  F    |  T   |      T       |

[Table incomplete - ran out of time]

### Part B (10 points)

Testing (p → q) ∧ (q → r) ≡ p → r

Let p=T, q=F, r=T:
- Left side: (T→F) ∧ (F→T) = F ∧ T = F
- Right side: T→T = T

They're not equivalent.

### Part C (5 points)

Let p = "it is raining", q = "the ground is wet"

The statement is: (p → q) ∧ (¬q → ¬p)

---

## Problem 3: Graph Theory (20 points)

### a) Draw the graph (5 points)

```
[Started but couldn't finish the drawing properly]
A connects to B, C
B connects to A, C, D
C connects to A, B, D, E
```

### b) Determine if Eulerian (7 points)

Degrees: A=2, B=3, C=4, D=4, E=3, F=2

Two vertices have odd degree (B and E)

The graph is Semi-Eulerian.

### c) Hamiltonian path (8 points)
