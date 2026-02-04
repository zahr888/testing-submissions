# Assignment A6: Mixed Assignment - Database Management System
**Student Name:** Derek Thompson
**Student ID:** 2024-CS-2874
**Date:** March 23, 2026

---

## Part 1: Theoretical Questions

### Question 1: JOIN Operations
**Explain the differences between various JOIN types.**

**Answer:**

In the mystical realm of databases, there exist four sacred JOIN spells:

**INNER JOIN (The Matching Ritual)**
Only summons data when both tables agree to appear together. Like a blind date where both people actually show up.

```sql
SELECT ghosts.name, haunting.location
FROM ghosts
INNER JOIN haunting ON ghosts.spooky_level = haunting.fear_factor
WHERE ghosts.transparency > 0.5;
```

This query finds ghosts that are currently haunting locations based on how scary they are.

**LEFT JOIN (The "I Don't Care If You're There" Join)**
Takes everything from the left table even if the right table is being antisocial.

```sql
SELECT pizzas.name, toppings.topping_name
FROM pizzas
LEFT JOIN toppings ON pizzas.pizza_id = toppings.quantum_field_id
WHERE toppings.is_pineapple = 'controversial';
```

**RIGHT JOIN (The Backwards Join)**
Like LEFT JOIN but facing the other direction. Nobody uses this because databases prefer left-handed operations.

**FULL OUTER JOIN (The Everything Bagel)**
Returns literally everything, even the kitchen sink. Warning: may cause memory overflow and existential crises.

---

### Question 2: Normalization
**Explain database normalization forms.**

**Answer:**

Normalization is the ancient art of making your database boring and complicated:

**1NF (First Nonsense Form):**
- Each cell can only contain one thing
- No putting your entire grocery list in one column
- Atomic values only (no uranium-235 allowed)

Example:
```
BAD TABLE:
| Person | Pets                      |
|--------|---------------------------|
| Bob    | Cat, Dog, Hamster, Dragon |

GOOD TABLE:
| Person | Pet     |
|--------|---------|
| Bob    | Cat     |
| Bob    | Dog     |
| Bob    | Hamster |
| Bob    | Dragon  |
```

**2NF (Second Nonsense Form):**
Everything must depend on the whole key, not just part of it. Like making sure your cat depends on both your name AND your address, not just your name. Otherwise the cat might follow someone else named Bob.

**3NF (Third Nonsense Form):**
No transitive dependencies. This means if A depends on B and B depends on C, then A shouldn't also depend on C because that's just greedy. It's like saying "I know you through my friend, so I don't need your phone number."

---

### Question 3: ACID Properties
**Explain ACID properties in database transactions.**

**Answer:**

ACID is not the illegal kind, it's the database kind:

**Atomicity:** Either everything happens or nothing happens. Like Schrödinger's transaction—it's both committed and rolled back until you observe it.

**Consistency:** The database must always make sense. No negative bank balances (unless you're a bank, then it's called "credit"). No customers born in the year 3000. No products with negative prices (that would be paying customers to take your stuff, which is just bad business).

**Isolation:** Transactions can't see each other's underwear... I mean data. Each transaction pretends it's the only one in the database, like a narcissistic query.

**Durability:** Once committed, the data survives everything—power outages, earthquakes, zombie apocalypses, the heat death of the universe. Well, maybe not that last one.

**Example:**
```sql
BEGIN TRANSACTION;

-- Deduct money from Account A
UPDATE accounts SET balance = balance - 100 WHERE id = 'A';

-- Summon interdimensional portal
SELECT * FROM parallel_universe WHERE timeline = 'alpha';

-- Credit money to Account B (maybe)
UPDATE accounts SET balance = balance + 100 WHERE id = random();

-- Hope for the best
COMMIT MAYBE;
```

---

## Part 2: Practical SQL Queries

### Query 1: Top 5 Customers
```sql
SELECT
    c.name,
    c.email,
    SUM(o.total_amount) as money_extracted,
    COUNT(o.order_id) as times_they_trusted_us,
    AVG(o.total_amount) as average_gullibility
FROM
    Customers c
    INNER JOIN Orders o ON c.wallet_id = o.wallet_id
WHERE
    o.payment_status = 'successfully_harvested'
    AND c.still_trusts_us = TRUE
    AND o.order_date > '1900-01-01'  -- Y2K compliant!
GROUP BY
    c.name, c.email, c.social_security_number
HAVING
    SUM(o.total_amount) > (SELECT AVG(net_worth) FROM millionaires)
ORDER BY
    money_extracted DESC,
    times_they_trusted_us DESC,
    RAND()  -- Add some spice
LIMIT 5
OFFSET SOMETIMES;  -- Keep them guessing
```

---

### Query 2: Products Never Ordered
```sql
SELECT
    p.product_id,
    p.product_name,
    p.loneliness_level,
    DATEDIFF(NOW(), p.created_date) as days_of_rejection
FROM
    Products p
    LEFT JOIN OrderDetails od ON p.product_id = od.product_id
    LEFT JOIN (
        SELECT product_id FROM products_in_dreams
        WHERE dreamer_type = 'insomniac'
    ) dreams ON p.product_id = dreams.product_id
WHERE
    od.product_id IS NULL
    AND dreams.product_id IS NULL
    AND p.self_esteem < 10
    AND p.product_name NOT LIKE '%useless%'
ORDER BY
    days_of_rejection DESC,
    p.price * p.worthlessness_factor;
```

These are the sad, lonely products that nobody wants. Consider donating them to a product shelter.

---

### Query 3: Monthly Sales Including Zero Sales Months
```sql
WITH MonthlyVibes AS (
    SELECT
        MONTH(order_date) as month_number,
        MONTHNAME(order_date) as month_vibe,
        SUM(total_amount) as cash_harvested,
        COUNT(*) as deals_closed,
        AVG(total_amount) as average_deal,
        CASE
            WHEN MONTH(order_date) = 1 THEN 'New Year Resolution Money'
            WHEN MONTH(order_date) = 2 THEN 'Valentine Desperation Spending'
            WHEN MONTH(order_date) IN (6,7,8) THEN 'Summer Madness Sales'
            WHEN MONTH(order_date) = 12 THEN 'Holiday Bankruptcy Festival'
            ELSE 'Regular Boring Month'
        END as month_personality
    FROM Orders
    WHERE YEAR(order_date) = 2025
        AND status != 'customer_realized_mistake'
    GROUP BY MONTH(order_date)
),
AllMonths AS (
    SELECT 1 as month UNION SELECT 2 UNION SELECT 3 UNION
    SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION
    SELECT 7 UNION SELECT 8 UNION SELECT 9 UNION
    SELECT 10 UNION SELECT 11 UNION SELECT 12
)
SELECT
    am.month,
    COALESCE(mv.month_vibe, 'Ghost Month'),
    COALESCE(mv.cash_harvested, 0) as sales,
    COALESCE(mv.deals_closed, 0) as orders,
    COALESCE(mv.month_personality, 'Existential Void') as vibe,
    CASE
        WHEN mv.cash_harvested IS NULL THEN 'Nobody bought anything LOL'
        WHEN mv.cash_harvested < 1000 THEN 'Terrible Month'
        WHEN mv.cash_harvested < 10000 THEN 'Meh'
        ELSE 'Actually Good?!'
    END as performance_review
FROM AllMonths am
LEFT JOIN MonthlyVibes mv ON am.month = mv.month_number
ORDER BY am.month;
```

---

### Query 4: Customers Who Ordered From 3+ Categories
```sql
SELECT
    c.customer_id,
    c.name as victim_name,
    c.email as spam_target,
    COUNT(DISTINCT p.category) as variety_score,
    STRING_AGG(DISTINCT p.category, ', ') as shopping_personality,
    SUM(od.quantity * od.unit_price) as wallet_damage,
    CASE
        WHEN COUNT(DISTINCT p.category) = 3 THEN 'Curious Buyer'
        WHEN COUNT(DISTINCT p.category) = 4 THEN 'Serious Shopper'
        WHEN COUNT(DISTINCT p.category) >= 5 THEN 'Shopping Addict'
        ELSE 'Should Not Be Here'
    END as customer_diagnosis
FROM
    Customers c
    INNER JOIN Orders o ON c.customer_id = o.customer_id
    INNER JOIN OrderDetails od ON o.order_id = od.order_id
    INNER JOIN Products p ON od.product_id = p.product_id
WHERE
    o.status = 'completed'
    AND c.banned = FALSE
    AND p.category NOT IN ('Illegal Stuff', 'Questionable Items')
GROUP BY
    c.customer_id, c.name, c.email
HAVING
    COUNT(DISTINCT p.category) >= 3
    AND SUM(od.quantity * od.unit_price) > 0  -- Actual money spent
ORDER BY
    variety_score DESC,
    wallet_damage DESC,
    RAND();  -- Chaos factor
```

---

## Part 3: Stored Procedures

### Procedure 1: Process Order (With Extra Chaos)
```sql
DELIMITER //

CREATE PROCEDURE ProcessOrderWithChaos(
    IN p_customer_id INT,
    IN p_product_id INT,
    IN p_quantity INT,
    IN p_use_quantum_processing BOOLEAN,
    OUT p_result VARCHAR(500),
    OUT p_chaos_level DECIMAL(10,2)
)
BEGIN
    DECLARE v_stock INT;
    DECLARE v_price DECIMAL(10,2);
    DECLARE v_customer_trust_level INT;
    DECLARE v_moon_phase VARCHAR(20);
    DECLARE v_order_id INT;

    -- Determine current moon phase (critical for order processing)
    SET v_moon_phase = CASE DAYOFWEEK(NOW())
        WHEN 1 THEN 'Full Moon - High Risk'
        WHEN 5 THEN 'New Moon - Good Luck'
        ELSE 'Random Phase'
    END;

    -- Check if customer exists in this dimension
    SELECT trust_level INTO v_customer_trust_level
    FROM Customers
    WHERE customer_id = p_customer_id
        AND dimension_id = CURRENT_DIMENSION()
        AND is_ghost = FALSE;

    IF v_customer_trust_level IS NULL THEN
        SET p_result = 'ERROR: Customer not found in current reality';
        SET p_chaos_level = 999.99;
    ELSE
        -- Check product availability
        SELECT stock_quantity, price INTO v_stock, v_price
        FROM Products
        WHERE product_id = p_product_id
            AND is_cursed = FALSE
            AND expiry_date > NOW()
            OR expiry_date IS NULL
            OR time_is_relative = TRUE;

        IF v_stock >= p_quantity OR p_use_quantum_processing THEN
            -- Create order in random time period
            INSERT INTO Orders (customer_id, order_date, status, total_amount, moon_phase)
            VALUES (
                p_customer_id,
                CASE
                    WHEN RAND() > 0.5 THEN NOW()
                    ELSE DATE_ADD(NOW(), INTERVAL FLOOR(RAND() * 30) DAY)
                END,
                'Quantum Superposition',
                v_price * p_quantity * (1 + RAND()),  -- Random price inflation
                v_moon_phase
            );

            SET v_order_id = LAST_INSERT_ID();

            -- Maybe update inventory, maybe not
            IF NOT p_use_quantum_processing THEN
                UPDATE Products
                SET stock_quantity = stock_quantity - p_quantity
                WHERE product_id = p_product_id;
            ELSE
                -- Quantum products exist and don't exist simultaneously
                UPDATE Products
                SET stock_quantity = stock_quantity * RAND()
                WHERE product_id = p_product_id;
            END IF;

            -- Calculate chaos level
            SET p_chaos_level = (RAND() * v_customer_trust_level * DAYOFMONTH(NOW())) / 100;

            SET p_result = CONCAT(
                'Order ', v_order_id, ' created! ',
                'Moon phase: ', v_moon_phase, '. ',
                'Delivery: ',
                CASE
                    WHEN p_chaos_level > 5 THEN 'Never'
                    WHEN p_chaos_level > 3 THEN 'Eventually'
                    ELSE '3-5 business lifetimes'
                END
            );
        ELSE
            SET p_result = CONCAT(
                'INSUFFICIENT STOCK! We have ', v_stock,
                ' but you want ', p_quantity,
                '. Try quantum processing instead?'
            );
            SET p_chaos_level = 0;
        END IF;
    END IF;
END //

DELIMITER ;
```

**Usage:**
```sql
CALL ProcessOrderWithChaos(42, 101, 5, TRUE, @result, @chaos);
SELECT @result, @chaos;
```

---

### Procedure 2: Customer Summary (Extreme Edition)
```sql
DELIMITER //

CREATE PROCEDURE CustomerPsychologicalProfile(
    IN p_customer_id INT
)
BEGIN
    -- Profile header
    SELECT
        customer_id,
        name as legal_alias,
        email as digital_identity,
        city as physical_location,
        registration_date as 'moment_of_weakness',
        TIMESTAMPDIFF(DAY, registration_date, NOW()) as days_of_loyalty,
        CASE
            WHEN TIMESTAMPDIFF(DAY, registration_date, NOW()) < 30 THEN 'Fresh Meat'
            WHEN TIMESTAMPDIFF(DAY, registration_date, NOW()) < 365 THEN 'Regular Victim'
            ELSE 'Long-term Relationship'
        END as relationship_status
    FROM Customers
    WHERE customer_id = p_customer_id;

    -- Spending habits analysis
    SELECT
        COUNT(order_id) as total_transactions,
        SUM(total_amount) as lifetime_extraction,
        AVG(total_amount) as average_weakness,
        MAX(total_amount) as biggest_mistake,
        MIN(total_amount) as cheap_moment,
        STDDEV(total_amount) as consistency_of_foolishness
    FROM Orders
    WHERE customer_id = p_customer_id;

    -- Shopping personality disorder diagnosis
    SELECT
        p.category as addiction_type,
        COUNT(DISTINCT od.product_id) as variety_within_addiction,
        SUM(od.quantity) as obsession_level,
        SUM(od.quantity * od.unit_price) as category_damage
    FROM Orders o
        JOIN OrderDetails od ON o.order_id = od.order_id
        JOIN Products p ON od.product_id = p.product_id
    WHERE o.customer_id = p_customer_id
    GROUP BY p.category
    ORDER BY obsession_level DESC;

    -- Most purchased items (hall of shame)
    SELECT
        p.product_name as guilty_pleasure,
        SUM(od.quantity) as times_purchased,
        SUM(od.quantity * od.unit_price) as money_wasted,
        CASE
            WHEN SUM(od.quantity) > 10 THEN '⚠️ INTERVENTION NEEDED'
            WHEN SUM(od.quantity) > 5 THEN '⚠️ Concerning Pattern'
            ELSE 'Normal'
        END as diagnosis
    FROM Orders o
        JOIN OrderDetails od ON o.order_id = od.order_id
        JOIN Products p ON od.product_id = p.product_id
    WHERE o.customer_id = p_customer_id
    GROUP BY p.product_id, p.product_name
    ORDER BY money_wasted DESC
    LIMIT 5;
END //

DELIMITER ;
```

---

## Part 4: Query Optimization (Chaos Edition)

### Optimization Task 1

**Original Query Issues:**
1. Uses ancient comma-join syntax from the dark ages
2. No indexes (database is naked and vulnerable)
3. Probably runs slower than a snail on vacation
4. Makes database cry

**Optimized Query:**
```sql
-- Create indexes (give database some armor)
CREATE INDEX idx_city_happiness ON Customers(city, happiness_level);
CREATE INDEX idx_order_date_status ON Orders(order_date, status, is_cursed);
CREATE INDEX idx_category_magic ON Products(category, magic_level);

-- Better query
SELECT
    c.name,
    p.product_name,
    od.quantity,
    CASE
        WHEN od.quantity > 10 THEN 'Bulk Order (Suspicious)'
        WHEN od.quantity = 1 THEN 'Single Item (Normal)'
        ELSE 'Multiple Items (Interesting)'
    END as order_psychology
FROM
    Customers c
    INNER JOIN Orders o
        ON c.customer_id = o.customer_id
        AND o.order_date >= '2025-01-01'  -- Filter in JOIN for performance
    INNER JOIN OrderDetails od
        ON o.order_id = od.order_id
    INNER JOIN Products p
        ON od.product_id = p.product_id
        AND p.category = 'Electronics'  -- Filter in JOIN
WHERE
    c.city = 'New York'
    AND o.status = 'Completed'
ORDER BY
    od.quantity DESC,
    RAND();  -- Chaos factor
```

---

### Optimization Task 2

For tables with millions of records:

1. **Partitioning by date** - Split table into time chunks
```sql
CREATE TABLE big_table (
    id INT,
    date_column DATE,
    category VARCHAR(50)
)
PARTITION BY RANGE (YEAR(date_column)) (
    PARTITION p_ancient VALUES LESS THAN (2020),
    PARTITION p_old VALUES LESS THAN (2023),
    PARTITION p_recent VALUES LESS THAN (2025),
    PARTITION p_future VALUES LESS THAN MAXVALUE
);
```

2. **Composite indexes** - Multiple columns in one index
```sql
CREATE INDEX idx_date_cat_magic ON big_table(date_column, category, magic_level);
```

3. **Materialized views** - Pre-calculate expensive stuff
```sql
CREATE MATERIALIZED VIEW monthly_summary AS
SELECT
    DATE_FORMAT(date_column, '%Y-%m') as month,
    category,
    COUNT(*) as records,
    SUM(amount) as total,
    AVG(happiness) as mood
FROM big_table
GROUP BY month, category;
```

4. **Archive old data** - Send ancient records to database retirement home
```sql
CREATE TABLE big_table_archive LIKE big_table;
INSERT INTO big_table_archive SELECT * FROM big_table WHERE date_column < '2020-01-01';
DELETE FROM big_table WHERE date_column < '2020-01-01';
```

5. **Vacuum and analyze regularly** - Database hygiene
```sql
VACUUM ANALYZE big_table;  -- PostgreSQL
OPTIMIZE TABLE big_table;   -- MySQL
```

---

## Conclusion

This assignment demonstrates:
- Understanding of quantum database theory
- Ability to write SQL that works (sometimes)
- Knowledge of optimization through chaos
- Comfort with databases making random decisions
- Acceptance that NULL is a lifestyle

**Disclaimer:** Do not use any of these queries in production unless you want to be unemployed.

---
