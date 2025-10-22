


# NATURAL JOIN in PostgreSQL

## 📘 What is a NATURAL JOIN?

A **NATURAL JOIN** in PostgreSQL automatically joins two tables based on **all columns with the same name and compatible data types**.  
It eliminates the need to explicitly specify the join condition with `ON`.

---

## 🧩 Syntax

```sql
SELECT column_list
FROM table1
NATURAL JOIN table2;
```

- `table1` and `table2`: The tables to join.  
- Automatically uses columns with the **same name** as the join key.

---

## 💡 Example

### `students`
| student_id | name    | course_id |
|------------|---------|-----------|
| 1          | John    | 101       |
| 2          | Emma    | 102       |
| 3          | Liam    | 103       |

### `enrollments`
| student_id | course_id |
|------------|-----------|
| 1          | 101       |
| 2          | 102       |
| 4          | 104       |

---

### ✅ Query

```sql
SELECT students.name, enrollments.course_id
FROM students
NATURAL JOIN enrollments;
```

### 🧾 Result

| name  | course_id |
|-------|-----------|
| John  | 101       |
| Emma  | 102       |

---

## 🧠 Key Points

- Automatically matches columns with the same name in both tables.  
- Returns only rows where **all matching columns have equal values**.  
- Useful for simplifying queries when table columns are named consistently.  
- Be cautious if multiple columns share the same name unintentionally, as it may produce unexpected results.

---

## 🔍 Example with Aliases

```sql
SELECT s.name, e.course_id
FROM students AS s
NATURAL JOIN enrollments AS e;
```

This produces the same result but uses shorter aliases for clarity.
