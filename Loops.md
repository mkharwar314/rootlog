> Understand how loops execute a block of code repeatedly and how repetition helps automate programming tasks.

## 1. Introduction to Loops

A loop is a programming structure that repeatedly executes a block of code while a condition is satisfied or for a specified number of iterations.

Without loops, programmers would need to write the same instructions repeatedly.

### Example Without a Loop

```
print("Hello")
print("Hello")
print("Hello")
print("Hello")
print("Hello")
```

### Example With a Loop

```
for i in range(5):
    print("Hello")
```

Both examples display `Hello` five times, but the loop makes the code shorter and easier to maintain.

## 2. Why Loops Are Important

Loops are used to:

1. Repeat operations.
    
2. Process large amounts of data.
    
3. Read records from files.
    
4. Automate repetitive tasks.
    
5. Analyze network and system information.
    
6. Process security logs.
    
7. Perform repeated validation.
    

### Cybersecurity Example

A security analyst may use a loop to examine multiple log entries and identify failed login attempts.

## 3. Types of Loops

Common loop structures include:

|Loop|Purpose|
|---|---|
|`for` loop|Repeats over a sequence or range|
|`while` loop|Repeats while a condition is true|
|Nested loop|A loop inside another loop|

Different programming languages implement these structures with slightly different syntax.

## 4. The `for` Loop in Python

A `for` loop iterates over items in a sequence or another iterable object.

### Syntax

```
for variable in sequence:
    # Code to execute
```

### Example

```
for number in range(5):
    print(number)
```

Output:

```
0
1
2
3
4
```

The `range(5)` function generates the values from `0` up to, but not including, `5`.

### 4.1 Using `range()`

Python's `range()` function is commonly used to generate a sequence of integers.

|Syntax|Result|
|---|---|
|`range(5)`|0, 1, 2, 3, 4|
|`range(1, 6)`|1, 2, 3, 4, 5|
|`range(2, 11, 2)`|2, 4, 6, 8, 10|

Example:

```
for number in range(1, 6):
    print(number)
```

### 4.2 Iterating Over a List

```
tools = ["Nmap", "Wireshark", "Burp Suite"]

for tool in tools:
    print(tool)
```

Output:

```
Nmap
Wireshark
Burp Suite
```

The loop processes each item in the list.

### 4.3 Iterating Over a String

```
word = "ROOTLOG"

for character in word:
    print(character)
```

Each character is processed separately.

## 5. The `while` Loop in Python

A `while` loop repeatedly executes a block as long as its condition remains true.

### Syntax

```
while condition:
    # Code to execute
```

### Example

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

The variable `count` increases after each iteration.

When it becomes greater than `5`, the condition becomes false and the loop stops.

### 5.1 Infinite Loops

An infinite loop continues running because its termination condition is never reached.

Example:

```
while True:
    print("Running")
```

This loop continues until it is interrupted.

Infinite loops can be intentional in services and interactive programs, but they must have a controlled termination mechanism.

## 6. Nested Loops

A nested loop is a loop placed inside another loop.

### Example

```
for i in range(1, 4):
    for j in range(1, 4):
        print(i, j)
```

Output:

```
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3
```

For each iteration of the outer loop, the inner loop completes all its iterations.

### Common Uses

- Working with tables.
    
- Processing two-dimensional data.
    
- Comparing multiple values.
    
- Generating patterns.
    
- Testing combinations.
    

## 7. Loops in C

C supports `for`, `while`, and `do-while` loops.

### 7.1 The `for` Loop

A `for` loop is useful when the number of iterations is known or controlled by a counter.

```
#include <stdio.h>

int main() {
    for (int i = 1; i <= 5; i++) {
        printf("%d\n", i);
    }

    return 0;
}
```

The three main parts are:

1. Initialization: `int i = 1`
    
2. Condition: `i <= 5`
    
3. Update: `i++`
    

### 7.2 The `while` Loop

```
#include <stdio.h>

int main() {
    int count = 1;

    while (count <= 5) {
        printf("%d\n", count);
        count++;
    }

    return 0;
}
```

The condition is checked before each iteration.

### 7.3 The `do-while` Loop

A `do-while` loop executes its body at least once because its condition is checked after the body.

```
#include <stdio.h>

int main() {
    int count = 1;

    do {
        printf("%d\n", count);
        count++;
    } while (count <= 5);

    return 0;
}
```

**Important:** A `do-while` loop ends with a semicolon after its condition.

## 8. Loops in JavaScript

JavaScript supports several loop structures.

### 8.1 The `for` Loop

```
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

### 8.2 The `while` Loop

```
let count = 1;

while (count <= 5) {
    console.log(count);
    count++;
}
```

### 8.3 The `do-while` Loop

```
let count = 1;

do {
    console.log(count);
    count++;
} while (count <= 5);
```

### 8.4 The `for...of` Loop

`for...of` iterates over the values of an iterable object, such as an array or string.

```
let tools = ["Nmap", "Wireshark", "Burp Suite"];

for (const tool of tools) {
    console.log(tool);
}
```

### 8.5 The `for...in` Loop

`for...in` iterates over enumerable property keys of an object.

```
let student = {
    name: "Student",
    course: "Cybersecurity"
};

for (const key in student) {
    console.log(key, student[key]);
}
```

For arrays, `for...of` is generally more suitable when you want the values.

## 9. Loop Control

Loop control statements change the normal execution of a loop.

Two important statements are:

- `break`
    
- `continue`
    

They are covered in detail in [[Break and Continue]].

### 9.1 Break

The `break` statement immediately terminates the nearest enclosing loop.

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

### 9.2 Continue

The `continue` statement skips the remaining statements in the current iteration and moves to the next iteration.

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

## 10. Loop Termination

A loop must have a suitable termination condition unless it is intentionally designed to run continuously.

Consider:

```
count = 1

while count <= 5:
    print(count)
    count += 1
```

The loop terminates because `count` eventually becomes `6`.

If the update statement is removed, the condition remains true and the loop becomes infinite.

### Common Loop Problems

- Missing counter updates.
    
- Incorrect conditions.
    
- Off-by-one errors.
    
- Unintended infinite loops.
    
- Incorrect indentation.
    
- Processing the same data repeatedly by mistake.
    

## 11. Loops and Time Complexity

Loops affect how much work a program performs.

### One Loop

```
for i in range(n):
    print(i)
```

The loop runs approximately `n` times.

Its time complexity is generally:

[  
O(n)  
]

### Nested Loops

```
for i in range(n):
    for j in range(n):
        print(i, j)
```

The inner loop runs `n` times for each of the `n` outer iterations.

Its time complexity is generally:

[  
O(n^2)  
]

Time complexity is covered in detail in [[Time and Space Complexity]].

## 12. Loops in Cybersecurity

Loops are widely used in security automation and analysis.

### 12.1 Log Analysis

A program can iterate through log entries and identify records that match a condition.

```
logs = [
    "Login successful",
    "Login failed",
    "Login failed",
    "Login successful"
]

for entry in logs:
    if "failed" in entry.lower():
        print("Failed login detected:", entry)
```

### 12.2 File Processing

A script can process multiple files in a directory.

### 12.3 Network Monitoring

A monitoring program can periodically check authorized systems or services.

### 12.4 Data Analysis

Loops can process event records, IP addresses, timestamps, and other security-related data.

**Important:** Repeated network activity should be limited to systems you own or are explicitly authorized to test. Add timeouts, rate limits, and termination controls where appropriate.

## 13. Common Mistakes

1. Forgetting to update a counter in a `while` loop.
    
2. Creating an unintended infinite loop.
    
3. Using an incorrect range.
    
4. Confusing `break` and `continue`.
    
5. Using nested loops unnecessarily.
    
6. Forgetting Python indentation.
    
7. Miscalculating the number of iterations.
    
8. Ignoring the performance cost of repeated operations.
    

## 14. Key Takeaways

- Loops repeat instructions.
    
- `for` loops iterate over sequences or ranges.
    
- `while` loops continue while a condition is true.
    
- Nested loops contain another loop.
    
- C and JavaScript also support `do-while`.
    
- `break` terminates a loop.
    
- `continue` skips the current iteration.
    
- Loop design affects program performance.
    
- Loops are important for automation, log analysis, and security tools.
    

## 15. Questions and Doubts

1. What is a loop?
    
2. Why are loops used in programming?
    
3. What is the difference between `for` and `while`?
    
4. What is an infinite loop?
    
5. What is a nested loop?
    
6. What is the difference between `while` and `do-while`?
    
7. What is the purpose of `break`?
    
8. What is the purpose of `continue`?
    
9. What is an off-by-one error?
    
10. How are loops used in cybersecurity?
    

## 16. Practical Tasks

### Task 1 — Number Sequence

Write a Python program that prints numbers from 1 to 20 using a `for` loop.

### Task 2 — Multiplication Table

Accept a number and display its multiplication table from 1 to 10.

### Task 3 — Sum of Numbers

Calculate the sum of all integers from 1 to 100 using a loop.

### Task 4 — Password Attempts

Create a simplified program that allows a maximum of three attempts to enter a demonstration password.

After three incorrect attempts, display an account lock message.

Use a placeholder password only. Do not use a real account password.

### Task 5 — Failed Login Analysis

Use this sample data:

```
logs = [
    "Login successful",
    "Login failed",
    "Login failed",
    "Login successful",
    "Login failed"
]
```

Write a program that counts the number of failed login entries.

### Task 6 — Compare Languages

Write a basic `for` loop in Python, C, and JavaScript that displays numbers from 1 to 5.

Compare their syntax.

## Related Notes

- [[Introduction to Programming]]
    
- [[Operators]]
    
- [[Conditional Statements]]
    
- [[Break and Continue]]
    
- [[Nested Loops]]
    
- [[Pattern Programming]]
    
- [[Algorithms]]
    
- [[Time and Space Complexity]]
    
- [[Introduction to Python]]
    
- [[C and C++ Programming]]
    
- [[JavaScript Programming]]
    
- [[Automation and Scripting]]
    
- [[Log Analysis with Python]]