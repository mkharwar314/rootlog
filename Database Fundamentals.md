> Understand how databases organize, store, retrieve, protect, and manage information.

## 1. What is a Database?

A **database** is an organized collection of data stored electronically so that it can be accessed, managed, updated, and retrieved efficiently.

Examples of information stored in databases:

- Student records.
    
- Employee information.
    
- Banking transactions.
    
- Customer accounts.
    
- Product inventories.
    
- Website user accounts.
    
- Security event records.
    

### Real-World Example

A college database might store:

|Student_ID|Name|Department|Age|
|---|---|---|---|
|101|Mohit|Cybersecurity|19|
|102|Rahul|Computer Science|20|
|103|Aman|Networking|18|

Each row represents one student, while each column represents a particular attribute.

## 2. Why Are Databases Needed?

Without a database, applications might store information in separate files, making it difficult to organize and maintain large amounts of data.

Databases provide:

1. **Organization:** Store information in a structured format.
    
2. **Retrieval:** Find required information quickly.
    
3. **Consistency:** Apply rules to maintain accurate data.
    
4. **Security:** Control who can access information.
    
5. **Scalability:** Handle growing amounts of information.
    
6. **Backup and Recovery:** Restore information after failures.
    
7. **Concurrency:** Allow multiple users or applications to work with data.
    

## 3. Types of Databases

Different databases use different methods to organize and retrieve information.

### 1. Relational Database

Stores data in tables containing rows and columns.

Examples:

- MySQL
    
- PostgreSQL
    
- Microsoft SQL Server
    
- SQLite
    
- Oracle Database
    

Common uses:

- Banking systems.
    
- Student management systems.
    
- E-commerce applications.
    

### 2. NoSQL Database

NoSQL databases use data models other than the traditional relational table model.

Common types include:

|Type|Description|Example|
|---|---|---|
|Document|Stores document-oriented records|MongoDB|
|Key-Value|Stores key-value pairs|Redis|
|Wide-Column|Stores data in column families|Apache Cassandra|
|Graph|Stores nodes and relationships|Neo4j|

Common uses:

- Large-scale applications.
    
- Real-time systems.
    
- Flexible data storage.
    
- Relationship-heavy data.
    

### 3. Hierarchical Database

Organizes data in a tree-like parent-child structure.

A child record generally has one parent.

Example:

```
Organization
    |
    +-- Department A
    |      |
    |      +-- Employee 1
    |      +-- Employee 2
    |
    +-- Department B
           |
           +-- Employee 3
```

### 4. Network Database

Organizes data using records connected through multiple relationships.

Unlike a simple hierarchical model, a record can participate in multiple relationships.

### 5. Object-Oriented Database

Stores information as objects, using concepts such as classes and objects.

## 4. Database vs DBMS vs RDBMS

These terms are related but have different meanings.

|Term|Meaning|
|---|---|
|Database|Organized collection of data|
|DBMS|Software used to manage databases|
|RDBMS|DBMS that uses the relational data model|

Example:

- Database: `college_db`
    
- DBMS: MySQL
    
- RDBMS: MySQL is an example of an RDBMS.
    

## 5. Database Components

A database environment includes several important components.

### Tables

Tables organize related data into rows and columns.

Example:

|ID|Name|Age|
|---|---|---|
|1|Mohit|19|
|2|Rahul|20|

### Rows

A row represents one complete record.

Example:

```
1 | Mohit | 19
```

### Columns

A column represents an attribute of the records.

Example:

- ID
    
- Name
    
- Age
    

### Schema

A schema describes the logical structure of database objects, such as tables, columns, relationships, and constraints.

### Queries

Queries are instructions used to retrieve or manipulate database information.

Example:

```
SELECT * FROM students;
```

## 6. Database Keys

Keys help identify records and establish relationships between tables.

### Primary Key

A primary key uniquely identifies each record in a table.

Example:

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);
```

A primary key must contain unique, non-NULL values.

### Foreign Key

A foreign key references a key in another table or, in some cases, the same table.

Example:

```
CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);

CREATE TABLE enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (course_id)
        REFERENCES courses(course_id)
);
```

### Candidate Key

A candidate key is a minimal set of attributes that can uniquely identify a record.

A table can have multiple candidate keys.

### Composite Key

A composite key uses two or more columns together to uniquely identify a record.

Example:

```
student_id + course_id
```

### Alternate Key

A candidate key that is not selected as the primary key is commonly called an alternate key.

## 7. Database Relationships

Relational databases connect tables using relationships.

### One-to-One

One record in a table relates to one record in another table.

Example:

```
Person ---- Passport
```

### One-to-Many

One record in a table relates to multiple records in another table.

Example:

```
Department
    |
    +-- Employee 1
    +-- Employee 2
    +-- Employee 3
```

### Many-to-Many

Multiple records in one table relate to multiple records in another table.

Example:

```
Students <----> Courses
```

A junction table, such as `enrollments`, is commonly used to implement this relationship in a relational database.

## 8. Database Normalization

Normalization is the process of organizing relational database tables to reduce unnecessary data duplication and improve data integrity.

### Why Normalization Is Important

It helps prevent:

- Duplicate information.
    
- Update anomalies.
    
- Insertion anomalies.
    
- Deletion anomalies.
    

### First Normal Form (1NF)

A table is in 1NF when each column contains atomic values and there are no repeating groups.

Poor design:

|Student_ID|Subjects|
|---|---|
|101|SQL, Python|

Improved design:

|Student_ID|Subject|
|---|---|
|101|SQL|
|101|Python|

### Second Normal Form (2NF)

A table must:

- Satisfy 1NF.
    
- Have no partial dependency of a non-key attribute on a candidate key.
    

This is especially relevant when a table has a composite candidate key.

### Third Normal Form (3NF)

A table must:

- Satisfy 2NF.
    
- Have no inappropriate transitive dependency of non-key attributes on candidate keys.
    

Normalization should be based on actual data dependencies, not simply splitting tables unnecessarily.

## 9. ACID Properties

ACID describes four important properties of database transactions.

|Property|Meaning|
|---|---|
|Atomicity|A transaction happens completely or not at all|
|Consistency|A transaction preserves database rules|
|Isolation|Concurrent transactions are controlled to prevent improper interference|
|Durability|Committed changes survive failures according to the database's durability guarantees|

### Example: Bank Transfer

Suppose ₹1,000 is transferred from Account A to Account B.

1. ₹1,000 is deducted from Account A.
    
2. ₹1,000 is added to Account B.
    

If the second operation fails, the transaction should not leave the database in an incorrect partial state.

This is where transaction properties become important.

## 10. Database Transactions

A transaction is a logical unit of database operations.

Example:

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

If an error occurs before committing, a transaction may be rolled back:

```
ROLLBACK;
```

The exact transaction syntax and behavior depend on the database system.

## 11. Database Security

Databases often contain sensitive information, making security essential.

Important security controls include:

### Authentication

Verify the identity of users connecting to the database.

### Authorization

Control what authenticated users are allowed to do.

### Least Privilege

Give users only the permissions required for their responsibilities.

### Encryption

Protect sensitive information:

- At rest.
    
- In transit.
    

### Backup and Recovery

Maintain protected backups and test recovery procedures.

### Auditing and Monitoring

Track important database activities, including:

- Login attempts.
    
- Permission changes.
    
- Data modifications.
    
- Administrative operations.
    

### Secure Query Execution

Use parameterized queries rather than constructing SQL queries through unsafe string concatenation.

## 12. Database Attacks

Common database-related security threats include:

|Attack|Description|
|---|---|
|SQL Injection|Malicious input changes the intended SQL query|
|Credential Theft|Attackers obtain database login credentials|
|Privilege Escalation|A user gains unauthorized permissions|
|Data Exfiltration|Sensitive information is extracted|
|Denial of Service|Database availability is disrupted|
|Misconfiguration|Weak settings expose database resources|

Understanding database architecture helps security professionals identify and prevent these threats.

## 13. Practical Example: Designing a College Database

Consider a college system containing students and courses.

### Students Table

|student_id|name|
|---|---|
|101|Mohit|
|102|Rahul|

### Courses Table

|course_id|course_name|
|---|---|
|1|Cybersecurity|
|2|Networking|

### Enrollments Table

|student_id|course_id|
|---|---|
|101|1|
|101|2|
|102|1|

The `enrollments` table connects students and courses.

This is an example of a many-to-many relationship.

## 14. Key Takeaways

- A database stores organized information.
    
- A DBMS manages database operations.
    
- Relational databases organize information into tables.
    
- Keys identify records and establish relationships.
    
- Normalization reduces unnecessary duplication.
    
- ACID properties support reliable transactions.
    
- Database security protects sensitive information.
    
- SQL is used to communicate with relational databases.
    

## 15. Related Topics

- [[Introduction to SQL]]
    
- [[Relational Databases]]
    
- [[SQL Data Types]]
    
- [[SQL Commands]]
    
- [[SQL Constraints]]
    
- [[SQL Transactions]]
    
- [[SQL User Management and Permissions]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    

## 16. My Understanding

Explain in your own words:

- What is a database?
    
- What is the difference between SQL and NoSQL databases?
    
- What is a primary key?
    
- What is a foreign key?
    
- What are the three common database relationships?
    
- What is normalization?
    
- What do ACID properties mean?
    
- Why is database security important?
    

## 17. Questions & Doubts

Record questions that need further research.