


---

# RIGHT JOIN in PostgreSQL

## 📘 What is a RIGHT JOIN?

A **RIGHT JOIN** (also called **RIGHT OUTER JOIN**) in PostgreSQL returns **all rows from the right table** and the **matching rows from the left table**.  
If there is no match in the left table, the result will still include the right table’s row, but with `NULL` values for the left table’s columns.

---

## 🧩 Syntax

```sql
SELECT column_list
FROM table1
RIGHT JOIN table2
ON table1.common_column = table2.common_column;
```

- `table1`: The **left** table (only matching rows will be returned).
- `table2`: The **right** table (all rows from this table will be returned).
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
RIGHT JOIN courses
ON students.course_id = courses.course_id;
```

### 🧾 Result

| name  | course_name |
|--------|--------------|
| John   | Math         |
| Emma   | Science      |
| NULL   | History      |

---

## 🧠 Key Points

- Returns **all rows from the right table**.
- Rows from the left table appear **only if there is a match**.
- Non-matching rows in the left table will have **NULL** values.
- Useful when you want to include all data from the right table, regardless of matches in the left one.
- Essentially the opposite of a **LEFT JOIN**.

---

## 🔍 Example with Aliases

```sql
SELECT s.name, c.course_name
FROM students AS s
RIGHT JOIN courses AS c
ON s.course_id = c.course_id;
```

This gives the same result using table aliases for simplicity.
