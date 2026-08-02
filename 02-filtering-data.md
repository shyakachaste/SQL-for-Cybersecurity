# Filtering Data with SQL

Filtering allows you to retrieve only the records that meet specific conditions instead of returning every row in a table.

In cybersecurity, filtering is essential for investigating specific users, devices, login attempts, IP addresses, operating systems, and security events.

---

# 1. DESCRIBE

## Description

The `DESCRIBE` command displays the structure of a table.

It shows:

- Column names
- Data types
- Additional table information

## Syntax

```sql
DESCRIBE table_name;
```

## Example

```sql
DESCRIBE machines;
```

```sql
DESCRIBE employees;
```

Use `DESCRIBE` whenever you are unsure about column names before writing a query.

---

# 2. Selecting Specific Columns

Instead of retrieving every column, you can select only the information you need.

## Syntax

```sql
SELECT column1, column2
FROM table_name;
```

## Example

```sql
SELECT device_id, operating_system
FROM machines;
```

Returns only the device ID and operating system.

---

# 3. WHERE Clause

## Description

The `WHERE` clause filters records that satisfy a specific condition.

## Syntax

```sql
SELECT columns
FROM table_name
WHERE condition;
```

---

## Example

Retrieve machines running **OS 2**:

```sql
SELECT device_id, operating_system
FROM machines
WHERE operating_system = 'OS 2';
```

Only rows matching the condition are returned.

---

# String Values

Text values must be enclosed in single quotes.

Correct:

```sql
WHERE operating_system = 'OS 2';
```

Incorrect:

```sql
WHERE operating_system = OS 2;
```

Column names should never be placed inside quotes.

---

# Filtering Departments

Example:

Retrieve Finance employees.

```sql
SELECT *
FROM employees
WHERE department = 'Finance';
```

---

Retrieve Sales employees.

```sql
SELECT *
FROM employees
WHERE department = 'Sales';
```

---

# Filtering by Office

Example:

```sql
SELECT *
FROM employees
WHERE office = 'South-109';
```

Returns the employee assigned to office **South-109**.

---

# 4. LIKE Operator

## Description

The `LIKE` operator searches for patterns instead of exact matches.

## Syntax

```sql
WHERE column LIKE 'pattern';
```

---

# Wildcard (%)

The `%` wildcard represents zero or more characters.

---

## Starts With

```sql
WHERE office LIKE 'South%';
```

Matches:

```text
South-101
South-204
South-310
```

---

## Ends With

```sql
WHERE office LIKE '%South';
```

Matches:

```text
Building-South
Office-South
```

---

## Contains

```sql
WHERE office LIKE '%South%';
```

Matches any value containing "South".

---

# Common Filtering Examples

Retrieve all employees in the South building.

```sql
SELECT *
FROM employees
WHERE office LIKE 'South%';
```

---

Retrieve all Finance employees.

```sql
SELECT *
FROM employees
WHERE department = 'Finance';
```

---

Retrieve machines running OS 2.

```sql
SELECT device_id, operating_system
FROM machines
WHERE operating_system = 'OS 2';
```

---

# Cybersecurity Use Cases

## Find compromised devices

```sql
SELECT *
FROM machines
WHERE operating_system = 'OS 2';
```

---

## Find employees in an affected building

```sql
SELECT *
FROM employees
WHERE office LIKE 'South%';
```

---

## Investigate users from a department

```sql
SELECT *
FROM employees
WHERE department = 'Finance';
```

---

## Identify a specific employee

```sql
SELECT *
FROM employees
WHERE office = 'South-109';
```

---

# Quick Reference

| SQL Statement | Purpose |
|--------------|---------|
| `DESCRIBE` | View table structure |
| `SELECT` | Retrieve data |
| `FROM` | Specify the table |
| `WHERE` | Filter records |
| `=` | Exact match |
| `LIKE` | Pattern matching |
| `%` | Wildcard for zero or more characters |

---

# Summary

The `WHERE` clause filters records based on conditions, while the `LIKE` operator searches for patterns in text values. These techniques help security analysts retrieve targeted information quickly during investigations and system audits.
