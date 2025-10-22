# INNER JOIN in PostgreSQL

## 🔍 Overview
An **INNER JOIN** in PostgreSQL returns rows when there is a match between columns in both tables. It is the most common type of join and helps combine related data from two or more tables.

## 🧩 Syntax
```sql
SELECT table1.column_name, table2.column_name
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
```

## 🧠 Explanation
- The `INNER JOIN` keyword selects records that have matching values in both tables.
- If there’s no match, the rows are excluded from the result.
- The `ON` condition specifies how the tables are related.

## 📘 Example
Let’s say we have two tables:

**employees**
| id | name  | department_id |
|----|--------|----------------|
| 1  | Alice  | 10             |
| 2  | Bob    | 20             |
| 3  | Carol  | 10             |

**departments**
| id | department_name |
|----|------------------|
| 10 | HR              |
| 20 | IT              |
| 30 | Finance          |

Now, let’s join them:

```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.id;
```

**Result:**
| name  | department_name |
|--------|-----------------|
| Alice  | HR              |
| Bob    | IT              |
| Carol  | HR              |

✅ Only rows where `employees.department_id` matches `departments.id` appear in the output.

## 💡 Key Points
- `INNER JOIN` = intersection of both tables.
- You can join more than two tables using multiple `INNER JOIN`s.
- It’s commonly used when you only want data that exists in both tables.

## 🔗 Alternative Syntax
You can also use:
```sql
SELECT *
FROM table1, table2
WHERE table1.common_column = table2.common_column;
```
However, using `INNER JOIN` is preferred for clarity and maintainability.
