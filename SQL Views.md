> Understand how SQL views provide virtual tables based on stored queries, simplify database operations, and control access to information.

## 1. What is a SQL View?

A view is a virtual table created using a SQL query.

It presents data from one or more existing tables without normally storing a separate copy of the underlying rows.

A view can be used to:

- Simplify complex SQL queries.
    
- Display selected columns.
    
- Restrict access to sensitive information.
    
- Organize frequently used queries.
    
- Present customized data to different users.
    

### Example

Suppose an `employees` table contains:

|employee_id|employee_name|department_id|salary|
|---|---|---|---|
|1|Mohit|10|35000|
|2|Rahul|20|42000|
|3|Aman|10|25000|

Instead of repeatedly writing a query to retrieve employee names and departments, we can create a view.

```
CREATE VIEW employee_details AS
SELECT employee_id, employee_name, department_id
FROM employees;
```

Now we can query the view:

```
SELECT *
FROM employee_details;
```

The view displays the selected columns from the underlying table.

## 2. How SQL Views Work

A normal database view stores its query definition.

When the view is queried, the database uses that definition to retrieve the underlying data.

Conceptually:

1. Create a view using SELECT.
    
2. The database stores the view definition.
    
3. Query the view like a table.
    
4. The database retrieves data from the underlying tables.
    

**Important:** A normal view generally does not store its own copy of the underlying data. Materialized views are a separate feature that can store query results.

## 3. Creating a View

The `CREATE VIEW` statement creates a new view.

### Syntax

```
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

### Example

```
CREATE VIEW high_salary_employees AS
SELECT employee_name, salary
FROM employees
WHERE salary > 40000;
```

This creates a view containing employees whose salaries exceed 40,000.

Query it:

```
SELECT *
FROM high_salary_employees;
```

## 4. Querying a View

A view can be queried using SELECT just like a regular table.

### Example

```
SELECT employee_name
FROM employee_details;
```

You can also apply conditions:

```
SELECT *
FROM employee_details
WHERE department_id = 10;
```

You can combine views with other tables using JOINs:

```
SELECT
    V.employee_name,
    D.department_name
FROM employee_details V
INNER JOIN departments D
ON V.department_id = D.department_id;
```

## 5. Updating a View

Some views are updatable, meaning INSERT, UPDATE, or DELETE operations through the view can modify the underlying table.

However, not every view supports these operations.

### Example

```
CREATE VIEW employee_basic AS
SELECT employee_id, employee_name, salary
FROM employees;
```

If the database supports updating this view:

```
UPDATE employee_basic
SET salary = 45000
WHERE employee_id = 1;
```

This updates the corresponding record in the underlying `employees` table.

### Conditions Affecting Updatability

A simple view based on one table is more likely to be updatable.

Views involving the following features may not be directly updatable, depending on the database:

- Aggregate functions.
    
- GROUP BY.
    
- DISTINCT.
    
- UNION.
    
- Certain JOINs.
    
- Calculated columns.
    

Database systems have different rules for view updatability.

## 6. Replacing a View

Some database systems support `CREATE OR REPLACE VIEW`.

It allows an existing view definition to be replaced.

### Example

```
CREATE OR REPLACE VIEW employee_details AS
SELECT employee_id, employee_name, department_id, salary
FROM employees;
```

This changes the definition to include salary.

**Database compatibility:** `CREATE OR REPLACE VIEW` is supported by several major databases, but syntax and behavior vary. Check your database documentation before using it.

## 7. Deleting a View

The `DROP VIEW` statement removes a view definition.

### Syntax

```
DROP VIEW view_name;
```

### Example

```
DROP VIEW employee_details;
```

This removes the view, not the underlying employee records.

Some databases support:

```
DROP VIEW IF EXISTS employee_details;
```

This avoids an error if the view does not exist.

## 8. Views with JOINs

Views can combine information from multiple tables.

### Example

```
CREATE VIEW employee_department_view AS
SELECT
    E.employee_id,
    E.employee_name,
    D.department_name
FROM employees E
INNER JOIN departments D
ON E.department_id = D.department_id;
```

Query:

```
SELECT *
FROM employee_department_view;
```

This view presents employee information alongside department names.

## 9. Views with Aggregate Functions

Views can also contain aggregate queries.

### Example

```
CREATE VIEW department_salary_summary AS
SELECT
    department_id,
    COUNT(*) AS employee_count,
    AVG(salary) AS average_salary
FROM employees
GROUP BY department_id;
```

Query:

```
SELECT *
FROM department_salary_summary;
```

This provides a summary of employee counts and average salaries by department.

Such views are generally not directly updatable.

## 10. Types of Views

Views can be classified in different ways depending on the database system and context.

### 10.1 Simple View

A simple view generally uses one base table without complex operations.

Example:

```
CREATE VIEW employee_names AS
SELECT employee_id, employee_name
FROM employees;
```

### 10.2 Complex View

A complex view may involve multiple tables, joins, aggregates, or other advanced SQL operations.

Example:

```
CREATE VIEW department_summary AS
SELECT
    department_id,
    COUNT(*) AS total_employees
FROM employees
GROUP BY department_id;
```

### 10.3 Materialized View

A materialized view stores the result of a query rather than calculating it from the underlying tables every time it is accessed.

It can improve performance for expensive reporting queries.

However, its stored results may become outdated when the underlying data changes.

Materialized views require a refresh mechanism.

**Important:** Materialized view syntax and support vary significantly across database systems. MySQL, PostgreSQL, and Oracle do not all implement this feature in the same way.

## 11. View vs Table

|View|Table|
|---|---|
|Represents data through a query.|Stores data in database rows.|
|Normal views generally do not store their own data.|Stores records physically or through the database's storage engine.|
|Usually depends on underlying tables.|Can exist independently.|
|Can simplify complex queries.|Stores the original data.|
|Changes to underlying data are reflected when queried.|Contains the stored records themselves.|

## 12. View vs Materialized View

|Normal View|Materialized View|
|---|---|
|Stores a query definition.|Stores query results.|
|Retrieves current underlying data when queried.|May contain results from an earlier refresh.|
|Usually requires no refresh operation.|Requires refreshing to reflect changes.|
|Usually uses less additional storage.|Requires additional storage.|
|Useful for simplifying queries.|Useful for expensive reporting and analytics.|

## 13. Advantages of SQL Views

### 13.1 Simplifies Queries

Complex queries can be stored as views and reused.

### 13.2 Improves Data Presentation

Users can see only the columns relevant to their work.

### 13.3 Supports Access Control

A database administrator can grant access to a view without granting direct access to the entire underlying table, depending on the database's permission model.

### 13.4 Improves Maintainability

Common query logic can be centralized in a view.

### 13.5 Supports Reporting

Views can provide summarized information for dashboards and reports.

## 14. Limitations of SQL Views

- A view depends on its underlying tables and objects.
    
- Complex views may be difficult to maintain.
    
- Some views cannot be updated directly.
    
- Poorly designed views can lead to inefficient queries.
    
- Normal views do not automatically improve query performance.
    
- Changes to underlying table structures can break dependent views.
    

## 15. SQL Views in Cybersecurity

Views can help database administrators and security analysts expose only the information required for a particular task.

### 15.1 Hide Sensitive Columns

Suppose an `users` table contains:

|user_id|username|email|password_hash|
|---|---|---|---|
|1|Mohit|[mohit@example.com](mailto:mohit@example.com)|hash_value_1|
|2|Rahul|[rahul@example.com](mailto:rahul@example.com)|hash_value_2|

An analyst may need usernames and email addresses but not password hashes.

Create a view:

```
CREATE VIEW user_public_details AS
SELECT user_id, username, email
FROM users;
```

Query:

```
SELECT *
FROM user_public_details;
```

The password hash is not exposed through this view.

**Important security distinction:** A view is not automatically a security boundary. The database administrator must configure permissions correctly and prevent users from accessing the underlying sensitive table directly.

### 15.2 Create a Security Event View

Assume a `security_logs` table contains:

- `event_id`
    
- `username`
    
- `source_ip`
    
- `event_type`
    
- `event_time`
    

Create a view for failed login events:

```
CREATE VIEW failed_login_events AS
SELECT
    event_id,
    username,
    source_ip,
    event_time
FROM security_logs
WHERE event_type = 'FAILED_LOGIN';
```

Query:

```
SELECT *
FROM failed_login_events;
```

This provides a reusable view of failed login events.

### 15.3 Restrict Access to a View

Some databases support granting permissions on views.

For example, in PostgreSQL:

```
GRANT SELECT
ON failed_login_events
TO security_analyst;
```

The analyst can be granted permission to read the view.

The exact syntax and security behavior depend on the database system.

## 16. Common Mistakes

|Mistake|Explanation|
|---|---|
|Assuming a view stores data|A normal view generally stores only its query definition.|
|Assuming every view is updatable|Complex views may not support direct modifications.|
|Forgetting underlying dependencies|A view can fail if its source table or columns change.|
|Assuming a view automatically secures data|Permissions on underlying tables must also be controlled.|
|Expecting a view to improve performance|A normal view does not automatically make a query faster.|
|Confusing views with materialized views|Materialized views store query results.|

## 17. Practical Lab — SQL Views

**Objective:** Create, query, and manage SQL views.

Use your SQL practice database.

### Step 1: Create an Employees Table

```
CREATE TABLE employees_view (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER,
    salary DECIMAL(10,2)
);
```

### Step 2: Insert Records

```
INSERT INTO employees_view
VALUES
(1, 'Mohit', 10, 35000),
(2, 'Rahul', 20, 42000),
(3, 'Aman', 10, 25000),
(4, 'Priya', 30, 50000),
(5, 'Neha', 20, 30000);
```

### Step 3: Create a Basic View

```
CREATE VIEW employee_names_view AS
SELECT employee_id, employee_name
FROM employees_view;
```

### Step 4: Query the View

```
SELECT *
FROM employee_names_view;
```

### Step 5: Create a Filtered View

```
CREATE VIEW high_salary_view AS
SELECT employee_name, salary
FROM employees_view
WHERE salary > 35000;
```

### Step 6: Query the Filtered View

```
SELECT *
FROM high_salary_view;
```

### Step 7: Create an Aggregate View

```
CREATE VIEW department_summary_view AS
SELECT
    department_id,
    COUNT(*) AS employee_count,
    AVG(salary) AS average_salary
FROM employees_view
GROUP BY department_id;
```

### Step 8: Query the Aggregate View

```
SELECT *
FROM department_summary_view;
```

### Step 9: Update an Updatable View

If your database supports updating this simple view:

```
UPDATE employee_names_view
SET employee_name = 'Mohit Kumar'
WHERE employee_id = 1;
```

Verify the change:

```
SELECT *
FROM employees_view;
```

### Step 10: Delete a View

```
DROP VIEW IF EXISTS high_salary_view;
```

Verify that the underlying table still exists:

```
SELECT *
FROM employees_view;
```

### Lab Observations

Record these questions in your notebook:

1. What is a SQL view?
    
2. What is the difference between a view and a table?
    
3. Why are views useful for access control?
    
4. What is a materialized view?
    
5. Why should database permissions also be configured on underlying tables?
    

## 18. Key Takeaways

- A view is a virtual table based on a SQL query.
    
- CREATE VIEW creates a view.
    
- SELECT retrieves data from a view.
    
- DROP VIEW removes a view definition.
    
- Views can combine multiple tables.
    
- Views can contain aggregate functions.
    
- Materialized views store query results.
    
- Views can help restrict exposure of sensitive columns when permissions are configured correctly.
    
- Views are useful for database reporting and security monitoring.
    

## 19. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[SQL Joins]]
    
- [[SQL Subqueries]]
    
- [[SQL Indexes]]
    
- [[SQL User Management and Permissions]]
    
- [[SQL Injection]]
    
- [[SQL Practical Labs]]