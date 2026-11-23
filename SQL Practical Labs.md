> Apply SQL concepts through hands-on exercises involving database creation, data manipulation, querying, relationships, transactions, permissions, and security.

## 1. Lab Environment

You can perform these labs using:

- SQLite
    
- MySQL
    
- PostgreSQL
    
- DB Browser for SQLite
    
- Python with SQLite
    

**Recommended starting point:** SQLite with Python.

SQLite does not require a separate database server and is suitable for beginner practice.

For database user-management and permission labs, use PostgreSQL or MySQL because SQLite does not provide built-in database users and GRANT/REVOKE privileges.

## 2. Lab 01 — Database Creation

**Objective:** Understand how to create a database and tables.

SQLite creates a database file when it connects to a new database.

```
import sqlite3

connection = sqlite3.connect("rootlog_lab.db")

cursor = connection.cursor()

print("Database connected successfully")

connection.close()
```

**Task:**

1. Create a database named `rootlog_lab.db`.
    
2. Connect to it.
    
3. Verify that the database file exists.
    

## 3. Lab 02 — Table Creation

**Objective:** Create tables using SQL.

```
CREATE TABLE students (
    student_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER,
    course TEXT
);
```

**Task:**

1. Create a `students` table.
    
2. Add columns for student ID, name, age, and course.
    
3. Identify the primary key.
    
4. Explain why `NOT NULL` is used.
    

## 4. Lab 03 — Inserting Records

**Objective:** Add records using INSERT.

```
INSERT INTO students
(student_id, name, age, course)
VALUES
(1, 'Rahul', 19, 'Cybersecurity');

INSERT INTO students
(student_id, name, age, course)
VALUES
(2, 'Aman', 20, 'Computer Science');

INSERT INTO students
(student_id, name, age, course)
VALUES
(3, 'Priya', 18, 'Cybersecurity');
```

**Task:**

- Insert at least five records.
    
- Use different names and courses.
    
- Try inserting a duplicate primary key and observe the result.
    

## 5. Lab 04 — Retrieving Records

**Objective:** Retrieve database records using SELECT.

```
SELECT * FROM students;
```

Retrieve specific columns:

```
SELECT name, course
FROM students;
```

Filter records:

```
SELECT *
FROM students
WHERE course = 'Cybersecurity';
```

Sort records:

```
SELECT *
FROM students
ORDER BY age DESC;
```

**Task:**

1. Display all students.
    
2. Display only names and courses.
    
3. Find students older than 18.
    
4. Sort students by age.
    

## 6. Lab 05 — Updating Records

**Objective:** Modify existing records.

```
UPDATE students
SET age = 21
WHERE student_id = 2;
```

Verify:

```
SELECT *
FROM students
WHERE student_id = 2;
```

**Task:**

- Update a student's course.
    
- Update a student's age.
    
- Observe what happens when you omit the WHERE condition in a disposable test table.
    

**Important:** An UPDATE statement without a WHERE clause can modify every row.

## 7. Lab 06 — Deleting Records

**Objective:** Remove database records.

```
DELETE FROM students
WHERE student_id = 3;
```

Verify:

```
SELECT * FROM students;
```

**Task:**

1. Delete one student.
    
2. Verify the remaining records.
    
3. Explain why WHERE is important in DELETE statements.
    

## 8. Lab 07 — SQL Constraints

**Objective:** Understand database integrity rules.

Create a table:

```
CREATE TABLE accounts (
    account_id INTEGER PRIMARY KEY,
    username TEXT NOT NULL UNIQUE,
    age INTEGER CHECK (age >= 18),
    email TEXT
);
```

Test the constraints:

```
INSERT INTO accounts
VALUES (1, 'student01', 20, 'student@example.com');
```

Try inserting:

- A duplicate username.
    
- A NULL username.
    
- An age below 18.
    

Observe which operations are rejected.

**Task:** Explain the purpose of PRIMARY KEY, UNIQUE, NOT NULL, and CHECK.

## 9. Lab 08 — Aggregate Functions

**Objective:** Perform calculations on database records.

```
SELECT COUNT(*)
FROM students;
```

```
SELECT AVG(age)
FROM students;
```

```
SELECT MAX(age)
FROM students;
```

```
SELECT MIN(age)
FROM students;
```

```
SELECT course, COUNT(*)
FROM students
GROUP BY course;
```

**Task:**

- Count all students.
    
- Calculate average age.
    
- Find the oldest student.
    
- Count students in each course.
    

## 10. Lab 09 — SQL Joins

**Objective:** Retrieve related information from multiple tables.

Create a courses table:

```
CREATE TABLE courses (
    course_id INTEGER PRIMARY KEY,
    course_name TEXT NOT NULL
);
```

Insert records:

```
INSERT INTO courses
VALUES
(1, 'Cybersecurity'),
(2, 'Computer Science'),
(3, 'Networking');
```

Create a student-course relationship table:

```
CREATE TABLE student_courses (
    student_id INTEGER,
    course_id INTEGER,
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

Insert relationships:

```
INSERT INTO student_courses
VALUES
(1, 1),
(2, 2),
(3, 1);
```

Perform an INNER JOIN:

```
SELECT students.name, courses.course_name
FROM students
INNER JOIN student_courses
ON students.student_id = student_courses.student_id
INNER JOIN courses
ON student_courses.course_id = courses.course_id;
```

**Task:**

- Identify the tables being joined.
    
- Explain the purpose of each JOIN condition.
    
- Observe how related records are combined.
    

## 11. Lab 10 — SQL Subqueries

**Objective:** Use one query inside another query.

```
SELECT *
FROM students
WHERE age > (
    SELECT AVG(age)
    FROM students
);
```

This retrieves students whose age is greater than the average age.

**Task:** Write a query to find students enrolled in the Cybersecurity course using a subquery.

## 12. Lab 11 — SQL Views

**Objective:** Create a virtual table based on a query.

```
CREATE VIEW cybersecurity_students AS
SELECT *
FROM students
WHERE course = 'Cybersecurity';
```

Retrieve records:

```
SELECT *
FROM cybersecurity_students;
```

Remove the view:

```
DROP VIEW cybersecurity_students;
```

**Task:** Create a view that displays only student names and courses.

## 13. Lab 12 — SQL Indexes

**Objective:** Understand how indexes support data retrieval.

Create an index:

```
CREATE INDEX idx_student_name
ON students(name);
```

Inspect the query plan in SQLite:

```
EXPLAIN QUERY PLAN
SELECT *
FROM students
WHERE name = 'Rahul';
```

Remove the index:

```
DROP INDEX idx_student_name;
```

**Task:** Explain why indexes can improve query performance and why excessive indexing can increase storage and write overhead.

## 14. Lab 13 — SQL Transactions

**Objective:** Understand transaction control.

```
BEGIN TRANSACTION;

UPDATE students
SET age = 22
WHERE student_id = 1;

SELECT *
FROM students;

ROLLBACK;
```

The ROLLBACK operation cancels the uncommitted change.

Now try:

```
BEGIN TRANSACTION;

UPDATE students
SET age = 22
WHERE student_id = 1;

COMMIT;
```

COMMIT saves the transaction.

**Task:**

- Perform an update followed by ROLLBACK.
    
- Perform another update followed by COMMIT.
    
- Compare the results.
    

## 15. Lab 14 — Database User Management

**Objective:** Understand how database privileges control access.

This lab requires PostgreSQL or MySQL, not SQLite.

PostgreSQL example:

```
CREATE ROLE student_reader;

GRANT CONNECT
ON DATABASE rootlog_lab
TO student_reader;
```

After connecting to the database, grant schema and table access:

```
GRANT USAGE
ON SCHEMA public
TO student_reader;

GRANT SELECT
ON ALL TABLES IN SCHEMA public
TO student_reader;
```

Inspect roles in the PostgreSQL `psql` terminal:

```
\du
```

**Task:**

1. Identify the role created.
    
2. Explain the difference between CONNECT and SELECT.
    
3. Explain why a read-only account is useful.
    

## 16. Lab 15 — SQL Injection Awareness

**Objective:** Understand unsafe query construction and secure parameterization.

Vulnerable Python example:

```
username = input("Enter username: ")

query = (
    "SELECT * FROM students WHERE name = '"
    + username
    + "'"
)

cursor.execute(query)
```

Secure version:

```
username = input("Enter username: ")

cursor.execute(
    "SELECT * FROM students WHERE name = ?",
    (username,)
)
```

**Task:**

1. Identify the vulnerability in the first example.
    
2. Explain why the second example is safer.
    
3. Explain why database permissions still matter.
    

Use a local disposable database only.

## 17. Lab 16 — SQL Security Review

**Objective:** Apply basic database security practices.

Review your database and answer:

- Are primary keys defined?
    
- Are appropriate constraints applied?
    
- Are database accounts given only necessary privileges?
    
- Are parameterized queries used?
    
- Are credentials stored securely?
    
- Are unnecessary accounts disabled?
    
- Are database backups maintained?
    
- Are sensitive records protected?
    
- Are database connections appropriately secured?
    

Record any weaknesses you identify.

## 18. Mini Project — Student Management Database

**Objective:** Combine SQL concepts into one small project.

Build a Student Management Database.

### Required tables

**Students**

|Column|Type|
|---|---|
|student_id|INTEGER|
|name|TEXT|
|age|INTEGER|
|email|TEXT|

**Courses**

|Column|Type|
|---|---|
|course_id|INTEGER|
|course_name|TEXT|

**Enrollments**

|Column|Type|
|---|---|
|enrollment_id|INTEGER|
|student_id|INTEGER|
|course_id|INTEGER|

### Required operations

- Create all three tables.
    
- Define primary and foreign keys.
    
- Insert at least five students.
    
- Insert at least three courses.
    
- Enroll students in courses.
    
- Retrieve student records.
    
- Update student information.
    
- Delete a record.
    
- Use JOIN to retrieve enrollment information.
    
- Create an index.
    
- Create a view.
    
- Demonstrate a transaction.
    
- Use parameterized queries in Python.
    

### Security requirements

- Use parameterized queries.
    
- Avoid hardcoded production credentials.
    
- Apply appropriate database permissions when using a DBMS that supports them.
    
- Do not store real personal information in the practice database.
    

### Project documentation

Record:

1. Project objective.
    
2. Database schema.
    
3. Table relationships.
    
4. SQL commands used.
    
5. Screenshots or query outputs.
    
6. Problems encountered.
    
7. Security measures implemented.
    
8. What you learned.
    

## 19. Lab Completion Tracker

- Lab 01 — Database Creation
    
- Lab 02 — Table Creation
    
- Lab 03 — Inserting Records
    
- Lab 04 — Retrieving Records
    
- Lab 05 — Updating Records
    
- Lab 06 — Deleting Records
    
- Lab 07 — SQL Constraints
    
- Lab 08 — Aggregate Functions
    
- Lab 09 — SQL Joins
    
- Lab 10 — SQL Subqueries
    
- Lab 11 — SQL Views
    
- Lab 12 — SQL Indexes
    
- Lab 13 — SQL Transactions
    
- Lab 14 — Database User Management
    
- Lab 15 — SQL Injection Awareness
    
- Lab 16 — SQL Security Review
    
- Mini Project — Student Management Database
    

## 20. Key Takeaways

- SQL is used to manage and query relational databases.
    
- Database constraints help maintain data integrity.
    
- JOINs combine related records.
    
- Transactions help maintain reliable database operations.
    
- Indexes can improve query performance.
    
- Database privileges control access.
    
- Parameterized queries help prevent SQL injection.
    
- Practical work is essential for developing database skills.
    

## 21. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[SQL Constraints]]
    
- [[SQL Joins]]
    
- [[SQL Subqueries]]
    
- [[SQL Views]]
    
- [[SQL Indexes]]
    
- [[SQL Transactions]]
    
- [[SQL User Management and Permissions]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    
- [[Introduction to Python]]
    
- [[Introduction to Secure Coding]]