> Understand how database permissions are granted and restricted to control who can access and manage database resources.

## 1. What is DCL?

**DCL (Data Control Language)** is a category of SQL commands used to manage database access permissions.

It helps database administrators control what users can do inside a database.

For example:

- Allow a user to read database records.
    
- Allow an application to insert records.
    
- Restrict a user from deleting records.
    
- Remove previously granted permissions.
    

### Main DCL Commands

|Command|Purpose|
|---|---|
|`GRANT`|Gives permissions to a user or role.|
|`REVOKE`|Removes previously granted permissions.|

**Important:** SQL permission syntax and behavior vary between database systems.

## 2. Database Users and Permissions

A database user is an account that connects to a database.

Each user should receive only the permissions required for their responsibilities.

### Example

Consider a college database with three users:

|User|Responsibility|Required Access|
|---|---|---|
|Admin|Manages the database|Administrative permissions|
|Teacher|Views and updates student records|SELECT, UPDATE|
|Student|Views permitted information|SELECT|

Giving every user administrative access creates unnecessary security risks.

## 3. GRANT Command

The `GRANT` command provides permissions to a database user or role.

### Basic Syntax

```
GRANT privilege_name
ON object_name
TO user_name;
```

### Grant SELECT Permission

```
GRANT SELECT
ON students
TO teacher;
```

This grants the `teacher` account permission to retrieve records from the `students` table.

### Grant INSERT Permission

```
GRANT INSERT
ON students
TO teacher;
```

This allows the user to insert records into the table.

### Grant Multiple Permissions

```
GRANT SELECT, INSERT, UPDATE
ON students
TO teacher;
```

This grants three permissions.

### Common Database Privileges

|Privilege|Purpose|
|---|---|
|SELECT|Retrieve records|
|INSERT|Add records|
|UPDATE|Modify records|
|DELETE|Remove records|
|EXECUTE|Execute permitted routines or procedures|
|REFERENCES|Create permitted foreign-key references|

Available privileges depend on the database system and object type.

## 4. REVOKE Command

The `REVOKE` command removes permissions previously granted to a user or role.

### Basic Syntax

```
REVOKE privilege_name
ON object_name
FROM user_name;
```

### Example: Remove SELECT Permission

```
REVOKE SELECT
ON students
FROM teacher;
```

This removes the specified SELECT permission from the teacher account.

### Remove Multiple Permissions

```
REVOKE INSERT, UPDATE
ON students
FROM teacher;
```

This removes the INSERT and UPDATE permissions.

**Important:** Revoking a permission does not necessarily remove access obtained through another role or permission grant. Database permission inheritance must also be considered.

## 5. GRANT vs REVOKE

|GRANT|REVOKE|
|---|---|
|Provides permissions.|Removes permissions.|
|Increases the specified access.|Reduces the specified access.|
|Uses `TO`.|Uses `FROM`.|

Example:

```
GRANT SELECT ON students TO teacher;
```

```
REVOKE SELECT ON students FROM teacher;
```

## 6. Principle of Least Privilege

The **Principle of Least Privilege (PoLP)** means giving users and applications only the minimum permissions necessary to perform their tasks.

### Example

A reporting application only needs to read student records.

It should receive:

```
GRANT SELECT
ON students
TO reporting_user;
```

It should not automatically receive:

- DELETE
    
- DROP
    
- ALTER
    
- Database administration privileges
    

### Why Least Privilege Matters

- Reduces accidental data modification.
    
- Limits damage from compromised accounts.
    
- Reduces unauthorized access.
    
- Helps enforce separation of responsibilities.
    
- Improves database security.
    

## 7. Database Roles

A role is a collection of permissions that can be assigned to users.

Instead of granting every permission individually, administrators can create roles for different responsibilities.

### Example Concept

A database might contain these roles:

|Role|Permissions|
|---|---|
|Read Only|SELECT|
|Data Editor|SELECT, INSERT, UPDATE|
|Database Administrator|Administrative permissions|

### Example SQL

The following is illustrative and uses common role syntax:

```
CREATE ROLE read_only;

GRANT SELECT
ON students
TO read_only;
```

A user can then be assigned the role using database-specific syntax.

For example, PostgreSQL supports:

```
GRANT read_only TO student_user;
```

Role creation, assignment, and inheritance syntax differ across database systems.

## 8. WITH GRANT OPTION

Some database systems allow a user to grant permissions to other users.

The `WITH GRANT OPTION` clause provides that additional capability.

### Example

```
GRANT SELECT
ON students
TO teacher
WITH GRANT OPTION;
```

The teacher can now grant the specified permission to other users, subject to database authorization rules.

**Security consideration:** Granting this option gives a user more authority than ordinary read access. Use it carefully.

## 9. DCL in Database Security

DCL is important for controlling access to sensitive information.

### 9.1 Unauthorized Access

An unauthorized user may attempt to access confidential records.

**Prevention:**

- Use appropriate user accounts.
    
- Apply least privilege.
    
- Review database permissions regularly.
    

### 9.2 Excessive Privileges

A user with unnecessary permissions may accidentally or deliberately modify important data.

**Prevention:**

- Assign role-based permissions.
    
- Avoid unnecessary administrator access.
    
- Separate administrative and ordinary accounts.
    

### 9.3 Compromised Accounts

If an account is compromised, attackers may misuse its permissions.

**Prevention:**

- Use strong authentication.
    
- Monitor account activity.
    
- Remove unused accounts.
    
- Revoke unnecessary permissions.
    

### 9.4 Privilege Escalation

Privilege escalation occurs when a user obtains permissions beyond those originally assigned.

**Prevention:**

- Review role membership.
    
- Restrict grant options.
    
- Audit permission changes.
    
- Avoid excessive administrative privileges.
    

## 10. DCL and Other SQL Language Categories

|Category|Purpose|Main Commands|
|---|---|---|
|DDL|Defines database structures.|CREATE, ALTER, DROP|
|DML|Manipulates stored records.|INSERT, UPDATE, DELETE|
|DQL|Retrieves records.|SELECT|
|DCL|Controls permissions.|GRANT, REVOKE|
|TCL|Manages transactions.|COMMIT, ROLLBACK, SAVEPOINT|

Some SQL references classify commands differently, but this is the classification used in ROOTLOG.

## 11. Database-Specific Differences

DCL syntax is not identical across database systems.

|Database|Permission Management|
|---|---|
|MySQL|Supports GRANT and REVOKE.|
|PostgreSQL|Supports GRANT and REVOKE with roles.|
|Oracle Database|Supports system and object privileges.|
|SQL Server|Supports GRANT, DENY, and REVOKE.|
|SQLite|Does not provide the same built-in SQL user and GRANT/REVOKE permission model.|

**Important:** SQLite generally relies on operating-system file permissions and application-level access controls rather than traditional database-user DCL commands.

Do not assume a DCL example for PostgreSQL or MySQL will work in SQLite.

## 12. Practical Lab — Database Permissions

**Objective:** Understand how database permissions are assigned and removed.

This lab uses PostgreSQL-style syntax. You need a PostgreSQL database and an account authorized to create roles and grant permissions.

### Step 1: Create a Test Table

```
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    age INTEGER
);
```

### Step 2: Create a Test User

```
CREATE ROLE lab_user
LOGIN
PASSWORD 'ChangeThisToAStrongPassword';
```

Use a strong, unique password in a real environment.

### Step 3: Grant SELECT Permission

```
GRANT SELECT
ON students
TO lab_user;
```

### Step 4: Grant INSERT Permission

```
GRANT INSERT
ON students
TO lab_user;
```

### Step 5: Check Permissions

In PostgreSQL, you can inspect table privileges using:

```
SELECT *
FROM information_schema.role_table_grants
WHERE grantee = 'lab_user';
```

### Step 6: Revoke INSERT Permission

```
REVOKE INSERT
ON students
FROM lab_user;
```

### Step 7: Verify Again

```
SELECT *
FROM information_schema.role_table_grants
WHERE grantee = 'lab_user';
```

Compare the results before and after revoking the permission.

### Lab Observations

Record these questions in your notebook:

1. What does GRANT do?
    
2. What does REVOKE do?
    
3. Why should ordinary users not receive administrator permissions?
    
4. What is the principle of least privilege?
    
5. How are database roles useful?
    

**Cleanup:** Remove the test role and table after completing the lab, once you have confirmed that they contain no data you need.

```
DROP ROLE lab_user;
DROP TABLE students;
```

If the role still owns objects or has active dependencies, resolve those dependencies before dropping it.

## 13. Key Takeaways

- DCL controls database permissions.
    
- GRANT provides access privileges.
    
- REVOKE removes previously granted privileges.
    
- Database roles group permissions.
    
- Least privilege reduces security risks.
    
- WITH GRANT OPTION allows permitted users to grant privileges to others.
    
- Permission syntax differs between database systems.
    
- SQLite does not implement traditional SQL user-based DCL.
    

## 14. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[SQL Commands]]
    
- [[DDL - Data Definition Language]]
    
- [[DML - Data Manipulation Language]]
    
- [[DQL - Data Query Language]]
    
- [[SQL User Management and Permissions]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[SQL Practical Labs]]