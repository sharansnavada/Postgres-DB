

# 🧩 PostgreSQL — Subqueries

## 1. Introduction

A **subquery** is a query nested inside another query.  
It helps perform operations that depend on the result of another SQL statement.

Subqueries can appear in:
- `SELECT` statements  
- `FROM` clauses  
- `WHERE` or `HAVING` conditions

---

## 2. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name operator (
    SELECT column_name
    FROM another_table
    WHERE condition
);
```

---

## 3. Example — Using Subquery in WHERE Clause

```sql
SELECT product_name, price
FROM products
WHERE price > (
    SELECT AVG(price)
    FROM products
);
```

✅ Explanation:
- The subquery calculates the **average price** of all products.
- The main query returns only those products with a **price greater than the average**.

---

## 4. Example — Using Subquery in FROM Clause

You can treat a subquery as a **temporary table** using the `FROM` clause.

```sql
SELECT category, AVG(avg_price) AS category_average
FROM (
    SELECT category, AVG(price) AS avg_price
    FROM products
    GROUP BY category
) AS subquery
GROUP BY category;
```

✅ Explanation:
- The inner subquery finds the **average price per category**.
- The outer query calculates the **average of those averages**.

---

## 5. Example — Subquery with IN Operator

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
    WHERE order_date > '2025-01-01'
);
```

✅ Explanation:
- The subquery returns all `customer_id`s who placed orders after January 1, 2025.
- The main query lists their names from the `customers` table.

---

## 6. Example — Subquery in SELECT Clause

```sql
SELECT
    customer_name,
    (SELECT COUNT(*) FROM orders WHERE orders.customer_id = customers.customer_id) AS total_orders
FROM customers;
```

✅ Explanation:
- For each customer, the subquery counts how many orders they’ve placed.

---

## 7. Correlated Subqueries

A **correlated subquery** references columns from the outer query.  
It runs **once for each row** of the outer query.

```sql
SELECT e1.employee_name, e1.salary
FROM employees e1
WHERE e1.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```

✅ Explanation:
- The subquery computes the **average salary per department**.
- The main query shows employees who earn **more than the department average**.

---

## 8. EXISTS with Subquery

`EXISTS` checks whether a subquery returns **any rows**.

```sql
SELECT customer_name
FROM customers c
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.customer_id
);
```

✅ Explanation:
- Returns customers who have at least one order in the `orders` table.

---

## ✅ Summary

- Subqueries are queries inside another query.
- They can be used in `WHERE`, `FROM`, or `SELECT` clauses.
- Correlated subqueries depend on values from the outer query.
- Use `EXISTS` or `IN` for checking presence of related records.

---

**Next Topic →** [Joins in PostgreSQL](./Joins.md)
