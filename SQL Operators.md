> Understand how SQL operators perform calculations, compare values, combine conditions, and manipulate data during database queries.

## 1. What are SQL Operators?

SQL operators are symbols or keywords used to perform operations on database values.

They help us:

- Compare values.
    
- Perform mathematical calculations.
    
- Combine multiple conditions.
    
- Search for specific records.
    
- Filter database results.
    

### Categories of SQL Operators

|Category|Purpose|
|---|---|
|Arithmetic Operators|Perform mathematical calculations.|
|Comparison Operators|Compare values.|
|Logical Operators|Combine conditions.|
|Special Operators|Perform specific filtering operations.|
|Set Operators|Combine results from multiple queries.|
|String Operators|Perform operations on text values.|

## 2. Arithmetic Operators

Arithmetic operators perform mathematical calculations.

|Operator|Meaning|Example|
|---|---|---|
|`+`|Addition|`10 + 5 = 15`|
|`-`|Subtraction|`10 - 5 = 5`|
|`*`|Multiplication|`10 * 5 = 50`|
|`/`|Division|`10 / 5 = 2`|
|`%`|Modulus (remainder)|`10 % 3 = 1`|

### Example

Assume an `employees` table contains a `salary` column.

```
SELECT employee_name, salary, salary + 5000 AS updated_salary
FROM employees;
```

This calculates a salary value increased by 5,000 without changing the stored data.

**Important:** Division and modulus behavior can vary depending on data types and database systems.

## 3. Comparison Operators

Comparison operators compare two values and evaluate a condition.

|Operator|Meaning|
|---|---|
|`=`|Equal to|
|`!=` or `<>`|Not equal to|
|`>`|Greater than|
|`<`|Less than|
|`>=`|Greater than or equal to|
|`<=`|Less than or equal to|

### Example: Equal To

```
SELECT *
FROM employees
WHERE department_id = 1;
```

### Example: Greater Than

```
SELECT *
FROM employees
WHERE salary > 30000;
```

### Example: Not Equal To

```
SELECT *
FROM employees
WHERE department_id <> 2;
```

Comparison conditions are commonly used with `WHERE`, `HAVING`, and join conditions.

## 4. Logical Operators

Logical operators combine or reverse conditions.

### 4.1 AND

Returns true when all specified conditions are true.

```
SELECT *
FROM employees
WHERE salary > 30000
AND department_id = 1;
```

Both conditions must be satisfied.

### 4.2 OR

Returns true when at least one specified condition is true.

```
SELECT *
FROM employees
WHERE department_id = 1
OR department_id = 2;
```

Either condition can be satisfied.

### 4.3 NOT

Reverses a condition.

```
SELECT *
FROM employees
WHERE NOT department_id = 1;
```

This retrieves records that do not satisfy the specified condition.

### AND vs OR vs NOT

|Operator|Behavior|
|---|---|
|AND|All conditions must be true.|
|OR|At least one condition must be true.|
|NOT|Reverses the condition.|

## 5. Special SQL Operators

Special operators make filtering and searching easier.

### 5.1 BETWEEN

Checks whether a value falls within a specified inclusive range.

```
SELECT *
FROM employees
WHERE salary BETWEEN 20000 AND 50000;
```

This includes values equal to 20,000 and 50,000.

### 5.2 IN

Checks whether a value matches any value in a specified list.

```
SELECT *
FROM employees
WHERE department_id IN (1, 2, 3);
```

This is often simpler than writing multiple OR conditions.

### 5.3 LIKE

Searches for a specified text pattern.

|Wildcard|Meaning|
|---|---|
|`%`|Matches zero or more characters.|
|`_`|Matches exactly one character.|

Examples:

```
SELECT *
FROM employees
WHERE employee_name LIKE 'M%';
```

Finds names beginning with M.

```
SELECT *
FROM employees
WHERE employee_name LIKE '%n';
```

Finds names ending with n.

```
SELECT *
FROM employees
WHERE employee_name LIKE '_a%';
```

Finds names whose second character is a.

**Note:** Case sensitivity depends on the database system and collation.

### 5.4 IS NULL

Checks whether a value is NULL.

```
SELECT *
FROM employees
WHERE department_id IS NULL;
```

Do not use `= NULL` to test for NULL values.

### 5.5 EXISTS

Checks whether a subquery returns at least one row.

```
SELECT *
FROM departments d
WHERE EXISTS (
    SELECT 1
    FROM employees e
    WHERE e.department_id = d.department_id
);
```

This retrieves departments that have at least one employee.

### 5.6 ANY

Compares a value against one or more values returned by a subquery.

```
SELECT *
FROM employees
WHERE salary > ANY (
    SELECT salary
    FROM employees
    WHERE department_id = 2
);
```

The condition is true when the salary is greater than at least one value returned by the subquery.

### 5.7 ALL

Compares a value against every value returned by a subquery.

```
SELECT *
FROM employees
WHERE salary > ALL (
    SELECT salary
    FROM employees
    WHERE department_id = 2
);
```

The condition is true when the salary is greater than every value returned by the subquery.

## 6. Set Operators

Set operators combine the results of multiple SELECT statements.

### 6.1 UNION

Combines the results of two queries and removes duplicate rows.

```
SELECT name
FROM current_students

UNION

SELECT name
FROM former_students;
```

### 6.2 UNION ALL

Combines the results without removing duplicates.

```
SELECT name
FROM current_students

UNION ALL

SELECT name
FROM former_students;
```

### 6.3 INTERSECT

Returns rows that appear in both query results.

```
SELECT name
FROM current_students

INTERSECT

SELECT name
FROM scholarship_students;
```

### 6.4 EXCEPT

Returns rows from the first query that do not appear in the second query.

```
SELECT name
FROM current_students

EXCEPT

SELECT name
FROM scholarship_students;
```

Some databases use `MINUS` instead of `EXCEPT`.

### Set Operator Requirements

For compatible set operations:

- Both queries should return the same number of columns.
    
- Corresponding columns should have compatible data types.
    
- The column order must correspond.
    

### UNION vs UNION ALL

|UNION|UNION ALL|
|---|---|
|Removes duplicate rows.|Keeps duplicate rows.|
|May require extra processing.|Often requires less processing.|
|Returns distinct combined results.|Returns all combined results.|

## 7. String Concatenation

String concatenation combines text values.

### Example Using ||

```
SELECT first_name || ' ' || last_name AS full_name
FROM employees;
```

This syntax is supported by PostgreSQL and SQLite.

### MySQL Example

```
SELECT CONCAT(first_name, ' ', last_name) AS full_name
FROM employees;
```

String concatenation syntax varies across database systems.

## 8. Operator Precedence

SQL operators have an order of evaluation known as operator precedence.

A simplified order is:

1. Parentheses.
    
2. Arithmetic operators.
    
3. Comparison operators.
    
4. NOT.
    
5. AND.
    
6. OR.
    

### Example Without Parentheses

```
SELECT *
FROM employees
WHERE department_id = 1
OR department_id = 2
AND salary > 30000;
```

Because AND has higher precedence than OR, this is generally interpreted as:

```
SELECT *
FROM employees
WHERE department_id = 1
OR (department_id = 2 AND salary > 30000);
```

### Example With Parentheses

```
SELECT *
FROM employees
WHERE (department_id = 1 OR department_id = 2)
AND salary > 30000;
```

Parentheses make the intended logic clear.

**Best practice:** Use parentheses when combining multiple AND and OR conditions.

## 9. SQL Operators and NULL

SQL uses three-valued logic:

- TRUE
    
- FALSE
    
- UNKNOWN
    

When a comparison involves NULL, the result is generally UNKNOWN rather than TRUE or FALSE.

Example:

```
SELECT *
FROM employees
WHERE salary = NULL;
```

This does not correctly retrieve NULL salaries.

Use:

```
SELECT *
FROM employees
WHERE salary IS NULL;
```

### Why This Matters

Conditions involving NULL can behave differently from ordinary comparisons.

For example:

```
SELECT *
FROM employees
WHERE salary <> 30000;
```

Rows with NULL salaries are not returned because the comparison evaluates to UNKNOWN.

## 10. SQL Operators in Cybersecurity

Operators are important in database security testing and application development.

### 10.1 SQL Injection

Attackers may attempt to manipulate SQL conditions using operators.

For example, an unsafe application might construct a query using untrusted input:

```
SELECT *
FROM users
WHERE username = 'input'
AND password = 'input';
```

If input is inserted directly into the query, an attacker may manipulate its logical conditions.

**Prevention:**

- Use parameterized queries.
    
- Avoid string concatenation with untrusted input.
    
- Apply least-privilege database permissions.
    
- Validate application input.
    

Related notes:

- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    

### 10.2 Access Control

Comparison and logical operators help applications enforce conditions when retrieving records.

However, authorization must be implemented correctly in the application and database layers.

### 10.3 Data Filtering

Operators allow security analysts to search logs and records for suspicious patterns.

Example:

```
SELECT *
FROM login_logs
WHERE status = 'FAILED'
AND attempt_count > 5;
```

This retrieves records matching both conditions.

## 11. Common Mistakes

|Mistake|Correct Approach|
|---|---|
|Using `= NULL`|Use `IS NULL`.|
|Forgetting parentheses|Group complex conditions.|
|Using `UNION` when duplicates matter|Use `UNION ALL`.|
|Confusing AND and OR|Check logical conditions carefully.|
|Assuming LIKE is always case-sensitive|Check database collation and behavior.|
|Comparing incompatible data types|Use compatible types.|
|Ignoring NULL behavior|Understand SQL three-valued logic.|

## 12. Practical Lab — SQL Operators

**Objective:** Practice different SQL operators using an employee database.

### Step 1: Create a Test Table

```
CREATE TABLE employee_demo (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER,
    salary DECIMAL(10,2)
);
```

### Step 2: Insert Test Records

```
INSERT INTO employee_demo
VALUES
(1, 'Mohit', 1, 35000),
(2, 'Rahul', 2, 42000),
(3, 'Aman', 1, 25000),
(4, 'Priya', 3, 50000),
(5, 'Neha', 2, 30000);
```

### Step 3: Practice Comparison Operators

```
SELECT *
FROM employee_demo
WHERE salary > 30000;
```

### Step 4: Practice Logical Operators

```
SELECT *
FROM employee_demo
WHERE department_id = 1
AND salary > 20000;
```

### Step 5: Practice BETWEEN

```
SELECT *
FROM employee_demo
WHERE salary BETWEEN 25000 AND 40000;
```

### Step 6: Practice IN

```
SELECT *
FROM employee_demo
WHERE department_id IN (1, 3);
```

### Step 7: Practice LIKE

```
SELECT *
FROM employee_demo
WHERE employee_name LIKE 'M%';
```

### Step 8: Practice Aggregate Filtering

```
SELECT department_id, COUNT(*)
FROM employee_demo
GROUP BY department_id
HAVING COUNT(*) > 1;
```

### Step 9: Practice UNION

```
SELECT employee_name
FROM employee_demo
WHERE department_id = 1

UNION

SELECT employee_name
FROM employee_demo
WHERE department_id = 2;
```

### Lab Questions

1. What is the difference between `=` and `LIKE`?
    
2. What is the difference between `AND` and `OR`?
    
3. What does BETWEEN do?
    
4. What is the difference between UNION and UNION ALL?
    
5. Why should NULL be checked using IS NULL?
    
6. Why are parentheses important in complex conditions?
    

## 13. Key Takeaways

- SQL operators perform calculations and comparisons.
    
- Arithmetic operators perform mathematical operations.
    
- Comparison operators evaluate relationships between values.
    
- Logical operators combine conditions.
    
- BETWEEN, IN, LIKE, and EXISTS simplify filtering.
    
- UNION and UNION ALL combine query results.
    
- Operator precedence determines evaluation order.
    
- NULL comparisons require special handling.
    
- Operators are important for querying, analysis, and secure application development.
    

## 14. Related Topics

- [[Introduction to SQL]]
    
- [[SQL Commands]]
    
- [[DML - Data Manipulation Language]]
    
- [[DQL - Data Query Language]]
    
- [[SQL Aggregate Functions]]
    
- [[SQL Joins]]
    
- [[SQL Subqueries]]
    
- [[SQL Constraints]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[SQL Practical Labs]]