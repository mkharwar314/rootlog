## 1. Introduction

Control flow determines the order in which statements are executed in a program.

By default, Python executes statements from top to bottom. Control flow statements allow a program to make decisions, repeat operations, and change the normal execution sequence.

Python control flow includes:

1. Conditional statements
    
2. Loops
    
3. Loop-control statements
    
4. Exception handling
    
5. Function calls and returns
    

Control flow is essential for building programs that respond to different conditions and situations.

## 2. Types of Control Flow

|Type|Purpose|Python Statements|
|---|---|---|
|Sequential|Executes statements in order|Normal statements|
|Selection|Chooses between alternatives|`if`, `elif`, `else`|
|Iteration|Repeats instructions|`for`, `while`|
|Jump|Changes normal execution|`break`, `continue`, `return`|

## 3. Sequential Execution

Sequential execution means instructions run one after another in the order they appear.

Example:

```
print("Starting program")

name = "ROOTLOG"

print("Learning Python")
print(name)
```

Output:

```
Starting program
Learning Python
ROOTLOG
```

Each statement executes before the next statement.

## 4. Conditional Statements

Conditional statements allow a program to execute different code depending on whether a condition is true or false.

Python provides:

- `if`
    
- `elif`
    
- `else`
    

Example:

```
age = 18

if age >= 18:
    print("Eligible")
else:
    print("Not eligible")
```

Output:

```
Eligible
```

### A. if Statement

The `if` statement executes a block when its condition evaluates to true.

```
temperature = 35

if temperature > 30:
    print("High temperature")
```

### B. if-else Statement

The `else` block executes when the `if` condition is false.

```
number = 7

if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

### C. if-elif-else Statement

The `elif` keyword allows multiple conditions to be checked in sequence.

```
marks = 75

if marks >= 90:
    print("Grade A")
elif marks >= 75:
    print("Grade B")
elif marks >= 50:
    print("Grade C")
else:
    print("Needs improvement")
```

Output:

```
Grade B
```

### D. Nested Conditional Statements

A conditional statement can be placed inside another conditional statement.

```
username = "admin"
authenticated = True

if username == "admin":
    if authenticated:
        print("Access granted")
    else:
        print("Authentication required")
else:
    print("Unknown user")
```

Detailed topic: [[Conditional Statements]]

## 5. Loops

Loops execute a block of code repeatedly.

Python provides two main loop types:

- `for`
    
- `while`
    

### A. For Loop

A `for` loop iterates over the elements of an iterable, such as a list, string, tuple, or range.

Example:

```
for number in range(1, 6):
    print(number)
```

Output:

```
1
2
3
4
5
```

### B. While Loop

A `while` loop repeatedly executes its block while its condition remains true.

Example:

```
count = 1

while count <= 5:
    print(count)
    count += 1
```

Output:

```
1
2
3
4
5
```

### C. Nested Loops

A loop can contain another loop.

Example:

```
for i in range(1, 4):
    for j in range(1, 3):
        print(i, j)
```

Nested loops are useful for processing tables, matrices, and combinations of values.

Detailed topic: [[Loops]] and [[Nested Loops]]

## 6. Loop Control Statements

Python provides statements that change the normal behavior of loops.

### A. break

The `break` statement immediately terminates the nearest enclosing loop.

```
for number in range(1, 6):
    if number == 4:
        break

    print(number)
```

Output:

```
1
2
3
```

### B. continue

The `continue` statement skips the remaining statements in the current iteration and proceeds to the next iteration.

```
for number in range(1, 6):
    if number == 3:
        continue

    print(number)
```

Output:

```
1
2
4
5
```

### C. pass

The `pass` statement does nothing. It acts as a placeholder where Python syntax requires a statement.

```
for number in range(1, 4):
    if number == 2:
        pass

    print(number)
```

Output:

```
1
2
3
```

Detailed topic: [[Break and Continue]]

## 7. Functions and Control Flow

Functions help organize program execution into reusable blocks.

The `return` statement exits a function and optionally sends a value back to the caller.

Example:

```
def check_status(status):
    if status == "ACTIVE":
        return "System running"

    return "System inactive"


result = check_status("ACTIVE")

print(result)
```

Output:

```
System running
```

Once a function executes `return`, that function call ends.

Detailed topic: [[Introduction to Functions]]

## 8. Exception Handling and Control Flow

Exception handling allows a program to respond to runtime errors without necessarily terminating unexpectedly.

Python provides:

- `try`
    
- `except`
    
- `else`
    
- `finally`
    
- `raise`
    

Example:

```
try:
    number = int(input("Enter a number: "))
    result = 100 / number

except ValueError:
    print("Enter a valid integer")

except ZeroDivisionError:
    print("Cannot divide by zero")

else:
    print("Result:", result)

finally:
    print("Program finished")
```

The `finally` block executes whether an exception occurred or not, subject to normal interpreter termination.

Detailed topic: [[Python Exception Handling]]

## 9. Control Flow Diagram

```
        Start
          |
          v
    Execute Statement
          |
          v
    Check Condition
          |
     +----+----+
     |         |
    True      False
     |         |
     v         v
  Execute    Alternative
  Block       Block
     |         |
     +----+----+
          |
          v
     Continue Program
          |
          v
         End
```

This is a simplified representation of conditional execution. Loops add repetition to the execution flow.

## 10. Control Flow in Cybersecurity

Control flow is important in security automation and analysis.

### A. Login Attempt Monitoring

A program can check whether a login attempt succeeded or failed.

```
status = "FAILED"

if status == "FAILED":
    print("Failed login detected")
else:
    print("Login successful")
```

### B. Port Status Checking

A program can classify port numbers.

```
port = 443

if port == 80:
    print("HTTP port")

elif port == 443:
    print("HTTPS port")

elif port == 22:
    print("SSH port")

else:
    print("Other port")
```

### C. Log Filtering

A loop can process multiple log entries and identify failed events.

```
logs = [
    "LOGIN SUCCESS",
    "LOGIN FAILED",
    "FILE ACCESS",
    "LOGIN FAILED"
]

for entry in logs:
    if "FAILED" in entry:
        print("Alert:", entry)
```

Output:

```
Alert: LOGIN FAILED
Alert: LOGIN FAILED
```

### D. File Processing

A program can process multiple files using loops and conditional statements.

For example, it can select files with specific extensions or identify empty files.

Always work with authorized files and controlled lab data.

## 11. Common Control Flow Mistakes

### A. Incorrect Indentation

Incorrect:

```
if True:
print("Hello")
```

Correct:

```
if True:
    print("Hello")
```

### B. Infinite While Loop

An infinite loop occurs when the loop condition never becomes false.

Example:

```
# Avoid running this without a termination mechanism.
while True:
    print("Running")
```

For an intentional infinite loop, provide a safe exit mechanism.

### C. Incorrect Condition

```
age = 18

if age > 18:
    print("Eligible")
```

This does not execute because `18 > 18` is false.

If the requirement includes age 18, use `>=`.

### D. Incorrect Loop Control

Remember:

- `break` exits the loop.
    
- `continue` skips the current iteration.
    
- `pass` does nothing.
    

These statements are not interchangeable.

## 12. Best Practices

1. Use clear and meaningful conditions.
    
2. Avoid unnecessary nested conditions.
    
3. Ensure `while` loops have appropriate termination logic.
    
4. Use `break` and `continue` only when they improve clarity.
    
5. Keep loop bodies focused.
    
6. Handle expected exceptions.
    
7. Test boundary conditions.
    
8. Avoid deeply nested control structures when simpler alternatives exist.
    

## 13. Practical Exercises

### Exercise 1: Number Classification

Ask the user to enter a number.

Determine whether it is:

- Positive
    
- Negative
    
- Zero
    

### Exercise 2: Even Numbers

Use a `for` loop to display all even numbers between 1 and 20.

### Exercise 3: Login Attempt Simulator

Create a program that:

1. Stores a sample password.
    
2. Allows a maximum of three attempts.
    
3. Compares the entered password with the sample password.
    
4. Displays access granted when correct.
    
5. Displays access denied after three unsuccessful attempts.
    

Use only a fictional password in your local lab.

### Exercise 4: Log Analyzer

Create a list containing five sample log entries.

Use a loop to identify and display entries containing `FAILED`.

### Exercise 5: Port Classifier

Ask the user to enter a port number.

Classify these ports:

- 22 — SSH
    
- 53 — DNS
    
- 80 — HTTP
    
- 443 — HTTPS
    

Display `Unknown port` for other values.

## 14. Key Takeaways

- Control flow determines the execution order of a program.
    
- Sequential execution runs statements in order.
    
- Conditional statements select which code block executes.
    
- Loops repeat operations.
    
- `break` terminates a loop.
    
- `continue` skips the current iteration.
    
- `pass` acts as a placeholder.
    
- `return` exits a function.
    
- Exception handling manages runtime errors.
    
- Control flow is essential for cybersecurity automation and log analysis.
    

## 15. Related Topics

- [[Introduction to Python]]
    
- [[Python Syntax]]
    
- [[Python Variables and Data Types]]
    
- [[Python Operators]]
    
- [[Conditional Statements]]
    
- [[Loops]]
    
- [[Break and Continue]]
    
- [[Nested Loops]]
    
- [[Introduction to Functions]]
    
- [[Python Exception Handling]]
    
- [[Python for Cybersecurity]]
    
- [[Automation and Scripting]]