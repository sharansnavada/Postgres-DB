


# PostgreSQL LIKE and ILIKE Operators

The `LIKE` operator is used for pattern matching in strings.  
The `ILIKE` operator is the case-insensitive version of `LIKE`.

## Basic Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE 'pattern';
```

- `%` → Matches zero or more characters.
- `_` → Matches exactly one character.
- `ILIKE` works the same as `LIKE` but ignores case.

## Examples

### Using LIKE
```sql
SELECT *
FROM students
WHERE first_name LIKE 'A%';
```
(Returns students whose first names start with "A")

```sql
SELECT *
FROM students
WHERE first_name LIKE '%son';
```
(Returns students whose first names end with "son")

```sql
SELECT *
FROM students
WHERE first_name LIKE '_a%';
```
(Returns students whose second letter is "a")

### Using ILIKE (case-insensitive)
```sql
SELECT *
FROM students
WHERE first_name ILIKE 'a%';
```
(Returns names starting with "a" or "A")

```sql
SELECT *
FROM students
WHERE first_name ILIKE '%son';
```
(Returns names ending with "son", "Son", "SON", etc.)

## Notes
- `LIKE` is case-sensitive in PostgreSQL.
- Use `ILIKE` for case-insensitive pattern matching.
- `%` and `_` are wildcards in patterns.
- You can combine with `NOT` to exclude matching patterns:
```sql
WHERE first_name NOT LIKE 'A%';
```
