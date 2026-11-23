> Understand how functions organize C programs into reusable, modular, and maintainable blocks of code.

## 1. What Is a Function?

A **function** is a named block of code designed to perform a specific task.

Instead of writing the same code repeatedly, we can define a function once and call it whenever required.

### Example

```
#include <stdio.h>

void greet() {
    printf("Hello, World!\n");
}

int main() {
    greet();
    greet();

    return 0;
}
```

**Output:**

```
Hello, World!
Hello, World!
```

The `greet()` function is executed twice when called twice.

## 2. Why Are Functions Important?

Functions help programmers:

- Reuse code instead of repeating it.
    
- Divide large programs into smaller parts.
    
- Improve readability and organization.
    
- Simplify testing and debugging.
    
- Make programs easier to maintain.
    

## 3. Three Main Parts of a Function

A C function generally involves three stages:

1. Function declaration (prototype)
    
2. Function definition
    
3. Function call
    

### A. Function Declaration

A declaration tells the compiler about the function's name, return type, and parameters.

```
int add(int, int);
```

This tells the compiler that `add()`:

- Returns an integer.
    
- Accepts two integer arguments.
    

### B. Function Definition

A definition contains the actual code that performs the task.

```
int add(int a, int b) {
    return a + b;
}
```

### C. Function Call

A function call executes the function.

```
int result = add(10, 20);
```

**Complete example:**

```
#include <stdio.h>

int add(int, int);

int main() {
    int result = add(10, 20);

    printf("Result: %d\n", result);

    return 0;
}

int add(int a, int b) {
    return a + b;
}
```

**Output:**

```
Result: 30
```

## 4. Function Syntax

```
return_type function_name(parameters) {
    // Statements
    return value;
}
```

|Component|Meaning|
|---|---|
|`return_type`|Type of value returned|
|`function_name`|Name of the function|
|`parameters`|Inputs received by the function|
|`return`|Sends a value back to the caller|

## 5. Types of Functions

Functions can be classified into two broad categories.

### A. Library Functions

These are predefined functions provided by C libraries.

Examples:

|Function|Purpose|Header|
|---|---|---|
|`printf()`|Displays output|`stdio.h`|
|`scanf()`|Reads formatted input|`stdio.h`|
|`strlen()`|Calculates string length|`string.h`|
|`sqrt()`|Calculates square root|`math.h`|
|`strcmp()`|Compares strings|`string.h`|

Example:

```
#include <stdio.h>
#include <string.h>

int main() {
    char name[] = "Cybersecurity";

    printf("Length: %zu\n", strlen(name));

    return 0;
}
```

### B. User-Defined Functions

These are functions created by programmers to perform specific tasks.

```
#include <stdio.h>

void displayMessage() {
    printf("Learning C Programming\n");
}

int main() {
    displayMessage();

    return 0;
}
```

## 6. Function Parameters and Arguments

**Parameters** are variables declared in a function definition.

**Arguments** are actual values passed when calling the function.

```
#include <stdio.h>

int multiply(int a, int b) {
    return a * b;
}

int main() {
    int result = multiply(5, 4);

    printf("%d\n", result);

    return 0;
}
```

In this example:

- `a` and `b` are parameters.
    
- `5` and `4` are arguments.
    

## 7. Return Types

The return type specifies what kind of value a function sends back.

### Integer Return Type

```
int getNumber() {
    return 100;
}
```

### Float Return Type

```
float getPrice() {
    return 99.50f;
}
```

### Character Return Type

```
char getGrade() {
    return 'A';
}
```

### Void Return Type

`void` indicates that a function does not return a value.

```
void showMessage() {
    printf("Welcome\n");
}
```

A `void` function can use `return;` to exit early, but it cannot return a value.

## 8. Call by Value

C passes function arguments by value.

This means the function receives a copy of the argument. Changes to the parameter do not directly change the original variable.

```
#include <stdio.h>

void changeValue(int x) {
    x = 100;
}

int main() {
    int number = 10;

    changeValue(number);

    printf("%d\n", number);

    return 0;
}
```

**Output:**

```
10
```

The original variable remains unchanged because `x` is a separate copy.

## 9. Using Pointers to Modify Original Variables

C does not have a separate call-by-reference parameter-passing mode. However, a function can receive a pointer and use it to modify the original object.

```
#include <stdio.h>

void changeValue(int *x) {
    *x = 100;
}

int main() {
    int number = 10;

    changeValue(&number);

    printf("%d\n", number);

    return 0;
}
```

**Output:**

```
100
```

Explanation:

- `&number` passes the address of the variable.
    
- `int *x` receives that address.
    
- `*x = 100` modifies the value stored at that address.
    

## 10. Scope of Function Variables

Variables declared inside a function generally have local scope.

They can only be accessed within their declared scope.

```
#include <stdio.h>

void display() {
    int number = 50;

    printf("%d\n", number);
}

int main() {
    display();

    return 0;
}
```

The variable `number` cannot be directly accessed from `main()`.

### Function Parameters

Parameters are local to the function in which they are declared.

```
int square(int number) {
    return number * number;
}
```

Here, `number` belongs to `square()`.

## 11. Function Prototypes and Header Files

A function prototype allows the compiler to know about a function before its definition appears.

Example:

```
int square(int);
```

Header files contain declarations that can be shared between source files.

For example:

```
#include <stdio.h>
#include <string.h>
```

For a custom project, you can create your own header file.

**math_utils.h**

```
#ifndef MATH_UTILS_H
#define MATH_UTILS_H

int add(int a, int b);

#endif
```

**math_utils.c**

```
#include "math_utils.h"

int add(int a, int b) {
    return a + b;
}
```

**main.c**

```
#include <stdio.h>
#include "math_utils.h"

int main() {
    printf("%d\n", add(10, 20));

    return 0;
}
```

Compile the files together:

```
gcc main.c math_utils.c -o program
```

Run on Linux:

```
./program
```

On Windows:

```
program.exe
```

## 12. Recursion

**Recursion** occurs when a function calls itself to solve a smaller version of a problem.

A recursive function needs:

1. Base case: stops the recursion.
    
2. Recursive case: calls the function again with a smaller or simpler input.
    

### Example: Factorial

Factorial of a positive integer is the product of all positive integers up to that number.

For example:

```
5! = 5 × 4 × 3 × 2 × 1
5! = 120
```

C program:

```
#include <stdio.h>

int factorial(int n) {
    if (n <= 1) {
        return 1;
    }

    return n * factorial(n - 1);
}

int main() {
    printf("%d\n", factorial(5));

    return 0;
}
```

**Output:**

```
120
```

### Important

Without a valid base case, recursion may continue until the program exhausts its available call stack.

Deep recursion can cause a stack overflow.

## 13. Passing Arrays to Functions

Arrays can be passed to functions for processing.

```
#include <stdio.h>

void displayArray(int numbers[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
}

int main() {
    int values[] = {10, 20, 30, 40};

    displayArray(values, 4);

    return 0;
}
```

**Output:**

```
10 20 30 40
```

Important points:

- The array name provides access to its first element when passed to a function.
    
- In a function parameter, `int numbers[]` is adjusted to `int *numbers`.
    
- The function does not automatically know the array's length.
    
- Pass the array size separately.
    

## 14. Function Pointers

A function pointer stores the address of a function.

It can be used to call a function indirectly.

```
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int (*operation)(int, int) = add;

    printf("%d\n", operation(10, 20));

    return 0;
}
```

**Output:**

```
30
```

Function pointers are useful in:

- Callback functions.
    
- Event handling.
    
- Sorting algorithms.
    
- Operating system interfaces.
    
- Modular software design.
    

They are an advanced C concept.

## 15. Static Functions

A function declared with `static` at file scope is accessible only within that source file.

```
static void internalFunction() {
    printf("Internal function\n");
}
```

This is useful when a function should remain private to one source file.

## 16. Inline Functions

The `inline` keyword suggests that the compiler may replace a function call with the function's body.

```
inline int square(int n) {
    return n * n;
}
```

Important: `inline` is a request or suggestion to the compiler, not a guarantee that the function will be expanded inline.

## 17. Variadic Functions

Variadic functions accept a variable number of arguments.

For example:

```
printf("Name: %s, Age: %d\n", "Alex", 20);
```

The `printf()` function accepts different numbers and types of arguments.

The `stdarg.h` header provides tools such as `va_list`, `va_start`, and `va_arg` for implementing variadic functions.

Incorrect handling of variadic arguments can cause undefined behavior.

## 18. Security Considerations in C Functions

Functions are important for writing secure programs.

### A. Validate Inputs

Never assume that function arguments are valid.

```
int divide(int a, int b) {
    if (b == 0) {
        return 0;
    }

    return a / b;
}
```

This example prevents division by zero, although a production function should ideally distinguish an error from a valid result.

### B. Avoid Unsafe Input Handling

Avoid functions such as `gets()`, which cannot limit the amount of input read.

Prefer bounded input methods such as `fgets()` and validate the resulting data.

### C. Avoid Excessive Recursion

Uncontrolled recursion can exhaust stack memory and crash a program.

### D. Check Pointer Validity

Before dereferencing a pointer, ensure it refers to a valid object.

Invalid pointer access can cause crashes or undefined behavior.

### E. Handle Return Values

Check function return values, especially when functions report errors.

## 19. Practical Exercises

Write C programs to perform these tasks:

1. Create a function that adds two integers.
    
2. Create a function that checks whether a number is even or odd.
    
3. Create a function that returns the square of a number.
    
4. Create a function that finds the largest of three numbers.
    
5. Create a recursive function to calculate factorial.
    
6. Create a function that accepts an array and calculates its sum.
    
7. Create a function that swaps two integers using pointer parameters.
    
8. Create a program with separate `.c` and `.h` files.
    

## 20. Key Takeaways

- A function is a reusable block of code.
    
- A function prototype declares a function before its definition.
    
- A function definition contains the implementation.
    
- A function call executes the function.
    
- Parameters receive arguments.
    
- Return types define the type of value returned.
    
- `void` means no value is returned.
    
- C passes arguments by value.
    
- Pointer parameters allow functions to modify caller-owned objects.
    
- Recursion occurs when a function calls itself.
    
- Arrays can be passed to functions, but their lengths should be supplied separately.
    
- Function pointers store function addresses.
    
- Secure functions validate inputs and handle errors properly.
    

## 21. Related Notes

- [[Introduction to C]]
    
- [[C Variables and Data Types]]
    
- [[C Operators and Control Flow]]
    
- [[C Arrays and Strings]]
    
- [[C Pointers]]
    
- [[C Memory Management]]
    
- [[Introduction to OOP]]
    
- [[Introduction to Secure Coding]]