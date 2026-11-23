> Understand how `break` and `continue` control loop execution and help programs manage repetitive operations.

## 1. Introduction

Loops execute a block of code repeatedly. Sometimes, a program needs to change the normal execution of a loop.

Two important loop-control statements are:

- **break:** Immediately terminates the nearest enclosing loop.
    
- **continue:** Skips the remaining statements in the current iteration and proceeds to the next iteration.
    

Both statements are commonly used with `for` and `while` loops.

## 2. The Break Statement

The `break` statement immediately terminates the nearest enclosing loop.

When `break` executes:

1. The current loop stops.
    
2. Remaining iterations are skipped.
    
3. Execution continues with the first statement after the loop.
    

### Example in Python

```
for number in range(1, 6):
    if number == 3:
        break

    print(number)
```

Output:

```
1
2
```

When `number` becomes `3`, the condition is true and the loop terminates.

### 2.1 Break in a While Loop

```
count = 1

while count <= 10:
    if count == 5:
        break

    print(count)
    count += 1
```

Output:

```
1
2
3
4
```

The loop stops when `count` reaches `5`.

## 3. The Continue Statement

The `continue` statement skips the remaining statements in the current iteration.

The loop then proceeds to its next iteration.

### Example in Python

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

When `number` becomes `3`, the `print()` statement is skipped for that iteration.

### 3.1 Continue in a While Loop

```
count = 0

while count < 5:
    count += 1

    if count == 3:
        continue

    print(count)
```

Output:

```
1
2
4
5
```

**Important:** In a `while` loop, make sure the condition variable is updated before `continue` when necessary. Otherwise, the loop may never terminate.

## 4. Break vs Continue

|Feature|`break`|`continue`|
|---|---|---|
|Purpose|Terminates the loop|Skips current iteration|
|Remaining iterations|Cancelled|Continue normally|
|Execution|Moves outside the loop|Moves to next iteration|
|Common use|Stop when a result is found|Skip unwanted values|

### Visual Explanation

```
BREAK:

Start loop
    |
Check condition
    |
Condition true?
    |
   YES
    |
Terminate loop
    |
Continue after loop


CONTINUE:

Start loop
    |
Check condition
    |
Condition true?
    |
   YES
    |
Skip remaining statements
    |
Next iteration
```

## 5. Break and Continue in C

C supports both statements.

### 5.1 Break in C

```
#include <stdio.h>

int main() {
    for (int i = 1; i <= 5; i++) {
        if (i == 3) {
            break;
        }

        printf("%d\n", i);
    }

    return 0;
}
```

Output:

```
1
2
```

### 5.2 Continue in C

```
#include <stdio.h>

int main() {
    for (int i = 1; i <= 5; i++) {
        if (i == 3) {
            continue;
        }

        printf("%d\n", i);
    }

    return 0;
}
```

Output:

```
1
2
4
5
```

## 6. Break and Continue in JavaScript

JavaScript also supports both statements.

### 6.1 Break in JavaScript

```
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }

    console.log(i);
}
```

### 6.2 Continue in JavaScript

```
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

The behavior is the same as in Python and C.

## 7. Break in Nested Loops

When `break` is used inside nested loops, it terminates only the nearest enclosing loop.

### Example

```
for i in range(1, 4):
    print("Outer:", i)

    for j in range(1, 4):
        if j == 2:
            break

        print("Inner:", j)
```

Output:

```
Outer: 1
Inner: 1
Outer: 2
Inner: 1
Outer: 3
Inner: 1
```

The inner loop terminates when `j` becomes `2`, but the outer loop continues.

## 8. Using a Loop Else in Python

Python supports an additional feature: the `else` clause on loops.

The `else` block executes when the loop finishes normally, without being terminated by `break`.

### Example

```
for number in range(1, 4):
    print(number)
else:
    print("Loop completed")
```

Output:

```
1
2
3
Loop completed
```

### Example with Break

```
for number in range(1, 4):
    if number == 2:
        break

    print(number)
else:
    print("Loop completed")
```

Output:

```
1
```

The `else` block does not execute because the loop ended through `break`.

This feature is useful when searching for an item and determining whether the search completed without finding it.

## 9. Practical Use Cases in Cybersecurity

### 9.1 Password Attempt Limits

A program can stop accepting attempts after a fixed number of failures.

```
attempts = 0
correct_password = "demo123"

while attempts < 3:
    password = input("Enter demonstration password: ")

    if password == correct_password:
        print("Access granted")
        break

    attempts += 1
    print("Incorrect password")

if attempts == 3:
    print("Maximum attempts reached")
```

This is a basic programming exercise, not a production authentication system.

### 9.2 Log Analysis

Use `continue` to skip irrelevant log entries.

```
logs = [
    "Login successful",
    "Login failed",
    "System started",
    "Login failed"
]

for entry in logs:
    if "failed" not in entry.lower():
        continue

    print("Suspicious entry:", entry)
```

### 9.3 Search Operations

Use `break` when the required result is found.

```
ports = [22, 53, 80, 443, 8080]

for port in ports:
    if port == 443:
        print("HTTPS port found")
        break
```

### 9.4 Data Filtering

Use `continue` to ignore records that do not meet specific conditions.

This is useful when processing large log files or datasets.

## 10. Common Mistakes

1. Confusing `break` with `continue`.
    
2. Assuming `break` terminates every nested loop.
    
3. Forgetting to update a `while` loop variable.
    
4. Placing `continue` before an essential update operation.
    
5. Using `break` when the program should only skip one iteration.
    
6. Creating unnecessary complex loop-control logic.
    
7. Forgetting that Python's loop `else` behaves differently from an ordinary `if-else`.
    

## 11. Key Takeaways

- `break` immediately terminates the nearest enclosing loop.
    
- `continue` skips the remaining statements in the current iteration.
    
- Both are supported in Python, C, and JavaScript.
    
- In nested loops, they affect the nearest enclosing loop.
    
- Python provides a loop `else` clause.
    
- These statements are useful in searching, filtering, validation, and automation.
    

## 12. Questions and Doubts

1. What is the purpose of the `break` statement?
    
2. What is the purpose of the `continue` statement?
    
3. What is the main difference between them?
    
4. What happens when `break` is used inside a nested loop?
    
5. Why can `continue` cause an infinite loop in a `while` loop?
    
6. What is Python's loop `else` clause?
    
7. How can `break` be used to limit password attempts?
    
8. How can `continue` help filter security logs?
    

## 13. Practical Tasks

### Task 1 — Stop at a Number

Write a Python program that prints numbers from 1 to 10 but stops when it reaches 6.

Use `break`.

### Task 2 — Skip Even Numbers

Write a program that displays only odd numbers from 1 to 20.

Use `continue`.

### Task 3 — Password Attempts

Create a demonstration program that permits three password attempts.

Stop the loop immediately when the correct demonstration password is entered.

### Task 4 — Failed Login Filtering

Use this sample data:

```
logs = [
    "Login successful",
    "Login failed",
    "System started",
    "Login failed",
    "File accessed",
    "Login successful"
]
```

Display only entries containing `Login failed`.

Use `continue`.

### Task 5 — Nested Loop

Create two nested loops. Use `break` in the inner loop and observe whether the outer loop continues.

## Related Notes

- [[Loops]]
    
- [[Conditional Statements]]
    
- [[Nested Loops]]
    
- [[Pattern Programming]]
    
- [[Input and Output]]
    
- [[Exception Handling]]
    
- [[Automation and Scripting]]
    
- [[Log Analysis with Python]]
    
- [[Introduction to Python]]
    
- [[C and C++ Programming]]
    
- [[JavaScript Programming]]