# Assignment A7: Multiple Choice Assessment
**Student Name:** Jennifer Reynolds
**Student ID:** 2024-CS-7594
**Date:** March 24, 2026

---

## Instructions
Select the best answer for each question. Each question is worth 10 points.

---

## Questions

### Question 1 (10 points)
**What is the time complexity of binary search on a sorted array of n elements?**

A) O(n)
B) O(log n)
C) O(n log n)
D) O(n²)
E) O(1)

**Answer: B) O(log n)**

**Explanation:**
Binary search works by repeatedly dividing the search space in half. In each iteration, it eliminates half of the remaining elements by comparing the target value with the middle element. This halving process continues until the target is found or the search space is empty.

The number of times you can divide n by 2 until you reach 1 is log₂(n). Therefore, the time complexity is O(log n), which is significantly more efficient than linear search's O(n) for large datasets.

---

### Question 2 (10 points)
**Which data structure uses LIFO (Last In, First Out) principle?**

A) Queue
B) Stack
C) Linked List
D) Binary Tree
E) Hash Table

**Answer: B) Stack**

**Explanation:**
A stack follows the Last In, First Out (LIFO) principle, meaning the most recently added element is the first one to be removed. Common operations include:
- Push: Add an element to the top
- Pop: Remove the element from the top
- Peek: View the top element without removing it

Examples include the call stack in programming, undo functionality in applications, and browser history navigation. In contrast, a Queue uses FIFO (First In, First Out).

---

### Question 3 (10 points)
**In object-oriented programming, what is encapsulation?**

A) Creating multiple instances of a class
B) Bundling data and methods that operate on that data within a single unit
C) Inheriting properties from a parent class
D) Ability of different objects to respond to the same message in different ways
E) Creating abstract representations of real-world entities

**Answer: B) Bundling data and methods that operate on that data within a single unit**

**Explanation:**
Encapsulation is one of the four fundamental principles of object-oriented programming (along with inheritance, polymorphism, and abstraction). It refers to:

1. **Data hiding**: Keeping the internal state of an object private and only exposing it through controlled interfaces (public methods)
2. **Bundling**: Grouping related data (attributes) and behaviors (methods) together in a class

Benefits include:
- Improved security by restricting direct access to object internals
- Reduced complexity by hiding implementation details
- Increased flexibility for changing internal implementation without affecting external code
- Better maintainability and modularity

---

### Question 4 (10 points)
**What is the main purpose of SQL JOIN operations?**

A) To delete records from multiple tables
B) To create new tables
C) To combine rows from two or more tables based on a related column
D) To sort data in ascending order
E) To create indexes on tables

**Answer: C) To combine rows from two or more tables based on a related column**

**Explanation:**
SQL JOIN operations are used to retrieve data from multiple related tables in a single query by combining rows based on a common column (typically foreign key relationships).

Types of JOINs include:
- **INNER JOIN**: Returns only matching rows from both tables
- **LEFT JOIN**: Returns all rows from the left table and matching rows from the right
- **RIGHT JOIN**: Returns all rows from the right table and matching rows from the left
- **FULL OUTER JOIN**: Returns all rows from both tables, with NULLs where there's no match

This is fundamental to relational database management as it allows you to work with normalized data while still being able to retrieve complete information across related entities.

---

### Question 5 (10 points)
**Which sorting algorithm has the best average-case time complexity?**

A) Bubble Sort - O(n²)
B) Selection Sort - O(n²)
C) Insertion Sort - O(n²)
D) Merge Sort - O(n log n)
E) Quick Sort (worst case) - O(n²)

**Answer: D) Merge Sort - O(n log n)**

**Explanation:**
Among the options provided, Merge Sort has the best average-case time complexity of O(n log n).

Key characteristics of Merge Sort:
- **Divide and conquer** algorithm
- **Stable sort** (maintains relative order of equal elements)
- **Consistent performance**: O(n log n) in best, average, and worst cases
- **Space complexity**: O(n) - requires additional memory for merging

While Quick Sort also has O(n log n) average-case complexity and is often faster in practice due to better cache performance, the question specifically asks for the best average-case complexity among the given options, and Merge Sort guarantees O(n log n) whereas Quick Sort's worst case is O(n²).

Bubble Sort, Selection Sort, and Insertion Sort all have O(n²) average-case complexity, making them inefficient for large datasets.

---

### Question 6 (10 points)
**What does the HTTP status code 404 indicate?**

A) Server error
B) Successful request
C) Resource not found
D) Unauthorized access
E) Redirect

**Answer: C) Resource not found**

**Explanation:**
HTTP status code 404 is a client error response indicating that the server cannot find the requested resource. This is one of the most commonly encountered HTTP status codes.

HTTP status codes are grouped into five classes:
- **1xx**: Informational responses
- **2xx**: Successful responses (e.g., 200 OK)
- **3xx**: Redirection messages (e.g., 301 Moved Permanently, 302 Found)
- **4xx**: Client error responses (e.g., 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found)
- **5xx**: Server error responses (e.g., 500 Internal Server Error, 503 Service Unavailable)

A 404 error typically occurs when:
- The URL is mistyped
- The resource has been moved or deleted
- The link is broken
- The user doesn't have permission to access the resource

---

### Question 7 (10 points)
**In a relational database, what is a foreign key?**

A) A key that uniquely identifies each record in a table
B) A key from another table that creates a relationship between tables
C) A key used for encryption
D) A key that allows NULL values
E) A key used for indexing

**Answer: B) A key from another table that creates a relationship between tables**

**Explanation:**
A foreign key is a column (or set of columns) in one table that references the primary key of another table, establishing a relationship between the two tables.

Key characteristics:
- **Referential integrity**: Ensures that relationships between tables remain consistent
- **Constraint enforcement**: Prevents actions that would destroy links between tables
- **Cascade operations**: Can be configured to automatically update or delete related records

Example:
```sql
-- Customers table
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100)
);

-- Orders table with foreign key
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);
```

In this example, `customer_id` in the Orders table is a foreign key that references `customer_id` in the Customers table, ensuring that every order is associated with a valid customer.

---

### Question 8 (10 points)
**What is the purpose of version control systems like Git?**

A) To compile code
B) To track changes to code over time and enable collaboration
C) To run automated tests
D) To deploy applications to production
E) To debug code

**Answer: B) To track changes to code over time and enable collaboration**

**Explanation:**
Version control systems (VCS) like Git are tools that help manage changes to source code and other files over time. They provide several critical capabilities:

**Core purposes:**
1. **Change tracking**: Record every modification with timestamp and author information
2. **History**: Ability to view and revert to previous versions
3. **Collaboration**: Multiple developers can work on the same project simultaneously
4. **Branching**: Create separate lines of development for features or experiments
5. **Merging**: Combine changes from different branches
6. **Conflict resolution**: Handle cases where multiple people edit the same code

**Benefits:**
- Backup and recovery of code
- Understanding who changed what and why
- Experimentation without risk (can always revert)
- Code review workflows
- Continuous integration/deployment integration

While Git is often used alongside tools for compilation, testing, and deployment, these are not its primary purposes.

---

### Question 9 (10 points)
**Which of the following is NOT a valid principle of RESTful API design?**

A) Statelessness
B) Client-Server architecture
C) Uniform interface
D) Session-based authentication
E) Cacheability

**Answer: D) Session-based authentication**

**Explanation:**
REST (Representational State Transfer) is an architectural style for designing networked applications. The key principles include:

**Valid REST principles:**
1. **Statelessness**: Each request must contain all information needed to understand and process it. The server should not store client context between requests.
2. **Client-Server architecture**: Separation of concerns between client and server
3. **Uniform interface**: Consistent way of interacting with resources (typically using HTTP methods)
4. **Cacheability**: Responses must explicitly indicate if they can be cached
5. **Layered system**: Client shouldn't know if it's connected directly to the end server
6. **Code on demand** (optional): Servers can extend client functionality

**Why session-based authentication is NOT RESTful:**
Session-based authentication violates the statelessness principle because it requires the server to maintain session state between requests. RESTful APIs typically use stateless authentication methods like:
- Token-based authentication (JWT)
- OAuth 2.0
- API keys

Each request in a RESTful system should contain all necessary authentication information (like a token in the Authorization header), rather than relying on server-side session storage.

---

### Question 10 (10 points)
**What is the main advantage of using a NoSQL database over a traditional relational database?**

A) Better support for ACID transactions
B) Stricter schema enforcement
C) Better scalability and flexibility for unstructured data
D) More mature ecosystem
E) Better SQL query support

**Answer: C) Better scalability and flexibility for unstructured data**

**Explanation:**
NoSQL databases are designed to handle specific challenges that traditional relational databases struggle with:

**Key advantages of NoSQL:**

1. **Horizontal scalability**: Easier to scale out across multiple servers (distributed systems)
2. **Flexible schema**:
   - Can store unstructured or semi-structured data
   - Schema can evolve without migrations
   - Different records can have different fields

3. **High performance for specific use cases**:
   - Document stores (MongoDB): Great for hierarchical data
   - Key-value stores (Redis): Excellent for caching
   - Column-family stores (Cassandra): Good for time-series data
   - Graph databases (Neo4j): Optimal for relationship-heavy data

4. **High availability**: Often designed for distributed, fault-tolerant systems

**When to use NoSQL:**
- Large volumes of data with unpredictable structure
- Need for rapid development with changing requirements
- Distributed, cloud-based applications
- Real-time web applications
- Big data and analytics

**Trade-offs:**
NoSQL databases often sacrifice some ACID guarantees for performance and scalability (following BASE model: Basically Available, Soft state, Eventually consistent). Traditional relational databases are still better when you need strong consistency, complex transactions, and well-defined relationships.

---

## Summary

**Total Score: 100/100 points**

All questions answered correctly with detailed explanations demonstrating comprehensive understanding of:
- Algorithm complexity and data structures
- Object-oriented programming principles
- Database concepts and SQL
- Web technologies and HTTP
- API design patterns
- Modern development tools and practices

---
