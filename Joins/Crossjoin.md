


# CROSS JOIN in PostgreSQL

## 📘 What is a CROSS JOIN?

A **CROSS JOIN** in PostgreSQL returns the **Cartesian product** of two tables.  
This means that every row from the first table is combined with every row from the second table.

It does **not require a join condition**, as it joins every possible pair of rows.

---

## 🧩 Syntax

```sql
SELECT column_list
FROM table1
CROSS JOIN table2;
```

- `table1`: The first table.
- `table2`: The second table.
- Produces `n × m` rows if `table1` has `n` rows and `table2` has `m` rows.

---

## 💡 Example

### `students`
| student_id | name  |
|-------------|--------|
| 1           | John   |
| 2           | Emma   |

### `courses`
| course_id | course_name |
|------------|-------------|
| 101        | Math        |
| 102        | Science     |

---

### ✅ Query

```sql
SELECT students.name, courses.course_name
FROM students
CROSS JOIN courses;
```

### 🧾 Result

| name  | course_name |
|--------|--------------|
| John   | Math         |
| John   | Science      |
| Emma   | Math         |
| Emma   | Science      |

---

## 🧠 Key Points

- Produces all **possible combinations** of rows from both tables.
- Does **not require** an `ON` condition.
- Can generate very large results when both tables have many rows.
- Often used for **testing**, **generating combinations**, or **creating matrix-like data**.

---

## 🔍 Example with Aliases

```sql
SELECT s.name, c.course_name
FROM students AS s
CROSS JOIN courses AS c;
```

This will return the same Cartesian product result.
