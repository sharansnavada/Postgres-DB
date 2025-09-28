

# PostgreSQL SELECT Keyword

The `SELECT` statement is used to retrieve data from a database.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name;
```

- `column1, column2`: The columns you want to fetch.
- `*`: Selects all columns from the table.
- `table_name`: The name of the table you are querying.

## Examples

### Select all columns
```sql
SELECT * 
FROM students;
```

### Select specific columns
```sql
SELECT first_name, last_name
FROM students;
```

### Select with a condition
```sql
SELECT first_name, age
FROM students
WHERE age > 20;
```

### Select with sorting
```sql
SELECT first_name, age
FROM students
ORDER BY age DESC;
```

### Select with limit
```sql
SELECT *
FROM students
LIMIT 5;
```

### Select with offset
```sql
SELECT *
FROM students
OFFSET 5
LIMIT 5;
```

## Notes
- Use `WHERE` to filter rows.
- Use `ORDER BY` to sort results.
- Use `LIMIT` and `OFFSET` for pagination.
- Combine with functions like `COUNT()`, `SUM()`, `AVG()` for aggregations.
