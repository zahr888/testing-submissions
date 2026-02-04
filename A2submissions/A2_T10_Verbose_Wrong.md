# Assignment A2: Structured Q&A Assessment
**Student Name:** Michael Patterson
**Student ID:** 2024-CS-2593
**Date:** March 20, 2026

---

## Section 1: Short Answer Questions (40 points)

### Question 1 (10 points)
**Define Big O notation and explain its importance in algorithm analysis. Provide an example of an algorithm with O(n²) time complexity.**

Big O notation, which is sometimes referred to as "Big Oh notation" in informal discussions among computer scientists and software engineers, is a mathematical notation that is used extensively throughout the field of computer science, particularly in the subdisciplines of algorithm analysis and computational complexity theory, to describe and characterize the limiting behavior of functions when the argument tends toward a particular value or toward infinity, though in the specific context of algorithm analysis where we are most concerned with understanding and predicting how algorithms will perform as the size of their input data grows larger and larger, Big O notation is primarily employed to classify algorithms according to how their running time or space requirements grow as a function of the input size, providing us with a standardized framework for discussing algorithmic efficiency that abstracts away from implementation details and hardware-specific considerations to focus on the fundamental growth rate characteristics.

The importance of Big O notation in algorithm analysis, which cannot be overstated given its ubiquitous presence in computer science education, technical interviews, software engineering discourse, and academic research, stems from several key factors that make it an indispensable tool in the modern computer scientist's toolkit. First and foremost, Big O notation provides a machine-independent way to characterize algorithm performance, meaning that when we say an algorithm is O(n log n), this classification holds true regardless of whether the algorithm is implemented in Python, Java, C++, or any other programming language, and regardless of whether it runs on a high-end server, a modest laptop, a mobile device, or any other computing platform, because we're describing the fundamental growth characteristics rather than absolute performance measurements that would vary with these factors.

Secondly, and equally importantly, Big O notation helps us make informed decisions when selecting between different algorithmic approaches to solve the same problem, as it allows us to predict how each algorithm will scale as our data grows from small test cases to production-scale datasets that might contain millions or billions of elements, which is crucial because an algorithm that seems perfectly adequate when tested on a small dataset with a few dozen elements might become completely impractical when applied to real-world data volumes. For instance, the difference between an O(n²) algorithm and an O(n log n) algorithm might be negligible when n equals 100, but when n reaches one million, the O(n²) algorithm could take literally days to complete while the O(n log n) algorithm finishes in seconds or minutes, making this distinction not just academically interesting but practically critical for building usable systems.

Thirdly, Big O notation facilitates communication and collaboration among software developers and computer scientists by providing a common vocabulary and conceptual framework that everyone in the field understands, so when one engineer tells another that a particular operation in their codebase is O(1), or that a certain query against their database is O(n), these statements convey precise technical meaning that guides decisions about whether optimization is needed, what the likely bottlenecks are, and how the system will behave under different load conditions.

An example of an algorithm with O(n²) time complexity, which is to say an algorithm whose running time grows proportionally to the square of its input size, is the Bubble Sort algorithm, which is a simple but inefficient sorting algorithm that is primarily of pedagogical value rather than practical utility given its poor performance characteristics compared to more sophisticated sorting algorithms like Quick Sort, Merge Sort, or Heap Sort, but which nevertheless serves as an excellent illustration of quadratic time complexity because its nested loop structure makes the O(n²) behavior transparent and easy to understand even for beginners who are just learning about algorithm analysis.

Bubble Sort works through a very straightforward process where it repeatedly steps through the list of elements to be sorted, comparing each pair of adjacent items and swapping them if they are in the wrong order according to the desired ordering, and this process of passing through the list is repeated over and over again until no more swaps are needed, which indicates that the list has become fully sorted. The reason this algorithm exhibits O(n²) time complexity is that in the worst case scenario, where the input array is sorted in reverse order compared to how we want it sorted, the algorithm must make approximately n passes through the array (where n is the number of elements), and during each pass, it performs up to n-1 comparisons, giving us roughly n multiplied by n operations, which simplifies to n² operations, and even though the exact number of operations is actually n(n-1)/2, which expands to (n² - n)/2, when we apply Big O notation we drop the constant factors like the division by 2 and we drop the lower-order terms like the -n, leaving us with simply O(n²) as our classification.

---

### Question 2 (10 points)
**What is the difference between a stack and a queue? Give one real-world application example for each data structure.**

Stacks and queues are both linear data structures but differ in their access principles. Stack uses LIFO while queue uses FIFO.

Stack application: Browser history. Each page visited is like pushing onto a stack, and the back button pops pages off.

Queue application: Print queue manages print jobs.

However, I should note that there are many other differences I could discuss at length regarding memory allocation, implementation variations, performance characteristics, and theoretical foundations, but I'll keep this concise as requested by the question format.

---

### Question 3 (10 points)
**Explain the concept of recursion. What are the two essential components that every recursive function must have?**

Recursion is a technique where a function solves a problem by calling itself.

Two components:
1. Base case - stops recursion
2. Recursive case - function calls itself with modified parameters

---

### Question 4 (10 points)
**Compare and contrast arrays and linked lists. List two advantages and two disadvantages of each.**

I believe this question deserves a nuanced answer that recognizes the complexity of comparing these data structures, but I'll try to be concise.

**Arrays:**
- Advantage 1: O(1) access time
- Advantage 2: Cache-friendly due to contiguous memory
- Disadvantage 1: Fixed size makes them inflexible
- Disadvantage 2: O(n) for insertions/deletions in middle

**Linked Lists:**
- Advantage 1: Dynamic size is more flexible
- Advantage 2: O(1) insertion/deletion with pointer
- Disadvantage 1: O(n) access time is problematic
- Disadvantage 2: Extra memory for pointers is wasteful

---

## Section 2: Problem-Solving Questions (40 points)

### Question 5 (15 points)

**a) Show the step-by-step process of sorting this array using Bubble Sort (10 points)**

While I understand this question asks for step-by-step details, I think it's more important to understand the conceptual approach rather than mechanically writing out every single comparison, but I'll provide the work:

[64, 34, 25, 12, 22, 11, 90]

Pass 1: [34, 25, 12, 22, 11, 64, 90]
Pass 2: [25, 12, 22, 11, 34, 64, 90]
Pass 3: [12, 22, 11, 25, 34, 64, 90]
Pass 4: [12, 11, 22, 25, 34, 64, 90]
Pass 5: [11, 12, 22, 25, 34, 64, 90]

I've simplified this by showing the array state after each pass rather than after each individual comparison, which I believe demonstrates understanding of the algorithm's behavior more efficiently than exhaustively listing every swap.

**b) What is the time complexity of Bubble Sort in the worst case? (5 points)**

O(n²) due to nested loops.

---

### Question 6 (15 points)

**a) Draw the resulting binary search tree (8 points)**

The tree structure after inserting 50, 30, 70, 20, 40, 60, 80 would form a perfectly balanced tree, which is actually quite fortuitous given the insertion order:

```
        50
       /  \
      30   70
     / \   / \
    20 40 60 80
```

**b) Show the tree after deleting node 30 (7 points)**

When deleting a node with two children, we must replace it with its inorder successor (smallest value in right subtree):

```
        50
       /  \
      40   70
     /    / \
    20   60 80
```

Though I should mention there are alternative deletion strategies like using the inorder predecessor, but this answer follows the standard approach.

---

### Question 7 (10 points)
**Write the pseudocode for a function that finds the maximum element in an array. Specify the time and space complexity.**

While I personally believe that pseudocode is somewhat arbitrary and varies between authors, here's my interpretation:

```
FUNCTION find_maximum(array):
    max_value = array[0]
    FOR each element in array:
        IF element > max_value:
            max_value = element
    RETURN max_value
```

Time: O(n) - must examine all elements
Space: O(1) - constant extra space

Though technically if we're being pedantic about the analysis, there are edge cases like empty arrays that this pseudocode doesn't handle, but I assume the question implies valid input.

---

## Section 3: True/False with Justification (20 points)

### Question 8 (5 points)
**A hash table always provides O(1) lookup time.**

**FALSE**

While hash tables typically provide O(1) average-case performance, the word "always" makes this statement false since collisions can degrade performance to O(n) in pathological cases, though admittedly with a good hash function this is unlikely in practice.

---

### Question 9 (5 points)
**In a balanced binary search tree, the height is always log₂(n) where n is the number of nodes.**

**TRUE**

Though I'd argue the question should say "approximately" log₂(n) since depending on the specific balancing criteria of different balanced tree variants (AVL, Red-Black, etc.), the exact height might vary slightly, but for all practical purposes this statement is correct.

---

### Question 10 (5 points)
**Depth-First Search (DFS) uses a queue data structure for traversal.**

**FALSE**

DFS uses a stack (either explicit or via recursion's call stack). BFS is the one that uses a queue, which many students confuse.

---

### Question 11 (5 points)
**Dynamic programming can only be applied to problems that exhibit optimal substructure.**

**FALSE**

DP requires both optimal substructure AND overlapping subproblems. Having just one property isn't sufficient, though I suppose one could argue about edge cases and theoretical scenarios where this might not be strictly true in all interpretations.

---
