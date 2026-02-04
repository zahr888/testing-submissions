# Assignment A2: Structured Q&A Assessment
**Student Name:** Emily Rodriguez
**Student ID:** 2024-CS-2847
**Date:** March 19, 2026

---

## Section 1: Short Answer Questions (40 points)

### Question 1 (10 points)
**Define Big O notation and explain its importance in algorithm analysis. Provide an example of an algorithm with O(n²) time complexity.**

Big O notation is a mathematical notation used to describe the upper bound of an algorithm's time or space complexity in terms of the input size (n). It characterizes the worst-case scenario and provides a way to compare the efficiency of different algorithms independent of hardware or implementation details.

Big O notation is important because it:
- Allows us to analyze algorithm scalability
- Helps predict performance as input size grows
- Enables comparison of different algorithmic approaches
- Identifies performance bottlenecks in code

An example of an algorithm with O(n²) time complexity is Bubble Sort. In Bubble Sort, we compare adjacent elements and swap them if they're in the wrong order, repeating this process through the array multiple times. The nested loops (one to iterate through the array, another to perform comparisons) result in approximately n × n operations, giving us O(n²) complexity.

---

### Question 2 (10 points)
**What is the difference between a stack and a queue? Give one real-world application example for each data structure.**

**Stack:**
- Follows LIFO (Last-In-First-Out) principle
- Elements are added and removed from the same end (top)
- Main operations: push (add), pop (remove), peek (view top)

**Queue:**
- Follows FIFO (First-In-First-Out) principle
- Elements are added at one end (rear) and removed from the other (front)
- Main operations: enqueue (add), dequeue (remove), front (view first)

**Real-world applications:**
- Stack: The "undo" feature in text editors uses a stack. Each action is pushed onto the stack, and pressing undo pops the most recent action.
- Queue: A printer queue manages print jobs in the order they were received. Jobs are processed FIFO, ensuring fairness.

---

### Question 3 (10 points)
**Explain the concept of recursion. What are the two essential components that every recursive function must have?**

Recursion is a programming technique where a function calls itself to solve a problem by breaking it down into smaller, similar subproblems. The function continues calling itself until it reaches a simple case that can be solved directly.

The two essential components of every recursive function are:

1. **Base Case (Termination Condition):** This is the condition that stops the recursion. It defines the simplest case that can be solved directly without further recursive calls. Without a base case, the function would call itself infinitely, causing a stack overflow.

2. **Recursive Case (Recursive Step):** This is where the function calls itself with a modified parameter that moves toward the base case. Each recursive call should work on a smaller or simpler version of the original problem.

Example: Calculating factorial(n)
- Base case: if n = 0, return 1
- Recursive case: return n × factorial(n-1)

---

### Question 4 (10 points)
**Compare and contrast arrays and linked lists. List two advantages and two disadvantages of each.**

**Arrays:**

Advantages:
1. Direct access to elements using index in O(1) time
2. Better cache locality due to contiguous memory, leading to faster iteration

Disadvantages:
1. Fixed size (in static arrays) makes resizing expensive, requiring allocation of new memory and copying
2. Insertion and deletion in the middle require shifting elements, resulting in O(n) complexity

**Linked Lists:**

Advantages:
1. Dynamic size - can grow or shrink easily without reallocation
2. Efficient insertion and deletion at known positions (O(1) if we have a pointer to the location)

Disadvantages:
1. No direct access - must traverse from head to reach an element, resulting in O(n) access time
2. Extra memory overhead for storing pointers/references in each node

---

## Section 2: Problem-Solving Questions (40 points)

### Question 5 (15 points)

**a) Show the step-by-step process of sorting this array using Bubble Sort (10 points)**

Given array: [64, 34, 25, 12, 22, 11, 90]

**Pass 1:**
- [34, 64, 25, 12, 22, 11, 90] - compared 64 and 34, swapped
- [34, 25, 64, 12, 22, 11, 90] - compared 64 and 25, swapped
- [34, 25, 12, 64, 22, 11, 90] - compared 64 and 12, swapped
- [34, 25, 12, 22, 64, 11, 90] - compared 64 and 22, swapped
- [34, 25, 12, 22, 11, 64, 90] - compared 64 and 11, swapped
- [34, 25, 12, 22, 11, 64, 90] - compared 64 and 90, no swap (90 in correct position)

**Pass 2:**
- [25, 34, 12, 22, 11, 64, 90] - swapped 34 and 25
- [25, 12, 34, 22, 11, 64, 90] - swapped 34 and 12
- [25, 12, 22, 34, 11, 64, 90] - swapped 34 and 22
- [25, 12, 22, 11, 34, 64, 90] - swapped 34 and 11 (64 in correct position)

**Pass 3:**
- [12, 25, 22, 11, 34, 64, 90] - swapped 25 and 12
- [12, 22, 25, 11, 34, 64, 90] - swapped 25 and 22
- [12, 22, 11, 25, 34, 64, 90] - swapped 25 and 11 (34 in correct position)

**Pass 4:**
- [12, 11, 22, 25, 34, 64, 90] - swapped 22 and 11 (25 in correct position)

**Pass 5:**
- [11, 12, 22, 25, 34, 64, 90] - swapped 12 and 11 (22 in correct position)

**Pass 6:**
- [11, 12, 22, 25, 34, 64, 90] - no swaps, array is sorted

**b) What is the time complexity of Bubble Sort in the worst case? (5 points)**

The time complexity of Bubble Sort in the worst case is **O(n²)**.

This occurs when the array is in reverse order. The outer loop runs n times, and for each iteration, the inner loop performs up to n comparisons. This gives us approximately n × n = n² operations, hence O(n²).

---

### Question 6 (15 points)

**a) Draw the resulting binary search tree (8 points)**

Insertion order: 50, 30, 70, 20, 40, 60, 80

```
        50
       /  \
      30   70
     / \   / \
    20 40 60 80
```

Step-by-step construction:
1. Insert 50 (root)
2. Insert 30 (30 < 50, goes left)
3. Insert 70 (70 > 50, goes right)
4. Insert 20 (20 < 50, go left; 20 < 30, goes left of 30)
5. Insert 40 (40 < 50, go left; 40 > 30, goes right of 30)
6. Insert 60 (60 > 50, go right; 60 < 70, goes left of 70)
7. Insert 80 (80 > 50, go right; 80 > 70, goes right of 70)

**b) Show the tree after deleting node 30 (7 points)**

When deleting node 30 (which has two children), we replace it with its inorder successor. The inorder successor of 30 is 40 (the smallest value in its right subtree).

```
        50
       /  \
      40   70
     /    / \
    20   60 80
```

Process:
1. Find node 30 (has two children: 20 and 40)
2. Find inorder successor: 40
3. Replace 30's value with 40's value
4. Delete the original 40 node (which has no children)
5. 20 becomes the left child of the new 40

---

### Question 7 (10 points)
**Write the pseudocode for a function that finds the maximum element in an array. Specify the time and space complexity.**

```
FUNCTION findMaximum(array):
    // Check if array is empty
    IF array.length == 0:
        RETURN error "Array is empty"

    // Initialize max with first element
    max = array[0]

    // Iterate through remaining elements
    FOR i = 1 TO array.length - 1:
        IF array[i] > max:
            max = array[i]

    RETURN max
```

**Time Complexity:** O(n)
- We must examine each element once to find the maximum
- The loop runs n times where n is the array length
- Each comparison is O(1)

**Space Complexity:** O(1)
- We only use a constant amount of extra space (the max variable and loop counter)
- Space used doesn't grow with input size

---

## Section 3: True/False with Justification (20 points)

### Question 8 (5 points)
**A hash table always provides O(1) lookup time.**

**FALSE**

Justification: While hash tables provide O(1) average-case lookup time, they do not always guarantee O(1) in all scenarios. In the worst case, when many keys hash to the same index (hash collisions), and collision resolution uses chaining, all elements might be in the same bucket, leading to O(n) lookup time where n is the number of elements. However, with a good hash function and proper load factor management, hash tables provide O(1) expected time for lookups in practice.

---

### Question 9 (5 points)
**In a balanced binary search tree, the height is always log₂(n) where n is the number of nodes.**

**TRUE**

Justification: In a balanced binary search tree (like AVL or Red-Black trees), the height is maintained to be approximately log₂(n) through balancing operations. A balanced tree ensures that the left and right subtrees of any node differ in height by at most a constant factor. This logarithmic height is crucial for maintaining O(log n) time complexity for search, insertion, and deletion operations. The base-2 logarithm comes from the binary nature of the tree - each level can have at most twice the nodes of the previous level.

---

### Question 10 (5 points)
**Depth-First Search (DFS) uses a queue data structure for traversal.**

**FALSE**

Justification: Depth-First Search uses a **stack** data structure, not a queue. DFS explores as far as possible along each branch before backtracking, which follows the LIFO (Last-In-First-Out) principle of stacks. The algorithm pushes neighbors onto the stack and pops the most recently added node, going deeper into the graph. In contrast, Breadth-First Search (BFS) uses a queue and follows FIFO (First-In-First-Out), exploring neighbors level by level. DFS can be implemented using explicit stacks or implicitly through recursion (which uses the call stack).

---

### Question 11 (5 points)
**Dynamic programming can only be applied to problems that exhibit optimal substructure.**

**FALSE**

Justification: While optimal substructure is important for dynamic programming, it is not the only requirement. Dynamic programming requires TWO properties:

1. **Optimal substructure:** An optimal solution contains optimal solutions to subproblems
2. **Overlapping subproblems:** The same subproblems are solved multiple times

A problem needs BOTH properties for dynamic programming to be applicable and beneficial. Optimal substructure alone could be solved with a greedy approach or divide-and-conquer. The overlapping subproblems property is what makes memoization or tabulation worthwhile, as we can store and reuse solutions to avoid redundant computation.

---
