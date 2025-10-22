

# INNER JOIN in PostgreSQL

## 📘 What is an INNER JOIN?

An **INNER JOIN** in PostgreSQL returns only the rows that have matching values in both tables.  
If there is no match between the tables, the rows are not included in the result.

It is the most common type of join used in SQL queries.

---

## 🧩 Syntax

```sql
SELECT column_list
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
```

- `table1` and `table2`: The tables you want to join.
- `common_column`: The column(s) that are common in both tables, used to match rows.

---

## 💡 Example

Let’s say we have two tables:

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
INNER JOIN courses
ON students.course_id = courses.course_id;
```

### 🧾 Result

| name  | course_name |
|--------|--------------|
| John   | Math         |
| Emma   | Science      |

---

## 🧠 Key Points

- Returns **only matching rows** between both tables.
- If a student doesn’t have a matching course (like Liam and Olivia in the above example), they will not appear in the result.
- Equivalent to writing just `JOIN` in PostgreSQL (since `JOIN` defaults to `INNER JOIN`).

---

## 🔍 Example with Aliases

```sql
SELECT s.name, c.course_name
FROM students AS s
JOIN courses AS c
ON s.course_id = c.course_id;
```

This produces the same result but uses shorter aliases for readability.
