# ➗ PostgreSQL — Mathematical Functions

## 1. Introduction

PostgreSQL offers a wide range of **mathematical functions and operators** that help perform arithmetic, rounding, trigonometric, and logarithmic calculations.

---

## 2. Basic Arithmetic Operators

| Operator | Description | Example | Result |
|-----------|--------------|----------|---------|
| `+` | Addition | `SELECT 10 + 5;` | 15 |
| `-` | Subtraction | `SELECT 10 - 5;` | 5 |
| `*` | Multiplication | `SELECT 10 * 5;` | 50 |
| `/` | Division | `SELECT 10 / 4;` | 2.5 |
| `%` | Modulus (Remainder) | `SELECT 10 % 3;` | 1 |

---

## 3. Common Mathematical Functions

| Function | Description | Example | Result |
|-----------|--------------|----------|---------|
| `ABS(x)` | Absolute value | `SELECT ABS(-5);` | 5 |
| `CEIL(x)` or `CEILING(x)` | Smallest integer ≥ x | `SELECT CEIL(4.2);` | 5 |
| `FLOOR(x)` | Largest integer ≤ x | `SELECT FLOOR(4.8);` | 4 |
| `ROUND(x, n)` | Rounds x to n decimal places | `SELECT ROUND(12.3456, 2);` | 12.35 |
| `POWER(x, y)` | x raised to power y | `SELECT POWER(2, 3);` | 8 |
| `SQRT(x)` | Square root | `SELECT SQRT(25);` | 5 |
| `CBRT(x)` | Cube root | `SELECT CBRT(27);` | 3 |
| `SIGN(x)` | Sign of a number (-1, 0, 1) | `SELECT SIGN(-10);` | -1 |
| `PI()` | Returns π (pi) | `SELECT PI();` | 3.141593 |

---

## 4. Trigonometric Functions

| Function | Description | Example | Result |
|-----------|--------------|----------|---------|
| `SIN(x)` | Sine of x (radians) | `SELECT SIN(PI()/2);` | 1 |
| `COS(x)` | Cosine of x (radians) | `SELECT COS(0);` | 1 |
| `TAN(x)` | Tangent of x | `SELECT TAN(PI()/4);` | 1 |
| `ASIN(x)` | Arc sine | `SELECT ASIN(1);` | 1.570796 |
| `ACOS(x)` | Arc cosine | `SELECT ACOS(0);` | 1.570796 |
| `ATAN(x)` | Arc tangent | `SELECT ATAN(1);` | 0.785398 |
| `ATAN2(y, x)` | Arc tangent of y/x | `SELECT ATAN2(1, 1);` | 0.785398 |

---

## 5. Logarithmic and Exponential Functions

| Function | Description | Example | Result |
|-----------|--------------|----------|---------|
| `LN(x)` | Natural logarithm | `SELECT LN(10);` | 2.302585 |
| `LOG(base, x)` | Logarithm base `base` | `SELECT LOG(10, 1000);` | 3 |
| `EXP(x)` | Exponential (e^x) | `SELECT EXP(1);` | 2.718282 |

---

## 6. Random and Rounding Functions

| Function | Description | Example | Result |
|-----------|--------------|----------|---------|
| `RANDOM()` | Random float between 0 and 1 | `SELECT RANDOM();` | 0.456782 (varies) |
| `TRUNC(x, n)` | Truncates to n decimal places | `SELECT TRUNC(12.9876, 2);` | 12.98 |
| `WIDTH_BUCKET(x, min, max, count)` | Returns the histogram bucket number | `SELECT WIDTH_BUCKET(5.35, 0.0, 10.0, 5);` | 3 |

---

## 7. Example Use Case

```sql
SELECT
    ABS(-10) AS abs_val,
    ROUND(PI(), 2) AS pi_value,
    POWER(3, 4) AS cube,
    SIN(RADIANS(90)) AS sin_value,
    LOG(10, 100) AS log_result;
```

Output:

| abs_val | pi_value | cube | sin_value | log_result |
|----------|-----------|------|------------|-------------|
| 10 | 3.14 | 81 | 1 | 2 |

---

## ✅ Summary

- PostgreSQL provides rich math support with functions like `POWER()`, `ROUND()`, `SQRT()`, etc.  
- Trigonometric functions use **radians**, not degrees.  
- Use `RANDOM()` for generating random numbers.  
- `LOG()` and `LN()` are useful for scientific or statistical calculations.

---

**Next Topic →** [String Functions in PostgreSQL](./String_Functions.md)
