# Assignment A6: Mixed Assignment - Database Management System
**Student Name:** Gregory Walsh
**Student ID:** 2024-CS-6852
**Date:** March 23, 2026

---

## Part 1: Theoretical Questions

### Question 1
**Explain JOIN operations**

Okay, so JOINs... I think they combine tables? Or do they merge rows? I'm not entirely sure about the terminology here. Let me try to explain what I understand:

INNER JOIN is when... I think it's when both tables have to have the data? Like, if one table doesn't have it, then it doesn't show up? Or maybe it shows NULL? Actually, I'm not sure if it's INNER JOIN or LEFT JOIN that shows NULL values. This is confusing.

```sql
SELECT * FROM customers
INNER JOIN orders ON customers.id = orders.id;
-- Wait, should this be customer_id? Or just id? I always forget which column name to use
```

LEFT JOIN is... I believe it takes everything from the left table? So if I do `customers LEFT JOIN orders`, it gives me all customers even if they don't have orders? But then what's the difference between LEFT JOIN and RIGHT JOIN? Is RIGHT JOIN just doing it backwards? That seems redundant. Why would anyone use RIGHT JOIN if you could just swap the tables and use LEFT JOIN?

```sql
-- I think this is correct? Maybe?
SELECT customers.name, orders.order_id
FROM customers
LEFT JOIN orders ON customers.customer_id = orders.customer_id;
-- Or should it be OUTER LEFT JOIN? I've seen both
```

FULL OUTER JOIN - I'm pretty sure this one returns everything from both tables, but I'm not confident about when you'd actually need this. Couldn't you just use two queries and combine them? Though I guess that might be inefficient...

---

### Question 2
**Database normalization**

Normalization is about... organizing data better? I think the point is to reduce duplication, but I'm not entirely clear on why we need multiple "normal forms." Isn't one enough?

**1NF:** Each cell should have one value. So like, instead of having "Math, Physics" in one cell, you split them into separate rows. I think. Unless you're supposed to split them into separate columns? Actually, I'm second-guessing myself here.

Example (I think):
```
Before 1NF:
| Student | Courses      |
|---------|--------------|
| John    | Math,Physics |

After 1NF:
| Student | Course  |
|---------|---------|
| John    | Math    |
| John    | Physics |
```

Though now I'm wondering if this violates some other rule because we're repeating "John"...

**2NF:** This one is about partial dependencies? Or was that 3NF? I always mix these up. I think 2NF means that... if you have a composite key (which is when the primary key is made of two columns, right?), then the other columns should depend on the whole key, not just part of it?

But what if you don't have a composite key? Does 2NF not apply then? Or is it automatically satisfied?

**3NF:** This is about transitive dependencies. I remember the term but I'm fuzzy on what it actually means. I think it's when A depends on B and B depends on C, so A indirectly depends on C? And that's bad because... reasons? Maybe it causes update anomalies? I should probably know this better.

---

### Question 3
**ACID properties**

ACID is an acronym. Let me see if I can remember:

**A - Atomicity:** This means the transaction is atomic, like an atom (indivisible). So either everything happens or nothing happens. I think this is correct, though I'm not 100% sure if "atomic" in database terms means the same thing as in chemistry.

**C - Consistency:** The database stays consistent. But consistent with what? I assume it means all the rules and constraints are maintained? Like if you have a foreign key, it still points to a valid record?

**I - Isolation:** Transactions are isolated from each other. So if two transactions are running at the same time, they don't interfere? But wait, if they're completely isolated, how do they both access the database? There must be some level of sharing, right? Maybe they just can't see each other's uncommitted changes?

**D - Durability:** Once a transaction is committed, it's permanent. Even if the power goes out? That seems like a strong guarantee. How do databases ensure this? Do they write to disk immediately? Or is there some kind of log?

Example:
```sql
BEGIN TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
-- I think this demonstrates ACID? Maybe just atomicity?
```

---

## Part 2: Practical SQL Queries

### Query 1
**Top 5 customers by spending**

Okay, so I need to join Customers and Orders, then sum up the total_amount, group by customer, and limit to 5. I think that's the approach, though I'm not sure about the exact syntax:

```sql
SELECT
    c.name,
    c.email,
    SUM(o.total_amount) as total
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
-- Should I specify INNER JOIN or is JOIN the same thing?
GROUP BY c.customer_id
-- Or should I group by c.name and c.email? I always forget which columns need to be in GROUP BY
ORDER BY total DESC
LIMIT 5;
```

Wait, I'm having second thoughts about the GROUP BY. I think if I select c.name and c.email, they also need to be in the GROUP BY clause. But why? If customer_id is unique, isn't that enough? This rule always confuses me.

---

### Query 2
**Products never ordered**

This one is tricky. I need to find products that aren't in the OrderDetails table. I could use a LEFT JOIN and look for NULLs, or maybe a NOT IN subquery? Let me try the LEFT JOIN approach:

```sql
SELECT p.product_id, p.product_name
FROM Products p
LEFT JOIN OrderDetails od ON p.product_id = od.product_id
WHERE od.product_id IS NULL;
```

Actually, should I check if od.order_detail_id is NULL instead? Or does it not matter? I think any column from OrderDetails would be NULL if there's no match, so it probably doesn't matter which one I check.

Alternative approach with NOT IN (though I'm not sure if this is more or less efficient):
```sql
SELECT product_id, product_name
FROM Products
WHERE product_id NOT IN (SELECT product_id FROM OrderDetails);
-- But what if OrderDetails has NULL product_ids? Does that cause problems?
```

---

### Query 3
**Monthly sales for 2025**

I need to show all 12 months even if some have no sales. This is the tricky part. I think I need to create a list of months somehow and then LEFT JOIN the actual sales data to it.

```sql
-- How do I create a list of months? Maybe use UNION?
SELECT 1 as month
UNION SELECT 2
UNION SELECT 3
-- ... this is going to be tedious
UNION SELECT 12;
-- Actually, is there a better way to do this? Like generate_series or something?
-- I'm not sure if MySQL has that

-- Then I'd join this with actual sales:
SELECT
    months.month,
    SUM(o.total_amount) as sales
FROM (
    SELECT 1 as month UNION SELECT 2 UNION -- ... etc
) months
LEFT JOIN Orders o ON MONTH(o.order_date) = months.month
WHERE YEAR(o.order_date) = 2025
-- Wait, this WHERE clause might filter out the months with no sales
-- Should the WHERE go inside a subquery instead?
GROUP BY months.month;
```

I'm not confident this is right. The WHERE clause placement is confusing me. If I filter for YEAR = 2025 on the Orders table, it might eliminate months before they get joined to the months list... or maybe not? I need to think about this more carefully.

---

### Query 4
**Customers who ordered from 3+ categories**

I need to join Customers, Orders, OrderDetails, and Products, then count distinct categories per customer. The HAVING clause is for filtering after grouping, right?

```sql
SELECT
    c.customer_id,
    c.name,
    COUNT(DISTINCT p.category) as category_count
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
-- Do I need to worry about duplicate orders here? Probably not because of DISTINCT
JOIN OrderDetails od ON o.order_id = od.order_id
JOIN Products p ON od.product_id = p.product_id
GROUP BY c.customer_id
-- Again, should I include c.name in GROUP BY? The rules are fuzzy to me
HAVING category_count >= 3;
-- Or is it COUNT(DISTINCT p.category) >= 3? Can I use the alias here?
```

---

## Part 3: Stored Procedures

### Procedure 1
**Process Order**

Stored procedures... I haven't written many of these. Let me try:

```sql
DELIMITER //
-- I think DELIMITER is needed? Or is it just for MySQL?

CREATE PROCEDURE ProcessOrder(
    IN customer_id INT,
    IN product_id INT,
    IN quantity INT
)
BEGIN
    -- Should I declare variables first? I think so
    DECLARE stock INT;
    DECLARE price DECIMAL(10,2);

    -- Get current stock and price
    SELECT stock_quantity, price INTO stock, price
    FROM Products WHERE product_id = product_id;
    -- Wait, that's ambiguous. The parameter has the same name as the column
    -- Should I use a different name? Or prefix with p_?

    -- Check if enough stock
    IF stock >= quantity THEN
        -- Create the order
        INSERT INTO Orders (customer_id, order_date, total_amount)
        VALUES (customer_id, NOW(), price * quantity);
        -- Or should I use CURDATE() instead of NOW()?

        -- Update stock
        UPDATE Products
        SET stock_quantity = stock_quantity - quantity
        WHERE product_id = product_id;
        -- Again, naming collision here

        -- Should I also insert into OrderDetails? The question doesn't specify
        -- but it seems like I should...

        SELECT 'Order created successfully' as result;
    ELSE
        SELECT 'Insufficient stock' as result;
    END IF;

    -- Do I need error handling? Like what if the INSERT fails?
    -- I think there's something called EXCEPTION HANDLER but I don't remember the syntax
END //

DELIMITER ;
```

I'm not very confident about this procedure. The parameter naming is definitely wrong (conflicting with column names), and I'm missing error handling and probably OrderDetails insertion.

---

### Procedure 2
**Customer Summary**

This one seems simpler? Maybe just a bunch of SELECT statements?

```sql
DELIMITER //

CREATE PROCEDURE CustomerSummary(IN cust_id INT)
BEGIN
    -- Show customer info
    SELECT * FROM Customers WHERE customer_id = cust_id;
    -- Should I select specific columns? SELECT * is easier but maybe not best practice

    -- Show order summary
    SELECT
        COUNT(*) as order_count,
        SUM(total_amount) as total_spent
    FROM Orders
    WHERE customer_id = cust_id;
    -- What if the customer has no orders? Will this return NULL or 0?
    -- I think NULL, so maybe I should use COALESCE?

    -- Maybe show their most ordered products?
    SELECT p.product_name, COUNT(*) as times_ordered
    FROM Orders o
    JOIN OrderDetails od ON o.order_id = od.order_id
    JOIN Products p ON od.product_id = p.product_id
    WHERE o.customer_id = cust_id
    GROUP BY p.product_id;
    -- Or GROUP BY p.product_name? Does it matter?
END //

DELIMITER ;
```

---

## Part 4: Query Optimization

### Task 1

The original query uses old comma-separated joins which are... bad? I think modern SQL prefers explicit JOIN syntax. Also, there should be indexes on the columns being filtered.

```sql
-- Add indexes maybe?
CREATE INDEX idx_city ON Customers(city);
CREATE INDEX idx_date ON Orders(order_date);
CREATE INDEX idx_category ON Products(category);
-- But are these the right indexes? Should they be composite indexes?
-- Like INDEX(city, customer_id)? I'm not sure

-- Rewritten query
SELECT c.name, p.product_name, od.quantity
FROM Customers c
INNER JOIN Orders o ON c.customer_id = o.customer_id
INNER JOIN OrderDetails od ON o.order_id = od.order_id
INNER JOIN Products p ON od.product_id = p.product_id
WHERE c.city = 'New York'
  AND o.order_date >= '2025-01-01'
  AND p.category = 'Electronics';
```

Is this actually faster though? I mean, it's more readable, but I'm not sure if the database executes it any differently than the comma-join version. Modern query optimizers are pretty smart, right?

---

### Task 2

For optimizing large tables with date ranges and categories... I think you'd want:

1. Indexes on date_column and category_column
   - Or a composite index? (date_column, category_column)?
   - Or two separate indexes? Which is better?

2. Maybe partition the table by date range?
   - But I don't really know how partitioning works
   - Is it automatic or do you have to query specific partitions?

3. Use query caching?
   - Though I think modern databases do this automatically
   - Or is it something you have to configure?

4. Archive old data to separate tables
   - Then use UNION to query when needed
   - But that sounds complicated

I feel like I understand the concepts at a high level but I'm not confident about the implementation details. How do you actually decide when to use composite indexes vs. separate indexes? And does partitioning really help that much?

---

## Conclusion

I've attempted all the questions but I'm not very confident in many of my answers. The theoretical concepts make sense when I read about them, but when I try to apply them I second-guess myself. SQL syntax is also confusing with all the different options (LEFT JOIN vs LEFT OUTER JOIN, JOIN vs INNER JOIN, etc.). I probably should have practiced more before attempting this assignment.

---
