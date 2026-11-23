> Understand how SQL transactions maintain database consistency, protect data integrity, and manage multiple database operations as a single logical unit.

## 1. What is a SQL Transaction?

A transaction is a sequence of database operations treated as one logical unit of work.

A transaction can contain operations such as:

- INSERT
    
- UPDATE
    
- DELETE
    
- SELECT
    

A transaction should either complete successfully or be rolled back when necessary.

### Example

Suppose ₹5,000 is transferred from Account A to Account B.

Two operations are required:

1. Deduct ₹5,000 from Account A.
    
2. Add ₹5,000 to Account B.
    

Both operations must succeed together.

If the deduction succeeds but the deposit fails, the database should not leave the transfer partially completed.

Transactions help prevent this problem.

## 2. Why Are Transactions Important?

Transactions help maintain:

- Data accuracy.
    
- Data consistency.
    
- Database reliability.
    
- Data integrity.
    
- Safe execution of multiple operations.
    
- Recovery from failed operations.
    

They are especially important in banking, payment systems, inventory systems, and security-sensitive applications.

## 3. ACID Properties

Transactions are commonly described using four properties known as ACID.

ACID stands for:

- Atomicity
    
- Consistency
    
- Isolation
    
- Durability
    

### 3.1 Atomicity

Atomicity means all operations in a transaction succeed together or none of them take effect.

Example:

During a bank transfer:

- Money is deducted from Account A.
    
- Money is added to Account B.
    

If one operation fails, the transaction can be rolled back.

**Remember:** All or nothing.

### 3.2 Consistency

Consistency means a successful transaction preserves the database's defined integrity rules.

Example:

A bank account should not violate its applicable balance constraints after a transaction.

**Remember:** Valid state before and after.

### 3.3 Isolation

Isolation controls how concurrent transactions interact.

It helps prevent one transaction from interfering incorrectly with another.

Example:

Two users attempt to update the same account balance simultaneously.

The database uses transaction isolation mechanisms to control the interaction.

**Remember:** Transactions should not interfere improperly.

### 3.4 Durability

Durability means committed changes are preserved even after a system failure, subject to the database's durability guarantees and configuration.

Example:

After a successful payment transaction is committed, its changes should remain recorded even if the application closes.

**Remember:** Committed means persisted.

### ACID Summary

|Property|Meaning|
|---|---|
|Atomicity|All operations succeed or none take effect.|
|Consistency|Database integrity rules remain satisfied.|
|Isolation|Concurrent transactions are controlled.|
|Durability|Committed changes are preserved.|

## 4. Transaction Control Commands

SQL provides transaction control commands to manage transactions.

|Command|Purpose|
|---|---|
|BEGIN / START TRANSACTION|Starts a transaction.|
|COMMIT|Permanently commits changes.|
|ROLLBACK|Reverses uncommitted changes.|
|SAVEPOINT|Creates a point within a transaction.|
|ROLLBACK TO SAVEPOINT|Reverts to a savepoint.|
|RELEASE SAVEPOINT|Removes a savepoint.|

Syntax and support can vary between database systems.

## 5. BEGIN or START TRANSACTION

This command begins a transaction.

### Syntax

```
BEGIN;
```

Some database systems also support:

```
START TRANSACTION;
```

After beginning a transaction, subsequent supported operations can be committed or rolled back.

## 6. COMMIT Command

The `COMMIT` command permanently saves the changes made by the current transaction.

### Example

```
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

COMMIT;
```

Both updates are committed together if the transaction completes successfully.

**Important:** Check that both updates affected the intended records before committing. A transaction does not automatically guarantee that your business logic is correct.

## 7. ROLLBACK Command

The `ROLLBACK` command reverses changes made by the current uncommitted transaction.

### Example

```
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

ROLLBACK;
```

The uncommitted update is reversed.

The account balance returns to its state before the transaction.

**Important:** ROLLBACK cannot normally undo changes that have already been committed.

## 8. SAVEPOINT Command

A savepoint creates a named point inside a transaction.

It allows partial rollback without cancelling the entire transaction.

### Example

```
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

SAVEPOINT transfer_step;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

ROLLBACK TO SAVEPOINT transfer_step;

COMMIT;
```

Explanation:

1. The transaction begins.
    
2. The first update is performed.
    
3. A savepoint is created.
    
4. The second update is performed.
    
5. The transaction rolls back to the savepoint.
    
6. The transaction commits the changes remaining before the savepoint.
    

The first update remains part of the committed transaction.

## 9. RELEASE SAVEPOINT

`RELEASE SAVEPOINT` removes a savepoint.

### Example

```
BEGIN;

SAVEPOINT first_step;

UPDATE accounts
SET balance = balance + 100
WHERE account_id = 1;

RELEASE SAVEPOINT first_step;

COMMIT;
```

The transaction commits the update.

The exact savepoint behavior can vary between database systems.

## 10. Transaction Example: Bank Transfer

Consider two accounts:

|Account ID|Balance|
|---|---|
|1|10000|
|2|5000|

We want to transfer ₹2,000 from Account 1 to Account 2.

### Step 1: Start Transaction

```
BEGIN;
```

### Step 2: Deduct Money

```
UPDATE accounts
SET balance = balance - 2000
WHERE account_id = 1;
```

### Step 3: Add Money

```
UPDATE accounts
SET balance = balance + 2000
WHERE account_id = 2;
```

### Step 4: Verify the Results

```
SELECT *
FROM accounts;
```

### Step 5: Commit

```
COMMIT;
```

Expected result:

|Account ID|Balance|
|---|---|
|1|8000|
|2|7000|

Total balance remains:

[  
8000 + 7000 = 15000  
]

A real payment system also needs validation, sufficient-balance checks, concurrency control, and appropriate error handling.

## 11. Transaction Isolation Levels

Isolation levels define how much one transaction is protected from changes made by other concurrent transactions.

Common SQL isolation levels include:

1. Read Uncommitted
    
2. Read Committed
    
3. Repeatable Read
    
4. Serializable
    

### 11.1 Read Uncommitted

Allows a transaction to read changes that another transaction has not committed.

This can cause dirty reads.

A dirty read occurs when a transaction reads data that may later be rolled back.

### 11.2 Read Committed

A transaction can read only committed data.

It prevents dirty reads.

However, repeated reads may return different results if another transaction commits changes between them.

### 11.3 Repeatable Read

Ensures that repeated reads of the same rows within a transaction remain consistent according to the database's isolation implementation.

Some systems may still allow phantom rows depending on their implementation and locking behavior.

### 11.4 Serializable

Provides the strongest standard isolation level.

It aims to make concurrent transactions behave as though they executed sequentially.

It can reduce concurrency and increase the possibility of blocking or transaction retries.

### Isolation Level Summary

|Isolation Level|Dirty Reads|Non-repeatable Reads|Phantom Reads|
|---|---|---|---|
|Read Uncommitted|Possible|Possible|Possible|
|Read Committed|Prevented|Possible|Possible|
|Repeatable Read|Prevented|Prevented|Possible under standard SQL rules|
|Serializable|Prevented|Prevented|Prevented|

Actual behavior varies by database engine. For example, PostgreSQL's Repeatable Read provides stronger snapshot behavior than the minimum standard requirement.

## 12. Common Transaction Problems

### 12.1 Dirty Read

A transaction reads uncommitted data from another transaction.

### 12.2 Non-Repeatable Read

A transaction reads the same row twice and gets different values because another transaction committed an update between the reads.

### 12.3 Phantom Read

A transaction repeats a query and finds additional or missing rows because another transaction inserted or deleted matching records.

### 12.4 Lost Update

Two transactions update the same data, and one update overwrites the other unexpectedly.

Database concurrency controls help prevent or detect these problems.

### 12.5 Deadlock

A deadlock occurs when transactions wait for resources held by each other.

Example:

- Transaction A locks Row 1 and waits for Row 2.
    
- Transaction B locks Row 2 and waits for Row 1.
    

Neither can continue without intervention.

Database systems typically detect deadlocks and abort one transaction so the other can proceed.

Applications should be prepared to retry transactions safely when appropriate.

## 13. Autocommit Mode

Autocommit is a database behavior in which individual statements are automatically committed when they complete successfully.

Many database clients and systems use autocommit by default.

Example:

```
UPDATE employees
SET salary = 45000
WHERE employee_id = 1;
```

With autocommit enabled, the change may be committed automatically.

To control multiple operations together, explicitly start a transaction using the appropriate syntax for your database.

**Important:** Transaction behavior depends on the database engine, client settings, and storage engine. Some statements can cause implicit commits in certain systems.

## 14. Transactions in Cybersecurity

Transactions are important for protecting sensitive database operations.

### 14.1 Prevent Partial User Updates

Suppose an application changes a user's role and records an audit event.

Both operations may need to succeed together.

```
BEGIN;

UPDATE users
SET role = 'security_analyst'
WHERE user_id = 10;

INSERT INTO audit_logs (
    user_id,
    action
)
VALUES (
    10,
    'ROLE_UPDATED'
);

COMMIT;
```

This keeps the role change and audit record in the same transaction when both tables support the required transactional behavior.

### 14.2 Protect Financial Records

Payment applications use transactions to maintain consistency during transfers.

### 14.3 Maintain Audit Data

Transactions can help ensure that a sensitive database modification and its associated audit record are committed together.

However, database administrators should also protect audit logs from unauthorized modification or deletion.

### 14.4 Handle Failed Security Operations

If a multi-step operation fails, ROLLBACK can prevent incomplete changes from being committed.

## 15. Common Transaction Mistakes

|Mistake|Explanation|
|---|---|
|Forgetting COMMIT|Changes may remain uncommitted.|
|Forgetting ROLLBACK after failure|Partial work may remain in the active transaction.|
|Assuming ROLLBACK reverses COMMIT|Committed changes generally cannot be rolled back with a later ROLLBACK.|
|Keeping transactions open too long|Can cause locks and reduce concurrency.|
|Ignoring deadlocks|Applications may need to retry aborted transactions.|
|Not checking affected rows|An UPDATE may affect zero or more rows than expected.|
|Assuming every table supports transactions|Some storage engines or systems may not provide transactional guarantees.|

## 16. Practical Lab — SQL Transactions

**Objective:** Practice BEGIN, COMMIT, ROLLBACK, and SAVEPOINT.

Use a database that supports transactions. SQLite is suitable for this lab.

### Step 1: Create an Accounts Table

```
CREATE TABLE accounts_lab (
    account_id INTEGER PRIMARY KEY,
    account_name VARCHAR(50),
    balance DECIMAL(10,2)
);
```

### Step 2: Insert Test Records

```
INSERT INTO accounts_lab
VALUES
(1, 'Mohit', 10000),
(2, 'Rahul', 5000);
```

### Step 3: Check Initial Balances

```
SELECT *
FROM accounts_lab;
```

### Step 4: Start a Transaction

```
BEGIN;
```

### Step 5: Transfer Money

```
UPDATE accounts_lab
SET balance = balance - 2000
WHERE account_id = 1;

UPDATE accounts_lab
SET balance = balance + 2000
WHERE account_id = 2;
```

### Step 6: Verify the Changes

```
SELECT *
FROM accounts_lab;
```

### Step 7: Commit the Transaction

```
COMMIT;
```

Check the balances again.

### Step 8: Test ROLLBACK

```
BEGIN;

UPDATE accounts_lab
SET balance = balance - 1000
WHERE account_id = 1;

SELECT *
FROM accounts_lab;

ROLLBACK;
```

Check the balances again.

The uncommitted change should have been reversed.

### Step 9: Test SAVEPOINT

```
BEGIN;

UPDATE accounts_lab
SET balance = balance + 500
WHERE account_id = 1;

SAVEPOINT first_update;

UPDATE accounts_lab
SET balance = balance + 1000
WHERE account_id = 2;

ROLLBACK TO SAVEPOINT first_update;

COMMIT;
```

Verify the final balances.

The first update should remain committed, while the second update should be reversed.

### Lab Observations

Record these questions in your notebook:

1. What is a transaction?
    
2. What are the four ACID properties?
    
3. What is the difference between COMMIT and ROLLBACK?
    
4. What is a SAVEPOINT?
    
5. What is a dirty read?
    
6. Why are transactions important in payment systems?
    
7. How can transactions protect audit records?
    

## 17. Key Takeaways

- A transaction is a logical unit of database work.
    
- ACID describes important transaction properties.
    
- Atomicity provides all-or-nothing behavior.
    
- Consistency preserves database integrity rules.
    
- Isolation controls concurrent transactions.
    
- Durability preserves committed changes.
    
- COMMIT saves transaction changes.
    
- ROLLBACK reverses uncommitted changes.
    
- SAVEPOINT supports partial rollback.
    
- Isolation levels control transaction interactions.
    
- Transactions are essential for reliable and secure database operations.
    

## 18. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[TCL - Transaction Control Language]]
    
- [[SQL Constraints]]
    
- [[SQL Joins]]
    
- [[SQL Indexes]]
    
- [[SQL User Management and Permissions]]
    
- [[SQL Injection]]
    
- [[SQL Practical Labs]]