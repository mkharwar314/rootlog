> Understand how attackers manipulate SQL queries through untrusted input, how SQL injection vulnerabilities occur, and how they can compromise databases.

## 1. Introduction to SQL Injection

SQL Injection (SQLi) is a web application security vulnerability in which an attacker inserts malicious SQL input into an application's database query.

It occurs when an application combines untrusted user input with SQL statements without safely separating data from query instructions.

An attacker may exploit this vulnerability to:

- Bypass authentication.
    
- Read confidential information.
    
- Modify database records.
    
- Delete database data.
    
- Access unauthorized database functionality.
    

SQL Injection is classified under **Injection** in the OWASP Top 10.

## 2. How SQL Injection Works

Consider a login form that accepts:

- Username
    
- Password
    

The application constructs a SQL query:

```
SELECT * FROM users
WHERE username = 'admin'
AND password = 'mypassword';
```

The application sends this query to the database.

If user input is directly concatenated into the SQL statement, an attacker may change the query's intended logic.

The core problem is that the application treats user-controlled input as part of the SQL command instead of treating it strictly as data.

## 3. Vulnerable SQL Query Example

Imagine an application written in Python:

```
username = input("Username: ")
password = input("Password: ")

query = (
    "SELECT * FROM users WHERE username = '"
    + username
    + "' AND password = '"
    + password
    + "'"
)
```

This code is vulnerable because it directly joins user input into the SQL query.

An attacker can provide specially crafted input that changes the SQL statement's meaning.

**Important:** This example is intentionally insecure. Do not use this pattern in real applications.

## 4. Common Types of SQL Injection

### 1. In-Band SQL Injection

In-band SQL injection occurs when the attacker uses the same communication channel to send SQL input and receive the results.

Two common forms are:

**Error-Based SQL Injection**

The attacker studies database error messages to learn information about the database structure or query execution.

**UNION-Based SQL Injection**

The attacker uses the SQL `UNION` operator to combine results from another query with the application's original query.

This can expose information from database tables when the vulnerable query and database permissions allow it.

### 2. Blind SQL Injection

Blind SQL injection occurs when the application does not directly display database results, but the attacker can infer information from application behavior.

Two common forms are:

**Boolean-Based Blind SQL Injection**

The attacker observes differences in application responses depending on whether a condition evaluates to true or false.

**Time-Based Blind SQL Injection**

The attacker observes response delays caused by conditional database operations.

### 3. Out-of-Band SQL Injection

Out-of-band SQL injection occurs when an attacker uses a separate communication channel to retrieve information.

It depends on database capabilities, network configuration, and the availability of an external communication channel.

It is less common than in-band and blind techniques.

## 5. SQL Injection Attack Flow

A typical SQL injection attack follows this process:

1. Identify an application input that interacts with a database.
    
2. Determine whether the input is handled unsafely.
    
3. Observe application responses and errors.
    
4. Identify how the input affects SQL query execution.
    
5. Attempt to access or modify information beyond the intended authorization.
    
6. Evaluate the impact within the permitted testing scope.
    

Real security testing must be authorized.

## 6. Authentication Bypass

A vulnerable login system may construct a query by directly inserting username and password values.

If an attacker changes the logical conditions of the query, the application may authenticate someone without correctly validating their credentials.

This is known as authentication bypass.

The actual impact depends on:

- Query construction.
    
- Database behavior.
    
- Application authentication logic.
    
- Database privileges.
    
- Additional security controls.
    

## 7. UNION-Based SQL Injection

The SQL `UNION` operator combines the results of two or more SELECT statements.

Example:

```
SELECT name FROM employees
UNION
SELECT username FROM users;
```

For UNION to work:

- Both SELECT statements must return the same number of columns.
    
- Corresponding columns must have compatible data types.
    

In a vulnerable application, attackers may abuse UNION to retrieve information from other tables.

## 8. Blind SQL Injection

Blind SQL injection is especially important because an application may not display database errors or query results.

### Boolean-Based Example

Suppose an application displays different responses depending on whether a database condition is true or false.

The attacker may infer information by observing those response differences.

### Time-Based Example

Some database systems support operations that introduce delays.

An attacker may infer whether a condition is true by measuring the application's response time.

**Security observation:** A lack of visible database errors does not prove that an application is protected against SQL injection.

## 9. Potential Impact

SQL injection can cause serious security problems.

|Impact|Explanation|
|---|---|
|Data Disclosure|Unauthorized access to sensitive records|
|Authentication Bypass|Access without valid authentication|
|Data Modification|Unauthorized changes to records|
|Data Deletion|Removal of database information|
|Privilege Abuse|Misuse of database permissions|
|Service Disruption|Database or application availability may be affected|

The actual impact depends on the vulnerability and the permissions of the database account used by the application.

## 10. SQL Injection in Different Database Systems

SQL injection can affect applications using different database systems.

Examples include:

- MySQL
    
- PostgreSQL
    
- Microsoft SQL Server
    
- Oracle Database
    
- SQLite
    

The underlying injection principle is similar, but SQL syntax, functions, error messages, and database behavior may differ.

## 11. Detection of SQL Injection

During authorized security testing, testers may investigate:

- Whether application inputs influence database queries.
    
- Whether unusual input causes database errors.
    
- Whether response behavior changes unexpectedly.
    
- Whether the application exposes database-specific error messages.
    
- Whether parameterized queries are used.
    
- Whether database permissions are unnecessarily broad.
    

Useful tools include:

|Tool|Purpose|
|---|---|
|Burp Suite|Inspect and modify HTTP requests|
|OWASP ZAP|Web application security testing|
|SQLMap|Automated SQL injection testing|
|Browser Developer Tools|Inspect application requests and responses|

Automated tools should only be used against systems you own or have explicit permission to test.

## 12. SQL Injection and OWASP

SQL Injection is an injection vulnerability.

The OWASP Top 10: 2025 categorizes injection under **A05: Injection**.

Injection vulnerabilities occur when untrusted input is interpreted as part of a command or query.

Other examples include:

- OS command injection.
    
- LDAP injection.
    
- XPath injection.
    

## 13. Safe SQL Injection Lab

Use a local, intentionally vulnerable training application or a disposable database.

Do not test random websites or production systems.

### Lab objective

Understand the difference between unsafe query construction and safe parameterized queries.

### Step 1: Create a sample table

```
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    username TEXT NOT NULL,
    password TEXT NOT NULL
);
```

### Step 2: Insert sample records

```
INSERT INTO users (username, password)
VALUES
('admin', 'admin123'),
('student', 'student123');
```

This is deliberately simplified training data. Real applications must never store plaintext passwords.

### Step 3: Understand the vulnerable pattern

```
username = input("Username: ")

query = (
    "SELECT * FROM users WHERE username = '"
    + username
    + "'"
)
```

Identify the security problem:

- User input is directly concatenated.
    
- The input can change the SQL statement's structure.
    
- The application does not separate query instructions from data.
    

### Step 4: Understand the secure pattern

Using Python's SQLite library:

```
import sqlite3

connection = sqlite3.connect("lab.db")

username = input("Username: ")

cursor = connection.cursor()

cursor.execute(
    "SELECT * FROM users WHERE username = ?",
    (username,)
)

result = cursor.fetchall()

print(result)

connection.close()
```

The `?` placeholder represents a parameter.

The database driver passes the input as data rather than allowing it to become part of the SQL command.

### Step 5: Compare both approaches

|Vulnerable approach|Secure approach|
|---|---|
|String concatenation|Parameterized query|
|User input becomes SQL text|User input remains data|
|Can change query structure|Separates data from SQL instructions|
|SQL injection risk|Strong primary defense|

## 14. Important Security Lessons

- Never directly concatenate untrusted input into SQL queries.
    
- Use parameterized queries or prepared statements.
    
- Apply least-privilege database permissions.
    
- Avoid exposing detailed database errors to users.
    
- Validate input according to business requirements.
    
- Keep database software and application libraries updated.
    
- Use secure authentication and authorization.
    
- Test applications regularly.
    

## 15. Key Takeaways

- SQL Injection is a database-related application security vulnerability.
    
- It occurs when untrusted input changes SQL query structure.
    
- Common categories include in-band, blind, and out-of-band SQL injection.
    
- SQL injection can expose, modify, or delete database information.
    
- Parameterized queries are the primary defense.
    
- Least privilege helps limit potential damage.
    
- Security testing must be authorized.
    

## 16. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[SQL Commands]]
    
- [[SQL User Management and Permissions]]
    
- [[SQL Injection Prevention]]
    
- [[Introduction to Secure Coding]]
    
- [[Input Validation]]
    
- [[Authentication and Authorization]]
    
- [[Burp Suite]]
    
- [[OWASP Top 10]]