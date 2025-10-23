
---

# 🧵 PostgreSQL — String Functions

## 1. Introduction

PostgreSQL provides a wide variety of **string functions** to manipulate and analyze text data.  
These functions help with tasks like trimming, concatenating, searching, replacing, and formatting strings.

---

## 2. Common String Functions

| Function | Description | Example | Result |
|----------|-------------|---------|--------|
| `LENGTH(str)` | Returns the length of a string | `SELECT LENGTH('PostgreSQL');` | 10 |
| `UPPER(str)` | Converts string to uppercase | `SELECT UPPER('postgres');` | POSTGRES |
| `LOWER(str)` | Converts string to lowercase | `SELECT LOWER('POSTGRES');` | postgres |
| `INITCAP(str)` | Capitalizes first letter of each word | `SELECT INITCAP('hello world');` | Hello World |
| `CONCAT(str1, str2, ...)` | Concatenates multiple strings | `SELECT CONCAT('Post', 'gre', 'SQL');` | PostgreSQL |
| `TRIM(str)` | Removes leading and trailing spaces | `SELECT TRIM('  hello  ');` | hello |
| `LTRIM(str)` | Removes leading spaces | `SELECT LTRIM('  hello');` | hello |
| `RTRIM(str)` | Removes trailing spaces | `SELECT RTRIM('hello  ');` | hello |
| `REPLACE(str, from, to)` | Replaces substring | `SELECT REPLACE('PostgreSQL', 'SQL', 'DB');` | PostgreDB |
| `SUBSTRING(str FROM start FOR length)` | Extracts a substring | `SELECT SUBSTRING('PostgreSQL' FROM 5 FOR 3);` | gre |
| `POSITION(sub IN str)` | Finds position of substring | `SELECT POSITION('gre' IN 'PostgreSQL');` | 5 |

---

## 3. Example Use Case

```sql
SELECT
    LENGTH('PostgreSQL') AS str_length,
    UPPER('postgres') AS upper_str,
    LOWER('POSTGRES') AS lower_str,
    INITCAP('hello world') AS init_cap,
    CONCAT('Post', 'gre', 'SQL') AS concat_str,
    TRIM('  text  ') AS trimmed_str,
    REPLACE('PostgreSQL', 'SQL', 'DB') AS replaced_str,
    SUBSTRING('PostgreSQL' FROM 5 FOR 3) AS sub_str;
```

Output:

| str_length | upper_str | lower_str | init_cap    | concat_str  | trimmed_str | replaced_str | sub_str |
|------------|-----------|-----------|------------|------------|------------|--------------|---------|
| 10         | POSTGRES  | postgres  | Hello World | PostgreSQL | text       | PostgreDB    | gre     |

---

## ✅ Summary

- String functions help in **manipulating and analyzing text data**.  
- Common operations include: **length, case conversion, trimming, concatenation, substring extraction, search, and replace**.  
- Useful for cleaning data, formatting output, or preparing strings for queries.

---

**Next Topic →** [Date and Time Functions in PostgreSQL](./Date_Functions.md)
