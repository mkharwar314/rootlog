> Learn how database users are created, authenticated, assigned privileges, and controlled to protect sensitive data.

## 1. Introduction

Database User Management is the process of creating and managing accounts that can access a database.

Database permissions determine what actions each account is allowed to perform.

For example:

- A database administrator can manage the entire database.
    
- An analyst may only read data.
    
- An application account may only insert and retrieve specific records.
    

Proper permission management prevents unauthorized access and reduces security risks.

## 2. Database Users vs Application Users

These are two different concepts.

**Database User**

- An account recognized by the Database Management System (DBMS).
    
- Used to connect directly to a database.
    
- Receives database-level permissions.
    

**Application User**

- A person who logs into an application.
    
- Usually authenticated by the application itself.
    
- May never connect directly to the database.
    

An application commonly uses a separate database service account to communicate with its database.

## 3. Authentication vs Authorization

|Concept|Meaning|
|---|---|
|Authentication|Verifies who you are|
|Authorization|Determines what you can do|

Example:

A database verifies a username and password. This is authentication.

After login, the database checks whether the account can read or modify a table. This is authorization.

## 4. Database Privileges

A privilege is permission to perform a particular operation.

Common SQL privileges include:

|Privilege|Purpose|
|---|---|
|SELECT|Read records|
|INSERT|Add records|
|UPDATE|Modify records|
|DELETE|Remove records|
|CREATE|Create database objects|
|ALTER|Modify database objects|
|DROP|Delete database objects|
|EXECUTE|Run permitted procedures or functions|

The exact privileges and their scope depend on the DBMS.

## 5. Principle of Least Privilege

The Principle of Least Privilege (PoLP) means giving each user or application only the permissions necessary to perform its job.

Example:

A reporting application only needs to read records.

It should receive:

- SELECT permission
    

It generally should not receive:

- DROP
    
- ALTER
    
- CREATE
    
- Unnecessary UPDATE or DELETE permissions
    

**Why is this important?**

If an account is compromised, an attacker has fewer permissions available.

## 6. Creating and Managing Database Users

SQL syntax differs between database systems.

The following examples use PostgreSQL.

### Create a user

```
CREATE USER analyst WITH PASSWORD 'ChangeThisStrongPassword!';
```

### Change a user's password

```
ALTER USER analyst WITH PASSWORD 'UseAnotherStrongPassword!';
```

### Remove a user

```
DROP USER analyst;
```

Important:

- These examples are PostgreSQL-specific.
    
- MySQL uses different account-management syntax.
    
- SQLite does not provide built-in database users in the same way.
    
- Never use example passwords in a real environment.
    

## 7. GRANT Statement

The GRANT statement assigns privileges to a database user or role.

### Syntax

```
GRANT privilege_name
ON object_name
TO user_or_role;
```

### Example

```
GRANT SELECT
ON employees
TO analyst;
```

This allows `analyst` to read records from the `employees` table, assuming the role also has the necessary schema access.

### Grant multiple privileges

```
GRANT SELECT, INSERT
ON employees
TO analyst;
```

This allows the account to read and insert records.

## 8. REVOKE Statement

The REVOKE statement removes previously granted privileges.

### Syntax

```
REVOKE privilege_name
ON object_name
FROM user_or_role;
```

### Example

```
REVOKE INSERT
ON employees
FROM analyst;
```

The user can no longer insert records using that granted privilege.

**Important:** Revoking one permission does not necessarily remove other permissions inherited through roles or granted separately.

## 9. Database Roles

A role is a database identity that can own objects and receive privileges. Roles can also be used to group permissions for multiple users.

Instead of assigning identical permissions to many accounts individually, an administrator can create a role and assign permissions to it.

### Create a role

```
CREATE ROLE read_only;
```

### Grant permissions to the role

```
GRANT SELECT
ON employees
TO read_only;
```

### Assign the role to a user

```
GRANT read_only TO analyst;
```

Now `analyst` receives the privileges associated with `read_only`.

### Why use roles?

- Simplifies permission management.
    
- Reduces repetitive commands.
    
- Makes access policies easier to review.
    
- Helps implement Role-Based Access Control.
    

## 10. Role-Based Access Control (RBAC)

RBAC is an access-control model in which permissions are assigned according to roles rather than individually to every user.

Example:

|Role|Permissions|
|---|---|
|Administrator|Database administration|
|Analyst|Read permitted data|
|Developer|Access required development objects|
|Application|Perform required application operations|

Users receive roles according to their responsibilities.

**Security benefit:** When someone's responsibilities change, administrators can update their role assignments instead of manually changing many individual privileges.

## 11. Object-Level Permissions

Database privileges can apply to different objects, depending on the DBMS.

Examples include:

- Database-level access
    
- Schema-level access
    
- Table-level access
    
- Column-level access
    
- Function or procedure execution permissions
    

For example, PostgreSQL supports granting SELECT on specific columns:

```
GRANT SELECT (name, email)
ON employees
TO analyst;
```

This grants access to those columns rather than every column in the table.

## 12. Secure Database Account Management

Follow these security practices:

### 1. Avoid shared accounts

Each person or service should have an identifiable account.

### 2. Remove unnecessary privileges

Do not give administrative permissions to ordinary application accounts.

### 3. Disable unused accounts

Unused accounts can become security weaknesses.

### 4. Protect credentials

- Never store database passwords in public repositories.
    
- Avoid hardcoding credentials in source code.
    
- Use environment variables or a secrets manager.
    
- Rotate credentials according to organizational policy.
    

### 5. Use secure connections

Use TLS to protect database connections when supported and properly configured.

### 6. Audit database access

Review:

- Who can connect.
    
- Which roles they have.
    
- Which objects they can access.
    
- Whether permissions are still necessary.
    

### 7. Separate accounts by purpose

Use separate accounts for administration, application services, reporting, and development.

## 13. Database Permissions and SQL Injection

Database permissions are an important layer of defense against SQL injection.

Suppose an application connects using an account with:

- SELECT
    
- INSERT
    
- UPDATE
    
- DELETE
    
- DROP
    

If an SQL injection vulnerability exists, the impact may be greater than if the application account only had the minimum required permissions.

However, **permissions do not prevent SQL injection by themselves.**

Use:

- Parameterized queries.
    
- Proper input handling.
    
- Least-privilege database accounts.
    
- Secure application design.
    

## 14. Checking User Permissions

Different DBMSs provide different commands.

### PostgreSQL

Inside the `psql` command-line interface:

```
\du
```

This displays database roles and their attributes.

To inspect table privileges, query the information schema:

```
SELECT *
FROM information_schema.table_privileges
WHERE grantee = 'analyst';
```

### MySQL

```
SHOW GRANTS FOR 'analyst'@'localhost';
```

These commands are database-specific. Do not assume that a command supported by one DBMS works in another.

## 15. PostgreSQL Practical Lab

This lab demonstrates basic role and permission management.

You need access to a PostgreSQL database with permission to create roles and tables.

### Step 1: Create a table

```
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(100)
);
```

### Step 2: Insert sample data

```
INSERT INTO employees (name, department)
VALUES
('Rahul', 'IT'),
('Aman', 'Security');
```

### Step 3: Create a read-only role

```
CREATE ROLE read_only;
```

### Step 4: Grant read permission

```
GRANT SELECT
ON employees
TO read_only;
```

### Step 5: Create a user

```
CREATE USER analyst WITH PASSWORD 'LabOnly_StrongPassword!';
```

### Step 6: Assign the role

```
GRANT read_only TO analyst;
```

### Step 7: Verify the role

In `psql`:

```
\du
```

### Step 8: Revoke the role

```
REVOKE read_only FROM analyst;
```

**Lab observation:**

Record:

- Which role did you create?
    
- Which permission did you grant?
    
- Which user received the role?
    
- What changed after revoking the role?
    

Use a disposable local lab database, not a production database.

## 16. Important Limitations

Not every database supports the same user-management system.

|DBMS|User and permission model|
|---|---|
|PostgreSQL|Roles and privileges|
|MySQL|Accounts, privileges, and roles|
|SQL Server|Logins, database users, roles, and permissions|
|SQLite|No built-in database-user and GRANT/REVOKE system|

SQLite file access is primarily controlled through operating-system permissions.

## 17. Key Takeaways

- Authentication verifies identity.
    
- Authorization controls permitted actions.
    
- Privileges define database operations.
    
- GRANT assigns permissions.
    
- REVOKE removes permissions.
    
- Roles simplify access management.
    
- RBAC assigns permissions through roles.
    
- Least privilege reduces the impact of compromised accounts.
    
- Database permissions are an important security control, but they do not replace secure coding.
    

## 18. Related Topics

- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[SQL Constraints]]
    
- [[SQL Transactions]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[Introduction to Secure Coding]]
    
- [[Authentication and Authorization]]
    
- [[Secrets Management]]