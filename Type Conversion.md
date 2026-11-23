> Understand how data changes from one type to another and why correct type conversion is important for reliable and secure programs.

## 1. Introduction to Type Conversion

Type conversion is the process of changing a value from one data type to another.

For example:

- Integer to string
    
- String to integer
    
- Float to integer
    
- Integer to float
    

### Example

```
age = "18"

age = int(age)

print(age)
print(type(age))
```

Output:

```
18
<class 'int'>
```

The value was originally a string and was converted into an integer.

## 2. Why Type Conversion Is Important

Type conversion is useful when:

1. Receiving numeric input from users.
    
2. Performing mathematical calculations.
    
3. Processing data from files.
    
4. Communicating with APIs.
    
5. Working with databases.
    
6. Converting data between programming languages or systems.
    

Without correct conversion, programs may produce unexpected results or errors.

## 3. Types of Type Conversion

There are two major categories:

### 3.1 Implicit Type Conversion

Implicit conversion happens automatically when a programming language converts a value into another compatible type.

Example in Python:

```
number = 10
decimal = 2.5

result = number + decimal

print(result)
print(type(result))
```

Output:

```
12.5
<class 'float'>
```

Python automatically converts the integer into a floating-point value during the operation.

### 3.2 Explicit Type Conversion

Explicit conversion happens when a programmer manually converts a value using a conversion function or operation.

Example:

```
number = "100"

converted = int(number)

print(converted)
print(type(converted))
```

Output:

```
100
<class 'int'>
```

## 4. Type Conversion in Python

Python provides several built-in conversion functions.

|Function|Purpose|Example|
|---|---|---|
|`int()`|Converts to integer|`int("25")`|
|`float()`|Converts to float|`float("3.14")`|
|`str()`|Converts to string|`str(100)`|
|`bool()`|Converts to Boolean|`bool(1)`|
|`list()`|Converts to list|`list("abc")`|
|`tuple()`|Converts to tuple|`tuple([1, 2])`|
|`set()`|Converts to set|`set([1, 1, 2])`|
|`dict()`|Creates a dictionary from suitable key-value pairs|`dict([("a", 1)])`|

### 4.1 Integer Conversion

```
number = int("50")

print(number)
```

Output:

```
50
```

Converting a floating-point value to an integer removes its fractional part; it does not round to the nearest integer.

```
number = int(9.8)

print(number)
```

Output:

```
9
```

### 4.2 Float Conversion

```
number = float("10.5")

print(number)
```

Output:

```
10.5
```

### 4.3 String Conversion

```
age = 18

message = "My age is " + str(age)

print(message)
```

Output:

```
My age is 18
```

### 4.4 Boolean Conversion

Python converts values according to their truthiness.

```
print(bool(1))
print(bool(0))
print(bool(""))
print(bool("Cybersecurity"))
```

Output:

```
True
False
False
True
```

Important:

- `0` is false.
    
- Empty strings are false.
    
- Non-empty strings are true, including `"False"`.
    

### 4.5 Collection Conversion

```
text = "ROOTLOG"

characters = list(text)

print(characters)
```

Output:

```
['R', 'O', 'O', 'T', 'L', 'O', 'G']
```

A set removes duplicate values:

```
numbers = [1, 2, 2, 3, 3]

unique_numbers = set(numbers)

print(unique_numbers)
```

Output:

```
{1, 2, 3}
```

## 5. Type Conversion in C

C supports explicit type conversion using type casting.

### 5.1 Implicit Conversion

```
#include <stdio.h>

int main() {
    int number = 10;
    float result = number;

    printf("%f\n", result);

    return 0;
}
```

The integer value is converted to a floating-point value.

### 5.2 Explicit Type Casting

```
#include <stdio.h>

int main() {
    float number = 9.8;

    int result = (int)number;

    printf("%d\n", result);

    return 0;
}
```

Output:

```
9
```

The cast `(int)` converts the floating-point value to an integer by discarding its fractional part.

**Important:** Conversion in C can cause data loss, overflow, or unexpected results if the destination type cannot represent the original value.

## 6. Type Conversion in JavaScript

JavaScript supports both automatic and explicit type conversion.

### 6.1 Implicit Conversion

```
let result = "10" + 5;

console.log(result);
```

Output:

```
105
```

The `+` operator performs string concatenation because one operand is a string.

Another example:

```
let result = "10" - 5;

console.log(result);
```

Output:

```
5
```

The subtraction operator converts the string into a number.

This behavior is called type coercion.

### 6.2 Explicit Conversion

JavaScript provides functions such as:

|Function|Purpose|
|---|---|
|`Number()`|Converts to number|
|`String()`|Converts to string|
|`Boolean()`|Converts to Boolean|
|`parseInt()`|Parses an integer|
|`parseFloat()`|Parses a floating-point number|

Example:

```
let age = "18";

let convertedAge = Number(age);

console.log(convertedAge);
console.log(typeof convertedAge);
```

Output:

```
18
number
```

### 6.3 Handling Invalid Conversion

```
let value = Number("hello");

console.log(value);
console.log(Number.isNaN(value));
```

Output:

```
NaN
true
```

`NaN` means Not-a-Number. It indicates that a numeric operation or conversion did not produce a valid number.

## 7. Type Conversion vs Type Casting vs Type Coercion

These terms are related but not identical in every programming language.

|Term|Meaning|
|---|---|
|Type Conversion|General process of changing a data type|
|Type Casting|Explicitly specifying a target type|
|Type Coercion|Automatic type conversion performed by a language|

Examples:

- Python: `int("20")` — explicit conversion.
    
- C: `(int)9.8` — type casting.
    
- JavaScript: `"10" - 5` — implicit coercion.
    

## 8. Common Type Conversion Errors

### 8.1 Invalid String Conversion

```
number = int("hello")
```

This raises a `ValueError`.

### 8.2 Unexpected Boolean Conversion

```
print(bool("False"))
```

Output:

```
True
```

A non-empty string is truthy, even if its contents say `"False"`.

### 8.3 Data Loss

```
number = int(9.99)

print(number)
```

Output:

```
9
```

The fractional part is discarded.

### 8.4 Overflow and Range Issues

In languages such as C, converting a value into a type that cannot represent it may produce implementation-dependent or otherwise unexpected results.

Always consider the valid range of the destination type.

## 9. Type Conversion in Cybersecurity

Type conversion is frequently used in security-related programming.

### 9.1 Processing Network Ports

A port entered by a user arrives as text and must be converted into an integer before numeric validation.

```
port_input = input("Enter port: ")

try:
    port = int(port_input)

    if 1 <= port <= 65535:
        print("Valid port")
    else:
        print("Invalid port range")

except ValueError:
    print("Port must be numeric")
```

### 9.2 Processing Log Data

Log files often store timestamps, event IDs, and other values as strings.

A program may need to convert them into numeric or date/time types before analysis.

### 9.3 Processing API Responses

JSON data can contain strings, numbers, Booleans, arrays, and objects.

A security script must understand the actual data type before processing a response.

### 9.4 Security Considerations

Incorrect conversion can cause:

- Validation bypasses.
    
- Incorrect access-control decisions.
    
- Unexpected application behavior.
    
- Data corruption.
    
- Parsing errors.
    

Never rely on type conversion alone as a security control. Validate the converted value and enforce the application's rules.

## 10. Best Practices

1. Understand the original data type before conversion.
    
2. Use explicit conversion when it improves clarity.
    
3. Handle invalid conversions with appropriate error handling.
    
4. Validate numeric ranges after conversion.
    
5. Avoid unnecessary conversions.
    
6. Consider precision and data loss.
    
7. Never assume external input has the expected type.
    
8. Use consistent types when comparing or processing data.
    

## 11. Key Takeaways

- Type conversion changes a value from one data type to another.
    
- Implicit conversion happens automatically.
    
- Explicit conversion is performed by the programmer.
    
- Type casting explicitly specifies a target type.
    
- Type coercion refers to automatic conversion.
    
- Conversion can cause errors or data loss.
    
- Input validation is important after conversion.
    
- Type conversion is widely used in cybersecurity scripts and applications.
    

## 12. Questions and Doubts

1. What is type conversion?
    
2. What is the difference between implicit and explicit conversion?
    
3. What does `int()` do in Python?
    
4. Why does `int(9.8)` return `9`?
    
5. What is type casting in C?
    
6. What is type coercion in JavaScript?
    
7. What does `NaN` mean?
    
8. Why should converted network port values be validated?
    

## 13. Practical Tasks

### Task 1 — Basic Conversion

Convert the following values in Python:

- `"100"` into an integer.
    
- `"25.5"` into a float.
    
- `500` into a string.
    

Print each result and its data type.

### Task 2 — Conversion Errors

Try converting `"Cybersecurity"` into an integer.

Handle the error using `try` and `except`.

### Task 3 — Boolean Conversion

Test the following values using `bool()`:

```
0
1
""
"False"
"ROOTLOG"
[]
[1, 2]
```

Record the results and explain why they occur.

### Task 4 — Network Port Conversion

Write a Python program that:

1. Accepts a port number as input.
    
2. Converts it into an integer.
    
3. Handles invalid input.
    
4. Checks whether it is between 1 and 65535.
    

### Task 5 — Compare Languages

Observe how Python, C, and JavaScript handle the conversion of a floating-point value into an integer.

Write down the similarities and differences.

## Related Notes

- [[Introduction to Programming]]
    
- [[Programming Languages]]
    
- [[Variables and Constants]]
    
- [[Data Types]]
    
- [[Operators]]
    
- [[Input and Output]]
    
- [[Conditional Statements]]
    
- [[Exception Handling]]
    
- [[Input Validation]]
    
- [[Introduction to Python]]
    
- [[C and C++ Programming]]
    
- [[JavaScript Programming]]