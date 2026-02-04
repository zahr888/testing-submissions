# Assignment A6: Mixed Assignment - Database Management System
**Student Name:** Daniel Martinez
**Student ID:** 2024-CS-7491
**Date:** March 23, 2026

---

## Part 1: Theoretical Questions (25 points)

### Question 1
**Explain the differences between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN with examples.**

INNER JOIN returns only matching rows from both tables. LEFT JOIN returns all rows from left table and matching from right. RIGHT JOIN is opposite of LEFT JOIN. FULL OUTER JOIN returns all rows from both tables.

Examples:
```sql
-- INNER JOIN
SELECT * FROM customers c
INNER JOIN orders o ON c.id = o.customer_id;

-- LEFT JOIN
SELECT * FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id;
```

---

### Question 2
**What is database normalization? Explain 1NF, 2NF, and 3NF.**

Normalization is organizing data to reduce redundancy.

- 1NF: No repeating groups, atomic values
- 2NF: In 1NF + no partial dependencies
- 3NF: In 2NF + no transitive dependencies

Example:
A table with multiple phone numbers in one column violates 1NF. Split them into separate rows.

---

### Question 3
**Explain ACID properties.**

- Atomicity: All or nothing
- Consistency: Database stays valid
- Isolation: Transactions don't interfere
- Durability: Changes are permanent

Example: In a bank transfer, both debit and credit must happen or neither happens (atomicity).

---

## Part 2: Practical SQL Queries (40 points)

### Query 1
**Top 5 customers by spending**

```sql
SELECT c.name, c.email, SUM(o.total_amount) as total
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id
ORDER BY total DESC
LIMIT 5;
```

---

### Query 2
**Products never ordered**

```sql
SELECT p.product_id, p.product_name
FROM Products p
LEFT JOIN OrderDetails od ON p.product_id = od.product_id
WHERE od.product_id IS NULL;
```

---

### Query 3
**Monthly sales for 2025**

```sql
SELECT
    MONTH(order_date) as month,
    SUM(total_amount) as sales
FROM Orders
WHERE YEAR(order_date) = 2025
GROUP BY MONTH(order_date)
ORDER BY month;
```

Note: This doesn't show months with zero sales but should work for most cases.

---

### Query 4
**Customers who ordered from 3+ categories**

```sql
SELECT c.name, COUNT(DISTINCT p.category) as categories
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
JOIN OrderDetails od ON o.order_id = od.order_id
JOIN Products p ON od.product_id = p.product_id
GROUP BY c.customer_id
HAVING categories >= 3;
```

---

## Part 3: Stored Procedures (20 points)

### Procedure 1
**Process a new order**

```sql
DELIMITER //
CREATE PROCEDURE ProcessOrder(
    IN customer_id INT,
    IN product_id INT,
    IN quantity INT
)
BEGIN
    DECLARE stock INT;
    DECLARE price DECIMAL(10,2);

    SELECT stock_quantity, price INTO stock, price
    FROM Products WHERE product_id = product_id;

    IF stock >= quantity THEN
        INSERT INTO Orders (customer_id, order_date, total_amount)
        VALUES (customer_id, NOW(), price * quantity);

        UPDATE Products
        SET stock_quantity = stock_quantity - quantity
        WHERE product_id = product_id;

        SELECT 'Order created' as message;
    ELSE
        SELECT 'Insufficient stock' as message;
    END IF;
END //
DELIMITER ;
```

---

### Procedure 2
**Customer purchase summary**

```sql
DELIMITER //
CREATE PROCEDURE CustomerSummary(IN cust_id INT)
BEGIN
    SELECT
        c.name,
        COUNT(o.order_id) as total_orders,
        SUM(o.total_amount) as total_spent
    FROM Customers c
    LEFT JOIN Orders o ON c.customer_id = o.customer_id
    WHERE c.customer_id = cust_id
    GROUP BY c.customer_id;
END //
DELIMITER ;
```

---

## Part 4: Query Optimization (15 points)

### Optimization Task 1

Original query uses old-style joins which are harder to read and optimize.

Improvements:
- Use modern JOIN syntax
- Add indexes on frequently queried columns
- Filter early in the query

```sql
CREATE INDEX idx_city ON Customers(city);
CREATE INDEX idx_date ON Orders(order_date);
CREATE INDEX idx_category ON Products(category);

SELECT c.name, p.product_name, od.quantity
FROM Customers c
INNER JOIN Orders o ON c.customer_id = o.customer_id
INNER JOIN OrderDetails od ON o.order_id = od.order_id
INNER JOIN Products p ON od.product_id = p.product_id
WHERE c.city = 'New York'
AND o.order_date >= '2025-01-01'
AND p.category = 'Electronics';
```

---

### Optimization Task 2

For large tables with date range queries:

1. Add indexes on date and category columns
2. Use partitioning by date if table is very large
3. Consider archiving old data
4. Use query caching for frequently accessed ranges
5. Make sure statistics are up to date

```sql
CREATE INDEX idx_date_cat ON table_name(date_column, category_column);
```

---
