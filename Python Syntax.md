## 1. Introduction

Python syntax refers to the set of rules that define how Python programs must be written and structured.

Syntax determines how instructions, variables, functions, statements, and expressions are organized.

Python is known for its readable syntax and uses indentation to define code blocks.

Example:

```
print("Hello, ROOTLOG!")
```

This is a valid Python statement that displays text on the screen.

## 2. Python Statements

A statement is an instruction that Python can execute.

Example:

```
name = "Mohit"
age = 18

print(name)
print(age)
```

Here:

- `name = "Mohit"` assigns a value.
    
- `age = 18` assigns an integer.
    
- `print(name)` displays the variable's value.
    

Python generally uses one statement per line.

Multiple statements can be written on one line using semicolons, but this is usually discouraged because it reduces readability.

## 3. Indentation

Indentation means adding spaces at the beginning of a line.

Python uses indentation to identify code blocks.

Unlike languages such as C and C++, Python does not use curly braces to define blocks.

Example:

```
if True:
    print("Inside the if block")

print("Outside the if block")
```

Output:

```
Inside the if block
Outside the if block
```

### Indentation Rules

1. Use consistent indentation.
    
2. Four spaces per indentation level is the recommended convention.
    
3. Do not mix tabs and spaces.
    
4. Statements belonging to the same block should have consistent indentation.
    

Incorrect example:

```
if True:
print("Hello")
```

This produces an `IndentationError`.

Correct example:

```
if True:
    print("Hello")
```

## 4. Comments

Comments are explanations written inside source code. Python ignores comments during normal execution.

Single-line comments begin with `#`.

Example:

```
# Display a message
print("Learning Python")
```

Comments help programmers understand code.

### Multiline Comments

Python does not have a dedicated multiline comment syntax.

You can write multiple single-line comments:

```
# This program calculates
# the sum of two numbers

a = 10
b = 20

print(a + b)
```

Triple-quoted strings are often used for documentation, but they are string literals rather than actual comments.

## 5. Variables

Variables are names that refer to objects in Python.

Example:

```
username = "student"
age = 18
score = 95.5
```

Python does not require you to declare a variable's type explicitly.

The type is determined by the object assigned to it.

Example:

```
value = 100
print(value)

value = "Python"
print(value)
```

Output:

```
100
Python
```

This demonstrates Python's dynamic typing.

## 6. Naming Rules

Python identifiers are names used for variables, functions, classes, and other objects.

### Valid Naming Rules

1. Names can contain letters.
    
2. Names can contain digits, but cannot begin with a digit.
    
3. Underscores are allowed.
    
4. Names are case-sensitive.
    
5. Python keywords cannot be used as identifiers.
    

Examples:

|Name|Validity|
|---|---|
|`username`|Valid|
|`user_name`|Valid|
|`user123`|Valid|
|`_private`|Valid|
|`123user`|Invalid|
|`user-name`|Invalid|
|`class`|Invalid|

### Case Sensitivity

```
name = "Mohit"
Name = "Rahul"

print(name)
print(Name)
```

Output:

```
Mohit
Rahul
```

Python treats `name` and `Name` as different identifiers.

### Naming Convention

Python commonly uses:

- `snake_case` for variables and functions.
    
- `PascalCase` for classes.
    
- `UPPER_CASE` for constants.
    

Example:

```
student_name = "Mohit"
MAX_ATTEMPTS = 5

class SecurityScanner:
    pass
```

These are conventions rather than mandatory syntax rules.

## 7. Keywords

Keywords are reserved words that have special meanings in Python.

They cannot be used as ordinary variable or function names.

Examples:

|Keyword|Purpose|
|---|---|
|`if`|Conditional execution|
|`else`|Alternative execution|
|`elif`|Additional condition|
|`for`|Iteration|
|`while`|Repeated execution|
|`break`|Exit a loop|
|`continue`|Skip to the next iteration|
|`def`|Define a function|
|`return`|Return a value|
|`class`|Define a class|
|`import`|Import a module|
|`try`|Begin exception handling|
|`except`|Handle an exception|
|`finally`|Execute cleanup code|
|`True`|Boolean true value|
|`False`|Boolean false value|
|`None`|Represents the absence of a value|

You can inspect Python keywords using:

```
import keyword

print(keyword.kwlist)
```

## 8. Input and Output Syntax

Python uses `print()` to display output and `input()` to receive user input.

### Output

```
print("Hello World")
```

### Input

```
name = input("Enter your name: ")

print("Welcome", name)
```

Important: `input()` returns a string.

If you need a number, convert the input.

```
age = int(input("Enter your age: "))

print(age)
```

## 9. Expressions and Operators

An expression is a combination of values, variables, and operators that produces a result.

Example:

```
a = 10
b = 5

result = a + b

print(result)
```

Output:

```
15
```

Python supports different operator categories:

- Arithmetic operators
    
- Comparison operators
    
- Logical operators
    
- Assignment operators
    
- Membership operators
    
- Identity operators
    
- Bitwise operators
    

Detailed topic: [[Operators]]

## 10. Conditional Syntax

Conditional statements execute code depending on whether a condition is true or false.

Example:

```
age = 18

if age >= 18:
    print("Eligible")
else:
    print("Not eligible")
```

Python uses a colon (`:`) after the condition and indentation for the code block.

Detailed topic: [[Conditional Statements]]

## 11. Loop Syntax

Loops execute a block of code repeatedly.

Python provides `for` and `while` loops.

### For Loop

```
for number in range(1, 6):
    print(number)
```

### While Loop

```
count = 1

while count <= 5:
    print(count)
    count += 1
```

Detailed topic: [[Loops]]

## 12. Function Syntax

Functions are reusable blocks of code.

Python uses the `def` keyword to define a function.

Example:

```
def greet():
    print("Welcome to ROOTLOG")


greet()
```

A function can accept parameters and return values.

```
def add(a, b):
    return a + b


result = add(10, 20)

print(result)
```

Detailed topic: [[Introduction to Functions]]

## 13. Import Syntax

The `import` statement allows a program to use functionality from modules.

Example:

```
import math

print(math.sqrt(25))
```

Output:

```
5.0
```

You can also import specific functions:

```
from math import sqrt

print(sqrt(36))
```

Detailed topic: [[Modules and Libraries]]

## 14. String Syntax

Strings represent text and can be created using single quotes, double quotes, or triple quotes.

Example:

```
name = "Python"
message = 'Learning programming'
description = """Python is a programming language."""

print(name)
print(message)
print(description)
```

### Escape Characters

Escape characters represent special characters inside strings.

|Escape|Meaning|
|---|---|
|`\n`|New line|
|`\t`|Tab|
|`\\`|Backslash|
|`\"`|Double quotation mark|
|`\'`|Single quotation mark|

Example:

```
print("Hello\nWorld")
```

Output:

```
Hello
World
```

## 15. Python Blocks

A block is a group of statements executed together under a control structure, function, class, or similar construct.

Example:

```
def check_status():
    status = "Active"

    if status == "Active":
        print("System is running")
```

The indentation shows which statements belong to the function and which belong to the conditional block.

## 16. Python Syntax Errors

A syntax error occurs when code violates Python's grammar rules.

### Example 1: Missing Colon

Incorrect:

```
if True
    print("Hello")
```

Correct:

```
if True:
    print("Hello")
```

### Example 2: Incorrect Indentation

Incorrect:

```
if True:
print("Running")
```

Correct:

```
if True:
    print("Running")
```

### Example 3: Unclosed String

Incorrect:

```
print("Hello)
```

Correct:

```
print("Hello")
```

### Common Python Errors

|Error|Meaning|
|---|---|
|`SyntaxError`|Code violates Python syntax|
|`IndentationError`|Incorrect indentation|
|`NameError`|An undefined name is referenced|
|`TypeError`|An operation is used with an inappropriate type|
|`ValueError`|A function receives a value of the correct type but an inappropriate value|

Understanding error messages is an important programming skill.

## 17. Python Syntax Best Practices

1. Use meaningful variable names.
    
2. Follow four-space indentation.
    
3. Use `snake_case` for functions and variables.
    
4. Keep functions focused on one responsibility.
    
5. Write comments when they clarify non-obvious logic.
    
6. Avoid unnecessarily long lines.
    
7. Use consistent formatting.
    
8. Follow PEP 8, the official Python style guide.
    

Official reference: [https://peps.python.org/pep-0008/](https://peps.python.org/pep-0008/)

## 18. Practical Exercises

### Exercise 1: Basic Syntax

Write a Python program that displays:

- Your name
    
- Your learning goal
    
- Your current programming language
    

### Exercise 2: Variables and Input

Ask the user for their name and age.

Display both values using `print()`.

### Exercise 3: Conditional Statement

Ask the user to enter a number.

Display whether the number is positive, negative, or zero.

### Exercise 4: Loop

Write a program that displays numbers from 1 to 10 using a `for` loop.

### Exercise 5: Function

Create a function named `calculate_hash_length()` that accepts a string and returns its length.

Test it using:

```
print(calculate_hash_length("ROOTLOG"))
```

Expected output:

```
7
```

## 19. Key Takeaways

- Python syntax defines how Python code must be written.
    
- Indentation is essential for defining code blocks.
    
- Variables refer to objects.
    
- Identifiers must follow naming rules.
    
- Keywords are reserved words.
    
- `print()` displays output and `input()` receives user input.
    
- Functions are defined using `def`.
    
- Modules are included using `import`.
    
- Syntax errors occur when code violates Python grammar.
    
- PEP 8 provides Python style recommendations.
    

## 20. Related Topics

- [[Introduction to Python]]
    
- [[Programming Languages]]
    
- [[Variables and Constants]]
    
- [[Data Types]]
    
- [[Operators]]
    
- [[Input and Output]]
    
- [[Conditional Statements]]
    
- [[Loops]]
    
- [[Introduction to Functions]]
    
- [[Modules and Libraries]]
    
- [[Python Control Flow]]