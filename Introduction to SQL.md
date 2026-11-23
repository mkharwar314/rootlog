> Understand SQL, how databases store information, and how applications communicate with relational databases.

## 1. What is SQL?

**SQL (Structured Query Language)** is a language used to communicate with relational database management systems (RDBMS).

It allows users and applications to:

- Create databases and tables.
    
- Insert records.
    
- Retrieve information.
    
- Update existing records.
    
- Delete records.
    
- Manage database permissions.
    
- Control database transactions.
    

SQL is widely used in web applications, enterprise systems, financial platforms, and cybersecurity investigations.

## 2. What is a Database?

A database is an organized collection of information stored electronically.

For example, a college database might contain:

- Student information.
    
- Teacher information.
    
- Course details.
    
- Examination results.
    
- Attendance records.
    

### Database Example

|Student_ID|Name|Course|Age|
|---|---|---|---|
|101|Rahul|Cybersecurity|18|
|102|Mohit|Computer Science|19|
|103|Aman|Networking|18|

This table stores information about students.

## 3. What is DBMS?

**DBMS (Database Management System)** is software used to create, manage, retrieve, and manipulate databases.

Examples:

- MySQL
    
- PostgreSQL
    
- Microsoft SQL Server
    
- Oracle Database
    
- SQLite
    

### DBMS Responsibilities

1. Data storage and retrieval.
    
2. Data organization.
    
3. Access control.
    
4. Data integrity.
    
5. Backup and recovery.
    
6. Transaction management.
    

## 4. What is RDBMS?

**RDBMS (Relational Database Management System)** stores data in tables consisting of rows and columns.

Tables can be connected through relationships.

Example:

**Students Table**

|Student_ID|Name|
|---|---|
|101|Mohit|
|102|Rahul|

**Courses Table**

|Course_ID|Course_Name|
|---|---|
|1|Cybersecurity|
|2|Networking|

A separate enrollment table can connect students to their courses.

This avoids unnecessarily repeating information.

## 5. What is SQL Used For?

SQL is used for five major categories of database operations.

|Operation|Purpose|
|---|---|
|CREATE|Create database objects|
|INSERT|Add records|
|SELECT|Retrieve records|
|UPDATE|Modify records|
|DELETE|Remove records|

Example:

```
SELECT * FROM students;
```

This retrieves all columns and rows from the `students` table.

## 6. SQL and Database Communication

A typical application communicates with a database through a backend.

```
User
  |
  v
Web Application
  |
  v
Backend Server
  |
  v
Database
  |
  v
SQL Query
  |
  v
Query Result
  |
  v
Backend Server
  |
  v
Web Application
```

Example:

A user logs into a website.

1. The user submits login details.
    
2. The backend receives the request.
    
3. The backend queries the database.
    
4. The database returns matching information.
    
5. The backend verifies the authentication details.
    
6. The application responds to the user.
    

**Important:** Authentication must be implemented securely. Passwords should be stored using appropriate password hashing, not plaintext.

## 7. SQL vs MySQL

These terms are related but different.

|SQL|MySQL|
|---|---|
|A database query language|A relational database management system|
|Defines how to communicate with databases|Implements database storage and management|
|Used by multiple database systems|Uses SQL to interact with its databases|

Other database systems, such as PostgreSQL and SQL Server, also support SQL.

However, SQL syntax and features can differ between database systems.

## 8. Types of SQL Commands

SQL commands are commonly divided into five categories.

|Category|Full Form|Purpose|
|---|---|---|
|DDL|Data Definition Language|Defines database structures|
|DML|Data Manipulation Language|Inserts, modifies and deletes data|
|DQL|Data Query Language|Retrieves data|
|DCL|Data Control Language|Manages permissions|
|TCL|Transaction Control Language|Manages transactions|

Examples:

- DDL: `CREATE`, `ALTER`, `DROP`
    
- DML: `INSERT`, `UPDATE`, `DELETE`
    
- DQL: `SELECT`
    
- DCL: `GRANT`, `REVOKE`
    
- TCL: `COMMIT`, `ROLLBACK`, `SAVEPOINT`
    

These categories are conventional classifications; some database documentation groups commands differently.

## 9. Important Database Terminology

|Term|Meaning|
|---|---|
|Table|Collection of related data|
|Row|One record in a table|
|Column|One attribute of a table|
|Primary Key|Uniquely identifies a row|
|Foreign Key|References a key in another table|
|Schema|Logical organization of database objects|
|Query|Instruction sent to a database|
|Constraint|Rule applied to database data|
|Index|Structure that can improve data retrieval|
|Transaction|Logical unit of database operations|

## 10. SQL in Cybersecurity

SQL is particularly important in cybersecurity because applications frequently store sensitive information in databases.

Cybersecurity professionals use SQL knowledge for:

### 1. SQL Injection Detection

Understanding SQL helps security professionals recognize how unsafe user input can alter database queries.

### 2. Database Security Auditing

Reviewing:

- Database users.
    
- Permissions.
    
- Access privileges.
    
- Configuration.
    
- Exposed database services.
    

### 3. Digital Forensics

Database records may contain useful evidence, including:

- User activity.
    
- Transaction records.
    
- Application events.
    
- Account information.
    

### 4. Secure Application Development

Developers use parameterized queries and appropriate database permissions to reduce security risks.

### 5. Data Protection

Database security includes:

- Access control.
    
- Encryption.
    
- Backup protection.
    
- Monitoring.
    
- Least privilege.
    

## 11. Practical Example

Consider a database named `college_db` with a table named `students`.

Example query:

```
SELECT * FROM students;
```

Retrieve only student names:

```
SELECT name FROM students;
```

Retrieve students older than 18:

```
SELECT * FROM students
WHERE age > 18;
```

These queries demonstrate how SQL retrieves information from a database.

## 12. Key Takeaways

- SQL stands for Structured Query Language.
    
- SQL communicates with relational databases.
    
- A database stores organized information.
    
- DBMS software manages databases.
    
- RDBMS stores data in related tables.
    
- SQL supports database creation, retrieval, modification and administration.
    
- SQL knowledge is essential for understanding SQL injection and database security.
    

## 13. Related Topics

- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Data Types]]
    
- [[SQL Commands]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[Secure Programming]]
    

## 14. My Understanding

Explain in your own words:

- What is SQL?
    
- What is a database?
    
- What is DBMS?
    
- What is RDBMS?
    
- What is the difference between SQL and MySQL?
    
- Why is SQL important in cybersecurity?
    

## 15. Questions & Doubts

Record questions that need further research.