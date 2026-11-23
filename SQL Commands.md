> Understand the different categories of SQL commands and how they are used to create, retrieve, modify, and manage database information.

## 1. Introduction to SQL Commands

SQL commands are instructions used to communicate with a database management system.

They allow users to:

- Create database structures.
    
- Insert information.
    
- Retrieve records.
    
- Modify existing data.
    
- Delete information.
    
- Manage permissions.
    
- Control transactions.
    

SQL commands are commonly classified into five categories:

1. DDL — Data Definition Language
    
2. DML — Data Manipulation Language
    
3. DQL — Data Query Language
    
4. DCL — Data Control Language
    
5. TCL — Transaction Control Language
    

## 2. DDL — Data Definition Language

DDL commands define and modify database structures.

Common DDL commands:

|Command|Purpose|
|---|---|
|CREATE|Creates database objects|
|ALTER|Modifies database structures|
|DROP|Removes database objects|
|TRUNCATE|Removes all rows from a table|
|RENAME|Renames a database object where supported|

### CREATE

Creates a database or database object.

Example:

```
CREATE DATABASE college_db;
```

Create a table:

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

### ALTER

Changes the structure of an existing table.

Add a column:

```
ALTER TABLE students
ADD email VARCHAR(100);
```

Modify a column's type in MySQL:

```
ALTER TABLE students
MODIFY age SMALLINT;
```

The syntax for changing column definitions differs between database systems.

### DROP

Permanently removes a database object.

Example:

```
DROP TABLE students;
```

This removes the table structure and its stored records.

### TRUNCATE

Removes all rows from a table while retaining its structure.

Example:

```
TRUNCATE TABLE students;
```

Transaction behavior, identity resets, and rollback support depend on the database system.

### RENAME

Renames a database object where supported.

Example in MySQL:

```
RENAME TABLE students TO college_students;
```

## 3. DML — Data Manipulation Language

DML commands manipulate records stored inside tables.

Common DML commands:

|Command|Purpose|
|---|---|
|INSERT|Adds records|
|UPDATE|Modifies records|
|DELETE|Removes records|

### INSERT

Adds new records.

```
INSERT INTO students (student_id, name, age)
VALUES (101, 'Mohit', 19);
```

Insert multiple records:

```
INSERT INTO students (student_id, name, age)
VALUES
(102, 'Rahul', 20),
(103, 'Aman', 18);
```

### UPDATE

Modifies existing records.

```
UPDATE students
SET age = 20
WHERE student_id = 101;
```

**Important:** Always check the WHERE condition before executing an UPDATE. Without it, every row may be modified.

### DELETE

Removes selected records.

```
DELETE FROM students
WHERE student_id = 103;
```

Without a WHERE condition, DELETE can remove all rows from the table.

## 4. DQL — Data Query Language

DQL retrieves information from a database.

The main DQL command is:

### SELECT

Retrieves records from a table.

```
SELECT * FROM students;
```

Retrieve specific columns:

```
SELECT name, age
FROM students;
```

Retrieve records matching a condition:

```
SELECT *
FROM students
WHERE age > 18;
```

Other commonly used SELECT clauses include:

- WHERE
    
- ORDER BY
    
- GROUP BY
    
- HAVING
    
- LIMIT
    

## 5. DCL — Data Control Language

DCL commands manage database access privileges.

Common commands:

|Command|Purpose|
|---|---|
|GRANT|Gives privileges|
|REVOKE|Removes privileges|

### GRANT

Gives a user permission to perform an operation.

Example:

```
GRANT SELECT
ON college_db.students
TO 'analyst'@'localhost';
```

This is MySQL-style syntax. User creation and permission syntax vary by database system.

### REVOKE

Removes previously granted permissions.

```
REVOKE SELECT
ON college_db.students
FROM 'analyst'@'localhost';
```

DCL is important for implementing least privilege.

## 6. TCL — Transaction Control Language

TCL commands manage database transactions.

Common commands:

|Command|Purpose|
|---|---|
|COMMIT|Saves transaction changes|
|ROLLBACK|Reverses uncommitted changes|
|SAVEPOINT|Creates a rollback point|

### COMMIT

Permanently commits a transaction.

```
START TRANSACTION;

UPDATE students
SET age = 21
WHERE student_id = 101;

COMMIT;
```

### ROLLBACK

Reverses changes made in the current uncommitted transaction.

```
START TRANSACTION;

UPDATE students
SET age = 25
WHERE student_id = 101;

ROLLBACK;
```

### SAVEPOINT

Creates a point inside a transaction.

```
START TRANSACTION;

UPDATE students
SET age = 21
WHERE student_id = 101;

SAVEPOINT first_update;

UPDATE students
SET age = 22
WHERE student_id = 102;

ROLLBACK TO SAVEPOINT first_update;

COMMIT;
```

After this transaction, the first update remains committed, while the second update is rolled back.

Transaction support and exact syntax vary between database systems and storage engines.

## 7. Comparison of SQL Command Categories

|Category|Full Form|Main Purpose|Examples|
|---|---|---|---|
|DDL|Data Definition Language|Defines structures|CREATE, ALTER, DROP|
|DML|Data Manipulation Language|Changes records|INSERT, UPDATE, DELETE|
|DQL|Data Query Language|Retrieves records|SELECT|
|DCL|Data Control Language|Manages permissions|GRANT, REVOKE|
|TCL|Transaction Control Language|Controls transactions|COMMIT, ROLLBACK|

## 8. Important Differences

### DELETE vs TRUNCATE vs DROP

|Feature|DELETE|TRUNCATE|DROP|
|---|---|---|---|
|Removes rows|Yes|Yes, all rows|Removes table itself|
|Supports WHERE|Yes|No|No|
|Table structure remains|Yes|Yes|No|
|Typical use|Remove selected records|Empty a table|Remove a table|

Exact transactional behavior and performance depend on the database system.

### DDL vs DML

|DDL|DML|
|---|---|
|Defines database structures|Manipulates stored records|
|Example: CREATE|Example: INSERT|
|Example: ALTER|Example: UPDATE|
|Example: DROP|Example: DELETE|

## 9. SQL Commands in Cybersecurity

Understanding SQL commands helps security professionals assess database activity.

### 1. Unauthorized Data Modification

Attackers may attempt to modify or delete records using UPDATE or DELETE.

### 2. Privilege Abuse

Misconfigured GRANT permissions can give users excessive database access.

### 3. Data Exfiltration

SELECT queries can be abused to retrieve sensitive information.

### 4. Destructive Database Operations

DROP and TRUNCATE can cause serious data loss if improperly authorized.

### 5. Transaction Abuse

Poor transaction handling can lead to inconsistent or incomplete operations.

### Security Recommendations

- Apply least privilege.
    
- Restrict administrative access.
    
- Use parameterized queries.
    
- Audit sensitive operations.
    
- Maintain protected backups.
    
- Test destructive operations in a lab first.
    

## 10. Practical Lab

Use a test database only.

### Step 1: Create a Database

```
CREATE DATABASE sql_practice;
```

### Step 2: Select the Database

```
USE sql_practice;
```

This syntax is supported by MySQL and some compatible systems.

### Step 3: Create a Table

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

### Step 4: Insert Records

```
INSERT INTO students VALUES
(101, 'Mohit', 19),
(102, 'Rahul', 20),
(103, 'Aman', 18);
```

### Step 5: Retrieve Records

```
SELECT * FROM students;
```

### Step 6: Update a Record

```
UPDATE students
SET age = 21
WHERE student_id = 102;
```

### Step 7: Delete a Record

```
DELETE FROM students
WHERE student_id = 103;
```

### Step 8: Test a Transaction

```
START TRANSACTION;

UPDATE students
SET age = 25
WHERE student_id = 101;

ROLLBACK;
```

Check whether the original age remains unchanged.

## 11. Key Takeaways

- SQL commands communicate with databases.
    
- DDL defines database structures.
    
- DML manipulates records.
    
- DQL retrieves records.
    
- DCL manages permissions.
    
- TCL manages transactions.
    
- DELETE removes selected rows.
    
- TRUNCATE removes all rows.
    
- DROP removes the database object.
    
- Destructive SQL commands must be used carefully.
    

## 12. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Data Types]]
    
- [[DDL - Data Definition Language]]
    
- [[DML - Data Manipulation Language]]
    
- [[DQL - Data Query Language]]
    
- [[DCL - Data Control Language]]
    
- [[TCL - Transaction Control Language]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    

## 13. My Understanding

Explain in your own words:

- What are SQL commands?
    
- What is DDL?
    
- What is DML?
    
- What is DQL?
    
- What is DCL?
    
- What is TCL?
    
- What is the difference between DELETE, TRUNCATE and DROP?
    
- Why should UPDATE and DELETE be used carefully?
    

## 14. Questions & Doubts

Record questions that need further research.