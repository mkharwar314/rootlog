> Understand how SQL transactions are controlled to maintain database consistency, reliability, and data integrity.

## 1. What is TCL?

**TCL (Transaction Control Language)** is a category of SQL commands used to manage transactions in a database.

A transaction is a group of database operations treated as one logical unit of work.

TCL helps control whether changes made during a transaction should be permanently saved or reversed.

### Main TCL Commands

|Command|Purpose|
|---|---|
|`COMMIT`|Permanently saves transaction changes.|
|`ROLLBACK`|Reverses uncommitted transaction changes.|
|`SAVEPOINT`|Creates a point inside a transaction to which you can roll back.|
|`ROLLBACK TO SAVEPOINT`|Reverses changes made after a savepoint.|
|`RELEASE SAVEPOINT`|Removes a savepoint.|

Exact syntax and behavior can vary between database systems.

## 2. Understanding Transactions

Consider a banking application where ₹1,000 must be transferred from Account A to Account B.

Two operations are required:

1. Deduct ₹1,000 from Account A.
    
2. Add ₹1,000 to Account B.
    

Both operations should succeed together.

If the first operation succeeds but the second fails, the database could become inconsistent.

Transactions help ensure that related operations are handled as one logical unit.

### Basic Transaction Structure

```
BEGIN;

-- SQL operations

COMMIT;
```

If an error occurs before committing, the application may roll back the transaction.

## 3. COMMIT Command

The `COMMIT` command saves all changes made during the current transaction.

### Syntax

```
COMMIT;
```

### Example

```
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```

Both updates are committed together if the transaction succeeds.

### Important Points

- COMMIT makes the transaction's changes permanent under normal transactional database behavior.
    
- A committed transaction cannot normally be reversed using `ROLLBACK`.
    
- Recovery after a commit generally requires a compensating operation or restoring data from a backup.
    

## 4. ROLLBACK Command

The `ROLLBACK` command reverses changes made during the current uncommitted transaction.

### Syntax

```
ROLLBACK;
```

### Example

```
BEGIN;

UPDATE students
SET age = 25
WHERE id = 1;

ROLLBACK;
```

The age update is reversed.

### When to Use ROLLBACK

- An SQL operation fails.
    
- Incorrect data is modified.
    
- A transaction produces unexpected results.
    
- A multi-step operation cannot be completed safely.
    

**Important:** Rollback behavior depends on the database engine and the operations involved. Some operations may cause implicit commits or may not be transactional.

## 5. SAVEPOINT Command

A `SAVEPOINT` creates a named point inside an active transaction.

It allows you to reverse only part of a transaction instead of cancelling everything.

### Syntax

```
SAVEPOINT savepoint_name;
```

### Example

```
BEGIN;

INSERT INTO students (id, name, age)
VALUES (1, 'Mohit', 18);

SAVEPOINT first_savepoint;

INSERT INTO students (id, name, age)
VALUES (2, 'Rahul', 19);

ROLLBACK TO SAVEPOINT first_savepoint;

COMMIT;
```

### Explanation

1. A transaction begins.
    
2. Mohit's record is inserted.
    
3. A savepoint is created.
    
4. Rahul's record is inserted.
    
5. The transaction rolls back to the savepoint.
    
6. Rahul's insertion is reversed.
    
7. Mohit's insertion remains and is committed.
    

## 6. RELEASE SAVEPOINT

The `RELEASE SAVEPOINT` command removes a savepoint.

### Syntax

```
RELEASE SAVEPOINT savepoint_name;
```

### Example

```
BEGIN;

INSERT INTO students (id, name, age)
VALUES (1, 'Mohit', 18);

SAVEPOINT first_savepoint;

UPDATE students
SET age = 19
WHERE id = 1;

RELEASE SAVEPOINT first_savepoint;

COMMIT;
```

The savepoint is removed. The transaction can still be rolled back as a whole before it is committed.

Support and exact behavior vary by database.

## 7. ACID Properties

Transactions are commonly explained through the four ACID properties.

ACID stands for:

- Atomicity
    
- Consistency
    
- Isolation
    
- Durability
    

### 7.1 Atomicity

A transaction is treated as one logical unit.

Either all required operations succeed, or the transaction is rolled back.

**Example:** A bank transfer should not deduct money without also crediting the destination account.

### 7.2 Consistency

A transaction should preserve database rules and constraints.

**Example:** A transaction should not leave an account balance violating an enforced business rule.

### 7.3 Isolation

Concurrent transactions should not interfere in ways that violate the database's isolation guarantees.

**Example:** Two users updating the same account should not cause an incorrect final balance.

Actual behavior depends on the database's isolation level.

### 7.4 Durability

Once a transaction is successfully committed, its changes should survive failures according to the database's durability guarantees.

**Example:** A committed bank transfer should remain recorded after a normal server restart.

### ACID Summary

|Property|Meaning|
|---|---|
|Atomicity|All or nothing|
|Consistency|Preserves valid database state|
|Isolation|Controls interference between transactions|
|Durability|Committed changes persist|

## 8. Transaction States

A transaction can pass through several states.

|State|Description|
|---|---|
|Active|Transaction is executing.|
|Partially Committed|Final operation has executed, but commit completion is not yet confirmed.|
|Committed|Changes have been successfully committed.|
|Failed|Transaction cannot continue successfully.|
|Aborted|Transaction has been rolled back.|

The exact terminology may differ across database documentation.

## 9. Transaction Isolation Levels

Isolation levels control how concurrent transactions interact.

Common SQL isolation levels include:

|Isolation Level|General Behavior|
|---|---|
|READ UNCOMMITTED|May allow dirty reads.|
|READ COMMITTED|Prevents dirty reads.|
|REPEATABLE READ|Provides stronger protection against changes to previously read rows.|
|SERIALIZABLE|Provides the strongest standard isolation level.|

Database implementations differ, so these descriptions are general rather than guarantees of identical behavior.

### Common Concurrency Problems

**Dirty Read:** A transaction reads data written by another transaction that has not committed.

**Non-Repeatable Read:** A transaction reads the same row twice and gets different values because another transaction committed an update between the reads.

**Phantom Read:** Repeating a query returns additional or missing rows because another transaction changed records matching the query condition.

Isolation levels help control these problems.

## 10. TCL vs DML

|DML|TCL|
|---|---|
|Manipulates database records.|Controls transactions.|
|Includes INSERT, UPDATE, DELETE.|Includes COMMIT, ROLLBACK, SAVEPOINT.|
|Changes data.|Controls whether transactional changes are saved or reversed.|

Example combining DML and TCL:

```
BEGIN;

UPDATE students
SET age = 20
WHERE id = 1;

COMMIT;
```

The UPDATE changes the record, while COMMIT saves the transaction.

## 11. TCL Security and Reliability

Transaction management is important for database security and reliability.

### 11.1 Prevent Partial Updates

Use transactions when multiple related operations must succeed together.

### 11.2 Avoid Unnecessary Long Transactions

Long-running transactions can hold locks, consume resources, and interfere with other database operations.

### 11.3 Handle Errors Properly

Applications should detect transaction failures and perform appropriate rollback or recovery.

### 11.4 Maintain Backups

Transactions do not replace backups.

Backups and recovery procedures are still necessary to protect against data loss, corruption, and destructive operations.

### 11.5 Control Concurrent Updates

Use appropriate isolation levels and locking mechanisms to prevent conflicting modifications.

## 12. Practical Lab — SQL Transactions

**Objective:** Understand COMMIT, ROLLBACK, and SAVEPOINT.

Use your `sql_practice` database.

### Step 1: Create a Test Table

```
CREATE TABLE transaction_demo (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    balance DECIMAL(10,2)
);
```

### Step 2: Insert Test Records

```
INSERT INTO transaction_demo
VALUES
(1, 'Mohit', 5000.00),
(2, 'Rahul', 3000.00);
```

### Step 3: Check Initial Balances

```
SELECT * FROM transaction_demo;
```

### Step 4: Start a Transaction

```
BEGIN;
```

### Step 5: Perform a Transfer

```
UPDATE transaction_demo
SET balance = balance - 1000
WHERE id = 1;

UPDATE transaction_demo
SET balance = balance + 1000
WHERE id = 2;
```

### Step 6: Verify the Changes

```
SELECT * FROM transaction_demo;
```

### Step 7: Roll Back

```
ROLLBACK;
```

Check the balances again:

```
SELECT * FROM transaction_demo;
```

The original balances should be restored.

### Step 8: Repeat and Commit

```
BEGIN;

UPDATE transaction_demo
SET balance = balance - 1000
WHERE id = 1;

UPDATE transaction_demo
SET balance = balance + 1000
WHERE id = 2;

COMMIT;
```

Verify the final balances.

### Step 9: Practice SAVEPOINT

```
BEGIN;

UPDATE transaction_demo
SET balance = balance - 500
WHERE id = 1;

SAVEPOINT transfer_point;

UPDATE transaction_demo
SET balance = balance + 500
WHERE id = 2;

ROLLBACK TO SAVEPOINT transfer_point;

COMMIT;
```

Inspect the results and identify which changes were retained.

**Note:** This lab uses common transaction syntax. Some database systems use different syntax or behavior. SQLite, for example, supports transactions and savepoints but uses `SAVEPOINT` and `ROLLBACK TO` syntax for savepoint operations.

### Lab Observations

Write down:

1. What happened after ROLLBACK?
    
2. What happened after COMMIT?
    
3. How does SAVEPOINT differ from ROLLBACK?
    
4. Why are transactions important in banking systems?
    
5. What do the four ACID properties mean?
    

## 13. Key Takeaways

- TCL manages database transactions.
    
- COMMIT saves transaction changes.
    
- ROLLBACK reverses uncommitted changes.
    
- SAVEPOINT creates a rollback point inside a transaction.
    
- ACID describes important transaction properties.
    
- Isolation levels control concurrent transaction behavior.
    
- Transactions help maintain database consistency.
    
- Backups remain necessary even when transactions are supported.
    

## 14. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[SQL Commands]]
    
- [[DDL - Data Definition Language]]
    
- [[DML - Data Manipulation Language]]
    
- [[DQL - Data Query Language]]
    
- [[DCL - Data Control Language]]
    
- [[SQL Constraints]]
    
- [[SQL Practical Labs]]