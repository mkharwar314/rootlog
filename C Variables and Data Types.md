> Understand how C stores information using variables, constants, data types, and memory representation.

## 1. What Is a Variable?

A **variable** is a named storage location used by a program to hold a value.

The value stored in a variable can change during program execution.

Example:

```
#include <stdio.h>

int main(void)
{
    int age = 18;

    printf("Age: %d\n", age);

    return 0;
}
```

Output:

```
Age: 18
```

Here:

- `int` specifies the data type.
    
- `age` is the variable name.
    
- `18` is the initial value.
    
- `=` is the assignment operator.
    

## 2. Declaring and Initializing Variables

### Variable Declaration

Declaration specifies a variable's name and type.

```
int age;
float percentage;
char grade;
```

### Variable Initialization

Initialization gives a variable its initial value.

```
int age = 18;
float percentage = 85.5f;
char grade = 'A';
```

### Declaration and Assignment

You can also assign a value after declaration:

```
int number;

number = 100;
```

**Important:** A local variable declared without initialization has an indeterminate value. Do not use it before assigning a valid value.

## 3. Rules for Naming Variables

C identifiers follow specific naming rules.

1. Names can contain letters, digits, and underscores.
    
2. Names cannot begin with a digit.
    
3. Spaces are not allowed.
    
4. C keywords cannot be used as variable names.
    
5. C identifiers are case-sensitive.
    

Valid examples:

```
int age;
int student_count;
int totalMarks;
int _value;
```

Invalid examples:

```
int 2age;
int student name;
int float;
```

`age` and `Age` are different identifiers.

## 4. What Are Data Types?

A **data type** specifies the kind of value a variable can represent and determines how the compiler handles that value.

C provides several fundamental data types.

|Data type|Purpose|Example|
|---|---|---|
|`int`|Integer values|`25`|
|`char`|Character values|`'A'`|
|`float`|Single-precision floating-point values|`10.5f`|
|`double`|Double-precision floating-point values|`25.678`|
|`void`|No value or type|`void main_function(void)`|

Actual storage sizes depend on the implementation and platform, except where the C standard specifies particular minimum requirements.

## 5. Integer Data Types

Integer types store whole-number values.

Common integer types include:

- `short`
    
- `int`
    
- `long`
    
- `long long`
    

They can also use:

- `signed`
    
- `unsigned`
    

Example:

```
#include <stdio.h>

int main(void)
{
    int age = 18;
    unsigned int count = 100;
    long population = 1000000L;

    printf("Age: %d\n", age);
    printf("Count: %u\n", count);
    printf("Population: %ld\n", population);

    return 0;
}
```

### Signed and Unsigned

**Signed integer:** Can represent negative and non-negative values.

**Unsigned integer:** Can represent only non-negative values.

For an unsigned integer type with N value bits, the range is:

[  
0 \text{ to } 2^N-1  
]

The exact range depends on the type and implementation.

## 6. Floating-Point Data Types

Floating-point types represent numbers with fractional parts.

Common types:

- `float`
    
- `double`
    
- `long double`
    

Example:

```
#include <stdio.h>

int main(void)
{
    float price = 99.5f;
    double pi = 3.1415926535;

    printf("Price: %.2f\n", price);
    printf("Pi: %.10f\n", pi);

    return 0;
}
```

Floating-point values have limited precision. They cannot represent every decimal number exactly.

For this reason, avoid assuming that floating-point calculations always produce mathematically exact results.

## 7. Character Data Type

The `char` type is used to represent character values.

Example:

```
#include <stdio.h>

int main(void)
{
    char grade = 'A';

    printf("Grade: %c\n", grade);

    return 0;
}
```

Output:

```
Grade: A
```

A character constant uses single quotation marks.

```
char letter = 'M';
```

A string uses double quotation marks.

```
char name[] = "Mohit";
```

A string in C is represented as an array of characters terminated by a null character `'\0'`.

## 8. Constants in C

A **constant** is a value that should not be modified during program execution.

C supports constants through `const` and preprocessor macros.

### Using `const`

```
#include <stdio.h>

int main(void)
{
    const float PI = 3.14159f;

    printf("PI: %.5f\n", PI);

    return 0;
}
```

Attempting to modify an object defined with `const` through an ordinary assignment violates the language constraints.

### Using `#define`

```
#include <stdio.h>

#define MAX_USERS 100

int main(void)
{
    printf("Maximum users: %d\n", MAX_USERS);

    return 0;
}
```

`#define` creates a preprocessor macro. It does not declare a typed variable.

## 9. Type Modifiers

Type modifiers change the range or properties of certain integer and character types.

Common modifiers:

- `signed`
    
- `unsigned`
    
- `short`
    
- `long`
    

Examples:

```
short int number1 = 100;
long int number2 = 100000L;
unsigned int number3 = 500;
long long int number4 = 9000000000LL;
```

Not every modifier combination is valid for every type.

## 10. The `sizeof` Operator

The `sizeof` operator returns the size, in bytes, of a type or object.

Example:

```
#include <stdio.h>

int main(void)
{
    printf("int: %zu bytes\n", sizeof(int));
    printf("char: %zu bytes\n", sizeof(char));
    printf("float: %zu bytes\n", sizeof(float));
    printf("double: %zu bytes\n", sizeof(double));

    return 0;
}
```

The `%zu` format specifier is used for values of type `size_t`.

**Important:** Do not assume that every computer uses the same size for every C data type. Use `sizeof` to inspect the current implementation.

## 11. Type Conversion

Type conversion changes a value from one data type to another.

C supports two common forms.

### 11.1 Implicit Conversion

The compiler performs conversion automatically according to C's conversion rules.

```
#include <stdio.h>

int main(void)
{
    int number = 10;
    float result = number;

    printf("%.2f\n", result);

    return 0;
}
```

Output:

```
10.00
```

### 11.2 Explicit Conversion (Type Casting)

The programmer specifies the desired type.

```
#include <stdio.h>

int main(void)
{
    int a = 10;
    int b = 3;

    float result = (float)a / b;

    printf("%.2f\n", result);

    return 0;
}
```

Output:

```
3.33
```

Without the cast, integer division would produce `3`.

Be careful: converting a value to a type that cannot represent it may produce an implementation-dependent or otherwise unexpected result, depending on the conversion.

## 12. Format Specifiers

Format specifiers tell functions such as `printf()` and `scanf()` how to interpret values.

|Specifier|Common use|
|---|---|
|`%d`|`int`|
|`%u`|`unsigned int`|
|`%ld`|`long int`|
|`%lld`|`long long int`|
|`%f`|`double` in `printf()`|
|`%c`|Character|
|`%s`|Null-terminated character string|
|`%zu`|`size_t`|
|`%p`|Pointer address|

**Important distinction:** In `printf()`, `%f` expects a `double`. In `scanf()`, `%f` expects a `float *`, while `%lf` expects a `double *`.

Incorrect format specifiers can cause undefined behaviour.

## 13. Taking User Input

C uses `scanf()` to read formatted input.

Example:

```
#include <stdio.h>

int main(void)
{
    int age;

    printf("Enter your age: ");

    if (scanf("%d", &age) != 1)
    {
        printf("Invalid input\n");
        return 1;
    }

    printf("Your age is %d\n", age);

    return 0;
}
```

### Understanding `&`

The `&` operator obtains the address of a variable.

`scanf()` needs the variable's address so it can store the input value there.

For more complex input, especially strings, functions such as `fgets()` are generally preferable to unbounded input methods.

## 14. Scope and Lifetime of Variables

### Scope

Scope determines where an identifier can be accessed in the source code.

Common scopes include:

- Block scope.
    
- File scope.
    
- Function prototype scope.
    
- Function scope, which applies to labels.
    

Example:

```
#include <stdio.h>

int main(void)
{
    int age = 18;

    {
        int marks = 90;
        printf("Marks: %d\n", marks);
    }

    printf("Age: %d\n", age);

    return 0;
}
```

`marks` is available only inside its block.

### Lifetime

Lifetime describes how long an object exists during program execution.

Examples:

- Automatic objects generally exist during execution of their enclosing block.
    
- Static-storage-duration objects exist for the entire program execution.
    
- Dynamically allocated objects exist from allocation until they are released.
    

Scope and lifetime are related concepts, but they are not the same.

## 15. Variables and Memory

Variables represent objects that may occupy storage in a program.

For example:

```
int age = 18;
```

The compiler determines how the object is represented and stored.

Depending on the declaration and implementation, objects may use:

- Automatic storage.
    
- Static storage.
    
- Dynamically allocated storage.
    

Understanding variable storage is important when learning:

- Pointers.
    
- Memory allocation.
    
- Stack and heap concepts.
    
- Buffer overflows.
    
- Memory corruption.
    

## 16. Common Programming Mistakes

|Mistake|Explanation|
|---|---|
|Uninitialized variable|Using a local variable before assigning a valid value|
|Incorrect format specifier|Using a format that does not match the argument type|
|Integer overflow|Performing an operation outside the representable range|
|Type conversion error|Converting values without considering their range or precision|
|Missing `&` in `scanf()`|Passing a value instead of the required address|
|Confusing `=` and `==`|Assignment versus equality comparison|

### Example: Uninitialized Variable

Incorrect:

```
int number;

printf("%d\n", number);
```

Correct:

```
int number = 10;

printf("%d\n", number);
```

## 17. C Data Types and Cybersecurity

Understanding C data types is important for identifying and preventing memory-related vulnerabilities.

### Integer Overflow

An integer operation can exceed the range of its type.

This can cause unexpected results and may lead to security problems when the result is used for memory allocation or bounds checking.

### Signedness Errors

Mixing signed and unsigned values can cause unexpected comparisons and conversions.

### Buffer Size Errors

Incorrect assumptions about the size of a data type or array can result in out-of-bounds memory access.

### Secure Programming Practices

1. Choose data types appropriate for the expected range.
    
2. Validate input before processing it.
    
3. Check arithmetic operations for overflow where necessary.
    
4. Match format specifiers with argument types.
    
5. Avoid using uninitialized variables.
    
6. Check array boundaries.
    
7. Use `size_t` for object sizes and array indexing where appropriate.
    

## 18. Practical Exercises

### Exercise 1 — Create Variables

Create a C program containing:

- An integer variable for age.
    
- A floating-point variable for percentage.
    
- A character variable for grade.
    

Print all three values.

### Exercise 2 — Use Constants

Create a constant named `PI` and calculate the area of a circle.

Formula:

[  
Area = \pi r^2  
]

### Exercise 3 — Explore `sizeof`

Write a program that displays the sizes of:

- `char`
    
- `short`
    
- `int`
    
- `long`
    
- `long long`
    
- `float`
    
- `double`
    

Observe the results on your system.

### Exercise 4 — Practice Type Conversion

Create two integer variables and divide them.

First use integer division, then use explicit type casting to produce a floating-point result.

Compare the outputs.

### Exercise 5 — Take User Input

Ask the user to enter:

- Name.
    
- Age.
    
- Percentage.
    

Display the entered information. Use `fgets()` for the name and validate numeric input.

## 19. Key Takeaways

- Variables store values used by a program.
    
- Data types define how values are represented and handled.
    
- C supports integer, character, floating-point, and other types.
    
- `const` declares objects that cannot be modified through ordinary assignment.
    
- `sizeof` returns the size of an object or type in bytes.
    
- Type conversion can be implicit or explicit.
    
- Scope determines where an identifier is accessible.
    
- Lifetime determines how long an object exists.
    
- Incorrect data-type handling can introduce security vulnerabilities.
    

## 20. Related Notes

- [[Introduction to C]]
    
- [[C Operators and Control Flow]]
    
- [[C Functions]]
    
- [[C Arrays and Strings]]
    
- [[C Pointers]]
    
- [[C Memory Management]]
    
- [[Data Types]]
    
- [[Type Conversion]]
    
- [[Secure Coding]]