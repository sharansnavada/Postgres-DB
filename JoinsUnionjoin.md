# UNION in PostgreSQL

## 📘 What is a UNION?

A **UNION** in PostgreSQL is used to combine the result sets of **two or more SELECT queries** into a single result set.  
It removes duplicate rows by default. If you want to include duplicates, you can use `UNION ALL`.

- **Note:** `UNION` is not a JOIN. It combines rows vertically rather than horizontally.

---

## 🧩 Syntax

```sql
SELECT column_list
FROM table1
WHERE condition

UNION

SELECT column_list
FROM table2
WHERE condition;
```

- `column_list` must have the **same number of columns** in both SELECT queries.
- Columns must have **compatible data types**.

---

## 💡 Example

### `students_2024`
| student_id | name    |
|------------|---------|
| 1          | John    |
| 2          | Emma    |
| 3          | Liam    |

### `students_2025`
| student_id | name    |
|------------|---------|
| 3          | Liam    |
| 4          | Olivia  |
| 5          | Noah    |

---

### ✅ Query (UNION)

```sql
SELECT name FROM students_2024
UNION
SELECT name FROM students_2025;
```

### 🧾 Result

| name   |
|--------|
| John   |
| Emma   |
| Liam   |
| Olivia |
| Noah   |

---

### ✅ Query (UNION ALL)

```sql
SELECT name FROM students_2024
UNION ALL
SELECT name FROM students_2025;
```

### 🧾 Result (with duplicates)

| name   |
|--------|
| John   |
| Emma   |
| Liam   |
| Liam   |
| Olivia |
| Noah   |

---

## 🧠 Key Points

- Combines results from multiple SELECT statements.
- Removes **duplicates** by default (`UNION`), keeps duplicates if `UNION ALL` is used.
- Number of columns and their data types must match across SELECT queries.
- Useful for merging datasets from multiple tables or periods.
