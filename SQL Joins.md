> Understand how SQL combines related data from multiple tables using common columns and relationships.

## 1. What are SQL Joins?

A SQL JOIN combines rows from two or more tables based on a related column.

In relational databases, information is often divided into multiple tables to reduce duplication and maintain consistency.

JOINs allow us to retrieve related information from these separate tables.

### Example

Consider two tables:

**Employees**

|employee_id|employee_name|department_id|
|---|---|---|
|1|Mohit|10|
|2|Rahul|20|
|3|Aman|10|
|4|Priya|30|

**Departments**

|department_id|department_name|
|---|---|
|10|Security|
|20|Development|
|40|Networking|

The `department_id` column connects the two tables.

A JOIN can combine employee information with department names.

## 2. Types of SQL Joins

The main SQL JOIN types are:

|JOIN|Purpose|
|---|---|
|INNER JOIN|Returns matching rows from both tables.|
|LEFT JOIN|Returns all rows from the left table and matching rows from the right.|
|RIGHT JOIN|Returns all rows from the right table and matching rows from the left.|
|FULL OUTER JOIN|Returns matching and non-matching rows from both tables.|
|CROSS JOIN|Returns every possible combination of rows.|
|SELF JOIN|Joins a table with itself.|

## 3. INNER JOIN

An INNER JOIN returns only rows that have matching values in both tables.

### Syntax

```
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### Example

```
SELECT
    Employees.employee_name,
    Departments.department_name
FROM Employees
INNER JOIN Departments
ON Employees.department_id = Departments.department_id;
```

### Result

|employee_name|department_name|
|---|---|
|Mohit|Security|
|Rahul|Development|
|Aman|Security|

Priya is excluded because department 30 has no matching record in the Departments table.

The Networking department is also excluded because no employee belongs to department 40.

**Remember:** INNER JOIN returns matching records only.

## 4. LEFT JOIN

A LEFT JOIN returns:

- Every row from the left table.
    
- Matching rows from the right table.
    
- NULL values for right-table columns when no match exists.
    

### Syntax

```
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

### Example

```
SELECT
    Employees.employee_name,
    Departments.department_name
FROM Employees
LEFT JOIN Departments
ON Employees.department_id = Departments.department_id;
```

### Result

|employee_name|department_name|
|---|---|
|Mohit|Security|
|Rahul|Development|
|Aman|Security|
|Priya|NULL|

Priya appears even though her department has no matching record.

**Remember:** LEFT JOIN preserves every row from the left table.

## 5. RIGHT JOIN

A RIGHT JOIN returns:

- Every row from the right table.
    
- Matching rows from the left table.
    
- NULL values for left-table columns when no match exists.
    

### Example

```
SELECT
    Employees.employee_name,
    Departments.department_name
FROM Employees
RIGHT JOIN Departments
ON Employees.department_id = Departments.department_id;
```

### Result

|employee_name|department_name|
|---|---|
|Mohit|Security|
|Aman|Security|
|Rahul|Development|
|NULL|Networking|

The Networking department appears even though no employee belongs to it.

**Remember:** RIGHT JOIN preserves every row from the right table.

Note: Some database systems do not support RIGHT JOIN directly. It can be rewritten by reversing the table order and using LEFT JOIN.

## 6. FULL OUTER JOIN

A FULL OUTER JOIN returns:

- Matching rows from both tables.
    
- Non-matching rows from the left table.
    
- Non-matching rows from the right table.
    

### Example

```
SELECT
    Employees.employee_name,
    Departments.department_name
FROM Employees
FULL OUTER JOIN Departments
ON Employees.department_id = Departments.department_id;
```

### Result

|employee_name|department_name|
|---|---|
|Mohit|Security|
|Rahul|Development|
|Aman|Security|
|Priya|NULL|
|NULL|Networking|

**Remember:** FULL OUTER JOIN preserves unmatched rows from both tables.

Note: MySQL does not directly support `FULL OUTER JOIN`. It can be implemented using a combination of LEFT JOIN and RIGHT JOIN with `UNION`.

## 7. CROSS JOIN

A CROSS JOIN produces the Cartesian product of two tables.

Every row from the first table is combined with every row from the second table.

### Syntax

```
SELECT *
FROM table1
CROSS JOIN table2;
```

### Example

Suppose:

**Colors**

|color|
|---|
|Red|
|Blue|

**Sizes**

|size|
|---|
|Small|
|Large|

Query:

```
SELECT Colors.color, Sizes.size
FROM Colors
CROSS JOIN Sizes;
```

### Result

|color|size|
|---|---|
|Red|Small|
|Red|Large|
|Blue|Small|
|Blue|Large|

If the first table has 2 rows and the second has 2 rows:

[  
2 \times 2 = 4 \text{ rows}  
]

**Remember:** CROSS JOIN produces every possible combination.

Be careful with large tables because the result can contain a very large number of rows.

## 8. SELF JOIN

A SELF JOIN joins a table with itself.

It is useful when records in one table have relationships with other records in the same table.

### Example: Employee and Manager

Consider:

|employee_id|employee_name|manager_id|
|---|---|---|
|1|Mohit|NULL|
|2|Rahul|1|
|3|Aman|1|
|4|Priya|2|

Here, `manager_id` refers to another employee's `employee_id`.

Query:

```
SELECT
    E.employee_name AS employee,
    M.employee_name AS manager
FROM Employees E
LEFT JOIN Employees M
ON E.manager_id = M.employee_id;
```

### Result

|employee|manager|
|---|---|
|Mohit|NULL|
|Rahul|Mohit|
|Aman|Mohit|
|Priya|Rahul|

`E` and `M` are aliases representing two logical references to the same table.

## 9. JOIN with Multiple Conditions

A JOIN can use multiple conditions with `AND` or other logical operators.

### Example

```
SELECT *
FROM Employees E
INNER JOIN Departments D
ON E.department_id = D.department_id
AND E.status = 'active';
```

This returns matching department records for active employees.

Be aware that putting a filter in the `ON` clause versus the `WHERE` clause can produce different results with OUTER JOINs.

## 10. JOIN with Aggregate Functions

JOINs can be combined with aggregate functions to generate reports.

### Example: Employee Count by Department

```
SELECT
    D.department_name,
    COUNT(E.employee_id) AS employee_count
FROM Departments D
LEFT JOIN Employees E
ON D.department_id = E.department_id
GROUP BY D.department_name;
```

This includes departments with zero employees.

**Important:** Use `COUNT(E.employee_id)` rather than `COUNT(*)` here. With a LEFT JOIN, `COUNT(*)` also counts the preserved department row even when there is no matching employee.

## 11. JOIN and NULL Values

When an OUTER JOIN finds no matching row, columns from the unmatched side contain NULL.

For example:

```
SELECT
    Employees.employee_name,
    Departments.department_name
FROM Employees
LEFT JOIN Departments
ON Employees.department_id = Departments.department_id;
```

If an employee has no matching department, `department_name` is NULL.

You can find unmatched employees using:

```
SELECT Employees.employee_name
FROM Employees
LEFT JOIN Departments
ON Employees.department_id = Departments.department_id
WHERE Departments.department_id IS NULL;
```

This is a common technique for finding records without matching relationships.

## 12. JOIN vs UNION

JOIN and UNION perform different operations.

|JOIN|UNION|
|---|---|
|Combines columns from related tables.|Combines rows from compatible query results.|
|Usually uses a relationship or join condition.|Does not require a relationship between tables.|
|Can increase the number of columns.|Keeps the same number of columns in each query result.|

Example:

```
SELECT employee_name FROM Employees
UNION
SELECT department_name FROM Departments;
```

`UNION` removes duplicate rows.

`UNION ALL` keeps duplicates.

## 13. SQL Joins in Cybersecurity

JOINs are useful when investigating security events stored in different tables.

### 13.1 Connect Login Logs with User Accounts

Assume:

- `users` stores user account details.
    
- `login_logs` stores login events.
    

```
SELECT
    users.username,
    login_logs.source_ip,
    login_logs.status
FROM users
INNER JOIN login_logs
ON users.user_id = login_logs.user_id;
```

This connects login events with account information.

### 13.2 Find Failed Login Attempts

```
SELECT
    users.username,
    login_logs.source_ip,
    COUNT(*) AS failed_attempts
FROM users
INNER JOIN login_logs
ON users.user_id = login_logs.user_id
WHERE login_logs.status = 'FAILED'
GROUP BY users.username, login_logs.source_ip;
```

This summarizes failed login attempts by user and source IP.

### 13.3 Find Events Without a Matching User

```
SELECT login_logs.*
FROM login_logs
LEFT JOIN users
ON login_logs.user_id = users.user_id
WHERE users.user_id IS NULL;
```

This identifies login records whose user ID has no matching account record.

Such records may indicate incomplete data, deleted accounts, or data-quality issues. They are not automatically evidence of an attack.

## 14. Common JOIN Mistakes

|Mistake|Explanation|
|---|---|
|Forgetting the ON condition|Can create an unintended Cartesian product.|
|Using the wrong join type|May exclude records that should be preserved.|
|Ambiguous column names|Use table names or aliases to identify columns.|
|Ignoring NULL values|OUTER JOIN results can contain NULL values.|
|Incorrect grouping|Group all selected non-aggregated columns when required.|
|Duplicate rows|A one-to-many relationship can produce multiple result rows.|
|Filtering in the wrong clause|WHERE can remove unmatched rows from an OUTER JOIN result.|

## 15. Practical Lab — SQL Joins

**Objective:** Learn how to combine related database tables.

Use your SQL practice database.

### Step 1: Create the Departments Table

```
CREATE TABLE departments (
    department_id INTEGER PRIMARY KEY,
    department_name VARCHAR(50)
);
```

### Step 2: Create the Employees Table

```
CREATE TABLE employees_join (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER
);
```

### Step 3: Insert Departments

```
INSERT INTO departments
VALUES
(10, 'Security'),
(20, 'Development'),
(30, 'Forensics'),
(40, 'Networking');
```

### Step 4: Insert Employees

```
INSERT INTO employees_join
VALUES
(1, 'Mohit', 10),
(2, 'Rahul', 20),
(3, 'Aman', 10),
(4, 'Priya', 30);
```

### Step 5: Practice INNER JOIN

```
SELECT
    employees_join.employee_name,
    departments.department_name
FROM employees_join
INNER JOIN departments
ON employees_join.department_id = departments.department_id;
```

### Step 6: Practice LEFT JOIN

```
SELECT
    employees_join.employee_name,
    departments.department_name
FROM employees_join
LEFT JOIN departments
ON employees_join.department_id = departments.department_id;
```

### Step 7: Practice RIGHT JOIN

Try:

```
SELECT
    employees_join.employee_name,
    departments.department_name
FROM employees_join
RIGHT JOIN departments
ON employees_join.department_id = departments.department_id;
```

If your database does not support RIGHT JOIN, reverse the table order and use LEFT JOIN.

### Step 8: Practice FULL OUTER JOIN

Try:

```
SELECT
    employees_join.employee_name,
    departments.department_name
FROM employees_join
FULL OUTER JOIN departments
ON employees_join.department_id = departments.department_id;
```

If unsupported, investigate how to reproduce the result using LEFT JOIN, RIGHT JOIN, and UNION.

### Step 9: Practice CROSS JOIN

```
SELECT *
FROM employees_join
CROSS JOIN departments;
```

### Step 10: Find Departments Without Employees

```
SELECT departments.department_name
FROM departments
LEFT JOIN employees_join
ON departments.department_id = employees_join.department_id
WHERE employees_join.employee_id IS NULL;
```

### Lab Observations

Record these questions in your notebook:

1. What is the difference between INNER JOIN and LEFT JOIN?
    
2. Why does an OUTER JOIN produce NULL values?
    
3. What is a Cartesian product?
    
4. What is the purpose of a SELF JOIN?
    
5. How can JOINs help correlate security logs with user accounts?
    

## 16. Key Takeaways

- JOINs combine related records from multiple tables.
    
- INNER JOIN returns matching records.
    
- LEFT JOIN preserves all rows from the left table.
    
- RIGHT JOIN preserves all rows from the right table.
    
- FULL OUTER JOIN preserves unmatched rows from both tables.
    
- CROSS JOIN generates every possible combination.
    
- SELF JOIN joins a table with itself.
    
- JOINs are essential for relational database analysis.
    
- Security analysts can use JOINs to correlate events, accounts, and network records.
    

## 17. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[SQL Aggregate Functions]]
    
- [[SQL Subqueries]]
    
- [[SQL Views]]
    
- [[SQL Indexes]]
    
- [[SQL Injection]]
    
- [[SQL Practical Labs]]