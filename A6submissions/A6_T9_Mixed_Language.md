# Assignment A6: Mixed Assignment - Database Management System
**Student Name:** Isabel Martinez
**Student ID:** 2024-CS-5716
**Date:** March 23, 2026

---

## Part 1: Theoretical Questions / Questions Théoriques / Preguntas Teóricas

### Question 1
**Explain JOIN operations / Expliquez les opérations JOIN / Explique las operaciones JOIN**

**Respuesta / Answer / Réponse:**

**INNER JOIN:**
Returns only matching rows / Retorna solo filas coincidentes / Retourne uniquement les lignes correspondantes.

```sql
SELECT clients.nom, commandes.order_id
FROM clientes
INNER JOIN orders ON customers.id = pedidos.customer_id;
```

**LEFT JOIN:**
Retourne todas las filas from the tabla izquierda et matching rows de la right table.

```sql
SELECT c.name, o.order_id
FROM Customers c
LEFT JOIN Ordenes o ON c.customer_id = o.customer_id;
```

**RIGHT JOIN:**
Similar to LEFT JOIN pero en direction opposée / opposite direction / dirección opuesta.

**FULL OUTER JOIN:**
Retorna all rows de both tables avec NULL values donde no hay match.

---

### Question 2
**Database Normalization / Normalización de Base de Datos / Normalisation de Base de Données**

La normalización est le proceso de organizing data pour reduce la redundancia.

**1NF (Primera Forma Normal / First Normal Form / Première Forme Normale):**
- Valores atomiques / atomic values / valores atómicos
- Pas de repeating groups / no grupos repetidos

**Exemple / Example / Ejemplo:**
```
BAD:
| ID | Nom | Courses          |
|----|-----|------------------|
| 1  | Juan| Math, Physique   |

GOOD:
| ID | Nom | Course   |
|----|-----|----------|
| 1  | Juan| Math     |
| 1  | Juan| Physique |
```

**2NF (Segunda Forma Normal):**
Must be en 1NF + pas de partial dependencies sur composite keys.

**3NF (Troisième Forme Normale):**
Debe estar in 2NF + no transitive dependencies.

---

### Question 3
**ACID Properties / Propriétés ACID / Propiedades ACID**

**Atomicidad / Atomicity / Atomicité:**
Toutes les operations se complètent o ninguna lo hace.

**Cohérence / Consistency / Consistencia:**
La base de données reste dans un valid state après each transaction.

**Isolation / Aislamiento:**
Les transactions ne interfèrent pas with each other.

**Durabilité / Durability / Durabilidad:**
Changes sont permanentes après commit.

**Ejemplo / Example / Exemple:**
```sql
BEGIN TRANSACTION;
UPDATE cuentas SET balance = saldo - 100 WHERE compte_id = 1;
UPDATE accounts SET solde = balance + 100 WHERE account_id = 2;
COMMIT;
```

---

## Parte 2: Practical SQL Queries / Requêtes SQL Pratiques / Consultas SQL Prácticas

### Requête 1 / Query 1 / Consulta 1
**Top 5 clientes by spending / meilleurs clients par dépenses**

```sql
SELECT
    c.nom AS nombre,
    c.email AS correo,
    SUM(o.total_amount) AS total_dépensé
FROM
    Customers c
    INNER JOIN Pedidos o ON c.customer_id = o.id_cliente
WHERE
    o.statut = 'Completado'
GROUP BY
    c.customer_id, c.name, c.email
ORDER BY
    total_dépensé DESC
LIMIT 5;
```

---

### Query 2 / Consulta 2 / Requête 2
**Products never ordered / Produits jamais commandés / Productos nunca pedidos**

```sql
SELECT
    p.product_id AS id_producto,
    p.nom_produit AS product_name,
    p.categoría AS category,
    p.precio AS price
FROM
    Productos p
    LEFT JOIN OrderDetails od ON p.product_id = od.id_producto
WHERE
    od.product_id IS NULL;
```

---

### Consulta 3 / Requête 3 / Query 3
**Monthly sales pour 2025 / Ventas mensuales para 2025**

```sql
WITH Meses AS (
    SELECT 1 AS mes UNION SELECT 2 UNION SELECT 3 UNION
    SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION
    SELECT 7 UNION SELECT 8 UNION SELECT 9 UNION
    SELECT 10 UNION SELECT 11 UNION SELECT 12
),
VentasMensuelles AS (
    SELECT
        MONTH(fecha_pedido) AS mois,
        SUM(montant_total) AS total_sales
    FROM Commandes
    WHERE YEAR(order_date) = 2025
      AND état = 'Terminé'
    GROUP BY MONTH(date_commande)
)
SELECT
    m.mes AS month,
    COALESCE(vm.total_sales, 0) AS ventas_totales
FROM Meses m
LEFT JOIN VentasMensuelles vm ON m.mes = vm.mois
ORDER BY m.month;
```

---

### Query 4 / Requête 4 / Consulta 4
**Clients qui ont ordered de at least 3 categorías différentes**

```sql
SELECT
    c.customer_id AS id_cliente,
    c.nom AS name,
    c.email AS correo,
    COUNT(DISTINCT p.categoria) AS compte_catégories
FROM
    Clientes c
    INNER JOIN Orders o ON c.id = o.customer_id
    INNER JOIN DetallePedido od ON o.order_id = od.commande_id
    INNER JOIN Produits p ON od.producto_id = p.product_id
WHERE
    o.statut = 'Completado'
GROUP BY
    c.customer_id, c.name, c.email
HAVING
    COUNT(DISTINCT p.category) >= 3
ORDER BY
    compte_catégories DESC;
```

---

## Partie 3: Stored Procedures / Procedimientos Almacenados / Procédures Stockées

### Procedure 1 / Procédure 1 / Procedimiento 1
**Process Order / Traiter Commande / Procesar Pedido**

```sql
DELIMITER //

CREATE PROCEDURE ProcesarPedido(
    IN p_id_cliente INT,
    IN p_product_id INT,
    IN p_cantidad INT,
    OUT p_order_id INT,
    OUT p_mensaje VARCHAR(255)
)
BEGIN
    DECLARE v_stock INT;
    DECLARE v_prix DECIMAL(10, 2);
    DECLARE EXIT HANDLER FOR SQLEXCEPTION
    BEGIN
        ROLLBACK;
        SET p_mensaje = 'Erreur: Transaction échouée / Error: Falló la transacción';
        SET p_order_id = NULL;
    END;

    START TRANSACTION;

    -- Vérifier si client existe / Check if customer exists / Verificar si cliente existe
    IF NOT EXISTS (SELECT 1 FROM Clients WHERE customer_id = p_id_cliente) THEN
        SET p_mensaje = 'Error: Cliente no encontrado / Client not found / Client non trouvé';
        SET p_order_id = NULL;
        ROLLBACK;
    ELSE
        -- Obtenir info produit / Get product info / Obtener info producto
        SELECT stock_quantity, precio INTO v_stock, v_prix
        FROM Products
        WHERE product_id = p_product_id;

        -- Vérifier stock / Check stock / Verificar stock
        IF v_stock < p_cantidad THEN
            SET p_mensaje = 'Erreur: Stock insuffisant / Insufficient stock / Stock insuficiente';
            SET p_order_id = NULL;
            ROLLBACK;
        ELSE
            -- Créer commande / Create order / Crear pedido
            INSERT INTO Pedidos (customer_id, fecha_pedido, montant_total, statut)
            VALUES (p_id_cliente, CURDATE(), v_prix * p_cantidad, 'En cours');

            SET p_order_id = LAST_INSERT_ID();

            -- Ajouter détails / Add details / Añadir detalles
            INSERT INTO OrderDetails (commande_id, producto_id, quantity, prix_unitaire)
            VALUES (p_order_id, p_product_id, p_cantidad, v_prix);

            -- Actualizar stock / Update stock / Mettre à jour stock
            UPDATE Productos
            SET stock_quantity = cantidad_stock - p_cantidad
            WHERE product_id = p_product_id;

            -- Marquer terminé / Mark completed / Marcar completado
            UPDATE Orders
            SET état = 'Completado'
            WHERE order_id = p_order_id;

            SET p_mensaje = 'Succès: Commande traitée / Success: Order processed / Éxito: Pedido procesado';
            COMMIT;
        END IF;
    END IF;
END //

DELIMITER ;
```

**Usage / Utilisation / Uso:**
```sql
CALL ProcesarPedido(1, 101, 5, @id_commande, @message);
SELECT @id_commande AS order_id, @message AS mensaje;
```

---

### Procédure 2 / Procedimiento 2 / Procedure 2
**Customer Summary / Résumé Client / Resumen Cliente**

```sql
DELIMITER //

CREATE PROCEDURE ResumenCliente(
    IN p_customer_id INT,
    IN p_fecha_inicio DATE,
    IN p_date_fin DATE
)
BEGIN
    -- Info cliente / Customer info / Information client
    SELECT
        customer_id AS id_cliente,
        nom AS name,
        email AS correo,
        ville AS city
    FROM Clientes
    WHERE customer_id = p_customer_id;

    -- Statistiques d'achats / Purchase statistics / Estadísticas de compras
    SELECT
        COUNT(o.order_id) AS total_commandes,
        SUM(o.montant_total) AS total_dépensé,
        AVG(o.total_amount) AS promedio_pedido,
        MIN(o.date_commande) AS primer_pedido,
        MAX(o.order_date) AS dernière_commande
    FROM Pedidos o
    WHERE o.id_cliente = p_customer_id
      AND o.order_date BETWEEN p_fecha_inicio AND p_date_fin
      AND o.statut = 'Completado';

    -- Décomposition par catégorie / Category breakdown / Desglose por categoría
    SELECT
        p.categoría AS category,
        COUNT(DISTINCT od.producto_id) AS produits,
        SUM(od.cantidad) AS quantité_totale,
        SUM(od.quantity * od.prix_unitaire) AS dépenses
    FROM Orders o
        INNER JOIN DetallePedido od ON o.commande_id = od.order_id
        INNER JOIN Productos p ON od.product_id = p.producto_id
    WHERE o.customer_id = p_customer_id
      AND o.fecha_pedido BETWEEN p_fecha_inicio AND p_date_fin
      AND o.état = 'Completado'
    GROUP BY p.category
    ORDER BY dépenses DESC;

    -- Top 5 produits / Top 5 products / Top 5 productos
    SELECT
        p.nom_produit AS product_name,
        p.category AS categoría,
        SUM(od.cantidad) AS quantité,
        SUM(od.quantity * od.precio_unitario) AS total_gastado
    FROM Commandes o
        INNER JOIN OrderDetails od ON o.order_id = od.commande_id
        INNER JOIN Products p ON od.product_id = p.producto_id
    WHERE o.id_cliente = p_customer_id
      AND o.order_date BETWEEN p_fecha_inicio AND p_date_fin
      AND o.statut = 'Completado'
    GROUP BY p.product_id, p.product_name, p.categoría
    ORDER BY total_gastado DESC
    LIMIT 5;
END //

DELIMITER ;
```

---

## Part 4: Query Optimization / Optimización de Consultas / Optimisation de Requêtes

### Tâche 1 / Task 1 / Tarea 1

**Problèmes / Problems / Problemas:**
- Old-style joins (sintaxis antigua / syntaxe ancienne)
- Pas d'indexes / No indexes / Sin índices
- Rendimiento lento / Slow performance / Performance lente

**Optimización / Optimization / Optimisation:**

```sql
-- Créer indexes / Create indexes / Crear índices
CREATE INDEX idx_ville ON Customers(city);
CREATE INDEX idx_fecha ON Orders(order_date);
CREATE INDEX idx_categoria ON Products(category);

-- Requête optimisée / Optimized query / Consulta optimizada
SELECT
    c.nom AS name,
    p.product_name AS nom_produit,
    od.cantidad AS quantity
FROM
    Clientes c
    INNER JOIN Pedidos o ON c.customer_id = o.id_cliente
    INNER JOIN OrderDetails od ON o.commande_id = od.order_id
    INNER JOIN Productos p ON od.product_id = p.producto_id
WHERE
    c.ville = 'New York'
    AND o.fecha_pedido >= '2025-01-01'
    AND p.categoría = 'Electronics';
```

---

### Tarea 2 / Task 2 / Tâche 2

Pour grandes tables / For large tables / Para tablas grandes:

1. **Partitionnement / Partitioning / Particionamiento:**
```sql
PARTITION BY RANGE (YEAR(date_colonne))
```

2. **Indexes composites / Composite indexes / Índices compuestos:**
```sql
CREATE INDEX idx_date_cat ON tabla(date_column, categoría);
```

3. **Vues matérialisées / Materialized views / Vistas materializadas:**
```sql
CREATE MATERIALIZED VIEW resumen_mensual AS
SELECT MONTH(fecha) AS mes, SUM(montant) AS total
FROM grande_table
GROUP BY mes;
```

4. **Archivage / Archiving / Archivado:**
Mover datos antiguos / Move old data / Déplacer anciennes données

5. **Mise en cache / Caching / Almacenamiento en caché:**
Cache pour requêtes fréquentes / Cache for frequent queries / Caché para consultas frecuentes

---

## Conclusion / Conclusión

Ce devoir démontre / This assignment demonstrates / Esta tarea demuestra:
- Compréhension des concepts de base de données
- Understanding of database concepts
- Comprensión de conceptos de bases de datos

---
