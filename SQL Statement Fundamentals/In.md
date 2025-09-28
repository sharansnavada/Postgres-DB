


# PostgreSQL IN Operator

The `IN` operator is used to filter rows where a column's value matches any value in a specified list.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

- `value1, value2, ...` → List of values to match.
- Can also be used with subqueries to match a dynamic list.

## Examples

### Select rows matching a list of values
```sql
SELECT *
FROM students
WHERE city IN ('London', 'Paris', 'Tokyo');
```

### Select rows NOT in a list
```sql
SELECT *
FROM students
WHERE city NOT IN ('London', 'Paris');
```

### Using IN with numbers
```sql
SELECT *
FROM students
WHERE age IN (18, 20, 22);
```

### Using IN with a subquery
```sql
SELECT *
FROM students
WHERE city IN (
    SELECT city
    FROM offices
    WHERE country = 'UK'
);
```

## Notes
- `IN` simplifies multiple `OR` conditions.
- Use `NOT IN` to exclude multiple values.
- When using `NOT IN` with subqueries, ensure the subquery does not return NULLs, or results may be unexpected.
