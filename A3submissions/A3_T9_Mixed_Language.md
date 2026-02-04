# Assignment A3: Problem-Solving and Logic Assessment
**Student Name:** Isabel Martinez
**Student ID:** 2024-CS-2741
**Date:** March 18, 2026

---

## Problem 1: Set Theory (20 points)

### a) A ∪ (B ∩ C)

Primero, encontramos B ∩ C:
B ∩ C = {4, 6, 8}

Luego, A ∪ (B ∩ C) = {1, 2, 3, 4, 5, 6, 8}

### b) (A - B) ∪ C

A - B = {1, 2, 3}
(A - B) ∪ C = {1, 2, 3, 4, 6, 8, 10}

### c) A' ∩ B'

Le complément de A est A' = {6, 7, 8, 9, 10}
Le complément de B est B' = {1, 2, 3, 9, 10}
A' ∩ B' = {9, 10}

### d) Venn Diagram

[Diagram showing tres círculos que se superponen]

---

## Problem 2: Logic and Propositional Calculus (25 points)

### Part A: Truth Table pour (p → q) ∧ (¬q ∨ r)

| p | q | r | p→q | ¬q | ¬q∨r | Resultado |
|---|---|---|-----|-------|------|-----------|
| V | V | V |  V  |  F    |  V   |     V     |
| V | V | F |  V  |  F    |  F   |     F     |
| V | F | V |  F  |  V    |  V   |     F     |
| V | F | F |  F  |  V    |  V   |     F     |
| F | V | V |  V  |  F    |  V   |     V     |
| F | V | F |  V  |  F    |  F   |     F     |
| F | F | V |  V  |  V    |  V   |     V     |
| F | F | F |  V  |  V    |  V   |     V     |

### Part B: Prove or disprove

Para probar si (p → q) ∧ (q → r) ≡ p → r, nous cherchons un contre-exemple.

When p=T, q=F, r=T:
- Côté gauche: (V→F) ∧ (F→V) = F ∧ V = F
- Right side: V→V = V

F ≠ V, donc they are NOT equivalent.

### Part C: Propositional Logic

Sea p = "está lloviendo", q = "le sol est mouillé"

La déclaration es: (p → q) ∧ (¬q → ¬p)

---

## Problem 3: Graph Theory (20 points)

### a) Dibujar el grafo

```
    A -------- B
    |        / |
    |      /   |
    C ------- D -------- F
     \       / \        /
      \     /   \      /
       \   /     \    /
         E -------
```

### b) Déterminer si Eulerian

Los grados de los vértices:
- deg(A) = 2
- deg(B) = 3
- deg(C) = 4
- deg(D) = 4
- deg(E) = 3
- deg(F) = 2

Hay dos vértices con degré impair (B et E).

**Réponse:** El grafo est Semi-Eulerian.

### c) Hamiltonian path

Un Hamiltonian path visite cada vértice exactement une fois.

Un chemin possible: A → B → D → F → E → C

---

## Problem 4: Combinatorics (20 points)

### Part A: Comité avec 3 mujeres

Necesitamos choisir 3 femmes de 6 et 2 hommes de 8.

C(6,3) × C(8,2) = 20 × 28 = 560

### Part B: Códigos PIN

Premier chiffre (par): 5 opciones
Dernier chiffre (impar): 5 choix
Segundo dígito: 8 restantes
Troisième chiffre: 7 remaining

Total: 5 × 5 × 8 × 7 = 1,400

### Part C: Arrangements de MATHEMATICS

MATHEMATICS tiene 11 lettres avec M, A, T chaque apareciendo 2 fois.

11!/(2!×2!×2!) = 39,916,800/8 = 4,989,600

---

## Problem 5: Proof par Induction (15 points)

**Probar:** 1 + 2 + 3 + ... + n = n(n+1)/2 pour tous n ≥ 1

**Caso base:** n = 1
1 = 1(2)/2 = 1 ✓

**Hipótesis inductiva:** Supposons que c'est vrai para n = k:
1 + 2 + ... + k = k(k+1)/2

**Paso inductivo:** Debemos probar pour n = k+1:
1 + 2 + ... + k + (k+1) = k(k+1)/2 + (k+1)
= (k+1)[k/2 + 1]
= (k+1)(k+2)/2 ✓

**Conclusión:** Par induction, la fórmula est vraie for all n ≥ 1.

---

## Problem 6: Relations et Functions (20 points)

### Part A: Analyser la relation R

R = {(1,1), (1,2), (2,1), (2,2), (3,3), (3,4), (4,3), (4,4)}

**Reflexive:** Todos los pares (a,a) están présents ✓

**Symmetric:** Si (a,b) ∈ R, entonces (b,a) ∈ R ✓
- (1,2) y (2,1) both present
- (3,4) et (4,3) both present

**Transitive:** Si (a,b) ∈ R et (b,c) ∈ R, entonces (a,c) ∈ R ✓

**Equivalence relation:** Oui, porque satisface all three properties.

### Part B: Analyser f(x) = 3x - 5

**Injective:** Si f(a) = f(b), entonces:
3a - 5 = 3b - 5
3a = 3b
a = b ✓

**Surjective:** Pour y = 2:
x = (2 + 5)/3 = 7/3 (no es un entier)

Por lo tanto, f est injective pero NOT surjective.
