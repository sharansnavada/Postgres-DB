# PostgreSQL COUNT() Function

The `COUNT()` function is used to return the number of rows that match a condition.

## Basic Syntax
```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

- `COUNT(*)` → Counts all rows, including NULLs.
- `COUNT(column_name)` → Counts only non-NULL values in that column.
- `COUNT(DISTINCT column_name)` → Counts unique non-NULL values.

## Examples

### Count all rows in a table
```sql
SELECT COUNT(*)
FROM students;
```

### Count non-NULL values in a column
```sql
SELECT COUNT(age)
FROM students;
```

### Count unique values
```sql
SELECT COUNT(DISTINCT city)
FROM students;
```

### Count with condition
```sql
SELECT COUNT(*)
FROM students
WHERE age > 18;
```

### Count grouped results
```sql
SELECT city, COUNT(*)
FROM students
GROUP BY city;
```

## Notes
- `COUNT()` is an aggregate function, often used with `GROUP BY`.
- When using `COUNT(column_name)`, NULL values are ignored.
- For performance on large tables, consider indexing the column being counted.
