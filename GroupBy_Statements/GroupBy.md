# GROUP BY in PostgreSQL

##  GROUP BY

The **GROUP BY** clause in PostgreSQL is used to **arrange identical data into groups**. It helps you summarize data by one or more columns and is commonly used with **aggregate functions** such as:

- `COUNT()` → counts the number of rows in each group  
- `SUM()` → adds up numeric values in each group  
- `AVG()` → calculates the average value in each group  
- `MAX()` → finds the maximum value in each group  
- `MIN()` → finds the minimum value in each group  

---

### 🔹 Basic Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
```

---

### 🔹 Example 1 – Count Employees per Department

```sql
SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department;
```

✅ **Explanation:**
- Groups all rows by `department`
- Counts how many employees belong to each department

🧩 **Output Example:**
| department | total_employees |
|-------------|----------------|
| HR          | 5              |
| IT          | 8              |
| Sales       | 3              |

---

### 🔹 Example 2 – Average Salary per Department

```sql
SELECT department, AVG(salary) AS average_salary
FROM employees
GROUP BY department;
```

✅ **Explanation:**
- Groups employees by department
- Calculates the average salary for each group

---

### 🔹 Example 3 – Group by Multiple Columns

You can group by more than one column.

```sql
SELECT department, job_title, COUNT(*) AS count
FROM employees
GROUP BY department, job_title;
```

✅ **Explanation:**
- Groups rows first by `department`, then by `job_title`
- Counts how many employees have each job title in each department

---
