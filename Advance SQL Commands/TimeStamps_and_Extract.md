# 🕒 PostgreSQL — Timestamps and Extract

## 1. Introduction

In PostgreSQL, **timestamps** store both **date and time** values.  
They’re often used for tracking when records are created, updated, or logged.

There are two main timestamp types:
- `timestamp` (or `timestamp without time zone`)
- `timestamptz` (or `timestamp with time zone`)

---

## 2. Creating a Table with Timestamps

```sql
CREATE TABLE events (
    id SERIAL PRIMARY KEY,
    event_name VARCHAR(50),
    event_time TIMESTAMP DEFAULT NOW()
);
```

✅ Here:
- `NOW()` inserts the **current date and time** when the row is created.
- Example inserted value: `2025-10-23 21:30:45`

---

## 3. Inserting and Viewing Timestamp Values

```sql
INSERT INTO events (event_name) VALUES ('PostgreSQL Study Session');
SELECT * FROM events;
```

Output example:

| id | event_name               | event_time           |
|----|--------------------------|----------------------|
| 1  | PostgreSQL Study Session | 2025-10-23 21:30:45  |

---

## 4. Getting the Current Date and Time

| Function | Description | Example Output |
|-----------|--------------|----------------|
| `NOW()` | Current date and time | `2025-10-23 21:30:45.123456+05:30` |
| `CURRENT_DATE` | Current date only | `2025-10-23` |
| `CURRENT_TIME` | Current time only | `21:30:45.123456+05:30` |
| `LOCALTIMESTAMP` | Current timestamp without timezone | `2025-10-23 21:30:45.123456` |

Example:
```sql
SELECT NOW(), CURRENT_DATE, CURRENT_TIME, LOCALTIMESTAMP;
```

---

## 5. Extracting Parts of a Timestamp

PostgreSQL provides the **`EXTRACT()`** function to get specific parts of a date or timestamp.

### Syntax:
```sql
EXTRACT(field FROM source)
```

**Common fields:**
- `year`
- `month`
- `day`
- `hour`
- `minute`
- `second`
- `dow` → day of week (0=Sunday)
- `doy` → day of year

### Example:
```sql
SELECT
    EXTRACT(YEAR FROM NOW()) AS year,
    EXTRACT(MONTH FROM NOW()) AS month,
    EXTRACT(DAY FROM NOW()) AS day,
    EXTRACT(DOW FROM NOW()) AS day_of_week;
```

Output example:

| year | month | day | day_of_week |
|------|--------|-----|-------------|
| 2025 | 10     | 23  | 4           |

---

## 6. Working with Time Intervals

You can add or subtract time intervals to timestamps.

```sql
SELECT
    NOW() AS current_time,
    NOW() + INTERVAL '1 day' AS tomorrow,
    NOW() - INTERVAL '2 hours' AS two_hours_ago;
```

Example Output:

| current_time           | tomorrow              | two_hours_ago         |
|-------------------------|-----------------------|-----------------------|
| 2025-10-23 21:30:45+05:30 | 2025-10-24 21:30:45+05:30 | 2025-10-23 19:30:45+05:30 |

---

## 7. Age Function

The **`AGE()`** function returns the time difference between two timestamps.

```sql
SELECT AGE(NOW(), TIMESTAMP '2020-05-10');
```

Output:
```
5 years 5 mons 13 days 21:30:45.123456
```

---

## 8. Formatting Timestamps

Use `TO_CHAR()` to format timestamps into readable strings.

```sql
SELECT TO_CHAR(NOW(), 'YYYY-MM-DD HH24:MI:SS') AS formatted_time;
```

Output:
```
2025-10-23 21:30:45
```

Other common patterns:
| Pattern | Description | Example |
|----------|--------------|----------|
| `YYYY` | Year | `2025` |
| `MM` | Month | `10` |
| `DD` | Day | `23` |
| `HH24` | Hour (24-hour) | `21` |
| `MI` | Minutes | `30` |
| `SS` | Seconds | `45` |

---

## 🧩 Example Use Case

```sql
CREATE TABLE logs (
    id SERIAL PRIMARY KEY,
    message TEXT,
    created_at TIMESTAMPTZ DEFAULT NOW()
);

INSERT INTO logs (message) VALUES ('User logged in');
INSERT INTO logs (message) VALUES ('Data updated');

SELECT
    id,
    message,
    TO_CHAR(created_at, 'DD Mon YYYY HH24:MI') AS log_time,
    EXTRACT(HOUR FROM created_at) AS hour_logged
FROM logs;
```

Output example:

| id | message         | log_time            | hour_logged |
|----|------------------|--------------------|--------------|
| 1  | User logged in  | 23 Oct 2025 21:31  | 21           |
| 2  | Data updated    | 23 Oct 2025 21:32  | 21           |

---

## ✅ Summary

- `timestamp` and `timestamptz` store date & time.  
- `NOW()` gives the current timestamp.  
- `EXTRACT()` pulls parts like year, month, or day.  
- `AGE()` calculates time difference.  
- `TO_CHAR()` formats timestamps.

---

**Next Topic →** [Date Functions in PostgreSQL](./Date_Functions.md)
