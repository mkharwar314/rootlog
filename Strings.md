> Understand how text is represented, stored, accessed, modified, and processed in programming languages.

## 1. What Is a String?

A **string** is a sequence of characters used to represent text.

Strings can contain:

- Letters
    
- Numbers
    
- Spaces
    
- Symbols
    
- Special characters
    

Examples:

```
name = "Mohit"
message = "Hello World"
password = "Cyber@123"
ip_address = "192.168.1.10"
```

All these values are strings because they are enclosed in quotation marks.

## 2. Creating Strings

Most programming languages support single or double quotation marks for creating strings.

### Python

```
name = "Mohit"
city = 'Mumbai'

print(name)
print(city)
```

Python also supports triple quotes for multiline strings.

```
message = """Welcome to
ROOTLOG
Cybersecurity Notes"""

print(message)
```

### C

C uses character arrays to represent strings.

```
#include <stdio.h>

int main() {
    char name[] = "Mohit";

    printf("%s\n", name);

    return 0;
}
```

C strings are null-terminated. The null character `\0` marks the end of the string.

### JavaScript

```
let name = "Mohit";
let city = 'Mumbai';

console.log(name);
console.log(city);
```

JavaScript also supports template literals using backticks.

```
let name = "Mohit";

console.log(`Hello, ${name}`);
```

## 3. String Indexing

Each character in a string has a position called an index.

Example:

```
text = "CYBER"
```

```
Character:  C   Y   B   E   R
Index:      0   1   2   3   4
```

Access a character using its index:

```
text = "CYBER"

print(text[0])
print(text[2])
print(text[4])
```

Output:

```
C
B
R
```

### Negative Indexing in Python

Python also supports negative indexes.

```
text = "CYBER"

print(text[-1])
print(text[-2])
```

Output:

```
R
E
```

`-1` refers to the last character.

## 4. String Slicing

String slicing extracts a portion of a string.

Syntax:

```
string[start:end]
```

The start index is included, but the end index is excluded.

Example:

```
text = "CYBERSECURITY"

print(text[0:5])
print(text[5:13])
```

Output:

```
CYBER
SECURITY
```

Other slicing examples:

```
text = "PROGRAMMING"

print(text[:4])
print(text[4:])
print(text[::2])
print(text[::-1])
```

- `[:4]` selects the beginning through index 3.
    
- `[4:]` selects from index 4 to the end.
    
- `[::2]` selects every second character.
    
- `[::-1]` reverses the string.
    

## 5. String Length

The `len()` function returns the number of characters in a Python string.

```
text = "CYBERSECURITY"

print(len(text))
```

Output:

```
13
```

Spaces and punctuation also count as characters.

```
message = "Hello World"

print(len(message))
```

Output:

```
11
```

## 6. String Concatenation

**Concatenation** means joining two or more strings.

```
first = "Cyber"
second = "Security"

result = first + second

print(result)
```

Output:

```
CyberSecurity
```

Add a space between words:

```
first = "Cyber"
second = "Security"

result = first + " " + second

print(result)
```

Output:

```
Cyber Security
```

## 7. String Repetition

Python allows strings to be repeated using the multiplication operator.

```
text = "Hi "

print(text * 3)
```

Output:

```
Hi Hi Hi
```

## 8. Common String Methods in Python

Python provides built-in string methods for processing text.

|Method|Purpose|
|---|---|
|`upper()`|Converts letters to uppercase|
|`lower()`|Converts letters to lowercase|
|`title()`|Capitalizes the first letter of each word|
|`capitalize()`|Capitalizes the first character|
|`strip()`|Removes leading and trailing whitespace|
|`replace()`|Replaces part of a string|
|`split()`|Splits a string into a list|
|`join()`|Joins strings from an iterable|
|`find()`|Finds the position of a substring|
|`count()`|Counts occurrences of a substring|
|`startswith()`|Checks the beginning of a string|
|`endswith()`|Checks the ending of a string|
|`isdigit()`|Checks whether characters are digits|

Examples:

### Uppercase and Lowercase

```
text = "Cybersecurity"

print(text.upper())
print(text.lower())
```

### Removing Whitespace

```
username = "  student  "

print(username.strip())
```

### Replacing Text

```
text = "I am learning programming"

print(text.replace("programming", "cybersecurity"))
```

### Splitting a String

```
data = "admin,user,guest"

users = data.split(",")

print(users)
```

Output:

```
['admin', 'user', 'guest']
```

### Joining Strings

```
users = ["admin", "user", "guest"]

result = ", ".join(users)

print(result)
```

Output:

```
admin, user, guest
```

## 9. String Immutability

In Python, strings are **immutable**.

Immutable means that an existing string cannot be modified character by character.

Example:

```
text = "HELLO"

text[0] = "Y"
```

This produces a `TypeError`.

To create a modified string, assign a new value:

```
text = "HELLO"

text = "Y" + text[1:]

print(text)
```

Output:

```
YELLO
```

The original string was not changed in place. A new string was created and assigned to `text`.

## 10. String Formatting

String formatting allows variables and values to be inserted into text.

### A. f-Strings in Python

```
name = "Mohit"
age = 18

message = f"My name is {name} and I am {age} years old."

print(message)
```

### B. format() Method

```
name = "Mohit"

message = "Hello, {}".format(name)

print(message)
```

### C. JavaScript Template Literals

```
let name = "Mohit";

let message = `Hello, ${name}`;

console.log(message);
```

String formatting is useful when generating reports, messages, and application output.

## 11. Escape Characters

Escape characters represent special characters inside strings.

|Escape Sequence|Meaning|
|---|---|
|`\n`|New line|
|`\t`|Tab|
|`\\`|Backslash|
|`\"`|Double quotation mark|
|`\'`|Single quotation mark|
|`\r`|Carriage return|
|`\0`|Null character|

Example:

```
message = "Hello\nCybersecurity"

print(message)
```

Output:

```
Hello
Cybersecurity
```

## 12. String Comparison

Strings can be compared using comparison operators.

```
first = "admin"
second = "user"

print(first == second)
print(first != second)
```

Output:

```
False
True
```

String comparisons are generally case-sensitive in Python.

```
print("Admin" == "admin")
```

Output:

```
False
```

For case-insensitive comparison:

```
first = "Admin"
second = "admin"

print(first.lower() == second.lower())
```

Output:

```
True
```

## 13. Strings and Character Encoding

Computers store text using numerical representations.

**Character encoding** defines how characters are represented as bytes.

Common concepts include:

- ASCII: A character encoding based on a limited set of characters.
    
- Unicode: A standard for representing characters from many writing systems.
    
- UTF-8: A widely used variable-length Unicode encoding.
    

Python strings represent Unicode text.

Convert a string into bytes:

```
text = "Cybersecurity"

data = text.encode("utf-8")

print(data)
```

Convert bytes back into a string:

```
data = b"Cybersecurity"

text = data.decode("utf-8")

print(text)
```

Encoding and decoding are important when working with files, network communication, and cryptographic operations.

## 14. String Processing in Cybersecurity

Strings are heavily used in cybersecurity tools and applications.

### A. Log Analysis

Security logs contain textual information about system activities.

Example:

```
log = "Failed login from 192.168.1.10"

if "Failed login" in log:
    print("Failed login event detected")
```

### B. Extracting IP Addresses

The `re` module supports pattern matching.

```
import re

log = "Connection from 192.168.1.10"

match = re.search(r"\b(?:\d{1,3}\.){3}\d{1,3}\b", log)

if match:
    print(match.group())
```

This pattern identifies an IPv4-like string. It does not validate whether every matched address is a valid IPv4 address.

### C. Username Validation

```
username = input("Enter username: ")

if username.isalnum():
    print("Contains only letters and numbers")
else:
    print("Contains other characters")
```

This is a basic character check, not a complete username validation policy.

### D. Password Length Check

```
password = input("Enter a test password: ")

if len(password) >= 12:
    print("Meets the minimum length check")
else:
    print("Too short")
```

This demonstrates length checking only. It does not establish whether a password is secure.

Never store or log real passwords in plain text.

### E. Processing HTTP Data

HTTP requests and responses contain textual components such as:

- Headers
    
- URLs
    
- Status messages
    
- JSON data
    
- Form values
    

String processing helps inspect and transform this information.

## 15. Secure String Handling

Improper string handling can introduce security vulnerabilities.

### A. SQL Injection

Unsafe example:

```
query = "SELECT * FROM users WHERE username = '" + username + "'"
```

Directly inserting untrusted input into an SQL query can allow SQL injection.

Use parameterized queries instead.

Example using SQLite:

```
import sqlite3

connection = sqlite3.connect(":memory:")

connection.execute(
    "CREATE TABLE users (username TEXT)"
)

username = input("Enter username: ")

connection.execute(
    "INSERT INTO users (username) VALUES (?)",
    (username,)
)

connection.commit()
connection.close()
```

The `?` placeholder keeps the user-provided value separate from the SQL command.

### B. Cross-Site Scripting (XSS)

Displaying untrusted text as HTML can allow attackers to inject executable content.

Applications should use context-appropriate output encoding and safe rendering methods.

### C. Input Validation

Validate input according to its expected format and purpose.

For example:

- Check whether a port is within the valid range.
    
- Validate an IP address using a proper networking library.
    
- Enforce username length limits.
    
- Reject unexpected input where appropriate.
    

### D. Sensitive Data Exposure

Avoid placing passwords, authentication tokens, and private information in logs or error messages.

## 16. Common String Errors

|Error|Explanation|
|---|---|
|Incorrect indexing|Accessing a position that does not exist|
|Incorrect slicing|Selecting the wrong range|
|Type mismatch|Combining strings and numbers incorrectly|
|Encoding errors|Incorrectly converting between text and bytes|
|Ignoring case sensitivity|Comparing text without considering capitalization|
|Unsafe concatenation|Building SQL queries with untrusted input|
|Forgetting immutability|Trying to modify a Python string in place|

## 17. Key Takeaways

- A string is a sequence of characters.
    
- Strings are used to represent textual information.
    
- String indexing commonly begins at zero.
    
- Slicing extracts a portion of a string.
    
- Concatenation joins multiple strings.
    
- Python strings are immutable.
    
- String methods help process and transform text.
    
- Character encoding converts text into bytes and back.
    
- Strings are important in log analysis, network communication, and security tools.
    
- Unsafe string handling can lead to vulnerabilities such as SQL injection and XSS.
    

## 18. Practical Tasks

### Task 1 — String Analysis

Create a Python program that accepts a string and displays:

1. Original text.
    
2. Uppercase version.
    
3. Lowercase version.
    
4. Total number of characters.
    
5. First character.
    
6. Last character.
    

### Task 2 — Username Checker

Write a program that:

1. Accepts a username.
    
2. Checks its length.
    
3. Checks whether it contains only letters and numbers.
    
4. Displays the result.
    

Use a simple validation rule of your choice and document it.

### Task 3 — Log Analyzer

Use this sample log:

```
Successful login from 192.168.1.5
Failed login from 192.168.1.10
Failed login from 192.168.1.20
Successful login from 192.168.1.15
```

Write a Python program that counts how many lines contain `Failed login`.

### Challenge — IP Address Extractor

Create a Python program that:

1. Accepts a sample log message.
    
2. Uses a regular expression to find IPv4-like strings.
    
3. Displays all matches.
    
4. Handles messages with no matches.
    

Remember that matching an IPv4-like pattern is not the same as validating an IP address.

## 19. Questions & Doubts

Use this section to record:

- What is a string?
    
- What is string immutability?
    
- What is the difference between indexing and slicing?
    
- What is the difference between ASCII and Unicode?
    
- Why is UTF-8 commonly used?
    
- How can unsafe string handling lead to SQL injection?
    

## Related Notes

- [[Introduction to Data Structures]]
    
- [[Arrays]]
    
- [[Lists]]
    
- [[Data Types]]
    
- [[Type Conversion]]
    
- [[Regular Expressions]]
    
- [[File Handling]]
    
- [[JSON]]
    
- [[SQL Injection]]
    
- [[Cross-Site Scripting Prevention]]
    
- [[Introduction to Python]]