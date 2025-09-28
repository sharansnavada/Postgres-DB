


# PostgreSQL ORDER BY Clause

The `ORDER BY` clause is used to sort the result set of a query by one or more columns.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;
```

- `ASC` → Sorts in ascending order (default).
- `DESC` → Sorts in descending order.
- Multiple columns can be used for sorting (first by column1, then column2, etc.).

## Examples

### Order by one column (ascending)
```sql
SELECT *
FROM students
ORDER BY age ASC;
```

### Order by one column (descending)
```sql
SELECT *
FROM students
ORDER BY age DESC;
```

### Order by multiple columns
```sql
SELECT *
FROM students
ORDER BY city ASC, age DESC;
```
(Sorts first by city alphabetically, then by age within each city.)

### Order by an alias
```sql
SELECT first_name, age * 12 AS age_in_months
FROM students
ORDER BY age_in_months DESC;
```

### Order by function result
```sql
SELECT first_name, LENGTH(first_name) AS name_length
FROM students
ORDER BY LENGTH(first_name) ASC;
```

## Notes
- `ORDER BY` comes **after** `WHERE` but **before** `LIMIT` or `OFFSET`.
- Sorting large tables can be slow; consider indexing columns used frequently in sorting.
- You can order by column names, aliases, or even expressions.
