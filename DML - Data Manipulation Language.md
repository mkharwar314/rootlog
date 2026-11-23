> Understand how SQL modifies, inserts, and deletes records stored in database tables.

## 1. What is DML?

**DML (Data Manipulation Language)** is a category of SQL commands used to manipulate the data stored inside database tables.

DML works with existing table structures. It changes the records without defining or changing the table's structure.

For example, in a student database, DML can be used to:

- Add a new student.
    
- Update a student's email address.
    
- Delete a student record.
    
- Insert multiple records into a table.
    

### Main DML Commands

|Command|Purpose|
|---|---|
|`INSERT`|Adds new records.|
|`UPDATE`|Modifies existing records.|
|`DELETE`|Removes records.|

**Important:** `SELECT` is commonly classified as DQL (Data Query Language) in this ROOTLOG structure. Some SQL references classify it differently.

## 2. INSERT Command

The `INSERT` command adds new records to a table.

### Basic Syntax

```
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);
```

### Example: Insert a Single Record

Assume we have a table named `students`.

```
INSERT INTO students (id, name, age)
VALUES (1, 'Mohit', 18);
```

This inserts one student record.

### Insert Multiple Records

```
INSERT INTO students (id, name, age)
VALUES
(2, 'Rahul', 19),
(3, 'Aman', 20),
(4, 'Priya', 18);
```

Multiple records can be inserted using one statement in databases that support this syntax.

### Insert Without Specifying Every Column

If a column has a default value or allows `NULL`, it may be omitted.

```
INSERT INTO students (id, name)
VALUES (5, 'Neha');
```

The omitted columns receive their default values or `NULL`, depending on the table definition.

### Insert Data from Another Table

`INSERT INTO ... SELECT` copies selected records from one table into another compatible table.

```
INSERT INTO student_backup (id, name, age)
SELECT id, name, age
FROM students;
```

The destination columns and selected values must have compatible data types and order.

### Best Practices for INSERT

- Specify column names instead of relying on table column order.
    
- Use appropriate data types.
    
- Avoid inserting unnecessary or duplicate records.
    
- Validate input before inserting it.
    
- Respect constraints such as primary keys and foreign keys.
    

## 3. UPDATE Command

The `UPDATE` command modifies existing records in a table.

### Basic Syntax

```
UPDATE table_name
SET column_name = new_value
WHERE condition;
```

### Example: Update One Record

```
UPDATE students
SET age = 19
WHERE id = 1;
```

This changes the age of the student whose ID is `1`.

### Update Multiple Columns

```
UPDATE students
SET name = 'Mohit Kumar',
    age = 20
WHERE id = 1;
```

This updates both the name and age of the matching student.

### The Importance of WHERE

The `WHERE` clause identifies which records should be updated.

**Without WHERE, every row in the table may be updated.**

For example:

```
UPDATE students
SET age = 18;
```

This changes the age of every student to `18`.

### Preview Records Before Updating

Before executing an update, inspect the target records:

```
SELECT *
FROM students
WHERE id = 1;
```

Then execute the update only after confirming the target.

## 4. DELETE Command

The `DELETE` command removes records from a table.

### Basic Syntax

```
DELETE FROM table_name
WHERE condition;
```

### Example: Delete One Record

```
DELETE FROM students
WHERE id = 3;
```

This removes the student whose ID is `3`.

### Delete Multiple Records

```
DELETE FROM students
WHERE age < 18;
```

This removes all records matching the condition.

### Delete All Records

```
DELETE FROM students;
```

This removes all rows from the table but keeps the table structure.

**Warning:** Without a `WHERE` clause, `DELETE` can remove every record in the table.

### Preview Before Deleting

Always inspect the records first:

```
SELECT *
FROM students
WHERE id = 3;
```

If the result is correct, execute the corresponding `DELETE` statement.

## 5. Difference Between DELETE, TRUNCATE, and DROP

These commands have different purposes.

|Command|Purpose|Table Structure|
|---|---|---|
|`DELETE`|Removes selected or all rows.|Preserved|
|`TRUNCATE`|Removes all rows from a table.|Preserved|
|`DROP`|Removes the table itself.|Removed|

Example:

```
DELETE FROM students
WHERE id = 1;
```

```
TRUNCATE TABLE students;
```

```
DROP TABLE students;
```

**Important:** `TRUNCATE` and `DROP` are DDL commands in many common SQL classifications. Their transaction and rollback behavior varies by database system.

Related note: [[DDL - Data Definition Language]]

## 6. UPSERT — Insert or Update

An **UPSERT** operation inserts a new record if it does not exist, or updates an existing record if a matching key already exists.

It combines insertion and updating behavior.

The exact syntax depends on the database.

### PostgreSQL Example

```
INSERT INTO students (id, name, age)
VALUES (1, 'Mohit', 19)
ON CONFLICT (id)
DO UPDATE SET
    name = EXCLUDED.name,
    age = EXCLUDED.age;
```

### MySQL Example

```
INSERT INTO students (id, name, age)
VALUES (1, 'Mohit', 19)
ON DUPLICATE KEY UPDATE
    name = VALUES(name),
    age = VALUES(age);
```

These examples are database-specific. Do not assume the same syntax works in every SQL database.

## 7. DML and Transactions

A transaction is a group of database operations treated as one logical unit.

Transactions help protect data when multiple modifications must succeed together.

### Important Transaction Commands

|Command|Purpose|
|---|---|
|`BEGIN` / `START TRANSACTION`|Starts a transaction.|
|`COMMIT`|Saves transaction changes.|
|`ROLLBACK`|Reverses uncommitted changes.|

Exact syntax and behavior depend on the database.

### Example: Transaction with UPDATE

```
START TRANSACTION;

UPDATE students
SET age = 20
WHERE id = 1;

ROLLBACK;
```

The update is rolled back, provided the database supports transactional execution for the operation and the transaction has not been committed.

To permanently save the change:

```
START TRANSACTION;

UPDATE students
SET age = 20
WHERE id = 1;

COMMIT;
```

### Why Transactions Matter

Imagine a banking application transferring ₹1,000 from Account A to Account B.

Two operations are required:

1. Deduct ₹1,000 from Account A.
    
2. Add ₹1,000 to Account B.
    

If the first operation succeeds but the second fails, the database could become inconsistent without proper transaction handling.

Transactions help ensure that related changes are handled together.

Related note: [[SQL Transactions]]

## 8. DML and Database Constraints

DML operations must follow the constraints defined in a database.

Common constraints include:

|Constraint|Purpose|
|---|---|
|`PRIMARY KEY`|Uniquely identifies each record.|
|`FOREIGN KEY`|Maintains relationships between tables.|
|`UNIQUE`|Prevents duplicate values.|
|`NOT NULL`|Prevents missing values in a column.|
|`CHECK`|Enforces a specified condition.|
|`DEFAULT`|Supplies a default value.|

### Example: Constraint Violation

Suppose `id` is the primary key.

```
INSERT INTO students (id, name, age)
VALUES (1, 'Rahul', 19);
```

If ID `1` already exists, the database rejects the insertion because a primary key cannot contain duplicate values.

Related note: [[SQL Constraints]]

## 9. Security Considerations in DML

DML operations can modify or destroy important information. Improperly implemented database operations can create serious security risks.

### 9.1 SQL Injection

Never directly concatenate untrusted user input into SQL statements.

Unsafe example:

```
query = "SELECT * FROM users WHERE name = '" + username + "'"
```

An attacker may manipulate the query through specially crafted input.

Use parameterized queries instead.

Example using Python's SQLite interface:

```
cursor.execute(
    "SELECT * FROM users WHERE name = ?",
    (username,)
)
```

### 9.2 Least Privilege

Database users should receive only the permissions required for their tasks.

For example:

- A reporting account may only need `SELECT`.
    
- An application account may need `SELECT`, `INSERT`, and `UPDATE`.
    
- Ordinary users should not receive unnecessary `DELETE` or administrative permissions.
    

### 9.3 Authorization

Before modifying a record, an application must verify that the current user is authorized to change it.

Being authenticated does not automatically mean a user is authorized to modify every record.

### 9.4 Audit Logging

Important database modifications should be logged where appropriate.

Audit records can help investigators identify:

- Which account performed an operation.
    
- What type of operation occurred.
    
- When the operation happened.
    
- Which records were affected.
    

### 9.5 Backup and Recovery

Maintain appropriate backups before performing high-impact database modifications.

A backup provides a recovery option if records are accidentally modified or deleted.

Related notes:

- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[SQL User Management and Permissions]]
    

## 10. Common DML Errors

|Error|Possible Cause|
|---|---|
|Duplicate key error|Inserting an existing primary key.|
|Foreign key violation|Referencing a record that does not exist.|
|NOT NULL violation|Inserting `NULL` into a required column.|
|Data type mismatch|Supplying an incompatible value.|
|Missing WHERE condition|Accidentally modifying more records than intended.|
|Permission denied|Database account lacks the required privilege.|

## 11. Practical Lab — DML Operations

**Objective:** Practice inserting, updating, and deleting records safely.

Use your `sql_practice` database from the earlier SQL labs.

### Step 1: Create a Test Table

```
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INTEGER
);
```

If the table already exists, use a different test table name or reset your practice table only after confirming that you do not need its existing data.

### Step 2: Insert Records

```
INSERT INTO students (id, name, age)
VALUES
(1, 'Mohit', 18),
(2, 'Rahul', 19),
(3, 'Aman', 20);
```

### Step 3: Verify Inserted Records

```
SELECT * FROM students;
```

### Step 4: Update a Record

```
UPDATE students
SET age = 19
WHERE id = 1;
```

Verify the result:

```
SELECT * FROM students
WHERE id = 1;
```

### Step 5: Delete a Record

First preview the target:

```
SELECT * FROM students
WHERE id = 3;
```

Then delete it:

```
DELETE FROM students
WHERE id = 3;
```

Verify the result:

```
SELECT * FROM students;
```

### Step 6: Practice a Transaction

If your database supports the following transaction syntax:

```
START TRANSACTION;

UPDATE students
SET age = 25
WHERE id = 2;

SELECT * FROM students
WHERE id = 2;

ROLLBACK;
```

Verify that the original age is restored.

### Lab Observations

Record these details in your notebook:

- How many records did you insert?
    
- Which record did you update?
    
- Which record did you delete?
    
- What happened after `ROLLBACK`?
    
- What happens if you execute `UPDATE` without `WHERE`?
    

## 12. Key Takeaways

- DML manipulates records stored in database tables.
    
- `INSERT` adds new records.
    
- `UPDATE` modifies existing records.
    
- `DELETE` removes records.
    
- `WHERE` identifies the target records for updates and deletions.
    
- Transactions help manage related database modifications.
    
- Constraints protect data integrity.
    
- Parameterized queries help prevent SQL injection.
    
- Least privilege limits the damage caused by unauthorized database operations.
    

## 13. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[SQL Commands]]
    
- [[DDL - Data Definition Language]]
    
- [[DQL - Data Query Language]]
    
- [[SQL Constraints]]
    
- [[SQL Transactions]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[SQL Practical Labs]]