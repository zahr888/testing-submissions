# Assignment A2: Structured Q&A Assessment
**Student Name:** David Park
**Student ID:** 2024-CS-3921
**Date:** March 20, 2026

---

## Section 1: Short Answer Questions (40 points)

### Question 1 (10 points)
Big O notation is used to describe how an algorithm's performance changes as the input size grows. It shows the upper bound or worst-case scenario for time or space complexity. Its important for algorithm analysis because it helps us compare different algorithms and understand which one will perform better with large inputs.

An example of O(n²) is bubble sort. It has nested loops where we compare each element with every other element, so if there's n elements, we do roughly n × n operations.

---

### Question 2 (10 points)
A stack uses LIFO (last in first out) while a queue uses FIFO (first in first out). In a stack, you add and remove from the top. In a queue, you add to the back and remove from the front.

Stack example: The back button in a web browser. Each page you visit gets added to a stack, and clicking back removes the most recent page.

Queue example: People waiting in line at a store checkout. The first person in line is served first.

---

### Question 3 (10 points)
Recursion is when a function calls itself to solve a problem. It breaks down a big problem into smaller versions of the same problem.

The two essential components are:
1. Base case - this stops the recursion so it doesn't go on forever
2. Recursive call - where the function calls itself with different parameters that get closer to the base case

For example in factorial, the base case is when n=0 return 1, and the recursive case is return n * factorial(n-1).

---

### Question 4 (10 points)
Arrays:
Advantages:
- Fast access to any element using index
- Good memory locality which makes them fast

Disadvantages:
- Fixed size (you cant easily add more elements)
- Slow to insert or delete in the middle because you have to shift elements

Linked Lists:
Advantages:
- Can easily grow or shrink in size
- Easy to insert or delete elements

Disadvantages:
- Slow to access specific elements because you have to traverse from the beginning
- Uses more memory because of the pointers

---

## Section 2: Problem-Solving Questions (40 points)

### Question 5 (15 points)

**a) Bubble sort steps:**

Original: [64, 34, 25, 12, 22, 11, 90]

Pass 1:
[34, 64, 25, 12, 22, 11, 90]
[34, 25, 64, 12, 22, 11, 90]
[34, 25, 12, 64, 22, 11, 90]
[34, 25, 12, 22, 64, 11, 90]
[34, 25, 12, 22, 11, 64, 90]

Pass 2:
[25, 34, 12, 22, 11, 64, 90]
[25, 12, 34, 22, 11, 64, 90]
[25, 12, 22, 34, 11, 64, 90]
[25, 12, 22, 11, 34, 64, 90]

Pass 3:
[12, 25, 22, 11, 34, 64, 90]
[12, 22, 25, 11, 34, 64, 90]
[12, 22, 11, 25, 34, 64, 90]

Pass 4:
[12, 11, 22, 25, 34, 64, 90]

Pass 5:
[11, 12, 22, 25, 34, 64, 90] - sorted!

**b)** The worst case time complexity is O(n²) because we have two nested loops.

---

### Question 6 (15 points)

**a) Binary search tree:**

```
        50
       /  \
      30   70
     / \   / \
    20 40 60 80
```

**b) After deleting 30:**

When we delete 30, we need to replace it with either the largest value from its left subtree or the smallest from its right subtree. I'll use 40 (smallest from right).

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
function findMax(array):
    if array is empty:
        return null

    max = array[0]

    for each element in array:
        if element > max:
            max = element

    return max
```

Time complexity: O(n) - we have to look at every element once
Space complexity: O(1) - we only use one variable for max

---

## Section 3: True/False with Justification (20 points)

### Question 8 (5 points)
**FALSE**

Hash tables usually give O(1) lookup time, but not always. If there are collisions (multiple keys hash to the same spot), it can be slower. In the worst case with many collisions, it could be O(n).

---

### Question 9 (5 points)
**TRUE**

In a balanced BST, the height is kept at log₂(n) through balancing operations. This is why operations stay fast at O(log n) even with lots of nodes.

---

### Question 10 (5 points)
**FALSE**

DFS uses a stack, not a queue. It goes deep into the graph before backtracking. BFS is the one that uses a queue.

---

### Question 11 (5 points)
**FALSE**

Dynamic programming needs both optimal substructure AND overlapping subproblems. Just having optimal substructure isn't enough. The overlapping part is what makes it worth storing solutions to reuse them.

---
