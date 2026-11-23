> Understand how programs create, read, write, append, modify, and manage files stored on a computer.

## 1. Introduction to File Handling

File Handling is the process of interacting with files through a programming language.

Programs use file handling to store and retrieve information permanently.

Examples:

- Saving user information.
    
- Reading configuration files.
    
- Creating log files.
    
- Storing application data.
    
- Processing cybersecurity investigation evidence.
    
- Reading network and system logs.
    

Unlike ordinary variables, which generally exist only while a program is running, files allow information to remain available after the program terminates.

## 2. Why File Handling Is Important

File handling is useful for:

|Purpose|Example|
|---|---|
|Data Storage|Save student records|
|Data Retrieval|Read saved information|
|Logging|Store application events|
|Configuration|Read application settings|
|Automation|Process multiple files|
|Digital Forensics|Examine evidence files|
|Security Monitoring|Analyze system logs|

## 3. Types of Files

Files are commonly classified into two major categories.

### 1. Text Files

Text files store information as readable characters.

Examples:

- `.txt`
    
- `.csv`
    
- `.json`
    
- `.xml`
    
- `.log`
    
- `.md`
    

Example:

```
Username: student
Course: Cybersecurity
Status: Active
```

### 2. Binary Files

Binary files store data as bytes rather than ordinary human-readable text.

Examples:

- `.jpg`
    
- `.png`
    
- `.pdf`
    
- `.exe`
    
- `.zip`
    
- `.mp3`
    

Binary files usually require appropriate software or libraries to interpret their contents.

## 4. Basic File Operations

Common file operations include:

|Operation|Description|
|---|---|
|Create|Create a new file|
|Open|Open an existing file|
|Read|Retrieve file contents|
|Write|Write data to a file|
|Append|Add data to the end|
|Close|Close an opened file|
|Delete|Remove a file|
|Rename|Change a filename|

## 5. File Handling in Python

Python provides built-in functions and methods for file operations.

The `open()` function is used to open files.

### Basic Syntax

```
file = open("example.txt", "r")
```

The syntax contains:

- Filename.
    
- File mode.
    

It returns a file object.

A file should be closed after use, or preferably managed using a `with` statement.

## 6. File Opening Modes

Python supports different file modes.

|Mode|Meaning|
|---|---|
|`r`|Read an existing file|
|`w`|Write; creates or truncates a file|
|`a`|Append; creates the file if necessary|
|`x`|Create a new file; fails if it already exists|
|`b`|Binary mode|
|`t`|Text mode|
|`r+`|Read and write without initially truncating|

Examples:

```
open("data.txt", "r")
open("data.txt", "w")
open("data.txt", "a")
open("image.png", "rb")
```

**Important:** Opening a file using `w` mode deletes its existing contents before writing new data.

## 7. Reading Files

Python provides multiple methods to read file contents.

### Using read()

```
with open("data.txt", "r") as file:
    content = file.read()
    print(content)
```

`read()` retrieves the file contents as a string in text mode.

### Using readline()

```
with open("data.txt", "r") as file:
    line = file.readline()
    print(line)
```

`readline()` reads one line.

### Using readlines()

```
with open("data.txt", "r") as file:
    lines = file.readlines()
    print(lines)
```

`readlines()` returns a list containing the lines.

### Reading Line by Line

```
with open("data.txt", "r") as file:
    for line in file:
        print(line.strip())
```

This approach is generally preferable for large text files because it avoids loading the entire file into memory.

## 8. Writing Files

The `write()` method writes data into a file.

```
with open("data.txt", "w") as file:
    file.write("Welcome to ROOTLOG")
```

If the file already exists, its previous contents are replaced.

### Writing Multiple Lines

```
lines = [
    "Cybersecurity\n",
    "Networking\n",
    "Digital Forensics\n"
]

with open("subjects.txt", "w") as file:
    file.writelines(lines)
```

`writelines()` does not automatically insert newline characters. Include them when required.

## 9. Appending Data

Append mode adds new content to the end of an existing file.

```
with open("data.txt", "a") as file:
    file.write("\nLearning Python File Handling")
```

Unlike write mode, append mode does not initially erase existing contents.

Common uses:

- Application logs.
    
- Activity records.
    
- Event tracking.
    
- Continuous data collection.
    

## 10. The with Statement

Python provides the `with` statement to manage files safely.

Example:

```
with open("data.txt", "r") as file:
    content = file.read()
    print(content)
```

Advantages:

- Automatically closes the file.
    
- Reduces resource-management errors.
    
- Improves readability.
    
- Helps prevent accidental file-handle leaks.
    

This is the recommended approach for ordinary file handling.

## 11. Working with File Paths

A file path identifies the location of a file.

Two common path types exist.

### Absolute Path

An absolute path specifies the complete location.

Windows example:

```
C:\Users\Student\Documents\data.txt
```

Linux example:

```
/home/student/data.txt
```

### Relative Path

A relative path specifies a location relative to the current working directory.

Example:

```
data.txt
```

Python can inspect the current working directory:

```
import os

print(os.getcwd())
```

It can also check whether a file exists:

```
import os

if os.path.exists("data.txt"):
    print("File exists")
else:
    print("File not found")
```

## 12. File and Directory Operations

Python provides the `os` module for interacting with the operating system.

### Rename a File

```
import os

os.rename("old.txt", "new.txt")
```

### Delete a File

```
import os

os.remove("new.txt")
```

### Create a Directory

```
import os

os.mkdir("reports")
```

### List Directory Contents

```
import os

files = os.listdir(".")

print(files)
```

**Caution:** File deletion and renaming operations can cause data loss. Verify the target path before executing them.

## 13. Working with Binary Files

Binary files should be opened using binary modes.

Example:

```
with open("source.jpg", "rb") as source:
    content = source.read()

with open("copy.jpg", "wb") as destination:
    destination.write(content)
```

This copies the file's bytes without interpreting them as text.

Binary file handling is useful for:

- Images.
    
- Executables.
    
- Archives.
    
- Forensic evidence.
    
- Network captures.
    

## 14. File Handling with CSV

CSV stands for Comma-Separated Values.

It is commonly used for structured tabular data.

Python provides the built-in `csv` module.

### Reading CSV

```
import csv

with open("students.csv", "r", newline="") as file:
    reader = csv.reader(file)

    for row in reader:
        print(row)
```

### Writing CSV

```
import csv

with open("students.csv", "w", newline="") as file:
    writer = csv.writer(file)

    writer.writerow(["Name", "Course"])
    writer.writerow(["Rahul", "Cybersecurity"])
    writer.writerow(["Aman", "Networking"])
```

CSV files are useful for storing records and exporting analysis results.

## 15. File Handling with JSON

JSON stands for JavaScript Object Notation.

It is a lightweight format used for storing and exchanging structured data.

Python provides the built-in `json` module.

### Writing JSON

```
import json

data = {
    "name": "Rahul",
    "course": "Cybersecurity",
    "year": 1
}

with open("student.json", "w") as file:
    json.dump(data, file, indent=4)
```

### Reading JSON

```
import json

with open("student.json", "r") as file:
    data = json.load(file)

print(data["name"])
```

JSON is commonly used in:

- Web APIs.
    
- Application configuration.
    
- Data exchange.
    
- Security tools.
    

## 16. Exception Handling in File Operations

File operations can fail for different reasons.

Examples:

- File does not exist.
    
- Permission is denied.
    
- Disk is full.
    
- File is locked.
    
- Invalid path is provided.
    

Python supports exception handling.

Example:

```
try:
    with open("data.txt", "r") as file:
        content = file.read()
        print(content)

except FileNotFoundError:
    print("File does not exist")

except PermissionError:
    print("Permission denied")

except OSError as error:
    print("File operation failed:", error)
```

Handling exceptions prevents unexpected file errors from terminating an application without proper handling.

## 17. File Handling in Cybersecurity

File handling is an important programming skill in cybersecurity.

### 1. Log Analysis

Security analysts read log files to identify suspicious activity.

### 2. File Integrity Monitoring

Programs calculate file hashes to detect unexpected changes.

### 3. Digital Forensics

Investigators examine files as potential evidence.

### 4. Malware Analysis

Analysts inspect suspicious files in controlled environments.

### 5. Automation

Scripts process large numbers of files and organize investigation results.

### 6. Configuration Auditing

Programs inspect configuration files for insecure settings.

## 18. File Security Best Practices

Follow these practices when developing file-processing applications:

- Validate file paths.
    
- Avoid trusting filenames supplied by users.
    
- Apply appropriate file permissions.
    
- Avoid executing untrusted files.
    
- Restrict access to sensitive files.
    
- Validate file formats and sizes.
    
- Handle errors securely.
    
- Avoid overwriting important files unintentionally.
    
- Keep backups of important information.
    
- Use hashes when integrity verification is required.
    

### Path Traversal

Path traversal is a vulnerability in which an attacker manipulates a file path to access files outside the intended directory.

For example, an application that accepts arbitrary user-supplied paths may unintentionally allow access to sensitive files.

Applications should resolve and validate paths against an explicitly permitted base directory.

## 19. Practical Lab

**Objective:** Build a simple Python file manager.

### Step 1 — Create a file

```
with open("rootlog.txt", "w") as file:
    file.write("ROOTLOG - Cybersecurity Knowledge Base\n")
    file.write("Learning Python File Handling\n")
```

### Step 2 — Read the file

```
with open("rootlog.txt", "r") as file:
    print(file.read())
```

### Step 3 — Append new content

```
with open("rootlog.txt", "a") as file:
    file.write("Learning Cybersecurity\n")
```

### Step 4 — Check file existence

```
import os

print(os.path.exists("rootlog.txt"))
```

### Step 5 — Calculate SHA-256

```
import hashlib

with open("rootlog.txt", "rb") as file:
    content = file.read()

file_hash = hashlib.sha256(content).hexdigest()

print("SHA-256:", file_hash)
```

This demonstrates a basic file-integrity verification technique.

### Step 6 — Record observations

Write down:

1. What happened when you used `w` mode?
    
2. What changed after using `a` mode?
    
3. Why did you open the file in binary mode for hashing?
    
4. What does SHA-256 help verify?
    

## 20. Key Takeaways

- File handling allows programs to store and retrieve persistent data.
    
- Text and binary files require different handling approaches.
    
- Python uses `open()` to access files.
    
- Common modes include `r`, `w`, `a`, and `x`.
    
- The `with` statement manages file resources safely.
    
- CSV and JSON support structured data handling.
    
- Exception handling manages file-related errors.
    
- File handling is essential for cybersecurity automation, log analysis, and digital forensics.
    

## 21. Related Topics

- [[Introduction to Python]]
    
- [[Python File Handling]]
    
- [[Python Exception Handling]]
    
- [[Python Modules]]
    
- [[JSON]]
    
- [[Log Analysis with Python]]
    
- [[File Integrity Monitoring]]
    
- [[Digital Forensics]]
    
- [[Programming Fundamentals Labs]]