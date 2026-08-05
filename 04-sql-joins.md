# SQL Joins

SQL joins combine data from multiple related tables using a common column.

Joins allow you to retrieve information stored across different tables in a relational database.

In cybersecurity, joins are commonly used to correlate users, devices, login attempts, assets, and security events.

---

# Why Use Joins?

Sometimes the information you need is stored in different tables.

Example:

**employees**

| employee_id | username | device_id |
|--------------|----------|-----------|
|1001|john|A123|

**machines**

| device_id | operating_system |
|------------|------------------|
|A123|Windows 11|

Neither table contains all the information.

Using a JOIN allows SQL to combine them into one result.

---

# Common Column

Tables are joined using a shared column.

Example:

```text
employees.device_id
machines.device_id
```

This shared column is called the **join key**.

---

# INNER JOIN

## Description

Returns only rows that exist in **both tables**.

If no matching record exists, the row is excluded.

---

## Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

---

## Example

Match employees with their assigned machines.

```sql
SELECT *
FROM machines
INNER JOIN employees
ON machines.device_id = employees.device_id;
```

Only employees with assigned machines are returned.

---

## Another Example

Retrieve employee login attempts.

```sql
SELECT *
FROM employees
INNER JOIN log_in_attempts
ON employees.username = log_in_attempts.username;
```

Only employees with login records appear.

---

# LEFT JOIN

## Description

Returns **all rows from the left table**, plus matching rows from the right table.

If there is no match, SQL returns **NULL** for the missing values.

---

## Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

---

## Example

```sql
SELECT *
FROM machines
LEFT JOIN employees
ON machines.device_id = employees.device_id;
```

Returns:

- Every machine
- Assigned employee (if one exists)
- NULL if the machine has no assigned employee

---

# RIGHT JOIN

## Description

Returns **all rows from the right table**, plus matching rows from the left table.

If there is no match, SQL returns **NULL**.

---

## Syntax

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

---

## Example

```sql
SELECT *
FROM machines
RIGHT JOIN employees
ON machines.device_id = employees.device_id;
```

Returns:

- Every employee
- Assigned machine (if one exists)
- NULL if the employee has no machine

---

# Understanding NULL

NULL means there is **no matching value**.

Example:

| Machine | Username |
|---------|----------|
|Laptop A|john|
|Laptop B|NULL|

Laptop B has not been assigned to any employee.

---

# Dot Notation

When two tables contain columns with the same name, specify which table the column belongs to.

Example:

```sql
machines.device_id
employees.device_id
```

This avoids ambiguity.

---

# Choosing Specific Columns

Instead of using:

```sql
SELECT *
```

You can return only the needed information.

Example:

```sql
SELECT machines.device_id,
       employees.username,
       machines.operating_system
FROM machines
INNER JOIN employees
ON machines.device_id = employees.device_id;
```

This makes the output easier to read.

---

# Cybersecurity Use Cases

## Match employees with company devices

```sql
SELECT *
FROM machines
INNER JOIN employees
ON machines.device_id = employees.device_id;
```

---

## Find unassigned devices

```sql
SELECT *
FROM machines
LEFT JOIN employees
ON machines.device_id = employees.device_id;
```

Rows with:

```text
username = NULL
```

represent devices without assigned users.

---

## Find employees without assigned devices

```sql
SELECT *
FROM machines
RIGHT JOIN employees
ON machines.device_id = employees.device_id;
```

Rows with machine information set to NULL indicate employees without assigned devices.

---

## Match login attempts with employees

```sql
SELECT *
FROM employees
INNER JOIN log_in_attempts
ON employees.username = log_in_attempts.username;
```

Useful for investigating authentication activity.

---

# Quick Reference

| Join | Returns |
|------|----------|
| INNER JOIN | Only matching rows from both tables |
| LEFT JOIN | All rows from the left table + matching rows |
| RIGHT JOIN | All rows from the right table + matching rows |
| NULL | No matching record exists |

---

# Summary

SQL joins combine related tables using a shared column.

- **INNER JOIN** returns only matching records.
- **LEFT JOIN** keeps all rows from the left table.
- **RIGHT JOIN** keeps all rows from the right table.
- **NULL** indicates that no matching record exists.

Joins are essential for security analysts because important information is often distributed across multiple tables, such as employees, devices, login attempts, and security events.
