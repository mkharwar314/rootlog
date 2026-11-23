> Understand how to retrieve, filter, sort, group, and analyze information stored in relational databases.

## 1. What is DQL?

**DQL (Data Query Language)** is the category of SQL used to retrieve data from database tables.

Its primary command is:

- `SELECT` — retrieves records from one or more tables.
    

DQL allows users and applications to search for specific information without modifying the stored records.

### Example

```
SELECT * FROM students;
```

This retrieves all columns and records from the `students` table.

## 2. SELECT Statement

The `SELECT` statement retrieves data from a database.

### Basic Syntax

```
SELECT column1, column2
FROM table_name;
```

### Retrieve All Columns

```
SELECT *
FROM students;
```

The `*` symbol represents all columns.

### Retrieve Specific Columns

```
SELECT name, age
FROM students;
```

This retrieves only the `name` and `age` columns.

**Best practice:** Select only the columns you need instead of always using `*`.

## 3. WHERE Clause

The `WHERE` clause filters records based on a specified condition.

### Syntax

```
SELECT column_name
FROM table_name
WHERE condition;
```

### Example

```
SELECT *
FROM students
WHERE age = 18;
```

This retrieves students whose age is 18.

### Comparison Operators

|Operator|Meaning|
|---|---|
|`=`|Equal to|
|`!=` or `<>`|Not equal to|
|`>`|Greater than|
|`<`|Less than|
|`>=`|Greater than or equal to|
|`<=`|Less than or equal to|

Example:

```
SELECT *
FROM students
WHERE age >= 18;
```

## 4. Logical Operators

Logical operators combine multiple conditions.

|Operator|Purpose|
|---|---|
|`AND`|All conditions must be true.|
|`OR`|At least one condition must be true.|
|`NOT`|Reverses a condition.|

### AND Example

```
SELECT *
FROM students
WHERE age >= 18 AND age <= 20;
```

### OR Example

```
SELECT *
FROM students
WHERE name = 'Mohit' OR name = 'Rahul';
```

### NOT Example

```
SELECT *
FROM students
WHERE NOT age = 18;
```

## 5. Special Filtering Operators

### 5.1 BETWEEN

Retrieves values within a specified range. The endpoints are included.

```
SELECT *
FROM students
WHERE age BETWEEN 18 AND 20;
```

### 5.2 IN

Checks whether a value matches any value in a list.

```
SELECT *
FROM students
WHERE age IN (18, 19, 20);
```

### 5.3 LIKE

Searches for a specified pattern in text.

|Pattern|Meaning|
|---|---|
|`'M%'`|Starts with M|
|`'%t'`|Ends with t|
|`'%oh%'`|Contains oh|
|`'_a%'`|Second character is a|

Example:

```
SELECT *
FROM students
WHERE name LIKE 'M%';
```

This retrieves names beginning with M.

### 5.4 IS NULL

Checks whether a column contains a `NULL` value.

```
SELECT *
FROM students
WHERE age IS NULL;
```

Use `IS NULL` rather than `= NULL`.

## 6. ORDER BY Clause

The `ORDER BY` clause sorts query results.

### Ascending Order

```
SELECT *
FROM students
ORDER BY age ASC;
```

`ASC` sorts from lowest to highest.

### Descending Order

```
SELECT *
FROM students
ORDER BY age DESC;
```

`DESC` sorts from highest to lowest.

### Sort by Multiple Columns

```
SELECT *
FROM students
ORDER BY age DESC, name ASC;
```

This sorts by age first and then by name when ages are equal.

## 7. DISTINCT Keyword

The `DISTINCT` keyword removes duplicate values from the query result.

### Example

```
SELECT DISTINCT age
FROM students;
```

This displays each different age only once.

For multiple columns:

```
SELECT DISTINCT name, age
FROM students;
```

Uniqueness is determined by the combination of selected columns.

## 8. LIMIT and OFFSET

These clauses control how many records are returned and where retrieval begins.

### LIMIT

```
SELECT *
FROM students
LIMIT 5;
```

Returns at most five records.

### OFFSET

```
SELECT *
FROM students
LIMIT 5 OFFSET 10;
```

Skips the first ten records and returns the next five.

**Database differences:** `LIMIT` is supported by SQLite, MySQL, and PostgreSQL. SQL Server commonly uses `TOP` or `OFFSET ... FETCH`.

## 9. Aggregate Functions

Aggregate functions perform calculations on multiple records and return a single result per group.

|Function|Purpose|
|---|---|
|`COUNT()`|Counts records or non-NULL values.|
|`SUM()`|Calculates the total.|
|`AVG()`|Calculates the average.|
|`MIN()`|Finds the minimum value.|
|`MAX()`|Finds the maximum value.|

### COUNT()

```
SELECT COUNT(*)
FROM students;
```

Counts all matching rows.

### SUM()

```
SELECT SUM(age)
FROM students;
```

Calculates the sum of non-NULL age values.

### AVG()

```
SELECT AVG(age)
FROM students;
```

Calculates the average age.

### MIN() and MAX()

```
SELECT MIN(age), MAX(age)
FROM students;
```

Returns the minimum and maximum age.

Related note: [[SQL Aggregate Functions]]

## 10. GROUP BY Clause

The `GROUP BY` clause groups records that share the same value in one or more columns.

It is commonly used with aggregate functions.

### Example

Assume a table named `employees` contains a `department` column.

```
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

This counts employees in each department.

### Grouping by Multiple Columns

```
SELECT department, job_title, COUNT(*)
FROM employees
GROUP BY department, job_title;
```

This groups records by department and job title.

## 11. HAVING Clause

The `HAVING` clause filters groups created by `GROUP BY`.

### Example

```
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

This displays departments containing more than five employees.

### WHERE vs HAVING

|WHERE|HAVING|
|---|---|
|Filters individual rows.|Filters groups.|
|Applied before grouping.|Applied after grouping.|
|Commonly used without aggregates.|Commonly used with aggregate conditions.|

## 12. SQL Joins

A JOIN combines related records from multiple tables.

Assume two tables:

**students**

|id|name|
|---|---|
|1|Mohit|
|2|Rahul|

**marks**

|student_id|score|
|---|---|
|1|85|
|2|90|

### 12.1 INNER JOIN

Returns matching records from both tables.

```
SELECT students.name, marks.score
FROM students
INNER JOIN marks
ON students.id = marks.student_id;
```

### 12.2 LEFT JOIN

Returns all records from the left table and matching records from the right table.

```
SELECT students.name, marks.score
FROM students
LEFT JOIN marks
ON students.id = marks.student_id;
```

If there is no match, right-table columns contain `NULL`.

### 12.3 RIGHT JOIN

Returns all records from the right table and matching records from the left table.

```
SELECT students.name, marks.score
FROM students
RIGHT JOIN marks
ON students.id = marks.student_id;
```

Support for `RIGHT JOIN` varies by database. SQLite supports it in modern versions.

### 12.4 FULL OUTER JOIN

Returns matching records and unmatched records from both tables.

```
SELECT students.name, marks.score
FROM students
FULL OUTER JOIN marks
ON students.id = marks.student_id;
```

Not every database supports `FULL OUTER JOIN` directly.

Related note: [[SQL Joins]]

## 13. Subqueries

A **subquery** is a query written inside another SQL query.

The inner query provides a result used by the outer query.

### Example

```
SELECT *
FROM students
WHERE age > (
    SELECT AVG(age)
    FROM students
);
```

This retrieves students whose age is greater than the average age.

### Subquery with IN

```
SELECT *
FROM students
WHERE id IN (
    SELECT student_id
    FROM marks
    WHERE score > 80
);
```

This retrieves students whose IDs appear in the result of the inner query.

Related note: [[SQL Subqueries]]

## 14. Aliases

An alias gives a temporary name to a column or table within a query.

### Column Alias

```
SELECT name AS student_name
FROM students;
```

### Table Alias

```
SELECT s.name
FROM students AS s;
```

Aliases improve readability, especially in complex queries involving joins.

## 15. SQL Query Execution Order

SQL statements are written in one order but logically processed in a different order.

A simplified logical processing order is:

1. `FROM` and `JOIN`
    
2. `WHERE`
    
3. `GROUP BY`
    
4. `HAVING`
    
5. `SELECT`
    
6. `DISTINCT`
    
7. `ORDER BY`
    
8. `LIMIT` / `OFFSET`
    

Understanding this order helps explain why a `SELECT` alias generally cannot be used in `WHERE`, but may be used in `ORDER BY` in many databases.

## 16. DQL Security Considerations

DQL operations retrieve data, but they can still create security risks.

### 16.1 Unauthorized Data Access

A user might retrieve information they are not authorized to access.

**Prevention:**

- Enforce authorization checks.
    
- Use database permissions.
    
- Restrict access to sensitive columns and records.
    

### 16.2 SQL Injection

Unsafe query construction can allow attackers to manipulate database queries.

Use parameterized queries.

Python SQLite example:

```
cursor.execute(
    "SELECT * FROM students WHERE name = ?",
    (username,)
)
```

### 16.3 Excessive Data Exposure

Applications should not return unnecessary sensitive information.

For example, a student search page should not expose password hashes or private account information.

### 16.4 Database Permissions

A reporting account should generally receive only the read permissions it requires.

Apply the principle of least privilege.

Related notes:

- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[SQL User Management and Permissions]]
    

## 17. Practical Lab — DQL Queries

**Objective:** Practice retrieving and analyzing records using SQL.

Use your existing `sql_practice` database and the `students` table from the DML lab.

### Step 1: Retrieve All Records

```
SELECT * FROM students;
```

### Step 2: Retrieve Specific Columns

```
SELECT name, age
FROM students;
```

### Step 3: Filter Records

```
SELECT *
FROM students
WHERE age >= 18;
```

### Step 4: Sort Records

```
SELECT *
FROM students
ORDER BY age DESC;
```

### Step 5: Remove Duplicate Values

```
SELECT DISTINCT age
FROM students;
```

### Step 6: Count Records

```
SELECT COUNT(*)
FROM students;
```

### Step 7: Calculate Average Age

```
SELECT AVG(age)
FROM students;
```

### Step 8: Group Records

```
SELECT age, COUNT(*)
FROM students
GROUP BY age;
```

### Step 9: Filter Groups

```
SELECT age, COUNT(*)
FROM students
GROUP BY age
HAVING COUNT(*) > 1;
```

### Lab Observations

Record the following in your notebook:

- What is the difference between `SELECT *` and selecting specific columns?
    
- What is the difference between `WHERE` and `HAVING`?
    
- What happens when you use `DISTINCT`?
    
- How does `GROUP BY` work with `COUNT()`?
    
- Why are parameterized queries important?
    

## 18. Key Takeaways

- DQL retrieves information from database tables.
    
- `SELECT` is its primary command.
    
- `WHERE` filters individual records.
    
- `ORDER BY` sorts query results.
    
- `DISTINCT` removes duplicate result combinations.
    
- Aggregate functions calculate values across records.
    
- `GROUP BY` organizes records into groups.
    
- `HAVING` filters grouped results.
    
- JOINs combine related records from multiple tables.
    
- Subqueries allow one query to use another query's result.
    
- Secure applications must restrict unauthorized data retrieval.
    

## 19. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[DDL - Data Definition Language]]
    
- [[DML - Data Manipulation Language]]
    
- [[SQL Aggregate Functions]]
    
- [[SQL Joins]]
    
- [[SQL Subqueries]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[SQL Practical Labs]]