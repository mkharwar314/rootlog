> Understand how database indexes improve data retrieval, optimize queries, and affect database performance and security.

## 1. What is a SQL Index?

An index is a database structure that helps retrieve records more efficiently.

It works similarly to the index at the back of a textbook.

Instead of searching every page, you use the index to locate the relevant information.

Similarly, a database can use an index to locate records without scanning every row of a table.

### Example

Suppose an `employees` table contains 100,000 records.

Without an index, finding an employee by ID may require examining many rows.

With an appropriate index, the database can locate the record more efficiently.

## 2. Why Are Indexes Important?

Indexes are used to:

- Improve data retrieval speed.
    
- Optimize search queries.
    
- Improve certain JOIN operations.
    
- Support sorting and grouping operations.
    
- Reduce unnecessary table scanning.
    

### Example Without an Index

```
SELECT *
FROM employees
WHERE employee_id = 100;
```

The database may perform a full table scan if no suitable index exists.

### Example With an Index

```
CREATE INDEX idx_employee_id
ON employees(employee_id);
```

The same query may now use the index to locate the record.

**Important:** Creating an index does not guarantee that the database will use it. The query optimizer chooses an execution plan based on factors such as table size, statistics, and query conditions.

## 3. How Indexes Work

Many database indexes use tree-based structures, commonly B-trees or B+ trees.

An index stores searchable key values along with references to the corresponding table records or rows.

Conceptually:

1. The database creates an index on a column.
    
2. It organizes indexed values into a searchable structure.
    
3. A query searches the index.
    
4. The database uses the index to locate matching records.
    

### Simplified Example

Suppose the employee IDs are:

`10, 20, 30, 40, 50`

An index helps the database locate the entry for employee ID `30` without necessarily scanning every row.

This is a conceptual example; actual index structures and lookup behavior depend on the database engine.

## 4. Creating an Index

The `CREATE INDEX` statement creates an index.

### Syntax

```
CREATE INDEX index_name
ON table_name(column_name);
```

### Example

```
CREATE INDEX idx_employee_name
ON employees(employee_name);
```

This creates an index on the `employee_name` column.

A query filtering by that column may benefit:

```
SELECT *
FROM employees
WHERE employee_name = 'Mohit';
```

## 5. Types of SQL Indexes

### 5.1 Single-Column Index

An index created on one column.

```
CREATE INDEX idx_salary
ON employees(salary);
```

Useful for queries that frequently search or filter by salary.

### 5.2 Composite Index

A composite index uses two or more columns.

```
CREATE INDEX idx_department_salary
ON employees(department_id, salary);
```

This may help queries such as:

```
SELECT *
FROM employees
WHERE department_id = 10
AND salary > 30000;
```

**Important:** Column order matters. An index on `(department_id, salary)` is generally most useful when queries use the leading column, department_id, or a suitable leftmost prefix.

It is not equivalent to a separate index on salary.

### 5.3 Unique Index

A unique index prevents duplicate indexed values.

```
CREATE UNIQUE INDEX idx_employee_email
ON employees(email);
```

This ensures that non-NULL email values are unique, subject to the database's NULL-handling rules.

Unique constraints are often the preferred way to express data-integrity requirements. Databases commonly implement them using unique indexes.

### 5.4 Clustered Index

A clustered index determines or strongly influences how table rows are organized by an indexed key.

The exact implementation differs between database systems.

For example:

- SQL Server supports clustered indexes.
    
- InnoDB organizes table data using the primary key as its clustered index.
    
- PostgreSQL's ordinary indexes do not provide the same continuously maintained clustered-table organization.
    

### 5.5 Non-Clustered Index

A non-clustered index is stored separately from the table's main row organization and contains indexed values with references to table records.

It can provide additional search paths without changing the table's primary storage organization.

The terminology and implementation vary by database system.

## 6. Primary Key and Indexes

A primary key uniquely identifies each record in a table.

Most relational database systems automatically create an index to enforce a primary key.

### Example

```
CREATE TABLE students (
    student_id INTEGER PRIMARY KEY,
    student_name VARCHAR(50),
    email VARCHAR(100)
);
```

The database generally creates an index to enforce uniqueness of `student_id`.

You should not automatically create another identical index on the primary key.

## 7. Unique Index vs Normal Index

|Normal Index|Unique Index|
|---|---|
|Improves data retrieval.|Improves retrieval and enforces uniqueness.|
|Allows duplicate indexed values.|Prevents duplicate indexed values.|
|Created using CREATE INDEX.|Created using CREATE UNIQUE INDEX.|

Example:

```
CREATE INDEX idx_student_name
ON students(student_name);
```

```
CREATE UNIQUE INDEX idx_student_email
ON students(email);
```

## 8. Composite Index and Column Order

A composite index contains multiple columns.

Example:

```
CREATE INDEX idx_department_salary
ON employees(department_id, salary);
```

This index may support:

```
SELECT *
FROM employees
WHERE department_id = 10;
```

It may also support:

```
SELECT *
FROM employees
WHERE department_id = 10
AND salary > 30000;
```

However, a query filtering only by salary may not benefit from this index because salary is not the leading column.

A separate index may be appropriate depending on workload and query plans.

## 9. Deleting an Index

The `DROP INDEX` statement removes an index.

Syntax varies across database systems.

### PostgreSQL

```
DROP INDEX idx_employee_name;
```

### MySQL

```
DROP INDEX idx_employee_name
ON employees;
```

### SQL Server

```
DROP INDEX idx_employee_name
ON employees;
```

**Important:** Check your database's syntax before executing DROP INDEX.

Removing an index does not delete the underlying table records, but it can affect query performance and constraints.

## 10. Viewing Index Information

Different databases provide different commands for inspecting indexes.

### SQLite

```
PRAGMA index_list('employees');
```

To inspect indexed columns:

```
PRAGMA index_info('idx_employee_name');
```

### MySQL

```
SHOW INDEX FROM employees;
```

### PostgreSQL

```
SELECT
    indexname,
    indexdef
FROM pg_indexes
WHERE tablename = 'employees';
```

### SQL Server

```
EXEC sp_helpindex 'employees';
```

## 11. Indexes and Query Performance

Indexes can improve query performance, but they also have costs.

### Advantages

- Faster lookups for suitable queries.
    
- Better performance for certain JOIN operations.
    
- More efficient filtering and sorting in suitable cases.
    
- Support for uniqueness constraints.
    

### Disadvantages

- Require additional storage.
    
- Slow down INSERT operations in many cases.
    
- Slow down UPDATE operations affecting indexed columns.
    
- Slow down DELETE operations because index entries must be maintained.
    
- Require maintenance and monitoring.
    

**Important:** Too many indexes can reduce overall database performance.

## 12. Full Table Scan vs Index Scan

### Full Table Scan

The database examines the table's rows to find matching records.

It may be appropriate for:

- Small tables.
    
- Queries returning a large percentage of rows.
    
- Queries without useful indexes.
    

### Index Scan

The database uses an index to locate relevant records.

It may be appropriate for:

- Selective searches.
    
- Large tables.
    
- Frequently queried indexed columns.
    

The optimizer decides which execution strategy is appropriate.

## 13. Query Execution Plan

A query execution plan describes how a database intends to execute a SQL statement.

It can show:

- Table scans.
    
- Index scans or seeks.
    
- JOIN strategies.
    
- Sorting operations.
    
- Estimated or actual costs.
    

### Example Using EXPLAIN

```
EXPLAIN
SELECT *
FROM employees
WHERE employee_name = 'Mohit';
```

`EXPLAIN` helps investigate whether an index is being considered.

Some database systems also support `EXPLAIN ANALYZE` to execute a query and report actual execution details. Use it carefully on expensive queries or production systems.

## 14. Indexes in Cybersecurity

Indexes can support security monitoring and investigation by improving searches across large datasets.

### 14.1 Searching Login Logs

Assume a table called `login_logs` contains a `username` column.

```
CREATE INDEX idx_login_username
ON login_logs(username);
```

This may improve queries filtering by username:

```
SELECT *
FROM login_logs
WHERE username = 'Mohit';
```

### 14.2 Searching by Source IP

```
CREATE INDEX idx_login_source_ip
ON login_logs(source_ip);
```

Query:

```
SELECT *
FROM login_logs
WHERE source_ip = '192.168.1.50';
```

This may help investigate activity associated with a particular source IP.

### 14.3 Composite Index for Security Events

```
CREATE INDEX idx_login_user_status
ON login_logs(username, status);
```

This may help queries such as:

```
SELECT *
FROM login_logs
WHERE username = 'Mohit'
AND status = 'FAILED';
```

Index design should be based on actual query patterns and execution plans.

## 15. Common Indexing Mistakes

|Mistake|Explanation|
|---|---|
|Creating too many indexes|Increases storage and write overhead.|
|Indexing every column|Many indexes may provide little benefit.|
|Ignoring column order|Composite index order affects usability.|
|Duplicating indexes|Redundant indexes waste resources.|
|Ignoring query plans|An index may not be used by the optimizer.|
|Forgetting write performance|Indexes must be maintained when data changes.|
|Assuming indexes secure data|Indexes improve access performance, not authorization.|

## 16. Practical Lab — SQL Indexes

**Objective:** Create, inspect, and remove indexes.

Use your SQL practice database.

### Step 1: Create a Table

```
CREATE TABLE employees_index (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER,
    salary DECIMAL(10,2)
);
```

### Step 2: Insert Records

```
INSERT INTO employees_index
VALUES
(1, 'Mohit', 10, 35000),
(2, 'Rahul', 20, 42000),
(3, 'Aman', 10, 25000),
(4, 'Priya', 30, 50000),
(5, 'Neha', 20, 30000);
```

### Step 3: Create a Single-Column Index

```
CREATE INDEX idx_emp_name
ON employees_index(employee_name);
```

### Step 4: Create a Composite Index

```
CREATE INDEX idx_emp_dept_salary
ON employees_index(department_id, salary);
```

### Step 5: Create a Unique Index

```
CREATE UNIQUE INDEX idx_emp_unique_name
ON employees_index(employee_name);
```

This works because the current employee names are unique.

### Step 6: Inspect Indexes

If you are using SQLite:

```
PRAGMA index_list('employees_index');
```

Inspect a particular index:

```
PRAGMA index_info('idx_emp_name');
```

### Step 7: Examine a Query Plan

```
EXPLAIN QUERY PLAN
SELECT *
FROM employees_index
WHERE employee_name = 'Mohit';
```

Observe whether SQLite uses an index.

### Step 8: Remove an Index

For SQLite:

```
DROP INDEX idx_emp_name;
```

Verify the remaining indexes:

```
PRAGMA index_list('employees_index');
```

### Lab Observations

Record these questions in your notebook:

1. What is a database index?
    
2. Why are indexes compared to textbook indexes?
    
3. What is the difference between a single-column and composite index?
    
4. Why can too many indexes reduce performance?
    
5. What information does EXPLAIN provide?
    
6. Why are indexes useful when searching large security logs?
    

## 17. Key Takeaways

- An index improves data retrieval for suitable queries.
    
- CREATE INDEX creates an index.
    
- UNIQUE INDEX enforces uniqueness.
    
- Composite indexes contain multiple columns.
    
- Index column order matters.
    
- Indexes require additional storage.
    
- Indexes can increase write overhead.
    
- EXPLAIN helps analyze query execution plans.
    
- Indexes support efficient searching in large security datasets.
    
- Indexes do not replace database permissions or security controls.
    

## 18. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[SQL Aggregate Functions]]
    
- [[SQL Joins]]
    
- [[SQL Subqueries]]
    
- [[SQL Views]]
    
- [[SQL Transactions]]
    
- [[SQL User Management and Permissions]]
    
- [[SQL Injection]]
    
- [[SQL Practical Labs]]