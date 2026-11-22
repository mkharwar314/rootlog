> Understand how programs make decisions and execute different instructions depending on whether conditions are true or false.

## 1. Introduction to Conditional Statements

Conditional statements allow a program to make decisions based on specific conditions.

A condition is an expression that evaluates to either:

- `True`
    
- `False`
    

The program uses the result to decide which instructions to execute.

### Example

```
age = 18

if age >= 18:
    print("Eligible to vote")
else:
    print("Not eligible to vote")
```

Output:

```
Eligible to vote
```

The program checks whether the age is at least 18 and selects the appropriate execution path.

## 2. Why Conditional Statements Are Important

Conditional statements are used to:

1. Validate user input.
    
2. Check authentication credentials.
    
3. Control access to resources.
    
4. Make decisions in applications.
    
5. Handle errors and exceptions.
    
6. Control program execution.
    

### Cybersecurity Example

A login system may check whether a password matches the stored password hash before allowing authentication to continue.

```
password_correct = True

if password_correct:
    print("Authentication successful")
else:
    print("Authentication failed")
```

This is a simplified demonstration, not a secure authentication implementation.

## 3. The `if` Statement

The `if` statement executes a block of code only when its condition is true.

### Syntax

```
if condition:
    # Code executes when condition is true
```

### Example

```
temperature = 30

if temperature > 25:
    print("It is warm")
```

Output:

```
It is warm
```

If the condition is false, the block is skipped.

## 4. The `if-else` Statement

The `if-else` statement provides two possible execution paths.

### Syntax

```
if condition:
    # Executes when true
else:
    # Executes when false
```

### Example

```
number = 7

if number % 2 == 0:
    print("Even number")
else:
    print("Odd number")
```

Output:

```
Odd number
```

The modulo operator `%` returns the remainder after division.

## 5. The `if-elif-else` Statement

The `elif` keyword means "else if".

It allows a program to check multiple conditions in sequence.

### Syntax

```
if condition1:
    # First condition
elif condition2:
    # Second condition
elif condition3:
    # Third condition
else:
    # Default case
```

### Example

```
marks = 75

if marks >= 90:
    print("Grade A")
elif marks >= 75:
    print("Grade B")
elif marks >= 50:
    print("Grade C")
else:
    print("Fail")
```

Output:

```
Grade B
```

Python checks conditions from top to bottom. Once a condition is true, the remaining branches are skipped.

## 6. Nested Conditional Statements

A nested conditional is a conditional statement placed inside another conditional block.

### Example

```
username = "admin"
password_correct = True

if username == "admin":
    if password_correct:
        print("Access granted")
    else:
        print("Incorrect password")
else:
    print("Unknown user")
```

Nested conditions are useful when one decision depends on another.

However, deeply nested conditions can make code difficult to understand. Consider using functions or logical operators when appropriate.

## 7. Comparison Operators in Conditions

Comparison operators compare values and produce a Boolean result.

|Operator|Meaning|Example|
|---|---|---|
|`==`|Equal to|`a == b`|
|`!=`|Not equal to|`a != b`|
|`>`|Greater than|`a > b`|
|`<`|Less than|`a < b`|
|`>=`|Greater than or equal to|`a >= b`|
|`<=`|Less than or equal to|`a <= b`|

Example:

```
port = 443

if port == 443:
    print("HTTPS port")
```

## 8. Logical Operators in Conditions

Logical operators combine or reverse conditions.

|Operator|Meaning|Result|
|---|---|---|
|`and`|Both conditions must be true|True only when both are true|
|`or`|At least one condition must be true|True when either is true|
|`not`|Reverses the Boolean result|True becomes False and vice versa|

### 8.1 AND Operator

```
age = 20
has_id = True

if age >= 18 and has_id:
    print("Requirements satisfied")
```

Both conditions must be true.

### 8.2 OR Operator

```
is_admin = False
is_authorized_user = True

if is_admin or is_authorized_user:
    print("Access condition satisfied")
```

At least one condition must be true.

### 8.3 NOT Operator

```
account_locked = False

if not account_locked:
    print("Account is not locked")
```

The `not` operator reverses the Boolean value.

## 9. Conditional Statements in C

C uses `if`, `else if`, and `else` for decision-making.

### Example

```
#include <stdio.h>

int main() {
    int age = 18;

    if (age >= 18) {
        printf("Eligible\n");
    } else {
        printf("Not eligible\n");
    }

    return 0;
}
```

Unlike Python, C uses braces `{}` to define blocks and parentheses around conditions.

### 9.1 Else-if Ladder

```
#include <stdio.h>

int main() {
    int marks = 75;

    if (marks >= 90) {
        printf("Grade A\n");
    } else if (marks >= 75) {
        printf("Grade B\n");
    } else if (marks >= 50) {
        printf("Grade C\n");
    } else {
        printf("Fail\n");
    }

    return 0;
}
```

## 10. Conditional Statements in JavaScript

JavaScript also supports `if`, `else if`, and `else`.

### Example

```
let age = 18;

if (age >= 18) {
    console.log("Eligible");
} else {
    console.log("Not eligible");
}
```

### 10.1 Strict Equality

JavaScript provides two equality operators:

|Operator|Meaning|
|---|---|
|`==`|Compares values after possible type coercion|
|`===`|Compares value and type without coercion|

Example:

```
console.log(10 == "10");  
console.log(10 === "10");
```

Output:

```
true
false
```

Using `===` is generally preferable when you want to avoid unexpected type coercion.

## 11. The `switch` Statement

A `switch` statement selects a code block based on the value of an expression.

It is available in languages such as C and JavaScript.

### C Example

```
#include <stdio.h>

int main() {
    int choice = 2;

    switch (choice) {
        case 1:
            printf("Start\n");
            break;

        case 2:
            printf("Settings\n");
            break;

        case 3:
            printf("Exit\n");
            break;

        default:
            printf("Invalid choice\n");
    }

    return 0;
}
```

The `break` statement prevents execution from continuing into the next case.

### JavaScript Example

```
let choice = 2;

switch (choice) {
    case 1:
        console.log("Start");
        break;

    case 2:
        console.log("Settings");
        break;

    case 3:
        console.log("Exit");
        break;

    default:
        console.log("Invalid choice");
}
```

Python does not have a traditional `switch` statement. It provides `match-case` in Python 3.10 and later.

## 12. Ternary Conditional Operator

The ternary operator provides a compact way to select between two expressions.

It is supported by C and JavaScript.

### C Example

```
int age = 20;

printf("%s", age >= 18 ? "Adult" : "Minor");
```

### JavaScript Example

```
let age = 20;

let result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

Python has a conditional expression with different syntax:

```
age = 20

result = "Adult" if age >= 18 else "Minor"

print(result)
```

Use these expressions for simple decisions. Complex logic is usually clearer with regular conditional blocks.

## 13. Conditional Statements in Cybersecurity

Conditional statements are essential for security-related logic.

### 13.1 Authentication

A program checks whether supplied credentials meet authentication requirements.

### 13.2 Access Control

A system checks whether a user has permission to access a resource.

### 13.3 Input Validation

A program checks whether user input meets expected requirements.

### 13.4 Network Monitoring

A monitoring script can check whether a port, service, or connection matches a defined condition.

### 13.5 Log Analysis

A program can identify suspicious events based on event IDs, source addresses, or failed login counts.

### Example: Simple Log Classification

```
failed_attempts = 6
threshold = 5

if failed_attempts > threshold:
    print("Investigate repeated failed logins")
else:
    print("No threshold exceeded")
```

This is a simple classification rule, not proof of an attack. Investigation requires additional context.

## 14. Common Mistakes

1. Using `=` instead of `==` in a comparison.
    
2. Forgetting the colon after Python's `if`, `elif`, or `else`.
    
3. Incorrect indentation in Python.
    
4. Forgetting braces in C or JavaScript.
    
5. Writing conditions in the wrong order.
    
6. Using too many nested conditions.
    
7. Ignoring unexpected input types.
    
8. Assuming a condition being true automatically makes an operation secure.
    

## 15. Key Takeaways

- Conditional statements allow programs to make decisions.
    
- `if` executes code when a condition is true.
    
- `else` handles the alternative path.
    
- `elif` checks additional conditions in Python.
    
- Nested conditions place decisions inside other decisions.
    
- Comparison and logical operators build conditions.
    
- `switch` is useful for selecting among fixed cases.
    
- Ternary expressions provide compact conditional logic.
    
- Conditional statements are important in authentication, access control, validation, and security monitoring.
    

## 16. Questions and Doubts

1. What is a conditional statement?
    
2. What is the difference between `if` and `if-else`?
    
3. What is the purpose of `elif`?
    
4. What is a nested conditional statement?
    
5. What is the difference between `and` and `or`?
    
6. What is the purpose of the `switch` statement?
    
7. What is the difference between `==` and `===` in JavaScript?
    
8. How are conditional statements used in cybersecurity?
    

## 17. Practical Tasks

### Task 1 — Even or Odd

Write a Python program that accepts an integer and checks whether it is even or odd.

### Task 2 — Grade Calculator

Accept marks from the user and display a grade:

- 90–100: A
    
- 75–89: B
    
- 50–74: C
    
- Below 50: Fail
    

Also reject marks outside the range 0–100.

### Task 3 — Login Decision

Create a simplified program that checks a username and a password.

Display whether the supplied values match the expected values.

Do not use real passwords or store actual credentials in this exercise.

### Task 4 — Port Classification

Accept a port number and classify:

- `22`: SSH
    
- `53`: DNS
    
- `80`: HTTP
    
- `443`: HTTPS
    
- Any other valid port: Other port
    

Validate that the port is between 1 and 65535.

### Task 5 — Compare Languages

Write a basic conditional program in Python, C, and JavaScript.

Identify how each language defines and executes conditional blocks.

## Related Notes

- [[Introduction to Programming]]
    
- [[Variables and Constants]]
    
- [[Data Types]]
    
- [[Operators]]
    
- [[Type Conversion]]
    
- [[Input and Output]]
    
- [[Loops]]
    
- [[Break and Continue]]
    
- [[Python Programming]]
    
- [[C and C++ Programming]]
    
- [[JavaScript Programming]]
    
- [[Input Validation]]
    
- [[Authentication and Authorization]]
    
- [[Secure Coding]]