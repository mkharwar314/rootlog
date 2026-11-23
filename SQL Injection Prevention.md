> Learn how to prevent SQL injection vulnerabilities using secure query construction, database permissions, input handling, and secure application development practices.

## 1. Introduction

SQL Injection Prevention is the process of protecting applications and databases from malicious SQL input.

SQL injection occurs when untrusted input is interpreted as part of an SQL command.

The primary defense is to separate SQL instructions from user-provided data.

Developers should combine secure query construction with appropriate database permissions and application security controls.

## 2. Why SQL Injection Prevention Matters

Without proper protection, attackers may:

- Read confidential database records.
    
- Bypass authentication.
    
- Modify stored information.
    
- Delete database records.
    
- Access unauthorized database functionality.
    

Prevention protects:

- Data confidentiality.
    
- Data integrity.
    
- Application availability.
    
- User privacy.
    
- Business operations.
    

## 3. Parameterized Queries

Parameterized queries are the primary defense against SQL injection.

They separate SQL instructions from user input.

Instead of combining input directly into a query, the application uses placeholders.

### Vulnerable Example

Python with SQLite:

```
import sqlite3

connection = sqlite3.connect("lab.db")

username = input("Enter username: ")

query = (
    "SELECT * FROM users WHERE username = '"
    + username
    + "'"
)

cursor = connection.cursor()
cursor.execute(query)
```

**Problem:**

User input becomes part of the SQL statement.

### Secure Example

```
import sqlite3

connection = sqlite3.connect("lab.db")

username = input("Enter username: ")

cursor = connection.cursor()

cursor.execute(
    "SELECT * FROM users WHERE username = ?",
    (username,)
)

result = cursor.fetchall()

print(result)

connection.close()
```

**Why is this secure?**

- The SQL query structure remains fixed.
    
- User input is supplied separately.
    
- The database driver handles the value as data.
    
- Input cannot simply introduce additional SQL instructions through that parameter.
    

## 4. Prepared Statements

A prepared statement is an SQL statement prepared separately from the values supplied to it.

The application provides parameters when executing the statement.

Example:

```
SELECT * FROM users
WHERE username = ?;
```

The application supplies the username separately.

Benefits:

- Separates SQL logic from user input.
    
- Reduces SQL injection risk.
    
- Makes repeated query execution easier.
    
- Improves query handling in many database systems.
    

Prepared statements are supported by many programming languages and database drivers.

## 5. Input Validation

Input validation checks whether user-provided data meets the application's expected requirements.

Examples:

|Input|Validation|
|---|---|
|Email|Check expected email format|
|Age|Accept an appropriate numeric range|
|Username|Enforce permitted characters and length|
|Phone number|Check expected format|
|Product ID|Require an integer or valid identifier|

Example in Python:

```
age = input("Enter your age: ")

if age.isdigit():
    age = int(age)

    if 1 <= age <= 120:
        print("Valid age")
    else:
        print("Age outside allowed range")
else:
    print("Invalid input")
```

**Important:** Input validation is an additional security control. It does not replace parameterized queries.

## 6. Avoid Dynamic SQL Concatenation

Dynamic SQL is SQL constructed at runtime.

It can be useful, but unsafe string concatenation creates injection risks.

### Unsafe Example

```
query = "SELECT * FROM users WHERE username = '" + username + "'"
```

### Safer Example

```
cursor.execute(
    "SELECT * FROM users WHERE username = ?",
    (username,)
)
```

When dynamic identifiers such as table names or column names are required, ordinary value placeholders usually cannot represent them.

Use:

- Strict allowlists of permitted identifiers.
    
- Safe identifier-quoting features provided by the database library.
    
- Fixed query templates wherever possible.
    

Never assume that escaping arbitrary input is a reliable replacement for parameterized queries.

## 7. Least Privilege

The Principle of Least Privilege means giving a database account only the permissions it needs.

Example:

A reporting application needs to retrieve records.

It should normally receive:

- SELECT
    

It should not automatically receive:

- DROP
    
- ALTER
    
- CREATE
    
- Unnecessary UPDATE or DELETE
    

Benefits:

- Limits the damage caused by compromised accounts.
    
- Reduces opportunities for unauthorized database changes.
    
- Helps control privilege escalation risks.
    

Least privilege does not prevent SQL injection, but it limits its potential impact.

## 8. Secure Error Handling

Database errors may reveal:

- Table names.
    
- Column names.
    
- Database software details.
    
- SQL query structure.
    
- Internal application information.
    

Avoid displaying detailed database errors to ordinary users.

Example of a safer application response:

```
An unexpected error occurred.
Please try again later.
```

Record technical details securely in application logs for debugging and incident investigation.

Do not expose sensitive information in those logs.

## 9. Stored Procedures

Stored procedures are database routines that execute predefined operations.

They can help centralize database logic and control access.

However, stored procedures are not automatically safe.

A stored procedure that constructs SQL using unsafe string concatenation can still be vulnerable.

Use parameterized statements inside stored procedures whenever dynamic input is involved.

## 10. Web Application Firewall (WAF)

A Web Application Firewall monitors HTTP traffic and may block requests that match suspicious patterns.

It can help detect or block some SQL injection attempts.

Benefits:

- Adds another layer of defense.
    
- Helps identify suspicious requests.
    
- Can provide temporary protection while vulnerabilities are fixed.
    

Limitations:

- May produce false positives.
    
- Can miss some attacks.
    
- Cannot reliably fix vulnerable application code.
    

A WAF should supplement secure development, not replace it.

## 11. Database and Application Security

Additional security practices include:

### 1. Keep software updated

Apply security patches to databases, frameworks, and libraries.

### 2. Protect database credentials

Use environment variables or a secrets manager rather than hardcoding credentials.

### 3. Use encrypted connections

Use TLS where supported and configure certificate validation correctly.

### 4. Restrict database network access

Allow connections only from systems that need them.

### 5. Monitor database activity

Review unusual queries, unexpected access, and suspicious account behavior.

### 6. Separate development and production

Do not use production databases as unrestricted testing environments.

## 12. SQL Injection Prevention in Different Languages

The exact parameter syntax depends on the programming language and database driver.

### Python with SQLite

```
cursor.execute(
    "SELECT * FROM users WHERE username = ?",
    (username,)
)
```

### Python with PostgreSQL using psycopg

```
cursor.execute(
    "SELECT * FROM users WHERE username = %s",
    (username,)
)
```

### Java with JDBC

```
String sql = "SELECT * FROM users WHERE username = ?";

PreparedStatement statement =
    connection.prepareStatement(sql);

statement.setString(1, username);

ResultSet result = statement.executeQuery();
```

### PHP with PDO

```
$stmt = $pdo->prepare(
    "SELECT * FROM users WHERE username = :username"
);

$stmt->execute([
    "username" => $username
]);
```

The placeholder syntax varies. Follow the documentation for the specific database driver.

## 13. SQL Injection Prevention Checklist

Use this checklist when reviewing an application:

- Parameterized queries are used.
    
- Untrusted input is not directly concatenated into SQL.
    
- Dynamic SQL identifiers use strict allowlists.
    
- Database accounts follow least privilege.
    
- Detailed database errors are not exposed to users.
    
- Database credentials are protected.
    
- Database connections use appropriate encryption.
    
- Database software and libraries are updated.
    
- Application logs are monitored.
    
- Security testing is performed regularly.
    

## 14. Practical Lab

### Objective

Compare an unsafe SQL query with a parameterized query.

### Step 1: Create a sample database

```
import sqlite3

connection = sqlite3.connect("security_lab.db")

cursor = connection.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY,
    username TEXT NOT NULL
)
""")

cursor.execute(
    "INSERT INTO users (username) VALUES (?)",
    ("student",)
)

connection.commit()
```

### Step 2: Execute a parameterized query

```
username = input("Enter username: ")

cursor.execute(
    "SELECT * FROM users WHERE username = ?",
    (username,)
)

print(cursor.fetchall())
```

### Step 3: Observe the result

Test with:

- `student`
    
- `admin`
    
- An empty string
    
- A string containing quotation marks
    

Observe how the application handles each value.

The SQL query structure remains unchanged because the input is passed as a parameter.

### Step 4: Record your observation

Write down:

1. What happens when the username exists?
    
2. What happens when it does not exist?
    
3. How does parameterization handle quotation marks?
    
4. Why is parameterization safer than concatenation?
    

### Step 5: Close the connection

```
connection.close()
```

## 15. Common Misconceptions

|Misconception|Correct understanding|
|---|---|
|Input validation alone prevents SQL injection|Parameterized queries are the primary defense|
|A WAF completely prevents SQL injection|A WAF is only an additional security layer|
|Stored procedures are always safe|Unsafe dynamic SQL inside them can remain vulnerable|
|Hiding database errors fixes SQL injection|It reduces information disclosure but does not fix the vulnerability|
|Escaping input is always sufficient|Escaping is context-dependent and error-prone|

## 16. Key Takeaways

- Parameterized queries are the primary defense against SQL injection.
    
- Prepared statements separate SQL instructions from user data.
    
- Input validation provides additional protection.
    
- Dynamic SQL must be handled carefully.
    
- Least privilege limits the impact of compromised accounts.
    
- Secure error handling reduces information disclosure.
    
- WAFs provide additional protection but cannot replace secure code.
    
- Security must be applied at both application and database levels.
    

## 17. Related Topics

- [[SQL Injection]]
    
- [[SQL User Management and Permissions]]
    
- [[Introduction to Secure Coding]]
    
- [[Input Validation]]
    
- [[Output Encoding]]
    
- [[Authentication and Authorization]]
    
- [[Secrets Management]]
    
- [[OWASP Top 10]]
    
- [[Introduction to Python]]
    
- [[Database Fundamentals]]