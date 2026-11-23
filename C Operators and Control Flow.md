> Learn how C operators perform calculations and comparisons, and how control-flow statements determine the order in which a program executes.

## 1. What Are Operators?

Operators are symbols that perform operations on variables and values.

Example:

```
int a = 10;
int b = 5;

int result = a + b;
```

Here:

- `+` is an operator.
    
- `a` and `b` are operands.
    
- `result` stores the result.
    

C provides several categories of operators.

## 2. Arithmetic Operators

Arithmetic operators perform mathematical calculations.

|Operator|Operation|Example|
|---|---|---|
|`+`|Addition|`a + b`|
|`-`|Subtraction|`a - b`|
|`*`|Multiplication|`a * b`|
|`/`|Division|`a / b`|
|`%`|Modulus (remainder)|`a % b`|

Example:

```
#include <stdio.h>

int main(void)
{
    int a = 10;
    int b = 3;

    printf("Addition: %d\n", a + b);
    printf("Subtraction: %d\n", a - b);
    printf("Multiplication: %d\n", a * b);
    printf("Division: %d\n", a / b);
    printf("Remainder: %d\n", a % b);

    return 0;
}
```

Output:

```
Addition: 13
Subtraction: 7
Multiplication: 30
Division: 3
Remainder: 1
```

**Important:** When both operands are integers, division produces an integer result, with any fractional part discarded.

## 3. Relational Operators

Relational operators compare two values.

They produce:

- `1` for true.
    
- `0` for false.
    

|Operator|Meaning|
|---|---|
|`==`|Equal to|
|`!=`|Not equal to|
|`>`|Greater than|
|`<`|Less than|
|`>=`|Greater than or equal to|
|`<=`|Less than or equal to|

Example:

```
#include <stdio.h>

int main(void)
{
    int a = 10;
    int b = 5;

    printf("%d\n", a > b);
    printf("%d\n", a == b);
    printf("%d\n", a < b);

    return 0;
}
```

Output:

```
1
0
0
```

## 4. Logical Operators

Logical operators combine or reverse conditions.

|Operator|Meaning|
|---|---|
|`&&`|Logical AND|
|`||`|Logical OR|
|`!`|Logical NOT|

### Logical AND

Returns true when both conditions are true.

```
if (age >= 18 && age <= 60)
{
    printf("Condition satisfied");
}
```

### Logical OR

Returns true when at least one condition is true.

```
if (role == 1 || role == 2)
{
    printf("Access category accepted");
}
```

### Logical NOT

Reverses the truth value.

```
if (!is_blocked)
{
    printf("Account is not blocked");
}
```

## 5. Assignment Operators

Assignment operators assign values to variables.

|Operator|Example|Equivalent|
|---|---|---|
|`=`|`a = 10`|Assign 10|
|`+=`|`a += 5`|`a = a + 5`|
|`-=`|`a -= 5`|`a = a - 5`|
|`*=`|`a *= 5`|`a = a * 5`|
|`/=`|`a /= 5`|`a = a / 5`|
|`%=`|`a %= 5`|`a = a % 5`|

Example:

```
int number = 10;

number += 5;

printf("%d", number);
```

Output:

```
15
```

## 6. Increment and Decrement Operators

These operators increase or decrease a variable by one.

|Operator|Meaning|
|---|---|
|`++`|Increment|
|`--`|Decrement|

### Pre-increment

Increments first, then produces the updated value.

```
int a = 5;

printf("%d\n", ++a);
```

Output:

```
6
```

### Post-increment

Produces the original value, then increments the variable.

```
int a = 5;

printf("%d\n", a++);
printf("%d\n", a);
```

Output:

```
5
6
```

The same distinction applies to pre-decrement and post-decrement.

## 7. Bitwise Operators

Bitwise operators perform operations on individual bits of integer values.

|Operator|Meaning|
|---|---|
|`&`|Bitwise AND|
|`|`|Bitwise OR|
|`^`|Bitwise XOR|
|`~`|Bitwise NOT|
|`<<`|Left shift|
|`>>`|Right shift|

Example:

```
#include <stdio.h>

int main(void)
{
    int a = 5;
    int b = 3;

    printf("AND: %d\n", a & b);
    printf("OR: %d\n", a | b);
    printf("XOR: %d\n", a ^ b);

    return 0;
}
```

Binary representation:

```
5 = 0101
3 = 0011
```

Results:

```
AND = 0001 = 1
OR  = 0111 = 7
XOR = 0110 = 6
```

Bitwise operations are useful in:

- Low-level programming.
    
- Permission flags.
    
- Hardware programming.
    
- Cryptographic implementations.
    
- Network protocol analysis.
    

## 8. Conditional Operator

The conditional operator `?:` is a compact way to select between two expressions.

Syntax:

```
condition ? expression1 : expression2;
```

Example:

```
#include <stdio.h>

int main(void)
{
    int age = 20;

    char *result = (age >= 18) ? "Adult" : "Minor";

    printf("%s\n", result);

    return 0;
}
```

Output:

```
Adult
```

Use it for simple conditions. Complex logic is generally easier to read with `if-else`.

## 9. Operator Precedence

Operator precedence determines which operations are grouped first in an expression.

Example:

```
int result = 10 + 5 * 2;
```

Multiplication is evaluated before addition.

Result:

```
20
```

Use parentheses to make expressions clearer:

```
int result = (10 + 5) * 2;
```

Result:

```
30
```

**Best practice:** Do not depend on unclear expressions. Use parentheses and avoid modifying the same variable multiple times within an expression.

## 10. What Is Control Flow?

Control flow determines the order in which program instructions execute.

C provides several control-flow structures:

1. Sequential execution.
    
2. Conditional statements.
    
3. Loops.
    
4. Jump statements.
    

## 11. Sequential Execution

In sequential execution, instructions run one after another.

Example:

```
#include <stdio.h>

int main(void)
{
    int a = 10;
    int b = 20;
    int sum = a + b;

    printf("Sum: %d\n", sum);

    return 0;
}
```

The statements execute in their written order.

## 12. Conditional Statements

Conditional statements execute different blocks depending on whether conditions are true or false.

### 12.1 `if` Statement

Executes a block when the condition is true.

```
int age = 20;

if (age >= 18)
{
    printf("Eligible");
}
```

### 12.2 `if-else` Statement

Provides two possible execution paths.

```
int number = 7;

if (number % 2 == 0)
{
    printf("Even");
}
else
{
    printf("Odd");
}
```

### 12.3 `else-if` Ladder

Checks multiple conditions in sequence.

```
int marks = 85;

if (marks >= 90)
{
    printf("Grade A");
}
else if (marks >= 75)
{
    printf("Grade B");
}
else if (marks >= 50)
{
    printf("Grade C");
}
else
{
    printf("Fail");
}
```

The first matching condition is executed.

### 12.4 Nested `if`

An `if` statement can be placed inside another `if` statement.

```
int age = 20;
int has_id = 1;

if (age >= 18)
{
    if (has_id == 1)
    {
        printf("Requirements satisfied");
    }
}
```

## 13. The `switch` Statement

A `switch` statement selects a code block based on an integer-compatible expression, an enumeration value, or a character.

Example:

```
#include <stdio.h>

int main(void)
{
    int choice = 2;

    switch (choice)
    {
        case 1:
            printf("Option One");
            break;

        case 2:
            printf("Option Two");
            break;

        case 3:
            printf("Option Three");
            break;

        default:
            printf("Invalid option");
    }

    return 0;
}
```

Output:

```
Option Two
```

### Understanding `break`

`break` exits the switch statement.

Without it, execution can continue into subsequent cases. This behaviour is called fall-through.

### Understanding `default`

The `default` block executes when no case matches.

## 14. Loops in C

Loops repeat a block of code while a condition is satisfied.

C provides three common loop structures:

- `for`
    
- `while`
    
- `do-while`
    

### 14.1 `for` Loop

A `for` loop is commonly used when the number of iterations is known.

Syntax:

```
for (initialization; condition; update)
{
    // Statements
}
```

Example:

```
#include <stdio.h>

int main(void)
{
    for (int i = 1; i <= 5; i++)
    {
        printf("%d\n", i);
    }

    return 0;
}
```

Output:

```
1
2
3
4
5
```

### 14.2 `while` Loop

A `while` loop repeats while its condition is true.

```
#include <stdio.h>

int main(void)
{
    int i = 1;

    while (i <= 5)
    {
        printf("%d\n", i);
        i++;
    }

    return 0;
}
```

### 14.3 `do-while` Loop

A `do-while` loop executes its body at least once before checking the condition.

```
#include <stdio.h>

int main(void)
{
    int i = 1;

    do
    {
        printf("%d\n", i);
        i++;
    }
    while (i <= 5);

    return 0;
}
```

## 15. Nested Loops

A nested loop is a loop inside another loop.

Example:

```
#include <stdio.h>

int main(void)
{
    for (int i = 1; i <= 3; i++)
    {
        for (int j = 1; j <= 3; j++)
        {
            printf("%d ", j);
        }

        printf("\n");
    }

    return 0;
}
```

Output:

```
1 2 3
1 2 3
1 2 3
```

Nested loops are useful for:

- Processing two-dimensional arrays.
    
- Working with tables.
    
- Pattern printing.
    
- Comparing multiple elements.
    

## 16. Jump Statements

Jump statements change the normal flow of program execution.

### 16.1 `break`

Terminates the nearest enclosing loop or switch statement.

```
for (int i = 1; i <= 5; i++)
{
    if (i == 3)
    {
        break;
    }

    printf("%d\n", i);
}
```

Output:

```
1
2
```

### 16.2 `continue`

Skips the remaining statements in the current loop iteration and proceeds to the next iteration.

```
for (int i = 1; i <= 5; i++)
{
    if (i == 3)
    {
        continue;
    }

    printf("%d\n", i);
}
```

Output:

```
1
2
4
5
```

### 16.3 `goto`

Transfers control to a labelled statement within the same function.

```
#include <stdio.h>

int main(void)
{
    int number = 1;

start:
    printf("%d\n", number);

    number++;

    if (number <= 3)
    {
        goto start;
    }

    return 0;
}
```

`goto` is generally avoided in ordinary application logic because it can make code harder to understand and maintain.

### 16.4 `return`

Terminates the current function and optionally returns a value.

```
int add(int a, int b)
{
    return a + b;
}
```

## 17. Short-Circuit Evaluation

Logical AND (`&&`) and logical OR (`||`) use short-circuit evaluation.

### AND

If the first condition is false, the second condition is not evaluated.

```
if (x != 0 && 100 / x > 2)
{
    printf("Condition satisfied");
}
```

The division is not evaluated when `x` is zero.

### OR

If the first condition is true, the second condition is not evaluated.

Short-circuit evaluation is useful for writing safe conditional expressions, but expressions should still be clear and easy to review.

## 18. Control Flow in Cybersecurity

Control-flow statements are important when implementing security logic.

### Example: Login Attempt Counter

```
#include <stdio.h>

int main(void)
{
    int attempts = 0;
    int max_attempts = 3;

    while (attempts < max_attempts)
    {
        printf("Login attempt: %d\n", attempts + 1);

        attempts++;
    }

    printf("Attempt limit reached.\n");

    return 0;
}
```

This example demonstrates a counter, not a complete authentication system.

A real login system must also use secure password hashing, proper account-state management, rate limiting, and appropriate error handling.

### Security Applications

Operators and control flow are used in:

- Input validation.
    
- Access-control decisions.
    
- Authentication logic.
    
- Network protocol handling.
    
- Permission checks.
    
- Security monitoring tools.
    

## 19. Common Mistakes

|Mistake|Explanation|
|---|---|
|Using `=` instead of `==`|Assignment instead of comparison|
|Missing `break`|May cause switch fall-through|
|Incorrect loop condition|May cause infinite loops or skipped iterations|
|Missing loop update|Can create an infinite loop|
|Integer division|Discards the fractional part|
|Confusing `&&` and `&`|Logical AND versus bitwise AND|
|Confusing `||`and`|`|Logical OR versus bitwise OR|
|Unclear operator precedence|Can produce unexpected expressions|

## 20. Practical Exercises

### Exercise 1 — Arithmetic Calculator

Write a program that accepts two integers and displays:

- Addition.
    
- Subtraction.
    
- Multiplication.
    
- Division, with a check for division by zero.
    

### Exercise 2 — Even or Odd

Accept an integer and determine whether it is even or odd.

### Exercise 3 — Grade Calculator

Accept marks and display a grade using an `if-else` ladder.

### Exercise 4 — Menu Program

Create a menu using `switch`:

1. Addition
    
2. Subtraction
    
3. Multiplication
    
4. Exit
    

### Exercise 5 — Multiplication Table

Use a `for` loop to print the multiplication table of a number.

### Exercise 6 — Login Attempt Counter

Write a program that allows a maximum of three attempts using a loop and a counter. Do not use real credentials.

## 21. Key Takeaways

- Operators perform calculations, comparisons, and logical operations.
    
- Arithmetic operators perform mathematical operations.
    
- Relational operators compare values.
    
- Logical operators combine conditions.
    
- Bitwise operators manipulate individual bits.
    
- Conditional statements control decisions.
    
- Loops repeat instructions.
    
- `break`, `continue`, `goto`, and `return` alter normal execution flow.
    
- Short-circuit evaluation can prevent unnecessary or unsafe operations.
    
- Control flow is fundamental to authentication and access-control logic.
    

## 22. Related Notes

- [[Introduction to C]]
    
- [[C Variables and Data Types]]
    
- [[C Functions]]
    
- [[C Arrays and Strings]]
    
- [[C Pointers]]
    
- [[C Memory Management]]
    
- [[Operators]]
    
- [[Conditional Statements]]
    
- [[Loops]]
    
- [[Break and Continue]]
    
- [[Secure Coding]]