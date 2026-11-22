> Understand how functions send results back to the part of a program that called them.

## 1. What Is a Return Value?

A **return value** is the result that a function sends back to its caller after performing an operation.

In Python, the `return` statement is used to send a value back.

Example:

```
def add(a, b):
    return a + b

result = add(10, 20)

print(result)
```

Output:

```
30
```

Explanation:

- `add()` receives two arguments.
    
- It calculates their sum.
    
- `return` sends the result back.
    
- The returned value is stored in `result`.
    

## 2. Return vs Print

`return` and `print()` have different purposes.

|`return`|`print()`|
|---|---|
|Sends a value back to the caller|Displays information on the screen|
|Can be stored in a variable|Does not provide the displayed value as the function result|
|Can be used in further calculations|Primarily used for output|
|Ends the current function execution|Does not normally end the function|

Example using `print()`:

```
def add(a, b):
    print(a + b)

result = add(10, 20)

print("Result variable:", result)
```

Output:

```
30
Result variable: None
```

The function displays `30`, but it does not return that value. Python returns `None` when a function finishes without an explicit return value.

Example using `return`:

```
def add(a, b):
    return a + b

result = add(10, 20)

print("Result variable:", result)
```

Output:

```
Result variable: 30
```

**Remember:** Use `print()` to display information and `return` to provide a result to other parts of your program.

## 3. Basic Return Statement

Syntax:

```
def function_name():
    return value
```

Example:

```
def get_message():
    return "Learning Programming"

message = get_message()

print(message)
```

Output:

```
Learning Programming
```

## 4. Returning Different Data Types

A Python function can return different types of values.

### Returning an Integer

```
def get_age():
    return 18

print(get_age())
```

### Returning a String

```
def get_name():
    return "Mohit"

print(get_name())
```

### Returning a Boolean

```
def is_valid():
    return True

print(is_valid())
```

### Returning a List

```
def get_numbers():
    return [10, 20, 30]

print(get_numbers())
```

### Returning a Dictionary

```
def get_student():
    return {
        "name": "Mohit",
        "role": "Student"
    }

print(get_student())
```

## 5. Returning Multiple Values

Python allows a function to return multiple values.

```
def calculate(a, b):
    total = a + b
    difference = a - b

    return total, difference

sum_result, difference_result = calculate(20, 10)

print("Sum:", sum_result)
print("Difference:", difference_result)
```

Output:

```
Sum: 30
Difference: 10
```

Technically, Python packages these returned values into a tuple, which can be unpacked into separate variables.

## 6. The Return Statement Ends Function Execution

When Python executes a `return` statement, the function immediately finishes.

Example:

```
def check_number(number):
    if number > 0:
        return "Positive"

    return "Zero or Negative"

print(check_number(10))
print(check_number(-5))
```

Output:

```
Positive
Zero or Negative
```

Any statements written after an executed `return` in the same function block are not executed.

## 7. Returning Values from Conditional Statements

Functions can return different results depending on conditions.

```
def check_login(failed_attempts):
    if failed_attempts >= 5:
        return "Account requires investigation"

    return "No alert"

print(check_login(2))
print(check_login(6))
```

Output:

```
No alert
Account requires investigation
```

This allows a function to make a decision and send the result to another part of the program.

## 8. Return Values in C

C functions can return values using a declared return type.

Example:

```
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(10, 20);

    printf("Result: %d\n", result);

    return 0;
}
```

Output:

```
Result: 30
```

Explanation:

- `int` specifies the return type.
    
- `add()` returns an integer.
    
- `result` stores the returned value.
    

A function declared with `void` does not return a value.

## 9. Return Values in JavaScript

JavaScript uses the `return` statement to send values back.

Example:

```
function add(a, b) {
    return a + b;
}

const result = add(10, 20);

console.log(result);
```

Output:

```
30
```

JavaScript functions return `undefined` if they finish without an explicit return value.

## 10. Return Values in Cybersecurity

Return values are important in security scripts because different operations produce results that other functions can use.

### Example 1: SHA-256 Hash Calculation

```
import hashlib

def calculate_hash(data):
    return hashlib.sha256(data.encode()).hexdigest()

hash_value = calculate_hash("ROOTLOG")

print("SHA-256:", hash_value)
```

The function returns the calculated hash as a string.

### Example 2: Checking a Password Length

```
def check_password_length(password):
    if len(password) >= 12:
        return True

    return False

result = check_password_length("ExamplePassword123")

print("Length requirement met:", result)
```

This checks only password length. It does not determine whether a password is secure overall.

### Example 3: Analyzing a Login Event

```
def analyze_login(status):
    if status == "Failed":
        return "Investigate login failure"

    return "Login successful"

result = analyze_login("Failed")

print(result)
```

The returned message can be passed to another function for reporting or logging.

## 11. Common Mistakes

1. Using `print()` when a function needs to return a value.
    
2. Forgetting the `return` statement.
    
3. Assuming that displaying a result means the function returned it.
    
4. Writing code after `return` and expecting it to execute.
    
5. Forgetting that a function without an explicit return value returns `None` in Python.
    
6. Returning the wrong data type.
    
7. Ignoring the value returned by a function.
    

## 12. Key Takeaways

- A return value is the result sent back by a function.
    
- Python uses the `return` statement.
    
- `return` and `print()` are not interchangeable.
    
- A returned value can be stored in a variable.
    
- Functions can return strings, numbers, lists, dictionaries, and other objects.
    
- Python can return multiple values using tuple packing.
    
- An executed `return` ends the current function.
    
- C requires a declared return type.
    
- JavaScript returns `undefined` when no explicit value is returned.
    

## 13. Questions and Doubts

- What is a return value?
    
- How is `return` different from `print()`?
    
- What happens when a Python function has no return statement?
    
- Can a function return multiple values?
    
- Why are return values useful in cybersecurity scripts?
    

## 14. Practical Tasks

Complete these tasks in Python:

1. Create a function that returns the square of a number.
    
2. Create a function that accepts two numbers and returns their average.
    
3. Create a function that returns `True` if a number is even and `False` otherwise.
    
4. Create a function that returns the largest of three numbers.
    
5. Create a function that returns both the sum and difference of two numbers.
    
6. Create a function that accepts a login status and returns an appropriate security message.
    
7. Create a function that calculates and returns the SHA-256 hash of a string.
    

**Challenge:** Create a program with three functions:

- One function accepts a username.
    
- One function checks whether the username is empty and returns a Boolean result.
    
- One function displays an appropriate message based on that result.