> Understand how SQL defines, stores, and handles different types of information inside database columns.

## 1. Introduction to SQL Data Types

A **SQL data type** defines the kind of value that a database column can store.

For example:

- Names are stored as text.
    
- Ages are stored as integers.
    
- Prices are stored as decimal numbers.
    
- Dates are stored using date-related types.
    
- True or false values use Boolean types where supported.
    

Data types help databases:

- Store information correctly.
    
- Validate input.
    
- Use storage efficiently.
    
- Perform calculations.
    
- Maintain data integrity.
    

## 2. Why Are Data Types Important?

Consider a student database.

|Column|Example Value|Suitable Type|
|---|---|---|
|student_id|101|INT|
|name|Mohit|VARCHAR|
|age|19|INT|
|percentage|85.75|DECIMAL|
|admission_date|2026-06-15|DATE|
|active|TRUE|BOOLEAN|

Choosing suitable data types prevents incorrect data storage and improves database design.

## 3. Numeric Data Types

Numeric types store numbers.

### 1. INT / INTEGER

Stores whole numbers.

Example:

```
CREATE TABLE students (
    student_id INT,
    age INT
);
```

Sample values:

```
101
18
25
```

### 2. SMALLINT

Stores smaller-range integer values than a typical INT.

Useful when the expected values fit within its supported range.

### 3. BIGINT

Stores large integer values.

Useful for:

- Large transaction identifiers.
    
- High-volume record counts.
    
- Large numeric identifiers.
    

### 4. DECIMAL / NUMERIC

Stores exact decimal values using specified precision and scale.

Syntax:

```
DECIMAL(precision, scale)
```

Example:

```
CREATE TABLE products (
    price DECIMAL(10,2)
);
```

This allows up to 10 total digits, with 2 digits after the decimal point.

Example value:

```
1250.75
```

Use DECIMAL for financial values where exact decimal representation matters.

### 5. FLOAT and REAL

Store approximate floating-point numbers.

Useful for scientific calculations and measurements where approximate precision is acceptable.

Avoid using approximate floating-point types for exact financial calculations.

## 4. Character and String Data Types

String types store text.

### 1. CHAR

Stores fixed-length character data.

Example:

```
country_code CHAR(2);
```

Example value:

```
IN
```

### 2. VARCHAR

Stores variable-length character data up to a defined maximum.

Example:

```
name VARCHAR(100);
```

This allows names containing up to 100 characters.

### 3. TEXT

Stores larger amounts of text.

Useful for:

- Descriptions.
    
- Articles.
    
- Comments.
    
- Long messages.
    

The maximum supported size and behavior depend on the database system.

### Comparison

|Type|Description|
|---|---|
|CHAR|Fixed-length character type|
|VARCHAR|Variable-length character type|
|TEXT|Large text storage type|

## 5. Date and Time Data Types

Date and time types store temporal information.

### 1. DATE

Stores a calendar date.

Example:

```
birth_date DATE;
```

Example value:

```
2007-08-15
```

### 2. TIME

Stores a time of day.

Example:

```
login_time TIME;
```

Example value:

```
09:30:00
```

### 3. DATETIME

Stores both date and time in database systems that support this type.

Example:

```
2026-11-23 09:30:00
```

### 4. TIMESTAMP

Stores a timestamp representing a date and time.

Its exact behavior, including time-zone handling and automatic updates, differs between database systems.

### 5. YEAR

Some database systems, such as MySQL, provide a YEAR type.

It is not a universal SQL data type.

## 6. Boolean Data Type

A Boolean represents a logical value:

- TRUE
    
- FALSE
    

Example:

```
CREATE TABLE accounts (
    account_id INT,
    is_active BOOLEAN
);
```

Some database systems implement Boolean values differently.

For example, MySQL supports `BOOLEAN` as a synonym for `TINYINT(1)`.

## 7. Binary Data Types

Binary types store raw bytes instead of ordinary text.

Examples include:

- BINARY
    
- VARBINARY
    
- BLOB
    

### BINARY

Stores fixed-length binary data.

### VARBINARY

Stores variable-length binary data.

### BLOB

Stores binary large objects.

Possible uses:

- Images.
    
- Documents.
    
- Audio.
    
- Other binary files.
    

However, many applications store large files in object or file storage systems and keep references to them in the database.

## 8. JSON Data Type

Some database systems support a JSON data type for storing structured JSON documents.

Example:

```
CREATE TABLE user_profiles (
    user_id INT,
    profile JSON
);
```

Example JSON value:

```
{
    "name": "Mohit",
    "role": "Cybersecurity Student",
    "skills": ["Linux", "Python", "Networking"]
}
```

JSON support and available operations differ between database systems.

## 9. Choosing the Correct Data Type

Consider the following table:

```
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    age SMALLINT,
    salary DECIMAL(10,2),
    joining_date DATE,
    is_active BOOLEAN
);
```

Explanation:

|Column|Data Type|Reason|
|---|---|---|
|employee_id|INT|Whole-number identifier|
|name|VARCHAR(100)|Variable-length text|
|age|SMALLINT|Small whole number|
|salary|DECIMAL(10,2)|Exact decimal amount|
|joining_date|DATE|Calendar date|
|is_active|BOOLEAN|Logical state|

Data type selection should consider expected values, constraints, precision, database compatibility, and future requirements.

## 10. NULL Values

`NULL` represents a missing, unknown, or unavailable value.

It is not the same as:

- Zero.
    
- An empty string.
    
- FALSE.
    
- A normal text value.
    

Example:

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    phone VARCHAR(20)
);
```

A student may have no recorded phone number.

```
INSERT INTO students
VALUES (101, 'Mohit', NULL);
```

### Checking NULL Values

Use `IS NULL`:

```
SELECT *
FROM students
WHERE phone IS NULL;
```

Use `IS NOT NULL`:

```
SELECT *
FROM students
WHERE phone IS NOT NULL;
```

Do not use:

```
WHERE phone = NULL;
```

SQL uses three-valued logic, so comparisons involving NULL generally produce UNKNOWN rather than TRUE or FALSE.

## 11. SQL Data Type Security Considerations

Data types are also important for database security and application reliability.

### 1. Input Validation

Validate incoming values before inserting them into a database.

Example:

- Age should be within an acceptable range.
    
- Email should follow the application's expected format.
    
- Identifiers should have the expected structure.
    

### 2. Avoid Unsafe Conversions

Unexpected type conversions can cause incorrect results or application errors.

### 3. Use Appropriate Precision

Use DECIMAL for exact financial values instead of relying on approximate floating-point calculations.

### 4. Avoid Excessively Broad Fields

Choose sensible limits for text and binary fields.

### 5. Do Not Depend Only on Data Types

A data type does not replace application validation, authorization, or parameterized SQL queries.

## 12. Practical Lab

Create a table using different SQL data types.

```
CREATE TABLE student_records (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age SMALLINT,
    percentage DECIMAL(5,2),
    admission_date DATE,
    is_active BOOLEAN
);
```

Insert sample records:

```
INSERT INTO student_records
VALUES
(101, 'Mohit', 19, 85.75, '2026-06-15', TRUE),
(102, 'Rahul', 20, 78.50, '2026-06-16', FALSE);
```

Retrieve all records:

```
SELECT * FROM student_records;
```

Retrieve students with percentages above 80:

```
SELECT name, percentage
FROM student_records
WHERE percentage > 80;
```

## 13. Key Takeaways

- SQL data types define what values columns can store.
    
- INT stores whole numbers.
    
- DECIMAL stores exact decimal values.
    
- FLOAT stores approximate floating-point values.
    
- VARCHAR stores variable-length text.
    
- DATE and TIME store temporal information.
    
- BOOLEAN represents logical values where supported.
    
- BLOB stores binary data.
    
- JSON stores structured JSON data in supporting databases.
    
- NULL represents missing or unknown information.
    
- Correct data type selection improves data integrity and database design.
    

## 14. Related Topics

- [[Introduction to SQL]]
    
- [[Database Fundamentals]]
    
- [[Relational Databases]]
    
- [[SQL Commands]]
    
- [[SQL Constraints]]
    
- [[SQL Operators]]
    
- [[SQL Injection]]
    
- [[SQL Injection Prevention]]
    

## 15. My Understanding

Explain in your own words:

- What is a SQL data type?
    
- What is the difference between INT and BIGINT?
    
- What is the difference between CHAR and VARCHAR?
    
- Why is DECIMAL preferred for financial values?
    
- What is the difference between DATE and TIMESTAMP?
    
- What does NULL mean?
    
- Why should applications validate data?
    

## 16. Questions & Doubts

Record questions that need further research.