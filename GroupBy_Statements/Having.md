# HAVING in PostgreSQL

##  HAVING

The **HAVING** clause is used to filter the results of a `GROUP BY` query.  
It is similar to `WHERE`, but:
- `WHERE` filters **rows before grouping**
- `HAVING` filters **groups after grouping**

---

### 🔹 Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

---

### 🔹 Example 1 – Departments with More Than 5 Employees

```sql
SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

✅ **Explanation:**
- Groups rows by `department`
- Filters only departments that have more than 5 employees

---

### 🔹 Example 2 – Average Salary Greater Than 50,000

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

✅ **Explanation:**
- Calculates average salary for each department
- Shows only departments with an average salary greater than ₹50,000

---

### 🔹 Example 3 – Combining WHERE and HAVING

```sql
SELECT department, COUNT(*) AS total_employees
FROM employees
WHERE status = 'Active'
GROUP BY department
HAVING COUNT(*) > 3;
```

✅ **Explanation:**
1. The `WHERE` clause filters only **active employees** before grouping.  
2. Then the `GROUP BY` creates groups by department.  
3. Finally, `HAVING` filters only departments with more than 3 active employees.

---

## 🧠 Key Differences Between WHERE and HAVING

| Feature | WHERE | HAVING |
|----------|--------|---------|
| Filters | Individual rows | Groups after aggregation |
| Used With | Can be used without GROUP BY | Used only with GROUP BY |
| Aggregates | Cannot use aggregate functions | Can use aggregate functions |
| Execution Order | Before grouping | After grouping |

---

### ✅ Summary

- Use **GROUP BY** to group rows that share the same values.
- Use **HAVING** to filter results after grouping.
- Always remember:  
  ➤ `WHERE` → filters rows before grouping  
  ➤ `HAVING` → filters groups after grouping

By practicing with real tables and sample data, you’ll quickly understand how these clauses help in summarizing and analyzing data effectively.
