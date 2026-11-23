> Understand how programs detect, handle, and recover from runtime errors without terminating unexpectedly.

## 1. Introduction to Exception Handling

Exception Handling is a programming technique used to manage errors that occur while a program is executing.

An exception is an event that interrupts the normal flow of a program.

Examples:

- Dividing a number by zero.
    
- Opening a file that does not exist.
    
- Converting invalid text into an integer.
    
- Accessing an unavailable list element.
    
- Connecting to an unreachable server.
    

Exception handling allows a program to respond to these situations instead of crashing unexpectedly.

## 2. Errors vs Exceptions

Errors and exceptions are related but have different meanings.

|Term|Meaning|
|---|---|
|Error|A problem that prevents code from working correctly|
|Exception|An event raised during execution that can often be handled|

Common categories of programming errors:

### 1. Syntax Errors

Occur when code violates the language's syntax rules.

Example:

```
if True
    print("Hello")
```

The missing colon causes a syntax error.

### 2. Runtime Errors

Occur while the program is executing.

Example:

```
result = 10 / 0
```

This raises a `ZeroDivisionError`.

### 3. Logical Errors

Occur when a program runs but produces an incorrect result.

Example:

```
length = 10
width = 5

area = length + width

print(area)
```

The code runs, but the area calculation should use multiplication.

Logical errors are generally identified through testing and debugging rather than exception handling.

## 3. Why Exception Handling Is Important

Exception handling helps to:

- Prevent unexpected program termination.
    
- Display meaningful error messages.
    
- Maintain application stability.
    
- Handle missing files and invalid input.
    
- Manage external resource failures.
    
- Improve debugging and maintenance.
    
- Protect sensitive internal information from being exposed.
    

## 4. Common Python Exceptions

|Exception|Description|
|---|---|
|`ZeroDivisionError`|Division by zero|
|`ValueError`|Invalid value supplied|
|`TypeError`|Operation on an inappropriate type|
|`NameError`|Undefined variable referenced|
|`IndexError`|Invalid sequence index|
|`KeyError`|Missing dictionary key|
|`FileNotFoundError`|File does not exist|
|`PermissionError`|Operation is not permitted|
|`ImportError`|Import operation fails|
|`ModuleNotFoundError`|Requested module cannot be found|
|`AttributeError`|Object does not have the requested attribute|
|`OSError`|Operating-system-related operation fails|

## 5. Basic Exception Handling

Python uses the `try` and `except` blocks.

### Syntax

```
try:
    # Code that may raise an exception

except ExceptionType:
    # Code to handle the exception
```

### Example

```
try:
    number = int(input("Enter a number: "))
    result = 10 / number

    print(result)

except ZeroDivisionError:
    print("Cannot divide by zero")

except ValueError:
    print("Please enter a valid integer")
```

Explanation:

1. Python executes the `try` block.
    
2. If an exception occurs, Python looks for a matching `except` block.
    
3. The matching handler executes.
    
4. If no exception occurs, the `except` blocks are skipped.
    

## 6. Multiple Exception Handling

A program can handle different exceptions separately.

```
try:
    number = int(input("Enter a number: "))
    result = 100 / number

except ValueError:
    print("Invalid number")

except ZeroDivisionError:
    print("Division by zero is not allowed")

except Exception as error:
    print("Unexpected error:", error)
```

Specific exceptions should generally be handled before broader exception classes.

Avoid catching every exception without understanding what went wrong.

## 7. The else Block

The `else` block executes when no exception occurs in the associated `try` block.

Example:

```
try:
    number = int(input("Enter a number: "))

except ValueError:
    print("Invalid input")

else:
    print("You entered:", number)
```

Purpose:

- Separates successful execution from error handling.
    
- Improves code readability.
    
- Makes program logic easier to understand.
    

## 8. The finally Block

The `finally` block executes whether an exception occurs or not, subject to normal program control flow.

Example:

```
try:
    file = open("data.txt", "r")
    content = file.read()

except FileNotFoundError:
    print("File not found")

finally:
    print("File operation completed")
```

Common uses:

- Releasing resources.
    
- Closing connections.
    
- Cleaning up temporary files.
    
- Performing final operations.
    

For ordinary file handling, Python's `with` statement is usually preferable because it manages file closure automatically.

## 9. Raising Exceptions

Python uses the `raise` keyword to generate an exception deliberately.

Example:

```
age = -5

if age < 0:
    raise ValueError("Age cannot be negative")
```

The `raise` keyword is useful when input or application data violates a required condition.

Another example:

```
def withdraw(balance, amount):
    if amount <= 0:
        raise ValueError("Amount must be positive")

    if amount > balance:
        raise ValueError("Insufficient balance")

    return balance - amount
```

## 10. Custom Exceptions

Programmers can create their own exception classes.

Custom exceptions are useful when an application has specific error conditions.

Example:

```
class InsufficientBalanceError(Exception):
    pass


def withdraw(balance, amount):
    if amount > balance:
        raise InsufficientBalanceError(
            "Insufficient account balance"
        )

    return balance - amount


try:
    result = withdraw(1000, 1500)
    print(result)

except InsufficientBalanceError as error:
    print(error)
```

Custom exceptions make application-specific errors easier to identify and handle.

## 11. Exception Propagation

Exception propagation occurs when an exception moves through function calls until a suitable handler is found.

Example:

```
def calculate():
    return 10 / 0


def process():
    calculate()


try:
    process()

except ZeroDivisionError:
    print("Division error handled")
```

The exception begins inside `calculate()` and propagates through `process()` until it reaches the `try` block.

If no appropriate handler exists, the program terminates with an unhandled exception.

## 12. Exception Handling with File Operations

File operations can fail for several reasons.

Example:

```
try:
    with open("report.txt", "r") as file:
        content = file.read()

    print(content)

except FileNotFoundError:
    print("Report file does not exist")

except PermissionError:
    print("You do not have permission to read this file")

except OSError as error:
    print("File operation failed:", error)
```

This approach provides more useful error handling than allowing an unexpected file error to terminate the application.

## 13. Exception Handling and Cybersecurity

Exception handling is important in cybersecurity applications.

### 1. Log Analysis

A log-processing program may encounter malformed or incomplete records.

Exception handling helps it manage invalid entries.

### 2. Network Programming

Network connections can fail because of:

- Timeouts.
    
- DNS failures.
    
- Connection refusal.
    
- Network interruptions.
    

### 3. File Integrity Monitoring

A file may disappear or become inaccessible during an integrity check.

### 4. Security Tools

Scanning and monitoring tools need to handle unexpected input and environmental failures.

### 5. Authentication Systems

Applications must handle failed authentication attempts without exposing internal implementation details.

## 14. Secure Exception Handling Practices

Exception handling must be designed carefully.

### 1. Avoid exposing sensitive details

Do not display:

- Database credentials.
    
- API keys.
    
- Internal server paths.
    
- Stack traces to ordinary users.
    
- Sensitive application configuration.
    

### 2. Catch specific exceptions

Prefer:

```
try:
    number = int("abc")

except ValueError:
    print("Invalid number")
```

Instead of blindly catching everything:

```
try:
    number = int("abc")

except:
    print("Something went wrong")
```

### 3. Log errors securely

Technical information should be recorded in protected logs when necessary.

### 4. Do not silently ignore errors

Ignoring exceptions can hide application failures and security problems.

### 5. Avoid using exceptions for ordinary control flow

Use normal conditions for expected situations.

## 15. Practical Lab

**Objective:** Build a simple error-resistant calculator.

### Step 1 — Create a calculator

```
def calculator():
    try:
        first = float(input("Enter first number: "))
        second = float(input("Enter second number: "))

        result = first / second

    except ValueError:
        print("Please enter valid numbers")

    except ZeroDivisionError:
        print("Cannot divide by zero")

    else:
        print("Result:", result)

    finally:
        print("Calculator operation finished")


calculator()
```

### Step 2 — Test different inputs

Try:

- `10` and `2`
    
- `10` and `0`
    
- `abc` and `2`
    

Observe which exception handler executes.

### Step 3 — Extend the program

Add:

- Addition.
    
- Subtraction.
    
- Multiplication.
    
- Division.
    

Handle invalid operators using an appropriate condition or custom exception.

### Step 4 — Record observations

Answer:

1. What happens when a `ValueError` occurs?
    
2. When does the `else` block execute?
    
3. Why does the `finally` block execute?
    
4. Why should specific exceptions be handled separately?
    

## 16. Key Takeaways

- Exceptions are events that interrupt normal program execution.
    
- `try` contains code that may raise exceptions.
    
- `except` handles matching exceptions.
    
- `else` executes when no exception occurs.
    
- `finally` is used for cleanup operations.
    
- `raise` generates an exception deliberately.
    
- Custom exceptions represent application-specific errors.
    
- Secure exception handling prevents information disclosure and improves reliability.
    

## 17. Related Topics

- [[Programming Fundamentals]]
    
- [[Python Programming]]
    
- [[Python File Handling]]
    
- [[Python Functions]]
    
- [[Debugging]]
    
- [[Logging]]
    
- [[Secure Error Handling]]
    
- [[File Handling]]
    
- [[Log Analysis with Python]]
    
- [[Python Programming Labs]]