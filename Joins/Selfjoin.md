---

# SELF JOIN in PostgreSQL

## 📘 What is a SELF JOIN?

A **SELF JOIN** in PostgreSQL is a join where a table is joined with itself.  
It’s useful when you want to compare rows within the same table — for example, to find relationships among records in a single table.

You must use **table aliases** to differentiate between the two instances of the same table.

---

## 🧩 Syntax

```sql
SELECT a.column_name, b.column_name
FROM table_name AS a
JOIN table_name AS b
ON a.common_column = b.related_column;
```

- `a` and `b` are **aliases** for the same table.  
- The join condition defines how rows relate to one another.

---

## 💡 Example

### `employees`
| emp_id | name   | manager_id |
|---------|--------|-------------|
| 1       | John   | NULL        |
| 2       | Emma   | 1           |
| 3       | Liam   | 1           |
| 4       | Olivia | 2           |

In this table:
- John is the manager of Emma and Liam.  
- Emma is the manager of Olivia.

---

### ✅ Query

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees AS e
JOIN employees AS m
ON e.manager_id = m.emp_id;
```

### 🧾 Result

| employee | manager |
|-----------|----------|
| Emma      | John     |
| Liam      | John     |
| Olivia    | Emma     |

---

## 🧠 Key Points

- A **SELF JOIN** joins a table to itself.  
- Commonly used to represent **hierarchical data**, such as employee-manager relationships.  
- Requires **aliases** to differentiate between instances of the same table.  
- Works with any type of join (e.g., `LEFT JOIN`, `INNER JOIN`).

---

## 🔍 Example with LEFT JOIN

To include all employees even if they don’t have a manager:

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees AS e
LEFT JOIN employees AS m
ON e.manager_id = m.emp_id;
```

### 🧾 Result

| employee | manager |
|-----------|----------|
| John      | NULL     |
| Emma      | John     |
| Liam      | John     |
| Olivia    | Emma     |

This shows every employee and their manager, including those without one (like John).
