# Assignment A3: Problem-Solving and Logic Assessment
**Student Name:** Robert Kim
**Student ID:** 2024-CS-4829
**Date:** March 18, 2026

---

## Problem 1: Set Theory (20 points)

### a) A ∪ (B ∩ C)

B ∩ C = {4, 6, 8}
A ∪ (B ∩ C) = {1, 2, 3, 4, 5, 6, 8}

### b) (A - B) ∪ C

A - B = {1, 2, 3}
(A - B) ∪ C = {1, 2, 3, 4, 6, 8, 10}

### c) A' ∩ B'

A' = {6, 7, 8, 9, 10}
B' = {1, 2, 3, 9, 10}
A' ∩ B' = {9, 10}

### d) Venn Diagram

```
The three circles overlap with:
- A contains {1,2,3,4,5}
- B contains {4,5,6,7,8}
- C contains {2,4,6,8,10}
- Intersection regions show shared elements
```

---

## Problem 2: Logic and Propositional Calculus (25 points)

### Part A: Truth Table

| p | q | r | p→q | ¬q | ¬q∨r | (p→q)∧(¬q∨r) |
|---|---|---|-----|-------|------|--------------|
| T | T | T |  T  |  F    |  T   |      T       |
| T | T | F |  T  |  F    |  F   |      F       |
| T | F | T |  F  |  T    |  T   |      F       |
| T | F | F |  F  |  T    |  T   |      F       |
| F | T | T |  T  |  F    |  T   |      T       |
| F | T | F |  T  |  F    |  F   |      F       |
| F | F | T |  T  |  T    |  T   |      T       |
| F | F | F |  T  |  T    |  T   |      T       |

### Part B: Logical Equivalence

Testing (p → q) ∧ (q → r) ≡ p → r

When p=T, q=F, r=T:
- Left: (T→F) ∧ (F→T) = F ∧ T = F
- Right: T→T = T
- F ≠ T

They are NOT equivalent.

### Part C: Propositional Logic

Let p = "it is raining", q = "the ground is wet"

(p → q) ∧ (¬q → ¬p)

---

## Problem 3: Graph Theory (20 points)

### a) Graph drawing

```
A--B--D--F
|\/|\/|\/|
|/\|/\|/\|
C--E------
```

### b) Eulerian check

Vertex degrees: A=2, B=3, C=4, D=4, E=3, F=2

Two vertices have odd degree (B and E), so the graph is Semi-Eulerian.

### c) Hamiltonian path

One Hamiltonian path: A → B → D → F → E → C

---

## Problem 4: Combinatorics (20 points)

### Part A

C(6,3) × C(8,2) = 20 × 28 = 560

### Part B

First digit (even): 5 choices
Last digit (odd): 5 choices
Second digit: 8 remaining
Third digit: 7 remaining

Total: 5 × 5 × 8 × 7 = 1400

### Part C

MATHEMATICS has 11 letters with M, A, T each appearing twice.

11!/(2!×2!×2!) = 39,916,800/8 = 4,989,600

---

## Problem 5: Proof by Induction (15 points)

**Base case:** n=1
1 = 1(2)/2 = 1 ✓

**Inductive hypothesis:** Assume true for n=k
1+2+...+k = k(k+1)/2

**Inductive step:** Prove for n=k+1
1+2+...+k+(k+1) = k(k+1)/2 + (k+1)
= (k+1)[k/2 + 1]
= (k+1)(k+2)/2 ✓

By induction, the formula holds for all n≥1.

---

## Problem 6: Relations and Functions (20 points)

### Part A

- Reflexive: Yes, all (a,a) pairs present
- Symmetric: Yes, if (a,b) then (b,a)
- Transitive: Yes, checked all combinations
- Equivalence relation: Yes

### Part B

f(x) = 3x - 5 from ℤ to ℤ

**Injective:** f(a)=f(b) → 3a-5=3b-5 → a=b ✓

**Surjective:** For y=2, need x=(2+5)/3=7/3 (not an integer) ✗

Function is injective but not surjective.
