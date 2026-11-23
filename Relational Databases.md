> Understand how relational databases organize information into tables and connect data using keys and relationships.

## 1. Introduction to Relational Databases

A **relational database** is a type of database that organizes information into tables consisting of rows and columns.

Tables can be connected through relationships using keys.

The relational model was introduced by Edgar F. Codd in 1970.

Examples of relational database systems:

- MySQL
    
- PostgreSQL
    
- Microsoft SQL Server
    
- Oracle Database
    
- SQLite
    

## 2. Structure of a Relational Database

A relational database consists of tables.

Consider a college database.

### Students Table

|student_id|name|age|
|---|---|---|
|101|Mohit|19|
|102|Rahul|20|
|103|Aman|18|

### Courses Table

|course_id|course_name|
|---|---|
|1|Cybersecurity|
|2|Networking|
|3|Programming|

Each table stores information about a particular entity.

### Important Terms

|Term|Meaning|
|---|---|
|Relation|A table in the relational model|
|Tuple|A row or record|
|Attribute|A column or property|
|Domain|The permitted set of values for an attribute|
|Schema|The logical definition of database structure|
|Relation instance|The actual data in a relation at a particular time|

## 3. Primary Keys

A **primary key** uniquely identifies each row in a table.

Example:

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

Here, `student_id` is the primary key.

### Primary Key Rules

- Values must be unique.
    
- Values cannot be NULL.
    
- A table has one primary key constraint.
    
- A primary key can consist of multiple columns.
    

## 4. Foreign Keys

A **foreign key** creates a relationship by referencing a candidate key, commonly the primary key, in another table.

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

The `course_id` in `enrollments` references `course_id` in `courses`.

A foreign key helps maintain referential integrity.

## 5. Relationships Between Tables

Relational databases support different types of relationships.

### One-to-One Relationship

One record in a table relates to one record in another table.

Example:

```
Person -------- Passport
```

### One-to-Many Relationship

One record in a table relates to multiple records in another table.

Example:

```
Department
    |
    +---- Employee 1
    +---- Employee 2
    +---- Employee 3
```

### Many-to-Many Relationship

Multiple records in one table can relate to multiple records in another table.

Example:

```
Students <------> Courses
```

A junction table implements this relationship.

Example:

```
Students
   |
   v
Enrollments
   |
   v
Courses
```

## 6. Junction Tables

A junction table connects two tables in a many-to-many relationship.

Example:

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);

CREATE TABLE enrollments (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id)
        REFERENCES students(student_id),
    FOREIGN KEY (course_id)
        REFERENCES courses(course_id)
);
```

The composite primary key prevents the same student-course combination from being inserted more than once.

## 7. Relational Database Operations

Relational databases support operations for retrieving and combining information.

### Selection

Selection filters rows based on a condition.

```
SELECT *
FROM students
WHERE age > 18;
```

### Projection

Projection selects particular columns.

```
SELECT name, age
FROM students;
```

### Join

A join combines related rows from multiple tables.

```
SELECT students.name, courses.course_name
FROM students
JOIN enrollments
    ON students.student_id = enrollments.student_id
JOIN courses
    ON enrollments.course_id = courses.course_id;
```

### Union

UNION combines compatible result sets and removes duplicate rows by default.

```
SELECT name FROM students
UNION
SELECT name FROM teachers;
```

The corresponding columns must have compatible data types.

## 8. Normalization in Relational Databases

Normalization organizes tables to reduce unnecessary data duplication and prevent data anomalies.

### First Normal Form (1NF)

- Each cell contains an atomic value.
    
- No repeating groups.
    

### Second Normal Form (2NF)

- The table satisfies 1NF.
    
- No non-key attribute depends on only part of a candidate key.
    

### Third Normal Form (3NF)

- The table satisfies 2NF.
    
- Non-key attributes do not have inappropriate transitive dependencies on candidate keys.
    

Normalization improves data consistency and maintainability.

## 9. Referential Integrity

Referential integrity ensures that relationships between tables remain valid.

Example:

If `course_id = 10` does not exist in the `courses` table, an enrollment record should not be allowed to reference it when a foreign key constraint is enforced.

Example:

```
FOREIGN KEY (course_id)
REFERENCES courses(course_id)
```

Foreign key actions can also define what happens when a referenced record is updated or deleted.

Common actions include:

- `CASCADE`
    
- `SET NULL`
    
- `RESTRICT`
    
- `NO ACTION`
    

The exact behavior can vary by database system.

## 10. Advantages of Relational Databases

1. Structured data organization.
    
2. Relationships between tables.
    
3. Data integrity through constraints.
    
4. Flexible querying using SQL.
    
5. Transaction support.
    
6. Access control and security features.
    
7. Reduced duplication through normalization.
    

## 11. Limitations of Relational Databases

1. Complex joins can become expensive.
    
2. Schema changes may require careful planning.
    
3. Horizontal scaling can be challenging depending on the system.
    
4. Strict structures may be inconvenient for highly variable data.
    
5. Poor indexing and query design can reduce performance.
    

The suitability of a relational database depends on the application's requirements.

## 12. Relational Databases in Cybersecurity

Relational databases are important targets and sources of evidence in cybersecurity.

### SQL Injection

Attackers may manipulate unsafe SQL queries through user input.

### Access Control

Database permissions determine who can read, modify, or administer data.

### Data Integrity

Constraints help prevent invalid or inconsistent records.

### Digital Forensics

Database tables, transaction logs, and audit records may help investigators reconstruct events.

### Database Auditing

Monitoring database activity can help identify:

- Suspicious logins.
    
- Unauthorized changes.
    
- Unusual data access.
    
- Permission modifications.
    

## 13. Practical Lab

Create a small relational database for a college.

### Step 1: Create Students Table

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

### Step 2: Create Courses Table

```
CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);
```

### Step 3: Create Enrollments Table

```
CREATE TABLE enrollments (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id)
        REFERENCES students(student_id),
    FOREIGN KEY (course_id)
        REFERENCES courses(course_id)
);
```

### Step 4: Insert Sample Data

```
INSERT INTO students VALUES
(101, 'Mohit', 19),
(102, 'Rahul', 20);

INSERT INTO courses VALUES
(1, 'Cybersecurity'),
(2, 'Networking');

INSERT INTO enrollments VALUES
(101, 1),
(101, 2),
(102, 1);
```

### Step 5: Retrieve Related Data

```
SELECT
    students.name,
    courses.course_name
FROM students
JOIN enrollments
    ON students.student_id = enrollments.student_id
JOIN courses
    ON enrollments.course_id = courses.course_id;
```

Observe how the database combines information from three tables.

## 14. Key Takeaways

- Relational databases store data in tables.
    
- Rows represent records.
    
- Columns represent attributes.
    
- Primary keys uniquely identify records.
    
- Foreign keys connect tables.
    
- Junction tables implement many-to-many relationships.
    
- Joins retrieve related information.
    
- Normalization reduces unnecessary duplication.
    
- Referential integrity protects relationships between tables.
    

## 15. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[SQL Data Types]]
    
- [[SQL Constraints]]
    
- [[SQL Joins]]
    
- [[SQL Subqueries]]
    
- [[SQL Indexes]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    

## 16. My Understanding

Explain in your own words:

- What is a relational database?
    
- What is a relation?
    
- What is a tuple?
    
- What is an attribute?
    
- What is the difference between a primary key and foreign key?
    
- What is a junction table?
    
- What is referential integrity?
    
- Why is normalization important?
    

## 17. Questions & Doubts

Record questions that need further research.