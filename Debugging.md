> Understand how to identify, analyze, locate, and fix errors in programs through systematic investigation and testing.

## 1. Introduction to Debugging

Debugging is the process of finding, analyzing, and correcting errors (bugs) in a program.

A bug is a defect in software that causes unexpected or incorrect behavior.

Examples:

- A program crashes unexpectedly.
    
- A calculation produces an incorrect result.
    
- A function returns the wrong value.
    
- An application fails to connect to a server.
    
- A security check can be bypassed.
    

Debugging helps developers understand why a program behaves differently from what was expected.

## 2. Why Debugging Is Important

Debugging helps to:

- Identify programming errors.
    
- Improve software reliability.
    
- Correct unexpected behavior.
    
- Improve application performance.
    
- Reduce security vulnerabilities.
    
- Understand unfamiliar code.
    
- Prevent recurring software failures.
    

In cybersecurity, debugging is also useful when analyzing scripts, investigating suspicious behavior, and reviewing security tools.

## 3. Types of Programming Bugs

### 1. Syntax Errors

Occur when code violates programming language syntax rules.

Example:

```
if True
    print("Hello")
```

The missing colon causes a syntax error.

### 2. Runtime Errors

Occur while a program is executing.

Example:

```
result = 10 / 0
```

This raises a `ZeroDivisionError`.

### 3. Logical Errors

Occur when a program runs successfully but produces an incorrect result.

Example:

```
length = 10
width = 5

area = length + width

print(area)
```

The correct formula should use multiplication.

### 4. Performance Bugs

Occur when software uses excessive resources or executes inefficiently.

Examples:

- Unnecessary repeated calculations.
    
- Memory leaks.
    
- Inefficient loops.
    
- Excessive database queries.
    

### 5. Security Bugs

Occur when software contains weaknesses that attackers may exploit.

Examples:

- SQL injection.
    
- Improper access control.
    
- Insecure authentication.
    
- Path traversal.
    
- Improper input handling.
    

## 4. Debugging Process

A systematic debugging process generally follows these steps:

1. **Identify:** Observe the unexpected behavior.
    
2. **Reproduce:** Find a reliable way to trigger the problem.
    
3. **Isolate:** Narrow down the affected code.
    
4. **Investigate:** Examine variables, execution flow, and errors.
    
5. **Fix:** Correct the underlying cause.
    
6. **Test:** Verify that the correction works.
    
7. **Regression Test:** Check that the fix has not broken existing functionality.
    
8. **Document:** Record the problem and its solution.
    

A good debugging process focuses on finding the root cause rather than merely hiding the error.

## 5. Print-Based Debugging

Print-based debugging uses output statements to inspect program execution.

Example:

```
def calculate_total(price, quantity):
    print("Price:", price)
    print("Quantity:", quantity)

    total = price * quantity

    print("Calculated total:", total)

    return total


calculate_total(100, 3)
```

Output:

```
Price: 100
Quantity: 3
Calculated total: 300
```

This technique helps developers understand variable values and execution flow.

**Limitation:** Excessive print statements can make large applications difficult to debug.

## 6. Debugging with Python's pdb

Python provides a built-in debugger called `pdb`.

It allows developers to pause program execution and inspect internal state.

Example:

```
import pdb

def calculate(a, b):
    result = a + b

    pdb.set_trace()

    return result


print(calculate(10, 20))
```

When execution reaches `pdb.set_trace()`, the debugger pauses.

Common commands:

|Command|Purpose|
|---|---|
|`n`|Execute the next line|
|`s`|Step into a function|
|`c`|Continue execution|
|`l`|Display nearby source code|
|`p variable`|Print a variable's value|
|`q`|Quit the debugger|

Example:

```
(Pdb) p result
30
```

This allows developers to inspect values without adding multiple print statements.

## 7. Breakpoints

A breakpoint is a location in a program where execution pauses during debugging.

Developers can use breakpoints to:

- Inspect variable values.
    
- Examine program state.
    
- Follow execution flow.
    
- Identify where incorrect behavior begins.
    

Most modern code editors and IDEs support graphical breakpoints.

For example, in Visual Studio Code:

1. Open a Python file.
    
2. Click beside a line number.
    
3. Start debugging.
    
4. Inspect variables when execution pauses.
    

## 8. Step-by-Step Execution

Debuggers commonly provide three execution controls.

|Operation|Meaning|
|---|---|
|Step Over|Execute the current line without entering called functions|
|Step Into|Enter a function being called|
|Step Out|Finish the current function and return to its caller|

These operations help developers understand how a program executes.

## 9. Inspecting Variables

Variables store values used by a program.

During debugging, inspecting variables helps identify incorrect data.

Example:

```
username = "student"
attempts = 5
is_authenticated = False

print(username)
print(attempts)
print(is_authenticated)
```

A debugger can inspect these variables at different execution points.

Important questions:

- Does the variable contain the expected value?
    
- Was it modified unexpectedly?
    
- Is its data type correct?
    
- Is its scope appropriate?
    

## 10. Logging vs Print Debugging

Logging records application events and diagnostic information.

Python provides the built-in `logging` module.

Example:

```
import logging

logging.basicConfig(
    level=logging.DEBUG,
    format="%(levelname)s: %(message)s"
)

logging.debug("Application started")
logging.info("User login attempted")
logging.warning("Multiple failed attempts detected")
logging.error("Database connection failed")
logging.critical("Application cannot continue")
```

Common logging levels:

|Level|Purpose|
|---|---|
|DEBUG|Detailed diagnostic information|
|INFO|Normal application events|
|WARNING|Unexpected situations|
|ERROR|Operations that failed|
|CRITICAL|Serious failures|

**Difference:**

- Print statements are mainly used for temporary inspection.
    
- Logging provides structured diagnostic records that can be configured and retained.
    

Never log passwords, authentication tokens, API keys, or other sensitive information.

## 11. Debugging Common Python Problems

### Problem 1: NameError

Incorrect code:

```
print(username)
```

If `username` has not been defined, Python raises a `NameError`.

Correction:

```
username = "student"

print(username)
```

### Problem 2: TypeError

Incorrect code:

```
age = 18

print("Age: " + age)
```

Python cannot concatenate a string and an integer directly.

Correction:

```
age = 18

print("Age:", age)
```

### Problem 3: IndexError

Incorrect code:

```
numbers = [10, 20, 30]

print(numbers[5])
```

The requested index does not exist.

Correction:

```
numbers = [10, 20, 30]

print(numbers[2])
```

### Problem 4: FileNotFoundError

Incorrect code:

```
file = open("missing.txt", "r")
```

The file does not exist at the specified location.

Correction:

```
import os

if os.path.exists("missing.txt"):
    with open("missing.txt", "r") as file:
        print(file.read())
else:
    print("File not found")
```

## 12. Debugging Tools

Common debugging tools include:

|Tool|Purpose|
|---|---|
|Python `pdb`|Command-line debugging|
|VS Code Debugger|Graphical debugging|
|PyCharm Debugger|Python debugging|
|GDB|Debugging compiled programs|
|LLDB|Debugging compiled programs|
|Chrome DevTools|JavaScript and browser debugging|
|Browser Console|Inspect browser errors|
|Wireshark|Analyze network traffic|

Different tools are used for different programming environments.

## 13. Debugging in Cybersecurity

Debugging is important in several cybersecurity activities.

### 1. Security Tool Development

Debug Python scripts used for automation, scanning, and monitoring.

### 2. Malware Analysis

Investigate program behavior in an isolated and authorized analysis environment.

### 3. Log Analysis

Identify why a monitoring script fails to process particular log entries.

### 4. Network Programming

Investigate connection failures, incorrect responses, and protocol-handling problems.

### 5. Secure Coding

Find weaknesses in authentication, input handling, access control, and data processing.

### 6. Digital Forensics

Debug scripts that parse evidence files or calculate file hashes.

## 14. Debugging and Security Risks

Debugging information can expose sensitive application details.

Examples:

- Stack traces revealing internal file paths.
    
- Database errors exposing query details.
    
- Debug endpoints exposing application information.
    
- Logs containing credentials.
    
- Development configurations accidentally enabled in production.
    

Security practices:

- Disable development debug modes in production.
    
- Restrict access to debugging interfaces.
    
- Protect application logs.
    
- Avoid exposing detailed errors to users.
    
- Never store secrets in source code.
    
- Remove temporary debugging code before deployment.
    

## 15. Practical Lab

**Objective:** Find and correct errors in a Python program.

### Step 1 — Create a buggy program

```
def calculate_average(numbers):
    total = 0

    for number in numbers:
        total += number

    average = total / len(numbers)

    return average


values = [10, 20, 30]

print(calculate_average(values))
```

This version works for a non-empty list.

### Step 2 — Test an empty list

```
values = []

print(calculate_average(values))
```

Observe the exception.

### Step 3 — Identify the root cause

The program attempts to divide by zero because the list contains no elements.

### Step 4 — Fix the problem

```
def calculate_average(numbers):
    if not numbers:
        return None

    total = sum(numbers)

    return total / len(numbers)


values = []

result = calculate_average(values)

if result is None:
    print("Cannot calculate average of an empty list")
else:
    print("Average:", result)
```

### Step 5 — Test multiple inputs

Try:

```
print(calculate_average([10, 20, 30]))
print(calculate_average([5, 15]))
print(calculate_average([]))
```

### Step 6 — Document your findings

Record:

1. What was the original problem?
    
2. Which line caused the exception?
    
3. What was the root cause?
    
4. How did you fix it?
    
5. How did you verify the correction?
    

## 16. Key Takeaways

- Debugging identifies and corrects software defects.
    
- Syntax, runtime, logical, performance, and security bugs require different investigation methods.
    
- Breakpoints help pause program execution.
    
- Debuggers allow developers to inspect variables and execution flow.
    
- Python provides `pdb` for debugging.
    
- Logging records application events.
    
- Regression testing helps ensure fixes do not introduce new problems.
    
- Debugging information must be protected in production environments.
    

## 17. Related Topics

- [[Programming Languages]]
    
- [[Python Programming]]
    
- [[Python Exception Handling]]
    
- [[Python Functions]]
    
- [[File Handling]]
    
- [[Algorithms]]
    
- [[Time and Space Complexity]]
    
- [[Regular Expressions]]
    
- [[Git and Version Control]]
    
- [[Introduction to Secure Coding]]
    
- [[Secure Error Handling]]
    
- [[Log Analysis with Python]]