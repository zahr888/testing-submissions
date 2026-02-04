# Assignment A2: Structured Q&A Assessment
**Student Name:** Carlos Ramirez
**Student ID:** 2024-CS-1847
**Date:** March 20, 2026

---

## Section 1: Short Answer Questions (40 points)

### Question 1 (10 points)
Big O notation est une notation mathématique qui describe the performance d'un algorithme. It's importante porque helps us compare different algorithms.

Un exemple de O(n²) es Bubble Sort. Cela se produit when we have dos bucles anidados, uno dentro del otro.

---

### Question 2 (10 points)
Une stack utilise LIFO (Last In First Out). A queue usa FIFO (First In First Out).

Real-world exemples:
- Stack: El botón "deshacer" en editores de texto uses une pile para trackear actions
- Queue: Une ligne d'attente at the bank where el primer person in line est served first

---

### Question 3 (10 points)
La recursión est quand une fonction calls itself para resolver un problème. C'est comme regarder dans un miroir qui reflète another mirror.

Les deux componentes esenciales sont:
1. Base case - c'est la condición that stops la recursión
2. Recursive case - où la fonction se llama a sí misma con diferentes parametres

Por ejemplo, para calcular factorial(5), nous appelons factorial(4), which llama factorial(3), et ainsi de suite hasta que llegamos au base case.

---

### Question 4 (10 points)
**Arrays:**

Avantages:
- Accès rápido aux elements usando index - O(1) temps
- Bonne localité de mémoire for iteración

Desventajas:
- Taille fixe - difficult de change la size
- Insertion y suppression en el milieu requiere déplacer elements - O(n)

**Listas enlazadas:**

Advantages:
- Tamaño dinámico - peuvent grandir or shrink facilmente
- Inserción eficiente when tenemos el pointeur

Disadvantages:
- Pas de acceso aleatorio - debe traverser depuis le début
- Plus de memoria overhead por los pointers

---

## Section 2: Problem-Solving Questions (40 points)

### Question 5 (15 points)

**a) Bubble Sort paso por paso:**

Array inicial: [64, 34, 25, 12, 22, 11, 90]

Premier passage:
- Comparar 64 et 34: swap → [34, 64, 25, 12, 22, 11, 90]
- Compare 64 y 25: intercambiar → [34, 25, 64, 12, 22, 11, 90]
- 64 et 12: swap → [34, 25, 12, 64, 22, 11, 90]
- 64 y 22: échanger → [34, 25, 12, 22, 64, 11, 90]
- 64 and 11: swap → [34, 25, 12, 22, 11, 64, 90]
- 64 et 90: no swap → [34, 25, 12, 22, 11, 64, 90]

Deuxième passage:
- 34 y 25: swap → [25, 34, 12, 22, 11, 64, 90]
- 34 et 12: échanger → [25, 12, 34, 22, 11, 64, 90]
- 34 and 22: swap → [25, 12, 22, 34, 11, 64, 90]
- 34 y 11: intercambiar → [25, 12, 22, 11, 34, 64, 90]

Troisième paso:
- 25 et 12: swap → [12, 25, 22, 11, 34, 64, 90]
- 25 y 22: échanger → [12, 22, 25, 11, 34, 64, 90]
- 25 and 11: swap → [12, 22, 11, 25, 34, 64, 90]

Cuarto passage:
- 22 et 11: échanger → [12, 11, 22, 25, 34, 64, 90]

Quinto paso:
- 12 y 11: swap → [11, 12, 22, 25, 34, 64, 90]

Maintenant c'est trié!

**b)** La complejidad en el worst case est O(n²) porque tenemos deux nested loops.

---

### Question 6 (15 points)

**a) Árbol de búsqueda binaria:**

Ordre d'insertion: 50, 30, 70, 20, 40, 60, 80

```
        50
       /  \
      30   70
     / \   / \
    20 40 60 80
```

**b) Après supprimer 30:**

When nous eliminamos un noeud avec deux enfants, reemplazamos it avec son inorder successor (el más pequeño node dans le right subtree).

El successor de 30 est 40.

```
        50
       /  \
      40   70
     /    / \
    20   60 80
```

---

### Question 7 (10 points)

```
FUNCIÓN encontrarMaximo(array):
    SI array est vide:
        RETORNAR error

    max = array[0]

    PARA cada elemento en array:
        SI elemento > max:
            max = elemento

    RETOURNER max
```

**Complejidad temporal:** O(n) - debemos examinar chaque élément une fois
**Complexité spatiale:** O(1) - sólo usamos une variable para el max

---

## Section 3: True/False with Justification (20 points)

### Question 8 (5 points)
**FALSO / FAUX**

Les hash tables généralement provide O(1) lookup pero not always. En cas de muchas colisiones, donde plusieurs clés hash al mismo bucket, el lookup puede être O(n) en el worst case.

---

### Question 9 (5 points)
**VERDADERO / TRUE**

Dans un balanced BST, la hauteur se mantiene en approximately log₂(n) through balancing operaciones. C'est pourquoi les opérations stay O(log n).

---

### Question 10 (5 points)
**FALSE / FALSO**

DFS utiliza une stack, pas une queue. Il va profond dans le graphe antes de backtracking. BFS est celui qui uses una cola.

---

### Question 11 (5 points)
**FAUX / FALSE**

Dynamic programming necesita BOTH optimal substructure ET overlapping subproblemas. Sólo avoir optimal substructure n'est pas suficiente. Los overlapping subproblemas est ce qui rend le memoization útil.

---
