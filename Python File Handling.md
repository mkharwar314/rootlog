## 1. Introduction

File handling is the process of creating, opening, reading, writing, updating, and deleting files using a programming language.

Python provides built-in functions and methods to work with files.

File handling is important because programs often need to store information permanently instead of keeping it only in memory.

### Example

```
file = open("notes.txt", "w")

file.write("Welcome to ROOTLOG")

file.close()
```

This creates a file named `notes.txt` and writes text into it.

## 2. Why Is File Handling Important?

File handling allows programmers to:

1. Store information permanently.
    
2. Read existing data.
    
3. Create new files.
    
4. Update stored information.
    
5. Process large amounts of data.
    
6. Generate reports.
    
7. Analyze logs and system records.
    

In cybersecurity, file handling is used for:

- Reading system logs.
    
- Analyzing security reports.
    
- Processing configuration files.
    
- Calculating file hashes.
    
- Creating audit reports.
    
- Monitoring file changes.
    

## 3. Types of Files

Files are broadly classified into two categories.

### A. Text Files

Text files store information as readable characters.

Examples:

- `.txt`
    
- `.csv`
    
- `.json`
    
- `.log`
    
- `.py`
    
- `.md`
    

Example content:

```
LOGIN_SUCCESS
LOGIN_FAILED
FILE_ACCESS
```

### B. Binary Files

Binary files store information as bytes.

Examples:

- `.exe`
    
- `.jpg`
    
- `.png`
    
- `.pdf`
    
- `.zip`
    

Binary files are generally not intended to be read directly as ordinary text.

Python uses binary modes to work with them.

## 4. Opening Files

Python uses the built-in `open()` function to open files.

### Syntax

```
file = open("filename.txt", "mode")
```

Parameters:

|Parameter|Meaning|
|---|---|
|Filename|Name or path of the file|
|Mode|Specifies how the file will be accessed|

Example:

```
file = open("sample.txt", "r")
```

This opens `sample.txt` in read mode.

If the file does not exist, Python raises `FileNotFoundError`.

## 5. File Opening Modes

Python provides several file modes.

|Mode|Meaning|
|---|---|
|`r`|Read an existing file|
|`w`|Write; creates or truncates a file|
|`a`|Append data to the end|
|`x`|Create a new file; fails if it exists|
|`b`|Binary mode modifier|
|`t`|Text mode modifier|
|`r+`|Read and write without truncating|
|`w+`|Read and write; truncates or creates|
|`a+`|Read and append; creates if needed|

### Example: Read Mode

```
file = open("sample.txt", "r")
```

### Example: Write Mode

```
file = open("sample.txt", "w")

file.write("Python File Handling")

file.close()
```

Warning: `w` mode deletes the existing contents before writing.

### Example: Append Mode

```
file = open("sample.txt", "a")

file.write("\nLearning Cybersecurity")

file.close()
```

Append mode adds content to the end of the file.

## 6. Closing Files

After working with a file, it should be closed.

```
file = open("sample.txt", "r")

content = file.read()

print(content)

file.close()
```

Closing a file releases the associated resources and ensures pending operations are properly finalized.

However, manually closing files can be forgotten when an error occurs.

Python provides a safer approach called a context manager.

## 7. Using the `with` Statement

The `with` statement automatically closes a file when the block finishes, including when an exception occurs.

Example:

```
with open("sample.txt", "r") as file:

    content = file.read()

    print(content)
```

This is the recommended approach for ordinary file operations.

Advantages:

- Automatically closes files.
    
- Reduces resource-management errors.
    
- Makes code cleaner.
    
- Handles exceptions more safely.
    

Prefer `with open(...)` over manually calling `close()` in most situations.

## 8. Reading Files

Python provides several methods for reading file contents.

### A. `read()`

Reads the entire file or a specified number of characters.

```
with open("sample.txt", "r") as file:

    content = file.read()

    print(content)
```

### B. `readline()`

Reads one line at a time.

```
with open("sample.txt", "r") as file:

    first_line = file.readline()

    print(first_line)
```

### C. `readlines()`

Reads all lines and returns them as a list.

```
with open("sample.txt", "r") as file:

    lines = file.readlines()

    print(lines)
```

Comparison:

|Method|Purpose|
|---|---|
|`read()`|Reads all or part of the file|
|`readline()`|Reads one line|
|`readlines()`|Returns all lines as a list|

### Reading Large Files

For large files, reading everything into memory may be inefficient.

Use a loop to process one line at a time.

```
with open("large.log", "r") as file:

    for line in file:
        print(line.strip())
```

This approach is useful when analyzing large log files.

## 9. Writing to Files

The `write()` method writes a string into a file.

Example:

```
with open("report.txt", "w") as file:

    file.write("ROOTLOG Security Report")
```

### Writing Multiple Lines

```
with open("report.txt", "w") as file:

    file.write("Security Report\n")
    file.write("Total Events: 10\n")
    file.write("Status: Complete\n")
```

The `\n` character creates a new line.

### Using `writelines()`

The `writelines()` method writes multiple strings from an iterable.

```
lines = [
    "LOGIN_SUCCESS\n",
    "LOGIN_FAILED\n",
    "FILE_ACCESS\n"
]

with open("events.txt", "w") as file:

    file.writelines(lines)
```

Note: `writelines()` does not automatically add newline characters.

## 10. Appending Data

Append mode adds new information without removing existing contents.

Example:

```
with open("events.txt", "a") as file:

    file.write("LOGIN_FAILED\n")
```

This is useful when adding new events to a log or report.

However, real system logs should be collected and handled using appropriate permissions and logging mechanisms. Do not modify evidence logs during forensic investigations.

## 11. File Position and Seeking

Python maintains a file position that determines where the next read or write occurs.

Two useful methods are:

- `tell()` — returns the current position.
    
- `seek()` — changes the current position.
    

Example:

```
with open("sample.txt", "r") as file:

    print(file.tell())

    content = file.read(5)

    print(content)

    print(file.tell())

    file.seek(0)

    print(file.read())
```

`seek(0)` moves the position to the beginning of the file.

File positions can behave differently in text and binary modes, so avoid assuming every offset represents a number of characters.

## 12. Working With File Paths

A file path identifies the location of a file.

### Relative Path

A relative path is interpreted from the program's current working directory.

```
with open("sample.txt", "r") as file:
    print(file.read())
```

### Absolute Path

An absolute path specifies the complete file location.

Windows example:

```
path = r"C:\Users\Student\Documents\sample.txt"
```

Linux example:

```
path = "/home/student/sample.txt"
```

### Using `pathlib`

Python provides the `pathlib` module for working with paths.

```
from pathlib import Path

file_path = Path("sample.txt")

print(file_path.exists())
print(file_path.name)
print(file_path.suffix)
```

`pathlib` makes path handling more readable and portable.

## 13. Checking Whether a File Exists

The `exists()` method checks whether a path exists.

Example:

```
from pathlib import Path

file_path = Path("sample.txt")

if file_path.exists():
    print("File exists")
else:
    print("File does not exist")
```

You can also check whether the path is specifically a file.

```
if file_path.is_file():
    print("It is a file")
```

## 14. Deleting Files

Python provides the `unlink()` method through `pathlib` to remove files.

Example:

```
from pathlib import Path

file_path = Path("old.txt")

if file_path.is_file():
    file_path.unlink()
    print("File deleted")
```

Warning: File deletion may be irreversible. Always verify the target path before deleting anything.

Do not run deletion scripts against important directories or system files.

## 15. Handling File Exceptions

File operations can fail for several reasons.

Common exceptions include:

|Exception|Meaning|
|---|---|
|`FileNotFoundError`|File does not exist|
|`PermissionError`|Insufficient permissions|
|`IsADirectoryError`|A directory was used where a file was expected|
|`UnicodeDecodeError`|Data cannot be decoded using the selected encoding|
|`OSError`|General operating-system-related file error|

### Example

```
try:

    with open("sample.txt", "r", encoding="utf-8") as file:

        content = file.read()

        print(content)

except FileNotFoundError:
    print("File not found")

except PermissionError:
    print("Permission denied")

except UnicodeDecodeError:
    print("Unable to decode file")
```

Exception handling prevents expected file errors from terminating a program unexpectedly.

## 16. Working With Encoding

Text files use character encodings to represent text.

UTF-8 is a widely used encoding.

Example:

```
with open("notes.txt", "w", encoding="utf-8") as file:

    file.write("Learning Python – ROOTLOG")
```

Reading:

```
with open("notes.txt", "r", encoding="utf-8") as file:

    print(file.read())
```

Specifying an encoding helps avoid inconsistent text handling across systems.

## 17. Working With CSV Files

CSV stands for Comma-Separated Values.

It is commonly used to store tabular data.

Python provides the built-in `csv` module.

### Example CSV File

```
username,role,status
student,analyst,active
admin,administrator,active
guest,user,inactive
```

### Reading CSV Files

```
import csv

with open("users.csv", "r", newline="", encoding="utf-8") as file:

    reader = csv.DictReader(file)

    for row in reader:
        print(row["username"], row["role"])
```

`DictReader` represents each row as a dictionary.

### Writing CSV Files

```
import csv

with open("users.csv", "w", newline="", encoding="utf-8") as file:

    writer = csv.writer(file)

    writer.writerow(["username", "role"])

    writer.writerow(["student", "analyst"])
    writer.writerow(["admin", "administrator"])
```

The `csv` module handles quoting and delimiters more reliably than manually joining strings.

## 18. Working With JSON Files

JSON stands for JavaScript Object Notation.

It is commonly used for configuration files, APIs, and structured data exchange.

Python provides the built-in `json` module.

### Example JSON Data

```
{
    "username": "student",
    "role": "analyst",
    "active": true
}
```

### Reading JSON

```
import json

with open("user.json", "r", encoding="utf-8") as file:

    data = json.load(file)

    print(data["username"])
```

### Writing JSON

```
import json

user = {
    "username": "student",
    "role": "analyst",
    "active": True
}

with open("user.json", "w", encoding="utf-8") as file:

    json.dump(user, file, indent=4)
```

`json.load()` reads JSON from a file, while `json.dump()` writes JSON to a file.

Detailed topic: [[JSON]]

## 19. Binary File Handling

Binary files contain bytes rather than ordinary text.

Python uses the `b` mode modifier.

### Reading Binary Files

```
with open("image.png", "rb") as file:

    data = file.read()

    print(data[:20])
```

### Writing Binary Files

```
data = b"ROOTLOG"

with open("sample.bin", "wb") as file:

    file.write(data)
```

Binary file handling is useful for:

- File analysis.
    
- Digital forensics.
    
- File integrity verification.
    
- Processing images and documents.
    
- Investigating suspicious files.
    

## 20. File Handling in Cybersecurity

File handling is important in many security operations.

### A. Reading Security Logs

```
with open("security.log", "r", encoding="utf-8") as file:

    for line in file:

        if "FAILED" in line:
            print(line.strip())
```

This example searches for failed events in a sample log.

### B. Calculating File Hashes

A cryptographic hash can help verify whether file contents have changed.

```
import hashlib

def calculate_sha256(file_path):

    sha256 = hashlib.sha256()

    with open(file_path, "rb") as file:

        for chunk in iter(lambda: file.read(4096), b""):
            sha256.update(chunk)

    return sha256.hexdigest()


print(calculate_sha256("sample.txt"))
```

This reads the file in chunks instead of loading the entire file into memory.

### C. Creating a Security Report

```
events = [
    "LOGIN_SUCCESS",
    "LOGIN_FAILED",
    "LOGIN_FAILED"
]

failed_count = events.count("LOGIN_FAILED")

with open("security_report.txt", "w", encoding="utf-8") as file:

    file.write("ROOTLOG Security Report\n")
    file.write(f"Total Events: {len(events)}\n")
    file.write(f"Failed Logins: {failed_count}\n")

print("Report generated")
```

### D. Checking File Integrity

A file's hash can be calculated at different times and compared.

If the hashes differ, the file contents differ, assuming the same hash algorithm and correct calculation.

A matching hash provides strong evidence of unchanged contents, but it does not establish who created the file or whether it was trustworthy initially.

## 21. Secure File Handling Practices

File handling can introduce security vulnerabilities when implemented carelessly.

Follow these practices:

1. Validate file paths before accessing them.
    
2. Avoid blindly trusting user-supplied filenames.
    
3. Use appropriate file permissions.
    
4. Avoid overwriting important files unintentionally.
    
5. Use context managers to manage files.
    
6. Specify text encodings explicitly.
    
7. Avoid opening untrusted files with unsafe processing tools.
    
8. Limit file size when processing untrusted input.
    
9. Handle exceptions carefully.
    
10. Avoid exposing sensitive file contents in error messages.
    

### Path Traversal

Path traversal occurs when an attacker manipulates a file path to access files outside an intended directory.

Example of a dangerous user-controlled path:

```
../../sensitive.txt
```

A simple approach for restricting access to a directory is to resolve the path and verify that it remains inside the intended directory.

```
from pathlib import Path

base_directory = Path("uploads").resolve()

filename = "report.txt"

target = (base_directory / filename).resolve()

if target.is_relative_to(base_directory):
    print("Path is inside the upload directory")
else:
    print("Invalid path")
```

This example assumes a trusted base directory and a fixed filename. Applications accepting untrusted filenames must also consider symbolic links, race conditions, file permissions, and platform-specific behavior.

## 22. Practical Exercises

### Exercise 1: Create a File

Create a file named `rootlog.txt`.

Write:

```
Welcome to ROOTLOG
Learning Python File Handling
```

Read the file and display its contents.

### Exercise 2: Append Data

Append the following line:

```
Cybersecurity Learning Journey
```

Read the file again and verify that the original contents remain.

### Exercise 3: Count Lines

Create a program that reads a text file and counts its total number of lines.

### Exercise 4: Search Logs

Create a sample log file containing:

```
LOGIN_SUCCESS
LOGIN_FAILED
FILE_ACCESS
LOGIN_FAILED
LOGIN_SUCCESS
```

Write a Python program that displays only lines containing `LOGIN_FAILED`.

### Exercise 5: Calculate SHA-256

Write a program that calculates the SHA-256 hash of a file.

Test it with a text file that you created.

Change one character in the file and calculate the hash again.

Compare both hashes.

### Exercise 6: CSV User Records

Create a CSV file containing three users.

Include:

- Username
    
- Role
    
- Account status
    

Read the CSV file using `csv.DictReader`.

### Exercise 7: JSON User Records

Create a JSON file containing information about a cybersecurity student.

Read the JSON file and display the username and course.

## 23. Key Takeaways

- File handling allows programs to store and retrieve information.
    
- Python uses `open()` to open files.
    
- File modes determine how files are accessed.
    
- `read()`, `readline()`, and `readlines()` read file contents.
    
- `write()` and `writelines()` write information.
    
- Append mode adds information without truncating existing contents.
    
- The `with` statement automatically manages file closure.
    
- `pathlib` helps manage file paths.
    
- Python supports text and binary files.
    
- The `csv` and `json` modules handle structured data.
    
- File handling is important for cybersecurity and digital forensics.
    
- Secure file handling requires path validation, permissions, and careful error handling.
    

## 24. Related Topics

- [[Introduction to Python]]
    
- [[Python Syntax]]
    
- [[Python Functions]]
    
- [[Python Data Structures]]
    
- [[Python Exception Handling]]
    
- [[Python Modules]]
    
- [[JSON]]
    
- [[Log Analysis with Python]]
    
- [[File Integrity Monitoring]]
    
- [[Digital Forensics]]
    
- [[Python for Cybersecurity]]