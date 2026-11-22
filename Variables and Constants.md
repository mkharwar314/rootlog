> Understand how programs store, access, modify, and manage data using variables and constants.

## 1. Introduction

Programs need to store information while they execute.

For example, a program may need to store:

- A user's name.
- An account balance.
- An IP address.
- A login status.
- A file size.
- A calculated result.

Variables and constants provide ways to represent and access this information.

**Variable:** A named reference to a value whose value can generally be changed during program execution.

**Constant:** A named value that is not intended to be reassigned after initialization, according to the language's rules.

Example in Python:

```
username = "student"
age = 20

print(username)
print(age)
```

Here:

- `username` refers to the string `"student"`.
- `age` refers to the integer `20`.

## 2. What Is a Variable?

A variable is a named storage abstraction used by a program to access data.

Example:

```
score = 50
print(score)
```

Output:

```
50
```

The variable `score` refers to the value `50`.

We can change its value:

```
score = 75
print(score)
```

Output:

```
75
```

The same variable name now refers to a different value.

### 2.1 Why Are Variables Important?

Variables help programmers:

- Store information.
- Reuse values.
- Perform calculations.
- Track program state.
- Process user input.
- Manage application data.

Without variables, programs would be difficult to write and maintain because values would have to be repeated throughout the code.

## 3. How Variables Work

Consider:

```
age = 20
```

The statement performs an assignment.

Conceptually:

```
Variable Name       Value
     age      --->   20
```

A variable name provides a way to refer to a value.

The exact implementation depends on the programming language. Variables do not always correspond to fixed physical memory locations.

For example, Python names refer to objects. In lower-level languages such as C, variables have more direct relationships with memory objects and storage.

## 4. Variable Declaration and Initialization

### 4.1 Variable Declaration

Declaration introduces a variable name and, in some languages, specifies its type.

Example in C:

```
int age;
```

This declares an integer variable named `age`.

### 4.2 Variable Initialization

Initialization assigns an initial value to a variable.

Example:

```
int age = 20;
```

Here, the variable is declared and initialized in the same statement.

### 4.3 Declaration and Initialization in Python

Python does not require a separate variable declaration for ordinary variables.

```
age = 20
```

The assignment creates a name binding to the value.

**Important:** Declaration and initialization rules differ between languages.

## 5. Variable Assignment

Assignment means associating a variable with a value.

Example:

```
name = "Mohit"
```

The `=` symbol is the assignment operator in Python.

### 5.1 Reassignment

A variable can receive a new value.

```
balance = 1000
balance = 1500

print(balance)
```

Output:

```
1500
```

### 5.2 Multiple Assignment

Python supports assigning multiple variables in one statement.

```
name, age, city = "Alex", 20, "Mumbai"

print(name)
print(age)
print(city)
```

### 5.3 Updating a Variable

Variables are often updated using arithmetic operations.

```
count = 10

count = count + 1

print(count)
```

Output:

```
11
```

A shorter form is:

```
count += 1
```

This is called augmented assignment.

## 6. Rules for Naming Variables

Variable naming rules depend on the programming language.

In Python, common rules include:

1. A variable name must begin with a letter or underscore.
2. It cannot begin with a digit.
3. It can contain letters, digits, and underscores.
4. Spaces are not allowed.
5. Reserved keywords cannot be used as variable names.
6. Python variable names are case-sensitive.

### Valid Variable Names

```
username = "student"
user_age = 20
ip_address = "192.168.1.10"
_private_value = 100
```

### Invalid Variable Names

```
2name = "Alex"
user name = "Alex"
class = "Cybersecurity"
```

These are invalid because they violate Python naming rules.

### 6.1 Case Sensitivity

Python treats uppercase and lowercase names as different identifiers.

```
name = "Alex"
Name = "Rahul"

print(name)
print(Name)
```

Output:

```
Alex
Rahul
```

### 6.2 Naming Conventions

Good variable names make code easier to understand.

Poor naming:

```
x = 500
y = 20
z = x + y
```

Clear naming:

```
account_balance = 500
deposit_amount = 20
updated_balance = account_balance + deposit_amount
```

Common Python conventions:

|Convention|Example|Typical Use|
|---|---|---|
|snake_case|`user_name`|Variables and functions|
|PascalCase|`UserAccount`|Classes|
|UPPER_CASE|`MAX_LIMIT`|Constants by convention|
|camelCase|`userName`|Common in JavaScript and Java|

## 7. What Is a Constant?

A constant is a value that should not be reassigned after it is defined.

Constants are useful for values that remain fixed throughout a program.

Examples:

- Maximum login attempts.
- Application version.
- Configuration values.
- Mathematical constants.
- Default network ports.

### 7.1 Constants in Python

Python does not enforce ordinary constant variables.

Developers commonly use uppercase names to indicate that a value should not be changed.

```
MAX_LOGIN_ATTEMPTS = 5
DEFAULT_PORT = 443

print(MAX_LOGIN_ATTEMPTS)
```

This is a naming convention, not a language-enforced restriction.

### 7.2 Constants in C

C provides the `const` keyword.

```
#include <stdio.h>

int main() {
    const int MAX_ATTEMPTS = 5;

    printf("%d\n", MAX_ATTEMPTS);

    return 0;
}
```

The program should not attempt to modify `MAX_ATTEMPTS`.

### 7.3 Constants in JavaScript

JavaScript provides `const`.

```
const MAX_ATTEMPTS = 5;

console.log(MAX_ATTEMPTS);
```

A `const` binding cannot be reassigned.

However, if the constant refers to an object or array, its contents may still be modified.

Example:

```
const settings = {
    theme: "dark"
};

settings.theme = "light";

console.log(settings.theme);
```

This is valid because the object reference was not reassigned.

## 8. Variable vs Constant

|Feature|Variable|Constant|
|---|---|---|
|Purpose|Stores a value that may change|Represents a value intended to remain fixed|
|Reassignment|Generally allowed|Restricted or discouraged|
|Use|Changing program data|Fixed configuration or values|
|Example|`balance = 500`|`MAX_ATTEMPTS = 5`|

The exact enforcement depends on the language.

## 9. Types of Variables by Scope

Scope describes where a variable name can be accessed in a program.

### 9.1 Local Variables

A local variable is defined within a function or local block and is generally accessible only within that scope.

Python example:

```
def login():
    username = "student"
    print(username)

login()
```

The variable `username` is local to the function.

### 9.2 Global Variables

A global variable is defined outside functions and can generally be accessed throughout the module or program according to language rules.

Python example:

```
application_name = "ROOTLOG"

def display():
    print(application_name)

display()
```

Output:

```
ROOTLOG
```

### 9.3 Block Scope

Some languages restrict variables to the block in which they are declared.

JavaScript example:

```
if (true) {
    let message = "Hello";
    console.log(message);
}
```

The variable `message` is limited to that block.

### 9.4 Scope Differences Between Languages

Scope rules differ across languages.

For example:

- Python primarily uses function, module, and enclosing scopes.
- JavaScript supports function scope and block scope, depending on the declaration keyword.
- C uses block scope for variables declared inside blocks.

Do not assume every language follows the same scope rules.

## 10. Variable Lifetime

Lifetime describes how long a variable or its associated storage exists during program execution.

Common concepts include:

**Automatic lifetime:** Storage is created when execution enters a relevant scope and ends when that scope exits, as with many local variables in C.

**Static lifetime:** Storage exists for the duration of the program.

**Dynamic allocation:** Storage is allocated and released according to program operations or memory-management rules.

Example in C:

```
#include <stdio.h>

void display() {
    int count = 10;
    printf("%d\n", count);
}

int main() {
    display();
    return 0;
}
```

The local variable `count` has automatic storage duration.

In languages with garbage collection, object lifetime may depend on whether an object remains reachable rather than simply on the scope of a variable name.

## 11. Variables and Memory

Variables are connected to memory, but the relationship depends on the programming language and implementation.

Consider:

```
int age = 20;
```

A typical C implementation reserves storage for an integer object.

Conceptually:

```
Memory
+------------------+
| Variable: age    |
| Value: 20        |
+------------------+
```

In Python:

```
age = 20
```

The name `age` refers to an integer object.

The Python runtime manages the object's memory.

Understanding these differences is useful when learning:

- Pointers.
- Memory allocation.
- Stack and heap concepts.
- Garbage collection.
- Memory corruption vulnerabilities.

## 12. Variables in Cybersecurity

Variables are used throughout cybersecurity programming.

### 12.1 Network Scanning

A script may store a target IP address and port.

```
target_ip = "192.168.1.10"
target_port = 80
```

### 12.2 Log Analysis

A program may store log information for analysis.

```
username = "student"
failed_attempts = 3
source_ip = "192.168.1.50"
```

### 12.3 File Integrity Monitoring

A program may store a file path and its calculated hash.

```
file_path = "evidence.txt"
expected_hash = "example_hash_value"
```

### 12.4 Authentication

A program may store the result of an authentication check.

```
login_successful = False
```

**Security warning:** Never hardcode real passwords, API keys, or secret tokens in source code. Use appropriate secret-management mechanisms.

## 13. Common Mistakes

|Mistake|Explanation|
|---|---|
|Using unclear names|Makes code difficult to understand|
|Using reserved keywords|Causes syntax errors|
|Confusing `=` and `==`|Assignment and comparison are different operations|
|Changing constants|Can cause unexpected behavior or violate intended design|
|Ignoring scope|Can lead to name errors or unexpected values|
|Hardcoding secrets|Can expose credentials in source code or repositories|
|Assuming variables always map directly to memory|The implementation depends on the language|

## 14. Practical Lab

### Lab 1: Create Variables in Python

Create a file named:

`variables_lab.py`

Add:

```
name = "ROOTLOG"
age = 20
course = "Cybersecurity"
is_student = True

print("Name:", name)
print("Age:", age)
print("Course:", course)
print("Student:", is_student)
```

Run:

```
python variables_lab.py
```

On Kali Linux, you may need:

```
python3 variables_lab.py
```

Observe how different values are stored and displayed.

### Lab 2: Update Variables

Add:

```
balance = 1000

print("Initial balance:", balance)

balance += 500

print("Updated balance:", balance)
```

Expected output:

```
Initial balance: 1000
Updated balance: 1500
```

### Lab 3: Work with Constants

Add:

```
MAX_LOGIN_ATTEMPTS = 5
DEFAULT_HTTPS_PORT = 443

print("Maximum attempts:", MAX_LOGIN_ATTEMPTS)
print("HTTPS port:", DEFAULT_HTTPS_PORT)
```

Remember that uppercase naming is a convention in Python, not an enforced constant declaration.

## 15. Key Takeaways

- Variables provide names for accessing values.
- Assignment associates a variable with a value.
- Initialization gives a variable its initial value.
- Naming rules vary between programming languages.
- Constants represent values intended to remain fixed.
- Scope determines where a variable can be accessed.
- Lifetime determines how long its storage or associated object exists.
- Variables have different relationships with memory in different languages.
- Secure programs must handle sensitive values carefully.

## 16. Questions for Self-Study

1. What is a variable?
2. Why are variables important?
3. What is the difference between declaration and initialization?
4. Explain variable assignment and reassignment.
5. What are the naming rules for Python variables?
6. What is a constant?
7. What is the difference between a variable and a constant?
8. Explain local and global variables.
9. What is variable scope?
10. What is variable lifetime?
11. How are variables related to memory?
12. Why should passwords and API keys not be hardcoded?

## 17. Practical Tasks

1. Create five variables containing different types of values.
2. Write a program that calculates the total price of three items.
3. Create a constant-style variable for the maximum number of login attempts.
4. Write a function containing a local variable.
5. Explain the difference between variable scope and lifetime.
6. Write down three examples of variables used in a cybersecurity tool.

## Related Notes

- [[Introduction to Programming]]
- [[Programming Languages]]
- [[Data Types]]
- [[Operators]]
- [[Input and Output]]
- [[Scope and Lifetime]]
- [[Introduction to Python]]
- [[Python Variables and Data Types]]
- [[C Variables and Data Types]]
- [[JavaScript Variables and Data Types]]
- [[Secure Programming]]