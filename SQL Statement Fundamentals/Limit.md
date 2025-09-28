


# PostgreSQL LIMIT Clause

The `LIMIT` clause is used to restrict the number of rows returned by a query.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
LIMIT number;
```

- `number` → The maximum number of rows to return.
- Often used with `ORDER BY` to fetch top results.

## Examples

### Get the first 5 rows
```sql
SELECT *
FROM students
LIMIT 5;
```

### Get the top 3 oldest students
```sql
SELECT *
FROM students
ORDER BY age DESC
LIMIT 3;
```

### Get the youngest student
```sql
SELECT *
FROM students
ORDER BY age ASC
LIMIT 1;
```

## Notes
- `LIMIT` is evaluated **after ORDER BY**.
- Use with `OFFSET` for pagination (e.g., showing results page by page).
- Without `ORDER BY`, the rows returned by `LIMIT` may be arbitrary.
