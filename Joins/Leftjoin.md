
---

# LEFT JOIN in PostgreSQL

## 📘 What is a LEFT JOIN?

A **LEFT JOIN** (also known as **LEFT OUTER JOIN**) in PostgreSQL returns **all rows from the left table** and the **matching rows from the right table**.  
If there is no match in the right table, the result will still include the left table’s row, but with `NULL` values for the right table’s columns.

---

## 🧩 Syntax

```sql
SELECT column_list
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;
```

- `table1`: The **left** table (all rows from this table will be returned).
- `table2`: The **right** table (only matching rows will be returned; unmatched ones will be `NULL`).
- `common_column`: The column(s) used to match rows between the tables.

---

## 💡 Example

### `students`
| student_id | name    | course_id |
|-------------|----------|-----------|
| 1           | John     | 101       |
| 2           | Emma     | 102       |
| 3           | Liam     | 103       |
| 4           | Olivia   | 105       |

### `courses`
| course_id | course_name |
|------------|-------------|
| 101        | Math        |
| 102        | Science     |
| 104        | History     |

---

### ✅ Query

```sql
SELECT students.name, courses.course_name
FROM students
LEFT JOIN courses
ON students.course_id = courses.course_id;
```

### 🧾 Result

| name   | course_name |
|---------|--------------|
| John    | Math         |
| Emma    | Science      |
| Liam    | NULL         |
| Olivia  | NULL         |

---

## 🧠 Key Points

- Returns **all rows from the left table**.
- Rows from the right table appear **only if there is a match**.
- Non-matching rows in the right table will have **NULL** values.
- Useful when you want to find all records from one table, even if they don’t have corresponding entries in the other.

---

## 🔍 Example with Aliases

```sql
SELECT s.name, c.course_name
FROM students AS s
LEFT JOIN courses AS c
ON s.course_id = c.course_id;
```

This query gives the same output but with table aliases for cleaner and more readable code.
