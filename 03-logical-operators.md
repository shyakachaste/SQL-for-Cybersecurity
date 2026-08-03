# Logical Operators in SQL

Logical operators allow you to combine multiple conditions when filtering data.

They help retrieve more specific information by checking whether one or more conditions are true.

In cybersecurity, logical operators are commonly used to investigate login attempts, suspicious activity, user accounts, devices, and security events.

---

# 1. AND Operator

## Description

The `AND` operator returns records only when **all conditions are true**.

## Syntax

```sql
SELECT columns
FROM table_name
WHERE condition1 AND condition2;
```

---

## Example

Retrieve failed login attempts after business hours.

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
```

Both conditions must be true:

- Login occurred after 18:00
- Login was unsuccessful

---

## Another Example

Retrieve Marketing employees located in the East building.

```sql
SELECT *
FROM employees
WHERE department = 'Marketing'
AND office LIKE 'East%';
```

Only employees matching **both** conditions are returned.

---

# 2. OR Operator

## Description

The `OR` operator returns records when **at least one condition is true**.

## Syntax

```sql
SELECT columns
FROM table_name
WHERE condition1 OR condition2;
```

---

## Example

Retrieve login attempts on two specific dates.

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09'
OR login_date = '2022-05-08';
```

Rows from either date are returned.

---

## Another Example

Retrieve employees in the Finance or Sales department.

```sql
SELECT *
FROM employees
WHERE department = 'Finance'
OR department = 'Sales';
```

Employees from either department are included.

---

# 3. NOT Operator

## Description

The `NOT` operator reverses a condition.

It returns records that **do not** match the specified condition.

## Syntax

```sql
SELECT columns
FROM table_name
WHERE NOT condition;
```

---

## Example

Retrieve employees who are not in Information Technology.

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

---

## Using NOT with LIKE

Retrieve login attempts that did not originate in Mexico.

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

This excludes:

```text
MEX
MEXICO
```

---

# Combining Logical Operators

Logical operators can be combined to create more specific queries.

Example:

```sql
SELECT *
FROM log_in_attempts
WHERE success = FALSE
AND country = 'Canada';
```

Retrieve failed login attempts originating from Canada.

---

Example:

```sql
SELECT *
FROM employees
WHERE department = 'Finance'
OR department = 'Marketing';
```

Returns employees from either department.

---

# Boolean Values

Some database columns store Boolean values.

Example:

```text
TRUE
FALSE
```

Example query:

```sql
SELECT *
FROM log_in_attempts
WHERE success = FALSE;
```

This returns only unsuccessful login attempts.

---

# Cybersecurity Use Cases

## Investigate failed logins after business hours

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00'
AND success = FALSE;
```

---

## Investigate logins outside a specific country

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

---

## Find employees in affected departments

```sql
SELECT *
FROM employees
WHERE department = 'Finance'
OR department = 'Sales';
```

---

## Find employees in a specific building

```sql
SELECT *
FROM employees
WHERE department = 'Marketing'
AND office LIKE 'East%';
```

---

# Quick Reference

| Operator | Purpose |
|----------|---------|
| `AND` | All conditions must be true |
| `OR` | At least one condition must be true |
| `NOT` | Reverse a condition |
| `LIKE` | Match text patterns |
| `%` | Wildcard matching zero or more characters |

---

# Summary

Logical operators make SQL queries more powerful by combining or excluding conditions. Security analysts use `AND`, `OR`, and `NOT` to investigate login activity, filter employees or devices, detect suspicious events, and retrieve precise security information from databases.
