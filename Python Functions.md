## 1. Introduction

A function is a reusable block of code designed to perform a specific task.

Functions help programmers divide large programs into smaller, manageable parts.

Instead of writing the same instructions repeatedly, you can define a function once and call it whenever required.

### Example

```
def greet():
    print("Welcome to ROOTLOG")


greet()
greet()
```

Output:

```
Welcome to ROOTLOG
Welcome to ROOTLOG
```

The function `greet()` is defined once but executed twice.

## 2. Why Are Functions Important?

Functions provide several benefits:

1. **Code Reusability:** Write code once and use it multiple times.
    
2. **Modularity:** Divide large programs into smaller components.
    
3. **Readability:** Make programs easier to understand.
    
4. **Maintainability:** Update logic in one place.
    
5. **Testing:** Individual functions can be tested separately.
    
6. **Debugging:** Errors can be isolated more easily.
    

## 3. Defining a Function

Python uses the `def` keyword to define a function.

### Syntax

```
def function_name(parameters):
    # Function body
    statements
    return value
```

Explanation:

|Component|Meaning|
|---|---|
|`def`|Keyword used to define a function|
|`function_name`|Name of the function|
|Parameters|Input values accepted by the function|
|Function body|Instructions executed when called|
|`return`|Sends a result back to the caller|

Example:

```
def display_message():
    print("Learning Python")


display_message()
```

## 4. Calling a Function

Defining a function does not automatically execute its body.

You must call the function using its name followed by parentheses.

Example:

```
def show_info():
    print("Cybersecurity Student")


show_info()
```

Output:

```
Cybersecurity Student
```

A function can be called multiple times.

## 5. Types of Functions in Python

Python functions can be broadly classified into:

### A. Built-in Functions

Built-in functions are already provided by Python.

Examples:

|Function|Purpose|
|---|---|
|`print()`|Displays output|
|`input()`|Accepts user input|
|`len()`|Returns the length of an object|
|`type()`|Identifies an object's type|
|`int()`|Converts a compatible value to an integer|
|`str()`|Converts an object to a string representation|
|`sum()`|Calculates the sum of an iterable|
|`max()`|Returns the largest item|
|`min()`|Returns the smallest item|
|`range()`|Creates a range of integers|

Example:

```
numbers = [10, 20, 30]

print(len(numbers))
print(sum(numbers))
print(max(numbers))
```

Output:

```
3
60
30
```

### B. User-Defined Functions

User-defined functions are created by programmers to perform specific tasks.

Example:

```
def calculate_total(a, b):
    return a + b


result = calculate_total(10, 20)

print(result)
```

Output:

```
30
```

### C. Anonymous Functions

Python supports small anonymous functions using the `lambda` keyword.

Example:

```
square = lambda number: number * number

print(square(5))
```

Output:

```
25
```

Lambda functions are useful for short expressions, especially when passing a function to another function.

They are not a replacement for every normal function.

## 6. Function Parameters and Arguments

Parameters and arguments are related but different concepts.

- **Parameter:** A variable listed in a function definition.
    
- **Argument:** The actual value supplied when the function is called.
    

Example:

```
def greet(name):
    print("Hello", name)


greet("Mohit")
```

Here:

- `name` is a parameter.
    
- `"Mohit"` is an argument.
    

Python supports different ways of passing arguments.

Detailed topic: [[Function Parameters and Arguments]]

## 7. Return Values

The `return` statement sends a value from a function back to its caller.

Example:

```
def add(a, b):
    result = a + b
    return result


answer = add(10, 20)

print(answer)
```

Output:

```
30
```

### Function Without Return

If a function does not explicitly return a value, Python returns `None`.

Example:

```
def display():
    print("Hello")


result = display()

print(result)
```

Output:

```
Hello
None
```

Detailed topic: [[Return Values]]

## 8. Default Parameters

A function parameter can have a default value.

The default value is used when the caller does not supply an argument for that parameter.

Example:

```
def greet(name="Student"):
    print("Welcome", name)


greet()
greet("Mohit")
```

Output:

```
Welcome Student
Welcome Mohit
```

Default parameters make functions more flexible.

## 9. Variable-Length Arguments

Python allows functions to accept a variable number of arguments.

### A. *args

`*args` collects additional positional arguments into a tuple.

Example:

```
def calculate_sum(*numbers):
    return sum(numbers)


print(calculate_sum(10, 20))
print(calculate_sum(10, 20, 30))
```

Output:

```
30
60
```

### B. **kwargs

`**kwargs` collects additional keyword arguments into a dictionary.

Example:

```
def display_info(**details):
    for key, value in details.items():
        print(key, ":", value)


display_info(
    username="student",
    course="Cybersecurity",
    year=1
)
```

Output:

```
username : student
course : Cybersecurity
year : 1
```

## 10. Scope of Variables in Functions

Scope determines where a variable can be accessed.

### A. Local Variable

A variable created inside a function is local to that function.

```
def display():
    message = "Hello"
    print(message)


display()
```

The variable `message` cannot normally be accessed outside the function.

### B. Global Variable

A variable defined outside functions has global scope within its module.

```
username = "student"


def display():
    print(username)


display()
```

### C. Modifying a Global Variable

The `global` keyword allows a function to rebind a global variable.

```
count = 0


def update_count():
    global count
    count = count + 1


update_count()

print(count)
```

Output:

```
1
```

Use global variables carefully because excessive shared state makes programs harder to maintain.

Detailed topic: [[Scope and Lifetime]]

## 11. Nested Functions

A nested function is a function defined inside another function.

Example:

```
def outer():
    print("Outer function")

    def inner():
        print("Inner function")

    inner()


outer()
```

Output:

```
Outer function
Inner function
```

Nested functions can help organize internal logic and are also used in closures and decorators.

## 12. Recursive Functions

A recursive function is a function that calls itself.

A recursive function needs:

1. A base case that stops recursion.
    
2. A recursive case that moves toward the base case.
    

Example:

```
def factorial(number):

    if number == 0:
        return 1

    return number * factorial(number - 1)


print(factorial(5))
```

Output:

```
120
```

Detailed topic: [[Recursion]]

## 13. Functions and Modular Programming

Functions help divide applications into independent components.

For example, a security application might contain:

```
def collect_logs():
    pass


def analyze_logs():
    pass


def generate_report():
    pass


def main():
    collect_logs()
    analyze_logs()
    generate_report()


if __name__ == "__main__":
    main()
```

Here:

- `collect_logs()` handles log collection.
    
- `analyze_logs()` handles analysis.
    
- `generate_report()` handles reporting.
    
- `main()` coordinates execution.
    

The `if __name__ == "__main__":` condition ensures that `main()` runs when the file is executed directly, rather than simply being imported as a module.

The `pass` statements are placeholders; these functions do not perform actual work yet.

## 14. Functions in Cybersecurity

Functions are useful for creating reusable security operations.

### A. File Hashing Function

```
import hashlib


def calculate_hash(data):
    return hashlib.sha256(data).hexdigest()


sample = b"ROOTLOG"

print(calculate_hash(sample))
```

The function accepts bytes and returns a SHA-256 hexadecimal digest.

### B. IP Address Validation Function

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

### C. Log Analysis Function

```
def find_failed_events(logs):

    for entry in logs:
        if "FAILED" in entry:
            print(entry)


sample_logs = [
    "LOGIN SUCCESS",
    "LOGIN FAILED",
    "FILE ACCESS",
    "LOGIN FAILED"
]

find_failed_events(sample_logs)
```

Output:

```
LOGIN FAILED
LOGIN FAILED
```

### D. Password Validation Function

```
def check_password_length(password):

    if len(password) >= 12:
        return True

    return False


print(check_password_length("ExamplePassword123"))
```

This checks only password length. It is not a complete password-strength or authentication system.

## 15. Best Practices for Writing Functions

1. Use meaningful function names.
    
2. Give each function a clear responsibility.
    
3. Avoid unnecessarily long functions.
    
4. Use parameters instead of excessive global variables.
    
5. Return results when the caller needs to use them.
    
6. Handle expected errors appropriately.
    
7. Add docstrings to explain public functions.
    
8. Follow consistent naming conventions.
    
9. Avoid unnecessary side effects.
    
10. Write tests for important functions.
    

### Example With a Docstring

```
def calculate_square(number):
    """Return the square of a number."""
    return number * number


print(calculate_square(5))
```

Output:

```
25
```

## 16. Common Function Errors

### A. Calling an Undefined Function

```
# This raises NameError:
# greet()
```

If `greet()` has not been defined or imported, Python cannot find it.

### B. Incorrect Number of Arguments

```
def add(a, b):
    return a + b


# This raises TypeError:
# add(10)
```

The function requires two arguments.

### C. Missing Return Statement

```
def add(a, b):
    result = a + b


print(add(10, 20))
```

Output:

```
None
```

The function calculates a result but does not return it.

### D. Incorrect Indentation

```
def greet():
    print("Hello")
```

The function body must be indented.

## 17. Practical Exercises

### Exercise 1: Greeting Function

Create a function named `greet()` that displays:

```
Welcome to ROOTLOG
```

Call the function three times.

### Exercise 2: Calculator Function

Create four functions:

- `add()`
    
- `subtract()`
    
- `multiply()`
    
- `divide()`
    

Each function should accept two numbers and return the result.

Handle division by zero safely.

### Exercise 3: File Hashing

Create a function named `calculate_sha256()`.

Requirements:

1. Accept a bytes object.
    
2. Calculate its SHA-256 digest.
    
3. Return the hexadecimal digest.
    
4. Test it with `b"ROOTLOG"`.
    

### Exercise 4: IP Validation

Create a function that accepts an IP address and returns whether it is valid.

Use Python's `ipaddress` module.

### Exercise 5: Log Analysis

Create a function that accepts a list of sample log entries.

Count and return the number of entries containing `FAILED`.

### Exercise 6: Password Validation

Create a function that checks whether a password contains at least 12 characters.

Return `True` or `False`.

Remember that length alone does not establish password security.

## 18. Key Takeaways

- A function is a reusable block of code.
    
- Python uses `def` to define functions.
    
- Functions execute when called.
    
- Parameters receive values from arguments.
    
- `return` sends a result to the caller.
    
- Python supports built-in, user-defined, and lambda functions.
    
- `*args` accepts variable positional arguments.
    
- `**kwargs` accepts variable keyword arguments.
    
- Variable scope determines where names can be accessed.
    
- Recursive functions call themselves.
    
- Functions help build modular cybersecurity applications.
    

## 19. Related Topics

- [[Introduction to Python]]
    
- [[Python Syntax]]
    
- [[Python Variables and Data Types]]
    
- [[Python Control Flow]]
    
- [[Function Parameters and Arguments]]
    
- [[Return Values]]
    
- [[Scope and Lifetime]]
    
- [[Recursion]]
    
- [[Modules and Libraries]]
    
- [[Python File Handling]]
    
- [[Python for Cybersecurity]]
    
- [[Automation and Scripting]]