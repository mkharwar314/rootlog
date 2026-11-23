> Understand how SQL defines, creates, modifies, and removes database structures using DDL commands.

## 1. Introduction to DDL

**DDL (Data Definition Language)** is a category of SQL commands used to define and modify database structures.

DDL is used to manage objects such as:

- Databases.
    
- Tables.
    
- Schemas.
    
- Views.
    
- Indexes.
    

Unlike DML, which primarily manipulates records, DDL focuses on the structure of database objects.

## 2. Main DDL Commands

|Command|Purpose|
|---|---|
|CREATE|Creates database objects|
|ALTER|Modifies existing structures|
|DROP|Removes database objects|
|TRUNCATE|Removes all rows from a table|
|RENAME|Renames database objects where supported|

## 3. CREATE Command

The `CREATE` command creates new database objects.

### Create a Database

```
CREATE DATABASE college_db;
```

### Create a Table

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    email VARCHAR(150)
);
```

### Explanation

- `CREATE TABLE` creates a new table.
    
- `student_id` stores student identifiers.
    
- `INT` defines an integer column.
    
- `VARCHAR(100)` stores variable-length text.
    
- `PRIMARY KEY` uniquely identifies each row.
    

## 4. ALTER Command

The `ALTER` command modifies an existing database structure.

### Add a Column

```
ALTER TABLE students
ADD phone VARCHAR(20);
```

### Remove a Column

```
ALTER TABLE students
DROP COLUMN phone;
```

### Rename a Column

In MySQL:

```
ALTER TABLE students
RENAME COLUMN name TO full_name;
```

### Change a Column's Data Type

In MySQL:

```
ALTER TABLE students
MODIFY age SMALLINT;
```

**Note:** ALTER syntax differs between database systems. Check the documentation for the DBMS you are using.

## 5. DROP Command

The `DROP` command permanently removes a database object.

### Drop a Table

```
DROP TABLE students;
```

### Drop a Database

```
DROP DATABASE college_db;
```

### Important Points

- DROP removes the object itself.
    
- Its associated data is also removed.
    
- Recovery may require restoring from a backup.
    
- Always verify the target before executing DROP.
    

## 6. TRUNCATE Command

The `TRUNCATE` command removes all records from a table while keeping its structure.

Example:

```
TRUNCATE TABLE students;
```

After execution:

- The table still exists.
    
- Its columns remain.
    
- Its records are removed.
    
- Database-specific identity and transaction behavior may apply.
    

Unlike DELETE, TRUNCATE does not support a WHERE clause.

## 7. RENAME Command

The RENAME operation changes the name of an existing database object where supported.

MySQL example:

```
RENAME TABLE students TO student_records;
```

The table name changes, but the stored records remain.

## 8. CREATE vs ALTER vs DROP vs TRUNCATE

|Feature|CREATE|ALTER|DROP|TRUNCATE|
|---|---|---|---|---|
|Creates an object|Yes|No|No|No|
|Changes structure|Creates initial structure|Yes|Removes structure|No|
|Removes all records|No|No|Yes, with object|Yes|
|Object remains|Yes|Yes|No|Yes|

## 9. DDL in Database Administration

Database administrators use DDL to:

1. Design database structures.
    
2. Create tables and schemas.
    
3. Modify columns.
    
4. Create indexes.
    
5. Manage views.
    
6. Remove obsolete objects.
    
7. Maintain database organization.
    

DDL should be managed carefully in production environments because structural changes can affect applications and stored information.

## 10. DDL Security Considerations

DDL commands can have significant security consequences.

### 1. Unauthorized Schema Changes

An attacker or unauthorized user may alter tables or database structures.

### 2. Destructive Operations

DROP and TRUNCATE can cause major data loss.

### 3. Excessive Privileges

Users with unnecessary schema-management permissions create additional risk.

### 4. Database Misconfiguration

Poorly designed tables or constraints can weaken data integrity.

### Security Best Practices

- Restrict DDL permissions.
    
- Separate development and production environments.
    
- Review schema changes before deployment.
    
- Maintain database backups.
    
- Audit administrative operations.
    
- Use version-controlled database migrations.
    
- Test changes before applying them to production.
    

## 11. Practical Lab

Perform the following operations in your test database.

### Step 1: Create a Database

```
CREATE DATABASE ddl_lab;
```

### Step 2: Select the Database

MySQL syntax:

```
USE ddl_lab;
```

### Step 3: Create a Table

```
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50)
);
```

### Step 4: Add a Column

```
ALTER TABLE employees
ADD email VARCHAR(150);
```

### Step 5: Rename the Table

MySQL syntax:

```
RENAME TABLE employees TO staff;
```

### Step 6: Inspect the Table

```
DESCRIBE staff;
```

### Step 7: Remove the Table

```
DROP TABLE staff;
```

Perform DROP only after verifying that you are working in your practice database.

## 12. Key Takeaways

- DDL stands for Data Definition Language.
    
- DDL manages database structures.
    
- CREATE creates database objects.
    
- ALTER modifies existing structures.
    
- DROP removes database objects.
    
- TRUNCATE removes all rows while retaining the table structure.
    
- RENAME changes object names where supported.
    
- DDL permissions should be restricted.
    
- Destructive operations require careful review.
    

## 13. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[DML - Data Manipulation Language]]
    
- [[DQL - Data Query Language]]
    
- [[DCL - Data Control Language]]
    
- [[TCL - Transaction Control Language]]
    
- [[SQL Constraints]]
    
- [[SQL Indexes]]
    

## 14. My Understanding

Explain in your own words:

- What is DDL?
    
- What is the purpose of CREATE?
    
- How does ALTER work?
    
- What is the difference between DROP and TRUNCATE?
    
- Why should DDL permissions be restricted?
    
- Why should database schema changes be tested?
    

## 15. Questions & Doubts

Record questions that need further research.