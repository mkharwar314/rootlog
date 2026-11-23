> Understand how SQL aggregate functions summarize, calculate, and analyze data across multiple database records.

## 1. What are Aggregate Functions?

Aggregate functions are SQL functions that perform calculations on a group of rows and return a single result for each group.

They are commonly used for:

- Counting records.
    
- Calculating totals.
    
- Finding averages.
    
- Identifying minimum and maximum values.
    
- Analyzing grouped data.
    

### Main Aggregate Functions

|Function|Purpose|
|---|---|
|`COUNT()`|Counts rows or non-NULL values.|
|`SUM()`|Calculates the total.|
|`AVG()`|Calculates the average.|
|`MIN()`|Finds the minimum value.|
|`MAX()`|Finds the maximum value.|

## 2. COUNT() Function

The `COUNT()` function counts records or non-NULL values.

### COUNT(*)

Counts all rows, including rows containing NULL values in individual columns.

```
SELECT COUNT(*)
FROM employees;
```

### COUNT(column)

Counts only non-NULL values in the specified column.

```
SELECT COUNT(salary)
FROM employees;
```

### COUNT(DISTINCT column)

Counts the number of unique non-NULL values.

```
SELECT COUNT(DISTINCT department_id)
FROM employees;
```

### Difference

|Expression|Behavior|
|---|---|
|`COUNT(*)`|Counts all rows.|
|`COUNT(column)`|Counts non-NULL values.|
|`COUNT(DISTINCT column)`|Counts unique non-NULL values.|

## 3. SUM() Function

The `SUM()` function calculates the total of numeric values.

### Example

```
SELECT SUM(salary)
FROM employees;
```

This calculates the total salary of all employees.

### SUM with WHERE

```
SELECT SUM(salary)
FROM employees
WHERE department_id = 1;
```

This calculates the total salary for department 1.

**Important:** SUM ignores NULL values. If there are no non-NULL input values, its result is generally NULL.

## 4. AVG() Function

The `AVG()` function calculates the arithmetic average of numeric values.

### Formula

[  
\text{Average} = \frac{\text{Sum of values}}{\text{Number of non-NULL values}}  
]

### Example

```
SELECT AVG(salary)
FROM employees;
```

This calculates the average salary.

### AVG with WHERE

```
SELECT AVG(salary)
FROM employees
WHERE department_id = 2;
```

This calculates the average salary in department 2.

**Important:** AVG ignores NULL values. It does not treat NULL as zero.

## 5. MIN() Function

The `MIN()` function returns the smallest value in a set.

### Example

```
SELECT MIN(salary)
FROM employees;
```

This returns the lowest non-NULL salary.

It can also work with dates and comparable text values.

```
SELECT MIN(joining_date)
FROM employees;
```

This returns the earliest non-NULL joining date.

## 6. MAX() Function

The `MAX()` function returns the largest value in a set.

### Example

```
SELECT MAX(salary)
FROM employees;
```

This returns the highest non-NULL salary.

Another example:

```
SELECT MAX(joining_date)
FROM employees;
```

This returns the latest non-NULL joining date.

## 7. Aggregate Functions with GROUP BY

The `GROUP BY` clause divides records into groups based on one or more columns.

Aggregate functions then calculate a separate result for each group.

### Example

```
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
```

This counts the employees in each department.

### Multiple Aggregate Functions

```
SELECT
    department_id,
    COUNT(*) AS employee_count,
    SUM(salary) AS total_salary,
    AVG(salary) AS average_salary,
    MIN(salary) AS minimum_salary,
    MAX(salary) AS maximum_salary
FROM employees
GROUP BY department_id;
```

This generates several statistics for every department.

## 8. HAVING with Aggregate Functions

The `HAVING` clause filters groups based on aggregate conditions.

### Example

```
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

This displays departments containing more than five employees.

### WHERE vs HAVING

|WHERE|HAVING|
|---|---|
|Filters individual rows.|Filters groups.|
|Applied before grouping.|Applied after grouping.|
|Cannot generally use aggregate functions directly in its condition.|Commonly uses aggregate functions.|

Example using both:

```
SELECT department_id, AVG(salary) AS average_salary
FROM employees
WHERE salary > 10000
GROUP BY department_id
HAVING AVG(salary) > 30000;
```

This:

1. Excludes employees earning 10,000 or less.
    
2. Groups the remaining employees by department.
    
3. Calculates each department's average salary.
    
4. Returns groups with an average above 30,000.
    

## 9. DISTINCT with Aggregate Functions

`DISTINCT` removes duplicate values before an aggregate calculation.

### Example

```
SELECT COUNT(DISTINCT department_id)
FROM employees;
```

Counts the number of different non-NULL department IDs.

Another example:

```
SELECT SUM(DISTINCT salary)
FROM employees;
```

Adds each distinct non-NULL salary value only once.

**Important:** `SUM(DISTINCT salary)` is not the same as total payroll. Multiple employees can legitimately receive the same salary.

## 10. Aggregate Functions and NULL

SQL aggregate functions generally ignore NULL values, with `COUNT(*)` being an important exception.

Consider these values:

|Salary|
|---|
|20000|
|30000|
|NULL|
|40000|

Results:

|Expression|Result|
|---|---|
|`COUNT(*)`|4|
|`COUNT(salary)`|3|
|`SUM(salary)`|90000|
|`AVG(salary)`|30000|
|`MIN(salary)`|20000|
|`MAX(salary)`|40000|

The average is calculated using the three non-NULL values.

## 11. Conditional Aggregation

Conditional aggregation calculates statistics for records that satisfy specified conditions.

A common technique uses `CASE` inside an aggregate function.

### Example: Count Active Employees

```
SELECT
    COUNT(
        CASE
            WHEN status = 'active' THEN 1
        END
    ) AS active_employees
FROM employees;
```

### Example: Count Active and Inactive Employees

```
SELECT
    COUNT(CASE WHEN status = 'active' THEN 1 END) AS active_count,
    COUNT(CASE WHEN status = 'inactive' THEN 1 END) AS inactive_count
FROM employees;
```

This calculates both counts in one query.

## 12. Aggregate Functions in Cybersecurity

Aggregate functions are useful in security monitoring, log analysis, and incident investigation.

### 12.1 Count Failed Login Attempts

Assume a table named `login_logs` contains a `status` column.

```
SELECT COUNT(*)
FROM login_logs
WHERE status = 'FAILED';
```

This counts failed login records.

### 12.2 Identify Frequently Targeted Accounts

```
SELECT username, COUNT(*) AS failed_attempts
FROM login_logs
WHERE status = 'FAILED'
GROUP BY username
HAVING COUNT(*) > 5;
```

This identifies accounts with more than five failed login records.

**Important:** Multiple failures alone do not prove a brute-force attack. Investigate timestamps, source addresses, account context, and other evidence.

### 12.3 Identify High-Volume Source Addresses

```
SELECT source_ip, COUNT(*) AS request_count
FROM web_logs
GROUP BY source_ip
HAVING COUNT(*) > 100;
```

This identifies source addresses associated with more than 100 log records.

A high request count is an investigation lead, not proof of malicious activity.

### 12.4 Find Earliest and Latest Events

```
SELECT
    MIN(event_time) AS first_event,
    MAX(event_time) AS latest_event
FROM security_logs;
```

This helps establish the time range represented by the records.

## 13. Common Mistakes

|Mistake|Explanation|
|---|---|
|Using COUNT(column) expecting all rows|COUNT(column) ignores NULL values.|
|Confusing SUM and COUNT|SUM adds numeric values; COUNT counts rows or values.|
|Forgetting GROUP BY|Non-aggregated selected columns generally need to be grouped.|
|Using WHERE with aggregate conditions|Use HAVING for group-level filtering.|
|Assuming NULL is zero|Aggregate functions generally ignore NULL.|
|Using SUM(DISTINCT) for payroll|Repeated legitimate salaries would be counted only once.|

## 14. Practical Lab — Aggregate Functions

**Objective:** Practice calculating statistics using SQL aggregate functions.

Use your `sql_practice` database.

### Step 1: Create a Test Table

```
CREATE TABLE employee_stats (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER,
    salary DECIMAL(10,2),
    status VARCHAR(20)
);
```

### Step 2: Insert Test Records

```
INSERT INTO employee_stats
VALUES
(1, 'Mohit', 1, 35000, 'active'),
(2, 'Rahul', 1, 40000, 'active'),
(3, 'Aman', 2, 25000, 'inactive'),
(4, 'Priya', 2, 50000, 'active'),
(5, 'Neha', 3, 30000, 'inactive');
```

### Step 3: Count Employees

```
SELECT COUNT(*)
FROM employee_stats;
```

### Step 4: Calculate Total Salary

```
SELECT SUM(salary)
FROM employee_stats;
```

### Step 5: Calculate Average Salary

```
SELECT AVG(salary)
FROM employee_stats;
```

### Step 6: Find Highest and Lowest Salary

```
SELECT
    MAX(salary) AS highest_salary,
    MIN(salary) AS lowest_salary
FROM employee_stats;
```

### Step 7: Count Employees by Department

```
SELECT department_id, COUNT(*) AS employee_count
FROM employee_stats
GROUP BY department_id;
```

### Step 8: Calculate Average Salary by Department

```
SELECT department_id, AVG(salary) AS average_salary
FROM employee_stats
GROUP BY department_id;
```

### Step 9: Find Departments with Average Salary Above 30000

```
SELECT department_id, AVG(salary) AS average_salary
FROM employee_stats
GROUP BY department_id
HAVING AVG(salary) > 30000;
```

### Step 10: Count Active Employees

```
SELECT COUNT(*)
FROM employee_stats
WHERE status = 'active';
```

### Lab Observations

Record these questions in your notebook:

1. What is the difference between COUNT(*) and COUNT(column)?
    
2. Why does AVG ignore NULL values?
    
3. What is the purpose of GROUP BY?
    
4. How does HAVING filter aggregate results?
    
5. How can aggregate functions help identify suspicious login activity?
    

## 15. Key Takeaways

- Aggregate functions summarize multiple database records.
    
- COUNT counts rows or non-NULL values.
    
- SUM calculates totals.
    
- AVG calculates averages.
    
- MIN finds the smallest value.
    
- MAX finds the largest value.
    
- GROUP BY calculates results for individual groups.
    
- HAVING filters groups.
    
- DISTINCT removes duplicate values before aggregation.
    
- Aggregate functions are useful in database reporting and cybersecurity log analysis.
    

## 16. Related Topics

- [[Introduction to SQL]]
    
- [[SQL Commands]]
    
- [[DQL - Data Query Language]]
    
- [[SQL Operators]]
    
- [[SQL Joins]]
    
- [[SQL Subqueries]]
    
- [[SQL Constraints]]
    
- [[SQL Injection]]
    
- [[SQL Practical Labs]]