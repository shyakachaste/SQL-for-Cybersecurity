# SQL Fundamentals

SQL (Structured Query Language) is a language used to communicate with relational databases. It allows users to retrieve, filter, sort, insert, update, and delete data stored in tables.

For cybersecurity professionals, SQL is commonly used to investigate login activity, analyze logs, search for suspicious behavior, and retrieve security-related information from databases.

---

# Database Concepts

## Database

A database is an organized collection of related data.

Example:

```
organization
```

---

## Table

A table stores related information in rows and columns.

Example:

```
machines
```

```
+-----------+------------------+---------------+
| device_id | operating_system | employee_id   |
+-----------+------------------+---------------+
```

---

## Row (Record)

A row represents one complete entry in a table.

Example:

```
device_id: 101
operating_system: Windows
employee_id: 1001
```

---

## Column

A column stores one type of information.

Example:

```
device_id
operating_system
employee_id
OS_patch_date
```

---

# SELECT Statement

## Description

The `SELECT` statement retrieves data from a database.

## Syntax

```sql
SELECT column_name
FROM table_name;
```

---

## Retrieve Every Column

Use `*` to select every column.

```sql
SELECT *
FROM machines;
```

Returns all data from the `machines` table.

---

## Retrieve Specific Columns

```sql
SELECT device_id, operating_system
FROM machines;
```

Returns only the selected columns.

---

# FROM Statement

## Description

`FROM` specifies the table that SQL should retrieve data from.

Example:

```sql
SELECT *
FROM login_attempts;
```

---

# ORDER BY

## Description

`ORDER BY` sorts query results.

## Ascending Order (Default)

```sql
SELECT *
FROM machines
ORDER BY device_id;
```

or

```sql
SELECT *
FROM machines
ORDER BY device_id ASC;
```

---

## Descending Order

```sql
SELECT *
FROM machines
ORDER BY device_id DESC;
```

---

# Example Queries

Retrieve all employee devices:

```sql
SELECT *
FROM machines;
```

---

Retrieve login attempts:

```sql
SELECT *
FROM login_attempts;
```

---

Retrieve only operating systems:

```sql
SELECT operating_system
FROM machines;
```

---

Sort login attempts by date:

```sql
SELECT *
FROM login_attempts
ORDER BY login_date;
```

---

Sort login attempts from newest to oldest:

```sql
SELECT *
FROM login_attempts
ORDER BY login_date DESC;
```

---

# Cybersecurity Use Cases

## Investigate login activity

```sql
SELECT *
FROM login_attempts;
```

---

## Review company devices

```sql
SELECT *
FROM machines;
```

---

## Find outdated operating systems

```sql
SELECT operating_system
FROM machines;
```

---

## Analyze events chronologically

```sql
SELECT *
FROM login_attempts
ORDER BY login_date;
```

---

# Quick Reference

| SQL Statement | Purpose |
|--------------|---------|
| `SELECT` | Retrieve data |
| `FROM` | Specify the table |
| `*` | Select every column |
| `ORDER BY` | Sort query results |
| `ASC` | Ascending order |
| `DESC` | Descending order |

---

# Summary

The `SELECT` statement retrieves information from a database, `FROM` specifies which table to query, and `ORDER BY` sorts the returned data. These are the foundation of SQL and are essential skills for security analysts investigating systems, users, and security events.
