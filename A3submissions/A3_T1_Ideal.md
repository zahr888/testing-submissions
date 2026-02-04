# Assignment A3: Problem-Solving and Logic Assessment
**Student Name:** Jessica Chang
**Student ID:** 2024-CS-3174
**Date:** March 17, 2026

---

## Problem 1: Set Theory (20 points)

Let U = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
Let A = {1, 2, 3, 4, 5}
Let B = {4, 5, 6, 7, 8}
Let C = {2, 4, 6, 8, 10}

### a) A ∪ (B ∩ C) (5 points)

First, find B ∩ C:
B ∩ C = {4, 5, 6, 7, 8} ∩ {2, 4, 6, 8, 10}
B ∩ C = {4, 6, 8}

Then, find A ∪ (B ∩ C):
A ∪ (B ∩ C) = {1, 2, 3, 4, 5} ∪ {4, 6, 8}
A ∪ (B ∩ C) = {1, 2, 3, 4, 5, 6, 8}

### b) (A - B) ∪ C (5 points)

First, find A - B (elements in A but not in B):
A - B = {1, 2, 3, 4, 5} - {4, 5, 6, 7, 8}
A - B = {1, 2, 3}

Then, find (A - B) ∪ C:
(A - B) ∪ C = {1, 2, 3} ∪ {2, 4, 6, 8, 10}
(A - B) ∪ C = {1, 2, 3, 4, 6, 8, 10}

### c) A' ∩ B' (5 points)

First, find A' (complement of A in U):
A' = U - A = {6, 7, 8, 9, 10}

Then, find B' (complement of B in U):
B' = U - B = {1, 2, 3, 9, 10}

Now, find A' ∩ B':
A' ∩ B' = {6, 7, 8, 9, 10} ∩ {1, 2, 3, 9, 10}
A' ∩ B' = {9, 10}

### d) Venn Diagram (5 points)

```
        U
    ___________
   |           |
   |  A     B  |
   | 1,2    7  |
   |  3\  /    |
   |    4,5    |
   |    \|/6,8 |
   |     C     |
   |     10    |
   |     9     |
   |___________|

Regions:
- Only A: {1, 2, 3}
- Only B: {7}
- Only C: {10}
- A ∩ B only: {5}
- A ∩ C only: {2}
- B ∩ C only: {6, 8}
- A ∩ B ∩ C: {4}
- Outside all: {9}
```

---

## Problem 2: Logic and Propositional Calculus (25 points)

### Part A: Truth Table for (p → q) ∧ (¬q ∨ r) (10 points)

| p | q | r | p → q | ¬q | ¬q ∨ r | (p → q) ∧ (¬q ∨ r) |
|---|---|---|-------|----|---------|--------------------|
| T | T | T |   T   | F  |    T    |         T          |
| T | T | F |   T   | F  |    F    |         F          |
| T | F | T |   F   | T  |    T    |         F          |
| T | F | F |   F   | T  |    T    |         F          |
| F | T | T |   T   | F  |    T    |         T          |
| F | T | F |   T   | F  |    F    |         F          |
| F | F | T |   T   | T  |    T    |         T          |
| F | F | F |   T   | T  |    T    |         T          |

### Part B: Prove or disprove (p → q) ∧ (q → r) ≡ p → r (10 points)

**This statement is FALSE (not a logical equivalence).**

**Counterexample:**
Let p = F, q = F, r = F

Left side: (p → q) ∧ (q → r)
- p → q = F → F = T
- q → r = F → F = T
- (p → q) ∧ (q → r) = T ∧ T = T

Right side: p → r
- p → r = F → F = T

Let's try another: p = T, q = F, r = T

Left side: (p → q) ∧ (q → r)
- p → q = T → F = F
- q → r = F → T = T
- (p → q) ∧ (q → r) = F ∧ T = F

Right side: p → r
- p → r = T → T = T

Since we get F ≠ T, the equivalence does not hold.

**Truth table verification:**

| p | q | r | p→q | q→r | (p→q)∧(q→r) | p→r | Equivalent? |
|---|---|---|-----|-----|-------------|-----|-------------|
| T | T | T |  T  |  T  |      T      |  T  |     ✓       |
| T | T | F |  T  |  F  |      F      |  F  |     ✓       |
| T | F | T |  F  |  T  |      F      |  T  |     ✗       |
| T | F | F |  F  |  T  |      F      |  F  |     ✓       |
| F | T | T |  T  |  T  |      T      |  T  |     ✓       |
| F | T | F |  T  |  F  |      F      |  T  |     ✗       |
| F | F | T |  T  |  T  |      T      |  T  |     ✓       |
| F | F | F |  T  |  T  |      T      |  T  |     ✓       |

The equivalence fails in rows 3 and 6, so they are NOT logically equivalent.

### Part C: Convert to propositional logic (5 points)

**Statement:** "If it is raining, then the ground is wet, and if the ground is not wet, then it is not raining."

Let:
- p = "It is raining"
- q = "The ground is wet"

**Propositional form:**
(p → q) ∧ (¬q → ¬p)

**Note:** The second part (¬q → ¬p) is actually the contrapositive of the first part (p → q), so this statement is a tautology. The entire expression is equivalent to just (p → q).

---

## Problem 3: Graph Theory (20 points)

Given: V = {A, B, C, D, E, F}
E = {(A,B), (A,C), (B,C), (B,D), (C,D), (C,E), (D,E), (D,F), (E,F)}

### a) Draw the graph (5 points)

```
    A -------- B
    |        / |
    |      /   |
    |    /     |
    |  /       |
    C -------- D -------- F
     \        / \        /
      \      /   \      /
       \    /     \    /
        \  /       \  /
         E ---------
```

### b) Determine if Eulerian, Semi-Eulerian, or neither (7 points)

**Check vertex degrees:**
- deg(A) = 2 (connects to B, C)
- deg(B) = 3 (connects to A, C, D)
- deg(C) = 4 (connects to A, B, D, E)
- deg(D) = 4 (connects to B, C, E, F)
- deg(E) = 3 (connects to C, D, F)
- deg(F) = 2 (connects to D, E)

**Eulerian Path/Circuit conditions:**
- Eulerian Circuit: All vertices have even degree
- Semi-Eulerian (Eulerian Path but not circuit): Exactly 2 vertices have odd degree
- Neither: More than 2 vertices have odd degree

**Analysis:**
Vertices with odd degree: B (degree 3) and E (degree 3)
Exactly 2 vertices have odd degree.

**Conclusion:** The graph is **Semi-Eulerian**. It has an Eulerian path but not an Eulerian circuit. The path must start at one odd-degree vertex (B or E) and end at the other.

### c) Find a Hamiltonian path or prove none exists (8 points)

**A Hamiltonian path visits each vertex exactly once.**

One possible Hamiltonian path:
**A → B → D → F → E → C**

Verification:
- Start at A
- A → B (edge exists) ✓
- B → D (edge exists) ✓
- D → F (edge exists) ✓
- F → E (edge exists) ✓
- E → C (edge exists) ✓
- All vertices visited exactly once ✓

Alternative paths also exist:
- A → C → E → F → D → B
- B → A → C → D → F → E
- F → D → B → C → A (then can't reach E, so incomplete)

**Answer:** A Hamiltonian path exists. One example is A → B → D → F → E → C.

---

## Problem 4: Combinatorics (20 points)

### Part A: Committee with exactly 3 women (8 points)

**Given:** 8 men, 6 women, committee of 5 people with exactly 3 women

This means we need 3 women and 2 men.

Number of ways = C(6, 3) × C(8, 2)

Calculate C(6, 3):
C(6, 3) = 6!/(3! × 3!) = (6 × 5 × 4)/(3 × 2 × 1) = 120/6 = 20

Calculate C(8, 2):
C(8, 2) = 8!/(2! × 6!) = (8 × 7)/2 = 56/2 = 28

Total ways = 20 × 28 = **560 different committees**

### Part B: 4-digit PIN codes (7 points)

**Conditions:**
- First digit must be even (0, 2, 4, 6, 8) → 5 choices
- No digit can be repeated
- Last digit must be odd (1, 3, 5, 7, 9) → 5 choices

**Step-by-step:**
1. Choose first digit (even): 5 choices
2. Choose last digit (odd): 5 choices
3. Choose second digit (any remaining): 10 - 2 = 8 choices
4. Choose third digit (any remaining): 10 - 3 = 7 choices

Total PINs = 5 × 5 × 8 × 7 = **1,400 different PIN codes**

### Part C: Arrangements of "MATHEMATICS" (5 points)

**Letters in MATHEMATICS:**
M - appears 2 times
A - appears 2 times
T - appears 2 times
H - appears 1 time
E - appears 1 time
I - appears 1 time
C - appears 1 time
S - appears 1 time

Total: 11 letters

Formula for permutations with repetition:
n!/(n₁! × n₂! × ... × nₖ!)

Number of arrangements = 11!/(2! × 2! × 2! × 1! × 1! × 1! × 1! × 1!)

= 39,916,800/(2 × 2 × 2)
= 39,916,800/8
= **4,989,600 different arrangements**

---

## Problem 5: Proof by Induction (15 points)

**Prove:** 1 + 2 + 3 + ... + n = n(n+1)/2 for all integers n ≥ 1

**Base Case:** n = 1

Left side: 1
Right side: 1(1+1)/2 = 1(2)/2 = 1

1 = 1 ✓ Base case holds.

**Inductive Hypothesis:**

Assume the formula holds for n = k, where k ≥ 1:
1 + 2 + 3 + ... + k = k(k+1)/2

**Inductive Step:**

We must prove the formula holds for n = k+1:
1 + 2 + 3 + ... + k + (k+1) = (k+1)(k+2)/2

Starting with the left side:
1 + 2 + 3 + ... + k + (k+1)

By the inductive hypothesis:
= k(k+1)/2 + (k+1)

Factor out (k+1):
= (k+1)[k/2 + 1]

Get common denominator:
= (k+1)[k/2 + 2/2]

Simplify:
= (k+1)[(k+2)/2]

= (k+1)(k+2)/2

This matches the formula for n = k+1.

**Conclusion:**

By the principle of mathematical induction, since:
1. The base case (n=1) is true
2. The inductive step proves that if the formula is true for n=k, then it's true for n=k+1

We conclude that 1 + 2 + 3 + ... + n = n(n+1)/2 for all integers n ≥ 1. ∎

---

## Problem 6: Relations and Functions (20 points)

### Part A: Analyze relation R (10 points)

Given: A = {1, 2, 3, 4}
R = {(1,1), (1,2), (2,1), (2,2), (3,3), (3,4), (4,3), (4,4)}

**Reflexive:** A relation is reflexive if (a,a) ∈ R for all a ∈ A.

Check: (1,1)✓, (2,2)✓, (3,3)✓, (4,4)✓

**Answer: R is reflexive.**

**Symmetric:** A relation is symmetric if (a,b) ∈ R implies (b,a) ∈ R.

Check pairs:
- (1,2) ∈ R and (2,1) ∈ R ✓
- (3,4) ∈ R and (4,3) ∈ R ✓
- All self-pairs are symmetric by definition ✓

**Answer: R is symmetric.**

**Transitive:** A relation is transitive if (a,b) ∈ R and (b,c) ∈ R implies (a,c) ∈ R.

Check:
- (1,2) and (2,1) → need (1,1) ✓ (present)
- (1,2) and (2,2) → need (1,2) ✓ (present)
- (2,1) and (1,1) → need (2,1) ✓ (present)
- (2,1) and (1,2) → need (2,2) ✓ (present)
- (3,4) and (4,3) → need (3,3) ✓ (present)
- (3,4) and (4,4) → need (3,4) ✓ (present)
- (4,3) and (3,3) → need (4,3) ✓ (present)
- (4,3) and (3,4) → need (4,4) ✓ (present)

**Answer: R is transitive.**

**Equivalence Relation:** A relation is an equivalence relation if it is reflexive, symmetric, and transitive.

**Answer: R is an equivalence relation** because it satisfies all three properties.

### Part B: Analyze function f(x) = 3x - 5 (10 points)

Function: f: ℤ → ℤ defined by f(x) = 3x - 5

**Injective (One-to-one):** A function is injective if f(a) = f(b) implies a = b.

Proof:
Assume f(a) = f(b)
Then 3a - 5 = 3b - 5
Adding 5 to both sides: 3a = 3b
Dividing by 3: a = b

Since f(a) = f(b) implies a = b, the function is injective.

**Answer: f is injective (one-to-one).**

**Surjective (Onto):** A function f: ℤ → ℤ is surjective if for every y ∈ ℤ, there exists x ∈ ℤ such that f(x) = y.

For f to be surjective, we need to show that for any integer y, we can find an integer x such that 3x - 5 = y.

Solving for x: 3x = y + 5, so x = (y + 5)/3

For x to be an integer, (y + 5) must be divisible by 3.

**Counterexample:** Let y = 1
Then x = (1 + 5)/3 = 6/3 = 2 ✓ (works)

Let y = 2
Then x = (2 + 5)/3 = 7/3 = 2.333... ✗ (not an integer)

Since there exist integers in the codomain (like y = 2) that have no pre-image in the domain, f is not surjective.

**Answer: f is not surjective (not onto).**

**Conclusion:** The function f(x) = 3x - 5 is **injective but not surjective**, therefore it is **not bijective**.

---
