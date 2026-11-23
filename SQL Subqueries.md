> Understand how to use queries inside other SQL queries to perform complex data retrieval, filtering, and analysis.

## 1. What is a Subquery?

A subquery is a SQL query written inside another SQL statement.

It is also called an **inner query** or **nested query**.

The query containing the subquery is called the **outer query**.

Subqueries are useful when the result of one query is needed by another query.

### Basic Syntax

```
SELECT column_name
FROM table_name
WHERE column_name = (
    SELECT column_name
    FROM another_table
);
```

The inner query executes to provide a result used by the outer query.

## 2. How Subqueries Work

Consider an `employees` table:

|employee_id|employee_name|salary|
|---|---|---|
|1|Mohit|35000|
|2|Rahul|42000|
|3|Aman|25000|
|4|Priya|50000|

Suppose we want to find employees earning more than the average salary.

First, calculate the average:

```
SELECT AVG(salary)
FROM employees;
```

Then use that result in the outer query:

```
SELECT employee_name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

The inner query calculates the average salary. The outer query returns employees earning more than that average.

## 3. Types of Subqueries

Subqueries can be classified by the number of values they return and how they relate to the outer query.

|Type|Description|
|---|---|
|Single-row subquery|Returns one row.|
|Multiple-row subquery|Returns multiple rows.|
|Multiple-column subquery|Returns multiple columns.|
|Scalar subquery|Returns exactly one value.|
|Correlated subquery|References columns from the outer query.|
|Non-correlated subquery|Can execute independently of the outer query.|

A scalar subquery returns one value: one row and one column.

## 4. Single-Row Subquery

A single-row subquery returns at most one row.

It is commonly used with comparison operators such as:

- `=`
    
- `>`
    
- `<`
    
- `>=`
    
- `<=`
    
- `<>`
    

### Example

Find employees earning more than the average salary:

```
SELECT employee_name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

The average salary subquery returns one value.

**Important:** If a subquery used with `=` returns multiple rows, the database generally raises an error.

## 5. Multiple-Row Subquery

A multiple-row subquery returns multiple rows.

It is commonly used with:

- `IN`
    
- `NOT IN`
    
- `ANY`
    
- `ALL`
    
- `EXISTS`
    

### Example Using IN

Find employees working in departments that are located in Mumbai.

Assume a `departments` table contains a `location` column.

```
SELECT employee_name
FROM employees
WHERE department_id IN (
    SELECT department_id
    FROM departments
    WHERE location = 'Mumbai'
);
```

The inner query returns department IDs. The outer query finds employees belonging to those departments.

### Example Using NOT IN

```
SELECT employee_name
FROM employees
WHERE department_id NOT IN (
    SELECT department_id
    FROM departments
    WHERE location = 'Mumbai'
);
```

This returns employees whose department IDs are not in the subquery result.

**NULL warning:** If the subquery returns a NULL value, `NOT IN` can produce unexpected results because SQL comparisons involving NULL evaluate to UNKNOWN. `NOT EXISTS` is often safer for this situation.

## 6. Subquery Using ANY

`ANY` compares a value against the values returned by a subquery.

The condition is true if at least one comparison succeeds.

### Example

```
SELECT employee_name, salary
FROM employees
WHERE salary > ANY (
    SELECT salary
    FROM employees
    WHERE department_id = 10
);
```

This returns employees whose salary is greater than at least one salary in department 10.

Equivalent logic for a greater-than comparison is that the salary is greater than the minimum qualifying salary, assuming the subquery returns at least one non-NULL value.

## 7. Subquery Using ALL

`ALL` compares a value against every value returned by a subquery.

The condition is true only if all comparisons succeed.

### Example

```
SELECT employee_name, salary
FROM employees
WHERE salary > ALL (
    SELECT salary
    FROM employees
    WHERE department_id = 10
);
```

This returns employees whose salary is greater than every non-NULL salary returned for department 10.

For a greater-than comparison, this generally means earning more than the maximum qualifying salary.

## 8. Subquery Using EXISTS

`EXISTS` checks whether a subquery returns at least one row.

It returns TRUE when at least one matching row exists.

### Example

Find employees who belong to a department:

```
SELECT employee_name
FROM employees E
WHERE EXISTS (
    SELECT 1
    FROM departments D
    WHERE D.department_id = E.department_id
);
```

The database checks whether a matching department record exists for each employee.

The `SELECT 1` is conventional because EXISTS checks for row existence, not the selected value.

## 9. Subquery Using NOT EXISTS

`NOT EXISTS` checks whether a subquery returns no rows.

### Example

Find departments that have no employees:

```
SELECT department_name
FROM departments D
WHERE NOT EXISTS (
    SELECT 1
    FROM employees E
    WHERE E.department_id = D.department_id
);
```

This returns departments without matching employee records.

`NOT EXISTS` is often preferable to `NOT IN` when NULL values may be present in the subquery result.

## 10. Correlated Subquery

A correlated subquery references a column from the outer query.

Its result depends on the current row being examined by the outer query.

### Example

Find employees earning more than the average salary in their own department:

```
SELECT
    E.employee_name,
    E.department_id,
    E.salary
FROM employees E
WHERE E.salary > (
    SELECT AVG(E2.salary)
    FROM employees E2
    WHERE E2.department_id = E.department_id
);
```

Explanation:

1. The outer query examines an employee.
    
2. The inner query calculates the average salary for that employee's department.
    
3. The outer query compares the employee's salary with that average.
    
4. Employees earning more than their department average are returned.
    

**Remember:** A correlated subquery depends on the outer query.

## 11. Non-Correlated Subquery

A non-correlated subquery does not reference columns from the outer query.

It can execute independently.

### Example

```
SELECT employee_name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

The inner query calculates the overall average salary without depending on a particular outer row.

## 12. Subqueries in Different SQL Clauses

Subqueries can appear in several parts of a SQL statement.

### 12.1 Subquery in WHERE

```
SELECT employee_name
FROM employees
WHERE department_id = (
    SELECT department_id
    FROM departments
    WHERE department_name = 'Security'
);
```

### 12.2 Subquery in FROM

A subquery in the FROM clause acts as a derived table.

```
SELECT department_id, average_salary
FROM (
    SELECT
        department_id,
        AVG(salary) AS average_salary
    FROM employees
    GROUP BY department_id
) AS department_summary
WHERE average_salary > 30000;
```

The inner query creates a temporary result for the outer query.

Many database systems require a table alias for a derived table.

### 12.3 Subquery in SELECT

A scalar subquery can be used in the SELECT list.

```
SELECT
    employee_name,
    salary,
    (
        SELECT AVG(salary)
        FROM employees
    ) AS company_average
FROM employees;
```

Each result row displays the employee's salary alongside the overall average.

The subquery must return a single value.

## 13. Multiple-Column Subquery

A multiple-column subquery returns more than one column.

Some databases support row-value comparisons.

### Example

```
SELECT employee_name, department_id, salary
FROM employees
WHERE (department_id, salary) IN (
    SELECT department_id, MAX(salary)
    FROM employees
    GROUP BY department_id
);
```

This finds employees whose department and salary match a department's maximum salary.

Row-value comparison support varies between database systems. A JOIN with a grouped subquery is a more portable alternative.

## 14. Subquery vs JOIN

Both subqueries and JOINs can retrieve related information, but they express different query structures.

|Subquery|JOIN|
|---|---|
|Places one query inside another.|Combines rows from multiple tables.|
|Useful for filtering based on another query's result.|Useful for retrieving related columns.|
|Can use EXISTS, IN, and scalar results.|Uses matching conditions between tables.|
|May be correlated or non-correlated.|Combines tables directly.|

### Subquery Example

```
SELECT employee_name
FROM employees
WHERE department_id IN (
    SELECT department_id
    FROM departments
    WHERE department_name = 'Security'
);
```

### JOIN Equivalent

```
SELECT E.employee_name
FROM employees E
INNER JOIN departments D
ON E.department_id = D.department_id
WHERE D.department_name = 'Security';
```

Both can return the same employee names.

**Important:** Neither approach is automatically faster in every database. Performance depends on indexes, data distribution, database optimization, and the query plan.

## 15. Common Subquery Mistakes

|Mistake|Explanation|
|---|---|
|Using `=` with multiple returned rows|A single-value comparison generally expects one value.|
|Using the wrong operator|Use IN or EXISTS when appropriate for multiple rows.|
|Ignoring NULL values|NULL can change the behavior of IN and NOT IN.|
|Forgetting correlation|A correlated subquery must correctly reference the outer query.|
|Returning multiple values in a scalar context|Scalar subqueries must return one value.|
|Assuming subqueries are always slow|Modern query optimizers can transform many subqueries efficiently.|

## 16. Subqueries in Cybersecurity

Subqueries can help investigate security events and identify suspicious patterns.

### 16.1 Find Users with Failed Login Attempts

Assume a `login_logs` table contains `user_id` and `status`.

```
SELECT username
FROM users
WHERE user_id IN (
    SELECT user_id
    FROM login_logs
    WHERE status = 'FAILED'
);
```

This finds users associated with at least one failed login record.

### 16.2 Find Accounts with More Than Five Failed Attempts

```
SELECT username
FROM users
WHERE user_id IN (
    SELECT user_id
    FROM login_logs
    WHERE status = 'FAILED'
    GROUP BY user_id
    HAVING COUNT(*) > 5
);
```

This identifies accounts with more than five failed login records.

Further investigation is necessary before concluding that an account is under attack.

### 16.3 Find Events from Unknown Accounts

```
SELECT *
FROM login_logs L
WHERE NOT EXISTS (
    SELECT 1
    FROM users U
    WHERE U.user_id = L.user_id
);
```

This identifies login records without a corresponding user record.

Possible explanations include deleted accounts, incomplete data, or data-integrity problems.

## 17. Practical Lab — SQL Subqueries

**Objective:** Practice single-row, multiple-row, correlated, and EXISTS subqueries.

Use your SQL practice database.

### Step 1: Create Employees Table

```
CREATE TABLE employees_subquery (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER,
    salary DECIMAL(10,2)
);
```

### Step 2: Insert Records

```
INSERT INTO employees_subquery
VALUES
(1, 'Mohit', 10, 35000),
(2, 'Rahul', 20, 42000),
(3, 'Aman', 10, 25000),
(4, 'Priya', 20, 50000),
(5, 'Neha', 30, 30000);
```

### Step 3: Find Employees Earning Above Average

```
SELECT employee_name, salary
FROM employees_subquery
WHERE salary > (
    SELECT AVG(salary)
    FROM employees_subquery
);
```

### Step 4: Find Employees in Department 10 or 20

```
SELECT employee_name
FROM employees_subquery
WHERE department_id IN (
    SELECT department_id
    FROM employees_subquery
    WHERE department_id IN (10, 20)
);
```

### Step 5: Find the Highest-Paid Employee

```
SELECT employee_name, salary
FROM employees_subquery
WHERE salary = (
    SELECT MAX(salary)
    FROM employees_subquery
);
```

### Step 6: Find Employees Earning Above Their Department Average

```
SELECT
    E.employee_name,
    E.department_id,
    E.salary
FROM employees_subquery E
WHERE E.salary > (
    SELECT AVG(E2.salary)
    FROM employees_subquery E2
    WHERE E2.department_id = E.department_id
);
```

### Step 7: Practice EXISTS

```
SELECT employee_name
FROM employees_subquery E
WHERE EXISTS (
    SELECT 1
    FROM employees_subquery E2
    WHERE E2.department_id = E.department_id
      AND E2.salary > 40000
);
```

This returns employees belonging to departments that have at least one employee earning more than 40,000.

### Step 8: Practice NOT EXISTS

```
SELECT employee_name
FROM employees_subquery E
WHERE NOT EXISTS (
    SELECT 1
    FROM employees_subquery E2
    WHERE E2.department_id = E.department_id
      AND E2.salary > 45000
);
```

This returns employees belonging to departments without an employee earning more than 45,000.

### Lab Observations

Record these questions in your notebook:

1. What is a subquery?
    
2. What is the difference between correlated and non-correlated subqueries?
    
3. What is the difference between IN and EXISTS?
    
4. Why can NOT EXISTS be safer than NOT IN when NULL values are present?
    
5. When might a JOIN be a better choice than a subquery?
    

## 18. Key Takeaways

- A subquery is a query inside another SQL statement.
    
- The inner query supplies information to the outer query.
    
- Single-row subqueries return at most one row.
    
- Multiple-row subqueries can work with IN, ANY, ALL, and EXISTS.
    
- Correlated subqueries depend on the outer query.
    
- Non-correlated subqueries can execute independently.
    
- Subqueries can appear in WHERE, FROM, and SELECT.
    
- Subqueries are useful for complex filtering and security-log investigations.
    

## 19. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[SQL Aggregate Functions]]
    
- [[SQL Joins]]
    
- [[SQL Views]]
    
- [[SQL Indexes]]
    
- [[SQL Injection]]
    
- [[SQL Practical Labs]]