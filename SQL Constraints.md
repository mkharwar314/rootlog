> Understand how SQL constraints enforce data integrity, accuracy, and consistency in relational databases.

## 1. What are SQL Constraints?

SQL constraints are rules applied to database columns or tables to control what data can be stored.

They help prevent invalid, duplicate, or inconsistent records.

For example:

- A student ID must be unique.
    
- A student's name cannot be empty.
    
- An employee's salary must satisfy a specified condition.
    
- A foreign key must reference an existing record.
    

### Why Are Constraints Important?

- Maintain data accuracy.
    
- Prevent duplicate records.
    
- Enforce relationships between tables.
    
- Reduce invalid data entry.
    
- Improve database reliability.
    
- Support application security and integrity.
    

## 2. Types of SQL Constraints

|Constraint|Purpose|
|---|---|
|PRIMARY KEY|Uniquely identifies each record.|
|FOREIGN KEY|Maintains relationships between tables.|
|UNIQUE|Prevents duplicate values.|
|NOT NULL|Prevents NULL values.|
|CHECK|Enforces a condition.|
|DEFAULT|Provides a default value.|

## 3. PRIMARY KEY Constraint

A **PRIMARY KEY** uniquely identifies every record in a table.

### Characteristics

- Must contain unique values.
    
- Cannot contain NULL values.
    
- A table can have only one primary key constraint.
    
- A primary key can consist of one or multiple columns.
    

### Example

```
CREATE TABLE students (
    student_id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    age INTEGER
);
```

Here, `student_id` uniquely identifies each student.

### Composite Primary Key

A composite primary key uses two or more columns together to identify a record.

```
CREATE TABLE enrollments (
    student_id INTEGER,
    course_id INTEGER,
    PRIMARY KEY (student_id, course_id)
);
```

The combination of `student_id` and `course_id` must be unique.

## 4. FOREIGN KEY Constraint

A **FOREIGN KEY** creates a relationship between two tables.

It ensures that a value in the referencing table corresponds to an existing key in the referenced table, subject to the constraint's rules.

### Example

```
CREATE TABLE departments (
    department_id INTEGER PRIMARY KEY,
    department_name VARCHAR(50)
);
```

Create an employees table:

```
CREATE TABLE employees (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER,
    FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
);
```

The `department_id` in `employees` references `department_id` in `departments`.

### Why Is It Important?

Without foreign key constraints, a database may contain references to records that do not exist.

This can create inconsistent relationships.

### ON DELETE Actions

Foreign keys can define what happens when a referenced record is deleted.

|Action|Behavior|
|---|---|
|CASCADE|Deletes referencing rows automatically.|
|SET NULL|Sets the referencing column to NULL.|
|SET DEFAULT|Sets the referencing column to its default value, where supported.|
|RESTRICT|Prevents deletion while referencing rows exist.|
|NO ACTION|Rejects the operation if the constraint would be violated, subject to database-specific timing rules.|

Example:

```
CREATE TABLE employees (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INTEGER,
    FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
        ON DELETE SET NULL
);
```

**Security consideration:** Cascading deletes can remove many related records. Use them only when that behavior is intentional.

## 5. UNIQUE Constraint

The **UNIQUE** constraint prevents duplicate values in a column or combination of columns.

### Example

```
CREATE TABLE users (
    user_id INTEGER PRIMARY KEY,
    username VARCHAR(50) UNIQUE,
    email VARCHAR(100) UNIQUE
);
```

This prevents two records from having the same username or email.

### UNIQUE vs PRIMARY KEY

|PRIMARY KEY|UNIQUE|
|---|---|
|Uniquely identifies a record.|Enforces uniqueness.|
|Cannot contain NULL.|NULL behavior varies by database.|
|Only one primary key constraint per table.|Multiple UNIQUE constraints are allowed.|

## 6. NOT NULL Constraint

The **NOT NULL** constraint prevents a column from storing NULL values.

### Example

```
CREATE TABLE users (
    user_id INTEGER PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL
);
```

Every inserted record must provide values for these required columns.

### Invalid Example

```
INSERT INTO users (user_id, username, email)
VALUES (1, NULL, 'mohit@example.com');
```

The database rejects this insertion because `username` cannot be NULL.

**Important:** NULL means an unknown or missing value. It is not the same as zero or an empty string.

## 7. CHECK Constraint

The **CHECK** constraint ensures that inserted or updated values satisfy a specified condition.

### Example

```
CREATE TABLE students (
    student_id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    age INTEGER CHECK (age >= 18)
);
```

This restricts age values to 18 or higher.

### Multiple Conditions

```
CREATE TABLE employees (
    employee_id INTEGER PRIMARY KEY,
    salary DECIMAL(10,2)
        CHECK (salary >= 0 AND salary <= 1000000)
);
```

The salary must be within the specified range.

**Important:** CHECK constraints are not a replacement for complete business-rule validation. NULL handling and enforcement details vary across databases.

## 8. DEFAULT Constraint

The **DEFAULT** constraint provides a predefined value when an INSERT statement does not supply a value for that column.

### Example

```
CREATE TABLE users (
    user_id INTEGER PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    status VARCHAR(20) DEFAULT 'active'
);
```

Insert a record:

```
INSERT INTO users (user_id, username)
VALUES (1, 'mohit');
```

The database automatically assigns `active` to the status column.

**Important:** Explicitly inserting NULL does not normally trigger the default value.

## 9. Column-Level and Table-Level Constraints

Constraints can be defined at the column level or table level.

### Column-Level Constraint

```
CREATE TABLE students (
    student_id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);
```

The constraints are defined alongside individual columns.

### Table-Level Constraint

```
CREATE TABLE enrollments (
    student_id INTEGER,
    course_id INTEGER,
    CONSTRAINT pk_enrollment
        PRIMARY KEY (student_id, course_id)
);
```

Table-level constraints are particularly useful for composite keys and constraints involving multiple columns.

## 10. Naming Constraints

You can assign names to constraints using the `CONSTRAINT` keyword.

### Example

```
CREATE TABLE students (
    student_id INTEGER,
    email VARCHAR(100),

    CONSTRAINT pk_students
        PRIMARY KEY (student_id),

    CONSTRAINT uq_students_email
        UNIQUE (email)
);
```

Naming constraints makes database maintenance and troubleshooting easier.

## 11. Adding and Removing Constraints

Constraints can sometimes be added or removed after a table has been created.

The exact syntax depends on the database system.

### Add a Constraint

Common syntax:

```
ALTER TABLE students
ADD CONSTRAINT uq_student_email
UNIQUE (email);
```

### Drop a Constraint

Common syntax:

```
ALTER TABLE students
DROP CONSTRAINT uq_student_email;
```

**Database differences:**

- PostgreSQL and SQL Server support this general DROP CONSTRAINT syntax.
    
- MySQL uses `DROP INDEX` to remove a UNIQUE constraint in common cases.
    
- SQLite has more limited ALTER TABLE support and may require rebuilding a table for certain changes.
    

Always check the database-specific documentation before modifying production schemas.

## 12. SQL Constraints and Data Integrity

Data integrity means maintaining the accuracy, validity, and consistency of stored data.

Constraints support several types of integrity.

|Integrity Type|Explanation|Related Constraint|
|---|---|---|
|Entity Integrity|Each record has a unique identity.|PRIMARY KEY|
|Referential Integrity|Relationships remain valid.|FOREIGN KEY|
|Domain Integrity|Values follow permitted rules.|CHECK, NOT NULL|
|Uniqueness Integrity|Duplicate values are prevented where required.|UNIQUE|

## 13. Security Considerations

Constraints are also useful in secure database design.

### 13.1 Prevent Invalid Data

CHECK and NOT NULL constraints reduce the chance of invalid records entering the database.

### 13.2 Prevent Duplicate Accounts

UNIQUE constraints can prevent duplicate usernames or email addresses.

### 13.3 Maintain Relationships

Foreign keys help prevent inconsistent references between related tables.

### 13.4 Avoid Dangerous Cascading Deletes

An incorrectly configured `ON DELETE CASCADE` may remove large amounts of related data.

Review relationships carefully before enabling cascading behavior.

### 13.5 Validate at Multiple Layers

Use both:

- Application-level validation for clear user feedback.
    
- Database constraints for reliable enforcement.
    

Application validation alone is insufficient because data may enter through scripts, APIs, or other applications.

## 14. Practical Lab — SQL Constraints

**Objective:** Create tables using different constraints and observe how they affect database operations.

Use your `sql_practice` database.

### Step 1: Create a Departments Table

```
CREATE TABLE departments (
    department_id INTEGER PRIMARY KEY,
    department_name VARCHAR(50) UNIQUE NOT NULL
);
```

### Step 2: Insert Departments

```
INSERT INTO departments
VALUES
(1, 'Cybersecurity'),
(2, 'Computer Science');
```

### Step 3: Create an Employees Table

```
CREATE TABLE employees (
    employee_id INTEGER PRIMARY KEY,
    employee_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    age INTEGER CHECK (age >= 18),
    status VARCHAR(20) DEFAULT 'active',
    department_id INTEGER,
    FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
);
```

### Step 4: Insert a Valid Employee

```
INSERT INTO employees (
    employee_id,
    employee_name,
    email,
    age,
    department_id
)
VALUES (
    1,
    'Mohit',
    'mohit@example.com',
    18,
    1
);
```

### Step 5: Test UNIQUE

Try inserting another employee with the same email.

```
INSERT INTO employees (
    employee_id,
    employee_name,
    email,
    age,
    department_id
)
VALUES (
    2,
    'Rahul',
    'mohit@example.com',
    20,
    2
);
```

The database should reject the duplicate email.

### Step 6: Test NOT NULL

```
INSERT INTO employees (
    employee_id,
    employee_name,
    email,
    age,
    department_id
)
VALUES (
    3,
    NULL,
    'aman@example.com',
    20,
    1
);
```

The database should reject the missing employee name.

### Step 7: Test CHECK

```
INSERT INTO employees (
    employee_id,
    employee_name,
    email,
    age,
    department_id
)
VALUES (
    4,
    'Aman',
    'aman@example.com',
    15,
    1
);
```

The database should reject the age because it violates the CHECK condition.

### Step 8: Test FOREIGN KEY

```
INSERT INTO employees (
    employee_id,
    employee_name,
    email,
    age,
    department_id
)
VALUES (
    5,
    'Priya',
    'priya@example.com',
    21,
    99
);
```

The database should reject the department reference if department ID 99 does not exist.

### Step 9: Verify Valid Records

```
SELECT * FROM employees;
```

### Lab Observations

Record these questions in your notebook:

1. What happens when a duplicate email is inserted?
    
2. What happens when a required name is NULL?
    
3. How does CHECK prevent invalid values?
    
4. Why does a foreign key reject an unknown department ID?
    
5. What is the difference between PRIMARY KEY and UNIQUE?
    

## 15. Key Takeaways

- Constraints enforce rules on database data.
    
- PRIMARY KEY uniquely identifies records.
    
- FOREIGN KEY maintains relationships.
    
- UNIQUE prevents duplicate values.
    
- NOT NULL prevents missing values.
    
- CHECK enforces specified conditions.
    
- DEFAULT supplies a value when one is omitted.
    
- Constraints help maintain database integrity.
    
- Application validation should be supported by database-level constraints.
    

## 16. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[DDL - Data Definition Language]]
    
- [[DML - Data Manipulation Language]]
    
- [[DQL - Data Query Language]]
    
- [[DCL - Data Control Language]]
    
- [[TCL - Transaction Control Language]]
    
- [[SQL Joins]]
    
- [[SQL Injection Prevention]]
    
- [[SQL Practical Labs]]