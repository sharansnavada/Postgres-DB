


# PostgreSQL SELECT DISTINCT Keyword

The `DISTINCT` keyword is used to return only **unique values** by removing duplicates from the result set.

## Basic Syntax
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

- `DISTINCT` applies to all the columns listed after it.
- If multiple columns are selected, the combination of their values must be unique.

## Examples

### Select unique values from one column
```sql
SELECT DISTINCT city
FROM students;
```
(Returns a list of unique cities where students live.)

### Select unique combinations from multiple columns
```sql
SELECT DISTINCT first_name, last_name
FROM students;
```
(Returns unique pairs of first_name and last_name.)

### Using DISTINCT with conditions
```sql
SELECT DISTINCT age
FROM students
WHERE age > 18;
```

### Using DISTINCT with ORDER BY
```sql
SELECT DISTINCT city
FROM students
ORDER BY city ASC;
```

## Notes
- `DISTINCT` works on the entire row of selected columns.
- It may increase query execution time on large datasets because duplicates must be removed.
- For counting unique values, use:
```sql
SELECT COUNT(DISTINCT column_name) FROM table_name;
```
