


---

## 🧭 Understanding `TO_CHAR()` in PostgreSQL

The `TO_CHAR()` function in PostgreSQL is used to **convert date, time, or number values into formatted text strings**.

### 📘 Syntax

```sql
TO_CHAR(value, format)
```

- **value** → the timestamp, date, or number you want to format.  
- **format** → the format string that defines how you want the output to appear.

---

### 🕒 Example 1 — Format Current Timestamp

```sql
SELECT TO_CHAR(NOW(), 'YYYY-MM-DD HH24:MI:SS') AS formatted_timestamp;
```

Output:
```
2025-10-23 21:30:45
```

✅ Explanation:
- `YYYY` → 4-digit year  
- `MM` → month  
- `DD` → day  
- `HH24` → hour (24-hour format)  
- `MI` → minutes  
- `SS` → seconds  

---

### 📅 Example 2 — Custom Date Formats

```sql
SELECT
    TO_CHAR(NOW(), 'Month DD, YYYY') AS full_date,
    TO_CHAR(NOW(), 'Dy, Mon DD') AS short_date,
    TO_CHAR(NOW(), 'YYYY/MM/DD') AS numeric_date;
```

Output:
| full_date         | short_date   | numeric_date |
|--------------------|--------------|---------------|
| October 23, 2025   | Thu, Oct 23  | 2025/10/23    |

---

### 🧠 Example 3 — Extracting Specific Components as Text

```sql
SELECT
    TO_CHAR(NOW(), 'Day') AS day_name,
    TO_CHAR(NOW(), 'HH12:MI AM') AS time_12hr,
    TO_CHAR(NOW(), 'HH24:MI') AS time_24hr;
```

Output:
| day_name | time_12hr  | time_24hr |
|-----------|-------------|-----------|
| Thursday  | 09:30 PM    | 21:30     |

---

### 💰 Example 4 — Formatting Numbers (Optional Use)

`TO_CHAR()` can also format numbers:

```sql
SELECT TO_CHAR(1234567.89, '9,999,999.99') AS formatted_number;
```

Output:
```
1,234,567.89
```

---

### ✅ Summary

- `TO_CHAR()` is powerful for **presenting timestamps and numbers in readable formats**.  
- Common use: `TO_CHAR(NOW(), 'YYYY-MM-DD HH24:MI:SS')`  
- Supports flexible tokens like:
  - `YYYY` — year  
  - `MM` — month  
  - `DD` — day  
  - `HH24` / `HH12` — hour  
  - `MI` — minutes  
  - `SS` — seconds  
  - `Month`, `Day`, `Dy`, `Mon` — textual date parts  

---

**Next Topic →** [Time Zone Handling in PostgreSQL](./TimeZone_Handling.md)
