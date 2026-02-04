# Assignment A6: Mixed Assignment - Database Management System
**Student Name:** Kyle Stevens
**Student ID:** 2024-CS-8134
**Date:** March 23, 2026

---

## Part 1: Theoretical Questions

### Question 1
INNER JOIN = matching rows. LEFT JOIN = all from left. RIGHT JOIN = all from right. FULL JOIN = all from both.

### Question 2
Normalization = reduce redundancy. 1NF = atomic values. 2NF = no partial dependencies. 3NF = no transitive dependencies.

### Question 3
ACID = Atomicity, Consistency, Isolation, Durability.

---

## Part 2: SQL Queries

### Query 1
```sql
SELECT name, SUM(total_amount) FROM Customers JOIN Orders GROUP BY customer_id LIMIT 5;
```

### Query 2
```sql
SELECT * FROM Products WHERE product_id NOT IN (SELECT product_id FROM OrderDetails);
```

### Query 3
```sql
SELECT MONTH(order_date), SUM(total_amount) FROM Orders WHERE YEAR(order_date)=2025 GROUP BY MONTH(order_date);
```

### Query 4
```sql
SELECT name FROM Customers WHERE customer_id IN (SELECT customer_id FROM Orders);
```

---

## Part 3: Stored Procedures

```sql
CREATE PROCEDURE ProcessOrder() BEGIN SELECT 'Done'; END;
```

---

## Part 4: Optimization

Add indexes.

---
