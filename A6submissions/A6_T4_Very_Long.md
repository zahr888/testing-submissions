# Assignment A6: Mixed Assignment - Database Management System
**Student Name:** Amanda Richardson
**Student ID:** 2024-CS-9267
**Date:** March 23, 2026

---

## Part 1: Theoretical Questions (25 points)

### Question 1: Comprehensive Analysis of SQL JOIN Operations

**Historical Context and Theoretical Foundation:**

The concept of JOIN operations in relational databases dates back to E.F. Codd's groundbreaking work on the relational model in 1970. Dr. Codd, working at IBM's San Jose Research Laboratory, published his seminal paper "A Relational Model of Data for Large Shared Data Banks" in the Communications of the ACM, fundamentally transforming how we think about data organization and retrieval. Before the relational model, databases were primarily hierarchical or network-based, which required programmers to understand the physical storage structure of data—a significant limitation that Codd's work elegantly addressed.

The relational algebra that underlies SQL JOIN operations is rooted in set theory, a branch of mathematical logic developed in the late 19th century by Georg Cantor. Set theory provides the mathematical foundation for understanding how collections of data (relations or tables, in database terminology) can be combined, filtered, and manipulated. The JOIN operation specifically implements the Cartesian product concept from set theory, but with additional filtering conditions that make it practical for real-world database applications.

When we discuss JOIN operations, we must first understand that a relational database table (or relation, to use the formal terminology from relational algebra) is essentially a set of tuples (rows) that share a common structure defined by attributes (columns). Each tuple represents a single entity or relationship in the domain being modeled, and the attributes represent the properties of that entity. The power of the relational model lies in its ability to express complex relationships between entities through the simple mechanism of shared attribute values—what we commonly call foreign keys referencing primary keys.

**INNER JOIN: The Foundation of Relational Queries**

The INNER JOIN, sometimes simply called JOIN, represents the most fundamental type of join operation in SQL. It implements what mathematicians call an "inner join" or "equijoin" in relational algebra, though the SQL syntax is more forgiving and allows for more complex join conditions than simple equality.

At its core, an INNER JOIN creates a result set that includes only those combinations of rows from both input tables where the join condition evaluates to TRUE. This is equivalent to taking the Cartesian product of the two tables (every possible combination of rows) and then filtering to keep only those combinations that satisfy the join predicate. However, modern database query optimizers are sophisticated enough to avoid actually computing the full Cartesian product, instead using various algorithms like nested loop joins, hash joins, or sort-merge joins depending on the characteristics of the data and available indexes.

The semantic interpretation of an INNER JOIN is that it represents an AND operation in logic: a row appears in the result if and only if it exists in the first table AND a matching row exists in the second table AND the join condition is satisfied. This makes INNER JOINs particularly useful when you need to find associations between entities where both entities must exist.

Consider the philosophical implications of this: an INNER JOIN essentially asks "What are the relationships that actually exist?" It ignores potential relationships where one side is missing. In a database of customers and orders, an INNER JOIN between these tables answers the question "Which customers have placed orders?" but tells us nothing about customers who haven't ordered or orders that somehow lack customer information (though the latter would typically violate referential integrity constraints).

From a performance perspective, INNER JOINs are generally the most efficient type of join because they allow the query optimizer the most freedom in choosing execution strategies. The optimizer can choose to scan either table first, can use indexes on either side of the join, and can even reorder multiple joins to find the most efficient execution plan. This is why database administrators and developers often prefer to restructure queries to use INNER JOINs when possible, as they tend to perform better than OUTER JOINs.

**Example of INNER JOIN with Extended Commentary:**

```sql
SELECT
    orders.order_id,
    orders.order_date,
    customers.customer_name,
    customers.email,
    customers.phone
FROM
    orders
    INNER JOIN customers ON orders.customer_id = customers.customer_id
WHERE
    orders.order_date >= '2025-01-01'
    AND orders.status = 'Completed';
```

In this example, we can observe several important aspects. First, we're qualifying column names with their table names (orders.order_id, customers.customer_name) which is considered best practice in production code as it makes the query more readable and prevents ambiguity if both tables happen to have columns with the same name. Some developers prefer to use table aliases (like 'o' for orders and 'c' for customers) to make the query more concise, though this can reduce readability if the aliases aren't intuitive.

The join condition `orders.customer_id = customers.customer_id` represents an equijoin—the most common type of join condition. This assumes that the orders table has a foreign key column customer_id that references the primary key customer_id in the customers table. In a well-designed database, this foreign key relationship would be enforced by a FOREIGN KEY constraint, ensuring referential integrity. However, it's worth noting that the INNER JOIN operation itself doesn't require such a constraint to exist; it merely performs the join based on the condition specified.

The WHERE clause filters the result set to include only orders from 2025 onwards that have been completed. An interesting question that often arises is whether filtering conditions should go in the WHERE clause or the ON clause of the JOIN. For INNER JOINs, these are functionally equivalent—the database will produce the same result either way—but convention suggests that conditions relating to the join relationship go in the ON clause, while conditions that filter the result set go in the WHERE clause. This distinction becomes more important with OUTER JOINs, as we'll discuss later.

**LEFT JOIN (LEFT OUTER JOIN): Including the Unmatched**

The LEFT JOIN, formally known as LEFT OUTER JOIN (the "OUTER" keyword is optional in most SQL dialects), represents a significant conceptual shift from the INNER JOIN. Where an INNER JOIN implements a logical AND operation, a LEFT JOIN implements something more like a conditional: "Give me all rows from the left table, and include matching rows from the right table if they exist."

From a set theory perspective, a LEFT JOIN is performing something similar to a union operation, but with an asymmetric treatment of the two input sets. It preserves all elements from the left set (table) while only including elements from the right set that have a corresponding match. For elements in the left set without matches, the result still includes those rows but with NULL values for all columns from the right table.

The concept of NULL in this context is philosophically interesting. NULL in SQL doesn't mean zero or empty string—it represents the absence of a value, or more precisely, an unknown or inapplicable value. When a LEFT JOIN produces NULL values for right table columns, it's indicating that no matching row was found. This is different from finding a row where the column actually contains NULL; it's the absence of any row at all.

LEFT JOINs are particularly useful in several scenarios:

1. **Finding gaps or missing relationships**: You can find all customers who haven't placed orders by looking for NULL values in the order columns after a LEFT JOIN.

2. **Preserving primary entity data**: When you want to list all entities from a primary table (like customers) but also include related data when available (like their orders), without excluding customers just because they have no orders.

3. **Generating reports with optional details**: Business reports often need to show all entries from a master table (like all products) while including additional information that might not exist for every entry (like sales figures).

**Example with Extended Analysis:**

```sql
SELECT
    customers.customer_id,
    customers.customer_name,
    customers.registration_date,
    COUNT(orders.order_id) AS order_count,
    COALESCE(SUM(orders.total_amount), 0) AS lifetime_value
FROM
    customers
    LEFT JOIN orders ON customers.customer_id = orders.customer_id
GROUP BY
    customers.customer_id,
    customers.customer_name,
    customers.registration_date
ORDER BY
    lifetime_value DESC;
```

This query demonstrates several sophisticated techniques. First, it uses COUNT on orders.order_id rather than COUNT(*). This is significant because COUNT(*) counts all rows, including those with NULL values, while COUNT(column) counts only non-NULL values. Since customers without orders will have NULL for orders.order_id after the LEFT JOIN, using COUNT(orders.order_id) correctly gives us 0 for customers with no orders.

The COALESCE function is another crucial element. COALESCE takes a list of expressions and returns the first non-NULL value. In this case, if a customer has no orders, SUM(orders.total_amount) would be NULL, but COALESCE converts that to 0, giving us a more meaningful result. This is a common pattern when working with LEFT JOINs and aggregates.

The GROUP BY clause is necessary because we're mixing aggregated functions (COUNT, SUM) with non-aggregated columns. Every non-aggregated column in the SELECT list must appear in the GROUP BY clause (in most SQL dialects). This groups all the orders for each customer together before applying the aggregate functions.

**Performance Considerations for LEFT JOINs:**

LEFT JOINs are generally more expensive than INNER JOINs from a computational perspective. The database engine must process all rows from the left table regardless of whether matches exist, and it must handle the generation of NULL values for non-matching rows. Additionally, the query optimizer has fewer options for reordering operations with LEFT JOINs because the asymmetric nature of the operation means the order of tables matters (unlike INNER JOINs where A JOIN B is equivalent to B JOIN A).

Indexes on the join columns become even more critical with LEFT JOINs. Without an index on the right table's join column, the database might have to perform a full table scan of the right table for every row in the left table—a nested loop that can be extremely slow for large tables.

**RIGHT JOIN (RIGHT OUTER JOIN): The Symmetric Alternative**

The RIGHT JOIN is the mirror image of the LEFT JOIN: it returns all rows from the right table and matching rows from the left table. Conceptually, `A LEFT JOIN B` is equivalent to `B RIGHT JOIN A`—they produce the same result set, just with columns in a different order if you use SELECT *.

In practice, RIGHT JOINs are used much less frequently than LEFT JOINs in production SQL code. This isn't because they're less capable or less efficient; it's purely a matter of convention and readability. Most SQL developers find it more natural to think about queries in a left-to-right manner, with the primary table on the left and optional related data being joined from the right.

Many SQL style guides actually recommend avoiding RIGHT JOINs entirely and rewriting them as LEFT JOINs by swapping the table order. This improves code consistency and makes queries easier to understand at a glance. However, there's no technical reason to avoid RIGHT JOINs, and in some complex queries with multiple joins, using a RIGHT JOIN might produce more readable code than restructuring everything.

**FULL OUTER JOIN: Completeness Without Bias**

The FULL OUTER JOIN (or FULL JOIN) represents the most inclusive type of join operation. It returns all rows from both tables, producing NULL values for columns from the non-matching side whenever a row from one table has no match in the other.

From a set theory perspective, a FULL OUTER JOIN is closest to a union operation, but unlike UNION which combines rows and removes duplicates, FULL OUTER JOIN preserves the relational structure by creating combinations of rows and using NULL to represent missing matches.

The use cases for FULL OUTER JOIN are more specialized than the other join types:

1. **Data synchronization and comparison**: Comparing two versions of a dataset to find what's been added, removed, or modified.

2. **Merging data from multiple sources**: When combining data from different systems where neither is the "primary" source.

3. **Gap analysis**: Finding both orphaned records (rows in table A with no match in B) and missing associations (rows in B with no match in A) in a single query.

**Implementation Note:**

It's worth noting that not all database systems support FULL OUTER JOIN natively. For example, MySQL didn't support FULL OUTER JOIN until version 8.0.14, and even then with limitations. In databases that don't support it, you can simulate a FULL OUTER JOIN by combining a LEFT JOIN and a RIGHT JOIN with UNION:

```sql
SELECT ... FROM A LEFT JOIN B ...
UNION
SELECT ... FROM A RIGHT JOIN B ...
```

However, this simulation is less efficient than a native FULL OUTER JOIN because it requires two separate join operations and a UNION operation to combine and deduplicate the results.

**Query Optimization and Join Algorithms:**

Modern database management systems employ several different algorithms for executing joins, and understanding these can help you write more efficient queries:

1. **Nested Loop Join**: The simplest conceptually—for each row in the outer table, scan the inner table looking for matches. This can be efficient for small tables or when the inner table has an index on the join column.

2. **Hash Join**: Build a hash table on one of the inputs (typically the smaller one), then probe it with rows from the other input. Very efficient for equijoins when neither input is particularly small.

3. **Sort-Merge Join**: Sort both inputs on the join key, then merge them together. Efficient when inputs are already sorted or when the sort operation is cheap.

The query optimizer chooses which algorithm to use based on statistics about the tables (row counts, value distributions), available indexes, and the type of join operation. You can sometimes see which algorithm is being used by examining the query execution plan with EXPLAIN or similar commands.

[The student continues with several more pages of historical context, theoretical discussion of relational algebra, philosophical implications of NULL values, and extended commentary on join algorithms, but never actually gets to completing the practical examples or the rest of the assignment...]

---

## Part 2: Practical SQL Queries

### Query 1: Top 5 Customers by Spending

Before I write the actual query, I think it's important to discuss the various approaches one could take to this problem...

[Assignment continues but never completes any actual queries...]

---
