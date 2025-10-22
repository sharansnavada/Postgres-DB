---

# FULL JOIN in PostgreSQL

## 📘 What is a FULL JOIN?

A **FULL JOIN** (also called **FULL OUTER JOIN**) in PostgreSQL returns **all rows from both tables**, whether they have matching rows or not.  
If a row from one table has no match in the other, the columns from the non-matching table will contain `NULL` values.

It combines the results of both **LEFT JOIN** and **RIGHT JOIN**.

---

## 🧩 Syntax

```sql
SELECT column_list
FROM table1
FULL JOIN table2
ON table1.common_column = table2.common_column;
```

- `table1`: The left table.  
- `table2`: The right table.  
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
FULL JOIN courses
ON students.course_id = courses.course_id;
```

### 🧾 Result

| name   | course_name |
|---------|--------------|
| John    | Math         |
| Emma    | Science      |
| Liam    | NULL         |
| Olivia  | NULL         |
| NULL    | History      |

---

## 🧠 Key Points

- Returns **all rows** from both tables.  
- Non-matching rows from either table are filled with **NULL**.  
- Essentially a combination of **LEFT JOIN** and **RIGHT JOIN**.  
- Useful when you need a complete dataset, including all non-matching records from both tables.

---

## 🔍 Example with Aliases

```sql
SELECT s.name, c.course_name
FROM students AS s
FULL JOIN courses AS c
ON s.course_id = c.course_id;
```

This gives the same result, showing all rows from both tables whether or not there’s a match.
