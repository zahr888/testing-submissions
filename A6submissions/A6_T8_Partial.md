# Assignment A6: Mixed Assignment - Database Management System
**Student Name:** Nathan Brooks
**Student ID:** 2024-CS-4938
**Date:** March 23, 2026

---

## Part 1: Theoretical Questions (25 points)

### Question 1 (8 points)
**Explain the differences between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN with examples.**

**Answer:**

**INNER JOIN:**
Returns only rows where there's a match in both tables.

```sql
SELECT customers.name, orders.order_id
FROM customers
INNER JOIN orders ON customers.customer_id = orders.customer_id;
```

This returns customers who have placed orders.

**LEFT JOIN:**
Returns all rows from the left table and matching rows from the right table. Non-matching rows from the right table show NULL values.

```sql
SELECT customers.name, orders.order_id
FROM customers
LEFT JOIN orders ON customers.customer_id = orders.customer_id;
```

This returns all customers, including those without orders.

**RIGHT JOIN:**
Returns all rows from the right table and matching rows from the left table.

```sql
SELECT customers.name, orders.order_id
FROM customers
RIGHT JOIN orders ON customers.customer_id = orders.customer_id;
```

**FULL OUTER JOIN:**
Returns all rows from both tables, with NULL values where there's no match.

```sql
SELECT customers.name, orders.order_id
FROM customers
FULL OUTER JOIN orders ON customers.customer_id = orders.customer_id;
```

---

### Question 2 (9 points)
**What is database normalization? Explain 1NF, 2NF, and 3NF with examples.**

**Answer:**

Database normalization is the process of organizing database tables to minimize redundancy and dependency.

**1NF (First Normal Form):**
- Each cell contains atomic values
- Each row is unique
- No repeating groups

Example violation:
```
Students
| ID | Name  | Courses           |
|----|-------|-------------------|
| 1  | John  | Math, Physics     |
```

Corrected:
```
Students
| ID | Name  | Course   |
|----|-------|----------|
| 1  | John  | Math     |
| 1  | John  | Physics  |
```

**2NF (Second Normal Form):**
- Must be in 1NF
- No partial dependencies on composite keys

Example violation with composite key (StudentID, CourseID):
```
Enrollment
| StudentID | CourseID | StudentName | CourseName |
|-----------|----------|-------------|------------|
| 1         | 101      | John        | Math       |
```

StudentName depends only on StudentID, not the full key.

Corrected:
```
Students                Courses                 Enrollment
| StudentID | Name |   | CourseID | Name |    | StudentID | CourseID |
|-----------|------|   |----------|------|    |-----------|----------|
```

**3NF (Third Normal Form):**
- Must be in 2NF
- No transitive dependencies

Example violation:
```
Employee
| EmpID | Name  | DeptID | DeptName    |
|-------|-------|--------|-------------|
| 1     | Alice | 10     | Sales       |
```

DeptName depends on DeptID, which depends on EmpID (transitive).

Corrected:
```
Employee                     Department
| EmpID | Name  | DeptID | | DeptID | DeptName |
|-------|-------|--------|
```

---

### Question 3 (8 points)
**Explain ACID properties in database transactions with real-world examples.**

**Answer:**

**Atomicity:**
A transaction is treated as a single unit—either all operations succeed or all fail.

Example: Bank transfer
```sql
BEGIN TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;
COMMIT;
```

If the second UPDATE fails, the first is rolled back.

**Consistency:**
Transactions must leave the database in a valid state, maintaining all constraints and rules.

Example: If there's a constraint that account balances cannot be negative, any transaction attempting to create a negative balance will be rejected.

**Isolation:**
Concurrent transactions execute independently without interfering with each other.

Example: Two users booking the last seat on a flight. Isolation ensures only one succeeds, preventing double-booking.

**Durability:**
Once committed, changes persist even after system failure.

Example: After an order confirmation, the order record remains in the database even if the server crashes immediately after.

---

## Part 2: Practical SQL Queries (40 points)

### Query 1 (10 points)
**Write a query to find the top 5 customers who have spent the most money.**

```sql
SELECT
    c.name,
    c.email,
    SUM(o.total_amount) AS total_spent
FROM
    Customers c
    INNER JOIN Orders o ON c.customer_id = o.customer_id
WHERE
    o.status = 'Completed'
GROUP BY
    c.customer_id, c.name, c.email
ORDER BY
    total_spent DESC
LIMIT 5;
```

---

### Query 2 (10 points)
**Write a query to find products that have never been ordered.**

```sql
SELECT
    p.product_id,
    p.product_name,
    p.category,
    p.price
FROM
    Products p
    LEFT JOIN OrderDetails od ON p.product_id = od.product_id
WHERE
    od.product_id IS NULL;
```

---

### Query 3 (10 points)
**Write a query to show monthly sales totals for 2025, including months with zero sales.**

```sql
WITH RECURSIVE Months AS (
    SELECT 1 AS month
    UNION ALL
    SELECT month + 1 FROM Months WHERE month < 12
),
MonthlySales AS (
    SELECT
        MONTH(order_date) AS month,
        SUM(total_amount) AS total_sales
    FROM Orders
    WHERE YEAR(order_date) = 2025
      AND status = 'Completed'
    GROUP BY MONTH(order_date)
)
SELECT
    m.month,
    COALESCE(ms.total_sales, 0) AS total_sales
FROM Months m
LEFT JOIN MonthlySales ms ON m.month = ms.month
ORDER BY m.month;
```

---

### Query 4 (10 points)
**Write a query to find customers who have ordered products from at least 3 different categories.**

```sql
SELECT
    c.customer_id,
    c.name,
    c.email,
    COUNT(DISTINCT p.category) AS category_count
FROM
    Customers c
    INNER JOIN Orders o ON c.customer_id = o.customer_id
    INNER JOIN OrderDetails od ON o.order_id = od.order_id
    INNER JOIN Products p ON od.product_id = p.product_id
GROUP BY
    c.customer_id, c.name, c.email
HAVING
    COUNT(DISTINCT p.category) >= 3
ORDER BY
    category_count DESC;
```

---

## Part 3: Stored Procedures (20 points)

### Procedure 1 (10 points)
**Create a stored procedure to process a new order.**

```sql
DELIMITER //

CREATE PROCEDURE ProcessOrder(
    IN p_customer_id INT,
    IN p_product_id INT,
    IN p_quantity INT,
    OUT p_order_id INT,
    OUT p_message VARCHAR(255)
)
BEGIN
    DECLARE v_stock INT;
    DECLARE v_price DECIMAL(10, 2);
    DECLARE EXIT HANDLER FOR SQLEXCEPTION
    BEGIN
        ROLLBACK;
        SET p_message = 'Error: Transaction failed';
        SET p_order_id = NULL;
    END;

    START TRANSACTION;

    -- Check if customer exists
    IF NOT EXISTS (SELECT 1 FROM Customers WHERE customer_id = p_customer_id) THEN
        SET p_message = 'Error: Customer not found';
        SET p_order_id = NULL;
        ROLLBACK;
    ELSE
        -- Get product info
        SELECT stock_quantity, price INTO v_stock, v_price
        FROM Products
        WHERE product_id = p_product_id;

        -- Check stock
        IF v_stock < p_quantity THEN
            SET p_message = 'Error: Insufficient stock';
            SET p_order_id = NULL;
            ROLLBACK;
        ELSE
            -- Create order
            INSERT INTO Orders (customer_id, order_date, total_amount, status)
            VALUES (p_customer_id, CURDATE(), v_price * p_quantity, 'Pending');

            SET p_order_id = LAST_INSERT_ID();

            -- Add order details
            INSERT INTO OrderDetails (order_id, product_id, quantity, unit_price)
            VALUES (p_order_id, p_product_id, p_quantity, v_price);

            -- Update stock
            UPDATE Products
            SET stock_quantity = stock_quantity - p_quantity
            WHERE product_id = p_product_id;

            -- Update order status
            UPDATE Orders
            SET status = 'Completed'
            WHERE order_id = p_order_id;

            SET p_message = 'Success: Order processed';
            COMMIT;
        END IF;
    END IF;
END //

DELIMITER ;
```

---

### Procedure 2 (10 points)
**Create a stored procedure to generate a customer purchase summary.**

```sql
DELIMITER //

CREATE PROCEDURE GetCustomerSummary(
    IN p_customer_id INT,
    IN p_start_date DATE,
    IN p_end_date DATE
)
BEGIN
    -- Customer info
    SELECT
        customer_id,
        name,
        email,
        city
    FROM Customers
    WHERE customer_id = p_customer_id;

    -- Purchase statistics
    SELECT
        COUNT(o.order_id) AS total_orders,
        SUM(o.total_amount) AS total_spent,
        AVG(o.total_amount) AS avg_order,
        MIN(o.order_date) AS first_order,
        MAX(o.order_date) AS last_order
    FROM Orders o
    WHERE o.customer_id = p_customer_id
      AND o.order_date BETWEEN p_start_date AND p_end_date
      AND o.status = 'Completed';

    -- Category breakdown
    SELECT
        p.category,
        COUNT(DISTINCT od.product_id) AS products,
        SUM(od.quantity) AS total_qty,
        SUM(od.quantity * od.unit_price) AS spending
    FROM Orders o
        INNER JOIN OrderDetails od ON o.order_id = od.order_id
        INNER JOIN Products p ON od.product_id = p.product_id
    WHERE o.customer_id = p_customer_id
      AND o.order_date BETWEEN p_start_date AND p_end_date
