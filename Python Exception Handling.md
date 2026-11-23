## 1. Introduction

Exception handling is a mechanism used to detect and manage errors that occur while a program is running.

An exception is an event that interrupts the normal execution of a program.

Python provides `try`, `except`, `else`, and `finally` blocks to handle exceptions.

### Example Without Exception Handling

```
number = int(input("Enter a number: "))

print(100 / number)
```

If the user enters `0`, Python raises a `ZeroDivisionError`.

If the user enters text instead of a number, Python raises a `ValueError`.

Without exception handling, the program terminates with an error traceback.

### Example With Exception Handling

```
try:
    number = int(input("Enter a number: "))
    print(100 / number)

except ZeroDivisionError:
    print("Cannot divide by zero")

except ValueError:
    print("Please enter a valid number")
```

The program handles expected errors instead of terminating with an unhandled exception.

## 2. Error vs Exception

Errors and exceptions are related but have different meanings.

|Term|Meaning|
|---|---|
|Error|General term for a problem in a program|
|Syntax Error|Problem with Python code structure|
|Exception|An event raised during program execution|

### Syntax Error Example

```
# Missing colon causes SyntaxError

# if number > 10
#     print("Large number")
```

A syntax error prevents the program from being parsed and executed normally.

### Exception Example

```
number = 10 / 0
```

This code is syntactically valid, but it raises `ZeroDivisionError` during execution.

## 3. Why Exception Handling Is Important

Exception handling helps programmers:

1. Prevent unexpected program termination.
    
2. Handle invalid user input.
    
3. Manage file access problems.
    
4. Handle network failures.
    
5. Improve application reliability.
    
6. Provide meaningful error messages.
    
7. Separate normal logic from error-handling logic.
    

In cybersecurity, exception handling is useful when reading logs, processing files, validating input, communicating with APIs, and building security tools.

## 4. Types of Exceptions in Python

Python provides many built-in exceptions.

|Exception|Meaning|
|---|---|
|`ZeroDivisionError`|Division by zero|
|`ValueError`|Correct type but invalid value|
|`TypeError`|Operation applied to an incompatible type|
|`NameError`|Variable or name is not defined|
|`IndexError`|Invalid sequence index|
|`KeyError`|Dictionary key does not exist|
|`FileNotFoundError`|File does not exist|
|`PermissionError`|Operation lacks required permissions|
|`ImportError`|Import operation fails|
|`ModuleNotFoundError`|Requested module cannot be found|
|`AttributeError`|Object does not have the requested attribute|
|`OSError`|Operating-system-related failure|
|`JSONDecodeError`|Invalid JSON document|

Example:

```
numbers = [10, 20, 30]

print(numbers[5])
```

This raises `IndexError` because index `5` does not exist.

## 5. The try Block

The `try` block contains code that might raise an exception.

Example:

```
try:
    result = 10 / 2
    print(result)
```

A `try` block must be followed by at least one `except` block or a `finally` block.

## 6. The except Block

The `except` block handles an exception raised inside the associated `try` block.

Example:

```
try:
    number = int("hello")

except ValueError:
    print("Invalid number")
```

Output:

```
Invalid number
```

### Handling Multiple Exceptions

You can use multiple `except` blocks to handle different exceptions.

```
try:
    number = int(input("Enter a number: "))
    result = 100 / number

except ValueError:
    print("Invalid input")

except ZeroDivisionError:
    print("Cannot divide by zero")
```

Each exception has its own handling logic.

## 7. The else Block

The `else` block executes only when the `try` block completes without raising an exception.

Example:

```
try:
    number = int(input("Enter a number: "))

except ValueError:
    print("Invalid input")

else:
    print("Valid number:", number)
```

Output for input `25`:

```
Valid number: 25
```

The `else` block is useful for separating successful execution from error handling.

## 8. The finally Block

The `finally` block executes whether an exception occurs or not, including when an exception is propagated.

Example:

```
try:
    print("Opening operation")

    result = 10 / 0

except ZeroDivisionError:
    print("Division error")

finally:
    print("Operation completed")
```

Output:

```
Opening operation
Division error
Operation completed
```

The `finally` block is commonly used for cleanup operations.

For file handling, context managers using `with` are generally preferred because they manage resources automatically.

## 9. Complete Exception Handling Structure

Python supports combining all four blocks.

```
try:
    number = int(input("Enter a number: "))

    result = 100 / number

except ValueError:
    print("Enter a valid integer")

except ZeroDivisionError:
    print("Number cannot be zero")

else:
    print("Result:", result)

finally:
    print("Program execution finished")
```

Execution order:

1. Python executes the `try` block.
    
2. If an exception occurs, the matching `except` block executes.
    
3. If no exception occurs, the `else` block executes.
    
4. The `finally` block executes afterward.
    

## 10. Catching Exception Details

Python allows you to capture exception information using `as`.

Example:

```
try:
    number = int("abc")

except ValueError as error:
    print("Error occurred:", error)
```

Output:

```
Error occurred: invalid literal for int() with base 10: 'abc'
```

This is useful when debugging programs.

However, avoid exposing internal exception details to ordinary users when they might contain sensitive paths, configuration information, or other internal data.

## 11. Generic Exception Handling

Python provides a general `Exception` class that can catch most ordinary application exceptions.

Example:

```
try:
    number = int(input("Enter a number: "))
    print(100 / number)

except Exception as error:
    print("An error occurred:", error)
```

This catches multiple exception types.

However, catching `Exception` everywhere is not recommended.

Why?

- It can hide programming mistakes.
    
- It makes debugging difficult.
    
- It can hide the actual cause of failure.
    
- It may cause a program to continue in an unsafe state.
    

Prefer handling specific exceptions whenever possible.

Avoid catching `BaseException` for ordinary application error handling because it also includes control-flow exceptions such as `KeyboardInterrupt` and `SystemExit`.

## 12. Raising Exceptions

Python uses the `raise` keyword to manually trigger an exception.

Example:

```
age = -5

if age < 0:
    raise ValueError("Age cannot be negative")
```

Output:

```
ValueError: Age cannot be negative
```

Raising exceptions helps enforce rules and validate program operations.

### Raising an Exception Inside a Function

```
def calculate_age(age):

    if age < 0:
        raise ValueError("Age cannot be negative")

    return age


print(calculate_age(18))
```

The function rejects invalid values rather than silently accepting them.

## 13. Custom Exceptions

Python allows programmers to create their own exception classes.

Custom exceptions are useful when an application has specific error conditions.

Example:

```
class InvalidIPError(Exception):
    pass


def validate_ip(ip_address):

    if not ip_address:
        raise InvalidIPError("IP address cannot be empty")


try:
    validate_ip("")

except InvalidIPError as error:
    print(error)
```

Output:

```
IP address cannot be empty
```

A custom exception makes application-specific errors easier to identify and handle.

## 14. Exception Propagation

Exception propagation occurs when an exception is raised in one function and moves up through the calling functions until a matching handler is found.

Example:

```
def function_c():
    return 10 / 0


def function_b():
    function_c()


def function_a():
    try:
        function_b()

    except ZeroDivisionError:
        print("Error handled in function_a")


function_a()
```

Output:

```
Error handled in function_a
```

The exception travels from `function_c()` through `function_b()` to `function_a()`.

This allows higher-level functions to handle errors from lower-level operations.

## 15. Re-raising Exceptions

Sometimes a function should log or inspect an exception and then allow it to continue propagating.

The `raise` statement without an argument re-raises the current exception inside an exception handler.

Example:

```
try:
    number = 10 / 0

except ZeroDivisionError:
    print("Logging division error")
    raise
```

The exception is raised again after the message is printed.

This is useful when an error should be recorded but not silently ignored.

## 16. Assertions

An assertion checks whether a condition is true.

Python uses the `assert` keyword.

Example:

```
age = 18

assert age >= 0, "Age cannot be negative"

print("Valid age")
```

If the condition is false, Python raises `AssertionError`.

Assertions are useful during development and testing.

Important: Do not use assertions for security checks or validation of untrusted input. Python can disable assertions when optimization is enabled.

Use explicit conditions and exceptions for security-critical validation.

## 17. Exception Handling With Files

File operations may fail because a file is missing, permissions are insufficient, or the storage device encounters an error.

Example:

```
try:
    with open("security.log", "r", encoding="utf-8") as file:
        content = file.read()

    print(content)

except FileNotFoundError:
    print("Log file not found")

except PermissionError:
    print("Permission denied")

except OSError:
    print("File operation failed")
```

The `with` statement automatically manages file closure.

Detailed topic: [[Python File Handling]]

## 18. Exception Handling in Cybersecurity

Exception handling is important when building security-related applications.

### A. IP Address Validation

```
import ipaddress


def validate_ip(address):

    try:
        ipaddress.ip_address(address)
        return True

    except ValueError:
        return False


print(validate_ip("192.168.1.10"))
print(validate_ip("999.999.999.999"))
```

Output:

```
True
False
```

### B. Safe File Reading

```
from pathlib import Path


def read_log_file(file_path):

    try:
        with Path(file_path).open(
            "r",
            encoding="utf-8"
        ) as file:
            return file.read()

    except FileNotFoundError:
        print("Log file not found")

    except PermissionError:
        print("Permission denied")

    except OSError:
        print("Unable to read file")

    return None


data = read_log_file("security.log")

if data is not None:
    print(data)
```

### C. Safe Integer Conversion

```
def convert_to_integer(value):

    try:
        return int(value)

    except ValueError:
        print("Invalid integer value")
        return None


print(convert_to_integer("100"))
print(convert_to_integer("hello"))
```

### D. Handling JSON Errors

```
import json


sample = '{"username": "student", "role": "analyst"}'

try:
    data = json.loads(sample)
    print(data["username"])

except json.JSONDecodeError:
    print("Invalid JSON data")

except KeyError:
    print("Username field is missing")
```

Exception handling allows a program to process invalid data without unexpectedly terminating.

## 19. Secure Exception Handling Practices

Exception handling itself can introduce security problems if implemented carelessly.

Follow these practices:

1. Catch specific exceptions whenever possible.
    
2. Do not silently ignore important exceptions.
    
3. Avoid exposing sensitive internal error details.
    
4. Log useful diagnostic information securely.
    
5. Avoid logging passwords, tokens, or secret keys.
    
6. Do not use exceptions as a replacement for ordinary control flow.
    
7. Validate untrusted input before processing it.
    
8. Do not continue when an error leaves the application in an unsafe state.
    
9. Use `finally` or context managers for cleanup.
    
10. Avoid broad exception handling that hides programming defects.
    

### Example: Avoid Exposing Internal Errors

Poor approach:

```
try:
    process_user_data()

except Exception as error:
    print(error)
```

Better approach:

```
import logging

logging.basicConfig(level=logging.ERROR)

try:
    process_user_data()

except ValueError:
    print("Invalid input provided")

except OSError:
    logging.exception("A file operation failed")
    print("Unable to process the requested file")
```

The user receives a general message, while diagnostic information is recorded for authorized troubleshooting.

In a real application, configure logging carefully and avoid recording sensitive data.

## 20. Common Mistakes

### Mistake 1: Incorrect Exception Name

```
try:
    number = int("hello")

except Valueerror:
    print("Invalid input")
```

`Valueerror` is incorrect. Python exception names are case-sensitive.

Correct name:

```
ValueError
```

### Mistake 2: Incorrect Exception Order

When catching exceptions using inheritance, more specific exception types should generally appear before their parent classes.

Example:

```
try:
    with open("missing.txt", "r") as file:
        print(file.read())

except FileNotFoundError:
    print("File not found")

except OSError:
    print("Operating system error")
```

`FileNotFoundError` is a subclass of `OSError`.

### Mistake 3: Empty Exception Handler

```
try:
    number = 10 / 0

except ZeroDivisionError:
    pass
```

This silently ignores the error.

Silent exception handling can make debugging and security monitoring difficult.

### Mistake 4: Using `finally` Incorrectly

A `finally` block is intended for cleanup and finalization, not for handling every error.

Use `except` to handle exceptions and `finally` when cleanup must happen regardless of success or failure.

## 21. Practical Exercises

### Exercise 1: Division Calculator

Create a program that:

1. Accepts two numbers.
    
2. Divides the first number by the second.
    
3. Handles invalid input.
    
4. Handles division by zero.
    
5. Displays the result when successful.
    

### Exercise 2: File Exception Handling

Create a program that attempts to read `security.log`.

Handle:

- `FileNotFoundError`
    
- `PermissionError`
    
- Other relevant `OSError` exceptions
    

### Exercise 3: IP Validation

Create a function that validates an IP address using the `ipaddress` module.

Return `True` for a valid IP address and `False` for an invalid one.

### Exercise 4: Custom Exception

Create a custom exception named `InvalidPasswordError`.

Write a function that raises this exception when a password contains fewer than 12 characters.

This is only a length check, not a complete password security policy.

### Exercise 5: JSON Validation

Create a JSON string and parse it using `json.loads()`.

Test your program with:

1. Valid JSON.
    
2. Invalid JSON.
    
3. Valid JSON with a missing required key.
    

Handle each situation appropriately.

### Exercise 6: Mini Security Log Reader

Create a program that:

1. Opens a sample log file.
    
2. Reads each line.
    
3. Counts failed login events.
    
4. Handles missing files.
    
5. Displays the total number of failed events.
    

## 22. Key Takeaways

- Exceptions are events that interrupt normal program execution.
    
- Python uses `try` and `except` to handle exceptions.
    
- `else` executes when no exception occurs.
    
- `finally` executes during normal completion and exception propagation.
    
- `raise` manually triggers exceptions.
    
- Custom exceptions represent application-specific failures.
    
- Exception propagation moves errors through function calls.
    
- Assertions are useful for development but not security validation.
    
- Specific exception handling improves reliability.
    
- Secure applications must handle errors without exposing sensitive information.
    

## 23. Related Topics

- [[Introduction to Python]]
    
- [[Python Functions]]
    
- [[Python File Handling]]
    
- [[Python Data Structures]]
    
- [[Python Modules]]
    
- [[Python for Cybersecurity]]
    
- [[Log Analysis with Python]]
    
- [[Secure Programming]]
    
- [[Secure Error Handling]]