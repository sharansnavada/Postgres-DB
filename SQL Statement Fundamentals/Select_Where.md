# PostgreSQL SELECT WHERE Clause

The `WHERE` clause is used to filter records that meet specific conditions.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

- `condition` → The criteria that rows must satisfy to be returned.
- Operators include `=`, `!=`, `<`, `>`, `<=`, `>=`, `AND`, `OR`, `NOT`, `IN`, `BETWEEN`, `LIKE`, and `ILIKE`.

## Examples

### Select with equality condition
```sql
SELECT *
FROM students
WHERE age = 20;
```

### Select with multiple conditions
```sql
SELECT *
FROM students
WHERE age > 18 AND city = 'New York';
```

### Select using OR
```sql
SELECT *
FROM students
WHERE city = 'London' OR city = 'Paris';
```

### Select with BETWEEN
```sql
SELECT *
FROM students
WHERE age BETWEEN 18 AND 25;
```

### Select with IN
```sql
SELECT *
FROM students
WHERE city IN ('London', 'Paris', 'Tokyo');
```

### Select with LIKE (case-sensitive)
```sql
SELECT *
FROM students
WHERE first_name LIKE 'A%';
```
(Returns names starting with "A")

### Select with ILIKE (case-insensitive)
```sql
SELECT *
FROM students
WHERE first_name ILIKE 'a%';
```

### Select with NOT
```sql
SELECT *
FROM students
WHERE city NOT IN ('London', 'Paris');
```

## Notes
- `WHERE` is used before `ORDER BY`, `GROUP BY`, and `LIMIT`.
- Use `ILIKE` instead of `LIKE` for case-insensitive matching in PostgreSQL.
- Combine multiple conditions with `AND`, `OR`, and parentheses `()` for clarity.
