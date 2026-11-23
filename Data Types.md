> Understand how programming languages classify, represent, store, and process different kinds of data.

## 1. Introduction

Every program works with data.

Examples include:

- Names and usernames.
- Age and account balances.
- IP addresses.
- Login status.
- File sizes.
- Network packets.
- Dates and timestamps.

A programming language needs a way to identify what kind of data a value represents.

A **data type** defines the category of a value and determines which operations are valid or meaningful for it.

Example:

```
name = "ROOTLOG"
age = 20
price = 99.50
is_student = True
```

Here:

- `name` is a string.
- `age` is an integer.
- `price` is a floating-point number.
- `is_student` is a Boolean.

## 2. Why Are Data Types Important?

Data types help programming languages:

- Interpret values correctly.
- Determine which operations are supported.
- Manage memory and representation.
- Detect certain programming errors.
- Organize information.
- Process data efficiently.

For example:

```
number1 = 10
number2 = 20

print(number1 + number2)
```

Output:

```
30
```

But:

```
text1 = "10"
text2 = "20"

print(text1 + text2)
```

Output:

```
1020
```

The first example performs numerical addition. The second joins two strings.

The same `+` operator can have different behavior depending on the data types.

## 3. Main Categories of Data Types

Data types are commonly divided into two broad categories.

```
Data Types
    |
    |----------------------|
    |                      |
Primitive / Basic       Composite / Complex
    |                      |
Integer                 List
Float                   Tuple
Boolean                 Dictionary
Character               Set
String                  Array
                        Object
```

This is a conceptual classification. Exact categories and terminology differ between languages.

## 4. Integer

An integer represents a whole number without a fractional part.

Examples:

```
age = 20
temperature = -5
count = 100
```

Integers can be:

- Positive.
- Negative.
- Zero.

Common uses:

- Counting login attempts.
- Tracking the number of files.
- Representing port numbers.
- Performing arithmetic calculations.

Example:

```
failed_attempts = 3
maximum_attempts = 5

print(maximum_attempts - failed_attempts)
```

Output:

```
2
```

**Note:** Integer ranges depend on the language and implementation. Python integers can grow beyond fixed-width machine integer ranges, subject to available memory. C integer types have implementation-dependent ranges.

## 5. Floating-Point

A floating-point type represents numbers that may contain fractional parts.

Examples:

```
price = 99.50
temperature = 36.6
percentage = 87.25
```

Common uses:

- Scientific calculations.
- Measurements.
- Financial calculations where approximate values are acceptable.
- Statistical analysis.

Example:

```
length = 10.5
width = 5.2

area = length * width

print(area)
```

Output:

```
54.6
```

### 5.1 Floating-Point Precision

Floating-point values are commonly represented using binary approximations.

As a result, some decimal values cannot be represented exactly.

Example:

```
print(0.1 + 0.2)
```

A typical Python result is:

```
0.30000000000000004
```

This is a representation limitation, not necessarily a programming error.

For applications requiring exact decimal arithmetic, such as financial calculations, use an appropriate decimal type or library.

## 6. Boolean

A Boolean represents a logical truth value.

It has two possible values:

- `True`
- `False`

Example:

```
is_authenticated = True
is_locked = False

print(is_authenticated)
print(is_locked)
```

Common uses:

- Authentication checks.
- Authorization decisions.
- Conditional statements.
- Security configuration.
- Validation results.

Example:

```
password_valid = True

if password_valid:
    print("Password accepted")
else:
    print("Password rejected")
```

Boolean values are especially important in program logic.

## 7. Character

A character represents a single character, such as a letter, digit, or symbol.

Example in C:

```
char grade = 'A';
char symbol = '#';
```

In C, a `char` occupies one byte, although its interpretation depends on the character encoding.

Python does not have a separate character data type. A single character is represented as a string of length one.

```
letter = "A"

print(type(letter))
```

Output:

```
<class 'str'>
```

## 8. String

A string represents a sequence of characters.

Examples:

```
username = "student"
ip_address = "192.168.1.10"
message = "Welcome to ROOTLOG"
```

Strings are used to store:

- Names.
- Email addresses.
- IP addresses in textual form.
- File paths.
- Log messages.
- User input.

Example:

```
username = "student"

print("Welcome", username)
```

Output:

```
Welcome student
```

### 8.1 String Operations

**Concatenation:** Joining strings.

```
first_name = "Cyber"
last_name = "Security"

full_name = first_name + " " + last_name

print(full_name)
```

**Length:** Finding the number of characters.

```
message = "ROOTLOG"

print(len(message))
```

**Indexing:** Accessing a character by position.

```
language = "Python"

print(language[0])
```

Output:

```
P
```

### 8.2 Strings and Security

Strings are frequently used to handle untrusted input.

For example:

```
username = input("Enter username: ")
print("Username:", username)
```

Security considerations include:

- Input validation.
- Output encoding.
- Safe database queries.
- Safe file path handling.
- Avoiding unsafe command construction.

Never assume a string supplied by a user is trustworthy.

## 9. Composite Data Types

Composite data types combine or organize multiple values.

### 9.1 List

A list stores multiple values in an ordered collection.

Example:

```
ports = [22, 80, 443, 8080]

print(ports)
```

Characteristics:

- Ordered.
- Mutable.
- Allows duplicate values.
- Can contain different data types in Python.

Changing a list:

```
ports.append(3306)

print(ports)
```

### 9.2 Tuple

A tuple stores multiple values in an ordered collection.

Example:

```
network_details = ("192.168.1.10", 443)

print(network_details)
```

Characteristics:

- Ordered.
- Immutable at the tuple level.
- Allows duplicate values.

A tuple is useful when a collection should not be structurally modified.

### 9.3 Dictionary

A dictionary stores information as key-value pairs.

Example:

```
user = {
    "username": "student",
    "role": "analyst",
    "active": True
}

print(user["username"])
```

Output:

```
student
```

Common uses:

- User records.
- Configuration data.
- API responses.
- Log entries.

### 9.4 Set

A set stores unique values.

Example:

```
ports = {22, 80, 443, 80}

print(ports)
```

The duplicate value `80` is stored only once.

Characteristics:

- Unique elements.
- No guaranteed positional indexing.
- Useful for membership checks and set operations.

### 9.5 Array

An array stores multiple elements, generally using a defined element type and a structured memory representation.

Example in C:

```
int ports[3] = {22, 80, 443};
```

Arrays are useful for storing collections of similar values.

In Python, lists are commonly used for general-purpose collections. Specialized arrays are also available through modules and libraries.

## 10. Data Types in Different Programming Languages

The same concept can have different names or behavior across languages.

|Concept|Python|C|JavaScript|
|---|---|---|---|
|Integer|`int`|`int`|`Number`|
|Floating-point|`float`|`float`, `double`|`Number`|
|Boolean|`bool`|`_Bool` / `bool`|`boolean`|
|Character|No separate type|`char`|No separate character primitive|
|String|`str`|Character arrays / strings through libraries|`string`|
|Collection|`list`|Arrays|`Array`|
|Key-value collection|`dict`|Structures or other data structures|`Object`, `Map`|

Important differences:

- Python is dynamically typed.
- C is statically typed.
- JavaScript is dynamically typed.
- JavaScript's `Number` type represents ordinary integer and floating-point numeric values using the same number type.
- C has several numeric types with different ranges and precision.

## 11. Type Checking

Type checking determines whether values and operations are compatible with the language's type rules.

### 11.1 Static Type Checking

In statically typed languages, types are checked before execution or during compilation.

Example in C:

```
int age = 20;
```

The compiler knows that `age` is declared as an integer.

### 11.2 Dynamic Type Checking

In dynamically typed languages, types are generally checked during execution.

Example in Python:

```
value = 100
value = "ROOTLOG"

print(value)
```

The name `value` can refer to objects of different types at different times.

## 12. Type Conversion

Type conversion means changing a value from one data type to another.

### 12.1 Implicit Conversion

Implicit conversion occurs automatically according to the language's rules.

Example in Python:

```
number = 10
decimal = 2.5

result = number + decimal

print(result)
```

Output:

```
12.5
```

Python converts the integer into a compatible numeric representation for the operation.

### 12.2 Explicit Conversion

Explicit conversion is performed by the programmer.

Example:

```
age = "20"

age_number = int(age)

print(age_number + 5)
```

Output:

```
25
```

Common Python conversion functions:

|Function|Purpose|
|---|---|
|`int()`|Converts to integer when possible|
|`float()`|Converts to floating-point|
|`str()`|Converts to string|
|`bool()`|Converts to Boolean|
|`list()`|Creates a list|
|`tuple()`|Creates a tuple|
|`set()`|Creates a set|

Conversion can fail when a value cannot be represented by the requested type.

Example:

```
number = int("hello")
```

This raises a `ValueError`.

## 13. Mutable and Immutable Data Types

Mutability describes whether an object's contents can be changed after creation.

### 13.1 Mutable Types

Mutable objects can be modified.

Common Python examples:

- Lists.
- Dictionaries.
- Sets.

Example:

```
ports = [22, 80, 443]

ports.append(8080)

print(ports)
```

The existing list object is modified.

### 13.2 Immutable Types

Immutable objects cannot be modified after creation.

Common Python examples:

- Integers.
- Floats.
- Booleans.
- Strings.
- Tuples.

Example:

```
name = "ROOTLOG"

name = name + "-LAB"

print(name)
```

This creates a new string value and reassigns the name. It does not modify the original string object.

**Important:** A tuple is immutable, but it can contain a mutable object. The tuple's structure cannot be changed, although the contained mutable object may still change.

## 14. Data Types and Memory

Different types of data require different representations.

For example:

- Integers represent whole numbers.
- Floating-point types represent approximate real numbers.
- Strings represent sequences of text.
- Boolean types represent logical values.

In lower-level languages such as C, the size and representation of many types are important when working with memory.

Example:

```
#include <stdio.h>

int main() {
    printf("Size of int: %zu bytes\n", sizeof(int));
    printf("Size of char: %zu byte\n", sizeof(char));

    return 0;
}
```

Compile and run this program to observe the sizes on your system.

The exact size of types such as `int` is implementation-dependent. The C standard guarantees that `sizeof(char)` is 1 byte, but a C byte is not required to be eight bits.

Understanding data representation is useful when studying:

- Memory management.
- Buffer overflows.
- Integer overflows.
- Binary analysis.
- File formats.
- Network protocols.

## 15. Data Types in Cybersecurity

Data types are used throughout security tools and applications.

### 15.1 IP Address Processing

```
source_ip = "192.168.1.50"
```

The address is stored as a string here.

For actual IP address operations, Python provides the `ipaddress` module.

```
import ipaddress

address = ipaddress.ip_address("192.168.1.50")

print(address.version)
```

Output:

```
4
```

### 15.2 Log Analysis

```
username = "student"
failed_attempts = 3
is_locked = False
```

Different types represent different pieces of log information.

### 15.3 File Analysis

```
file_name = "evidence.txt"
file_size = 2048
is_verified = True
```

### 15.4 Network Programming

```
target_ip = "192.168.1.10"
target_port = 443
timeout_seconds = 5.0
```

Correct data types help programs handle network information consistently.

## 16. Common Mistakes

|Mistake|Explanation|
|---|---|
|Treating numbers stored as strings as integers|Arithmetic operations may behave differently|
|Confusing `True` with `"True"`|One is Boolean; the other is a string|
|Assuming all languages have identical types|Type systems differ|
|Ignoring conversion errors|Invalid input can cause exceptions|
|Assuming a tuple makes all contained objects immutable|Mutability of contained objects is separate|
|Assuming floating-point values are always exact|Many decimal values are approximations|
|Trusting user input|Untrusted data must be validated and handled safely|

## 17. Practical Lab

### Lab 1: Identify Data Types

Create a file named:

`data_types_lab.py`

Add:

```
username = "student"
age = 20
percentage = 85.5
is_active = True
ports = [22, 80, 443]

print(type(username))
print(type(age))
print(type(percentage))
print(type(is_active))
print(type(ports))
```

Run:

```
python data_types_lab.py
```

On Kali Linux, use `python3` if required.

Observe the output and identify each type.

### Lab 2: Type Conversion

```
age = "20"

age = int(age)

print(age + 5)
```

Expected output:

```
25
```

### Lab 3: Mutable and Immutable Objects

```
numbers = [10, 20, 30]

numbers.append(40)

print(numbers)

name = "ROOTLOG"

name = name + " LAB"

print(name)
```

Observe how lists and strings behave differently.

### Lab 4: IP Address Data

```
import ipaddress

ip = ipaddress.ip_address("192.168.1.10")

print("IP:", ip)
print("Version:", ip.version)
print("Is private:", ip.is_private)
```

This uses Python's standard library to inspect an IP address.

## 18. Key Takeaways

- Data types classify values used by programs.
- Common basic types include integers, floats, Booleans, characters, and strings.
- Composite types organize multiple values.
- Different languages implement data types differently.
- Type checking can be static or dynamic.
- Type conversion changes a value's representation or type.
- Mutable objects can be modified; immutable objects cannot.
- Data representation matters in memory and low-level programming.
- Correct type handling is important for secure software development.

## 19. Questions for Self-Study

1. What is a data type?
2. Why are data types important?
3. Explain integer, floating-point, Boolean, character, and string types.
4. What are composite data types?
5. Explain lists, tuples, dictionaries, and sets.
6. What is the difference between static and dynamic typing?
7. What is type conversion?
8. Explain implicit and explicit conversion.
9. What is the difference between mutable and immutable objects?
10. Why can floating-point calculations produce unexpected decimal results?
11. How are data types related to memory?
12. Why is correct type handling important in cybersecurity?

## 20. Practical Tasks

1. Create variables using five different data types.
2. Write a program that converts a numeric string into an integer.
3. Create a list containing five network ports.
4. Create a dictionary containing a username, role, and account status.
5. Demonstrate the difference between a mutable list and an immutable string.
6. Write a short explanation of how data types affect memory representation.

## Related Notes

- [[Introduction to Programming]]
- [[Programming Languages]]
- [[Variables and Constants]]
- [[Operators]]
- [[Input and Output]]
- [[Type Conversion]]
- [[Python Variables and Data Types]]
- [[C Variables and Data Types]]
- [[JavaScript Variables and Data Types]]
- [[SQL Data Types]]
- [[Memory Management]]
- [[Secure Programming]]