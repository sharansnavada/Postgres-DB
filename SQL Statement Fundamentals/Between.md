


# PostgreSQL BETWEEN Operator

The `BETWEEN` operator is used to filter the result set within a specified range.  
It is inclusive, meaning the boundary values are included.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

- `value1` → The lower boundary.
- `value2` → The upper boundary.
- Works with numbers, text, and dates.

## Examples

### Select rows with numeric range
```sql
SELECT *
FROM students
WHERE age BETWEEN 18 AND 25;
```
(Returns students aged 18 to 25, inclusive)

### Select rows with NOT BETWEEN
```sql
SELECT *
FROM students
WHERE age NOT BETWEEN 18 AND 25;
```

### Select rows with date range
```sql
SELECT *
FROM students
WHERE admission_date BETWEEN '2023-01-01' AND '2023-12-31';
```

### Select rows with text range
```sql
SELECT *
FROM students
WHERE first_name BETWEEN 'A' AND 'M';
```

## Notes
- `BETWEEN` includes both boundary values (`value1` and `value2`).
- For dates, ensure proper format `'YYYY-MM-DD'`.
- Equivalent to using `>=` and `<=` operators:
```sql
WHERE column_name >= value1 AND column_name <= value2;
```
