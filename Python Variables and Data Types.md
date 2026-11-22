## 1. Introduction

Variables and data types are fundamental concepts in Python programming.

- **Variable:** A name that refers to an object stored in memory.
    
- **Data Type:** Defines the kind of value an object represents and the operations that can be performed on it.
    

Example:

```
name = "ROOTLOG"
age = 18
height = 5.8
is_student = True
```

Here:

|Variable|Value|Data Type|
|---|---|---|
|`name`|`"ROOTLOG"`|`str`|
|`age`|`18`|`int`|
|`height`|`5.8`|`float`|
|`is_student`|`True`|`bool`|

## 2. Variables in Python

A variable is a name that refers to an object.

Python does not require explicit variable declarations. A variable is created when a value is assigned to it.

Example:

```
username = "student"
attempts = 5
score = 95.5

print(username)
print(attempts)
print(score)
```

Output:

```
student
5
95.5
```

### Variable Assignment

The assignment operator `=` assigns an object to a variable name.

```
x = 10
```

This means the name `x` refers to the integer object `10`.

### Multiple Variable Assignment

Python allows multiple variables to be assigned in one statement.

```
a, b, c = 10, 20, 30

print(a)
print(b)
print(c)
```

### Assigning the Same Value

```
x = y = z = 100

print(x, y, z)
```

All three names refer to the same integer object.

## 3. Rules for Naming Variables

Python identifiers must follow specific rules.

### Rules

1. A variable name can contain letters.
    
2. It can contain numbers, but cannot begin with a number.
    
3. Underscores are allowed.
    
4. Spaces are not allowed.
    
5. Variable names are case-sensitive.
    
6. Python keywords cannot be used as variable names.
    

### Valid Variable Names

```
username = "Mohit"
user_name = "Mohit"
user123 = "Mohit"
_private = "Data"
```

### Invalid Variable Names

```
# 123user = "Mohit"
# user-name = "Mohit"
# user name = "Mohit"
# class = "Cybersecurity"
```

These examples are invalid because they violate Python naming rules.

### Naming Conventions

Python commonly follows these conventions:

|Convention|Example|Usage|
|---|---|---|
|`snake_case`|`user_name`|Variables and functions|
|`PascalCase`|`SecurityScanner`|Classes|
|`UPPER_CASE`|`MAX_ATTEMPTS`|Constants|

These are style conventions, not mandatory syntax rules.

## 4. Dynamic Typing

Python is a dynamically typed language.

This means you do not need to declare a variable's type explicitly. The type is associated with the object, and a variable name can later refer to an object of a different type.

Example:

```
value = 100

print(value)
print(type(value))

value = "Python"

print(value)
print(type(value))
```

Output:

```
100
<class 'int'>
Python
<class 'str'>
```

The variable `value` first refers to an integer and later refers to a string.

**Important:** Dynamic typing does not mean Python ignores data types. Operations still follow type rules.

## 5. Checking Data Types

Python provides the built-in `type()` function to identify an object's type.

Example:

```
name = "Python"
age = 18
price = 99.5
active = True

print(type(name))
print(type(age))
print(type(price))
print(type(active))
```

Output:

```
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
```

You can also use `isinstance()` to check whether an object belongs to a particular type.

```
age = 18

print(isinstance(age, int))
```

Output:

```
True
```

## 6. Built-in Python Data Types

Python provides several built-in data types.

### A. Numeric Types

Python has three main built-in numeric types.

#### 1. Integer (`int`)

An integer represents a whole number without a decimal point.

Examples:

```
age = 18
count = 100
temperature = -5

print(type(age))
```

Output:

```
<class 'int'>
```

#### 2. Float (`float`)

A float represents a number with a fractional component.

Examples:

```
price = 99.99
height = 5.8
temperature = 36.5

print(type(price))
```

Output:

```
<class 'float'>
```

#### 3. Complex (`complex`)

A complex number contains a real part and an imaginary part.

Example:

```
number = 3 + 4j

print(number)
print(type(number))
```

Output:

```
(3+4j)
<class 'complex'>
```

The imaginary component uses `j` in Python.

### B. Boolean (`bool`)

Boolean values represent logical truth values.

Python has two Boolean values:

- `True`
    
- `False`
    

Example:

```
is_authenticated = True
is_locked = False

print(type(is_authenticated))
```

Output:

```
<class 'bool'>
```

Boolean values are commonly used in conditions and access-control decisions.

### C. String (`str`)

A string represents a sequence of characters.

Strings can be written using:

- Single quotes
    
- Double quotes
    
- Triple quotes
    

Example:

```
username = "student"
language = 'Python'
message = """Learning cybersecurity."""

print(username)
print(language)
print(message)
```

Strings are immutable, meaning their individual characters cannot be changed in place.

### D. Sequence Types

Sequence types store collections of items in a particular order.

#### 1. List (`list`)

A list is an ordered, mutable collection.

Example:

```
tools = ["Nmap", "Wireshark", "Burp Suite"]

tools.append("Metasploit")

print(tools)
```

Lists allow duplicate values and different data types.

#### 2. Tuple (`tuple`)

A tuple is an ordered, immutable collection.

Example:

```
ports = (22, 80, 443)

print(ports)
print(type(ports))
```

Once created, tuple elements cannot be reassigned.

#### 3. Range (`range`)

A range represents a sequence of integers, commonly used in loops.

Example:

```
numbers = range(1, 6)

for number in numbers:
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

### E. Set (`set`)

A set is an unordered collection of unique elements.

Example:

```
ports = {80, 443, 22, 80}

print(ports)
```

The duplicate value `80` is stored only once.

Sets are useful for removing duplicates and performing mathematical set operations.

### F. Dictionary (`dict`)

A dictionary stores data as key-value pairs.

Example:

```
student = {
    "name": "Mohit",
    "course": "Cybersecurity",
    "year": 1
}

print(student["name"])
print(student["course"])
```

Output:

```
Mohit
Cybersecurity
```

Dictionary keys must be hashable. Dictionary values can be of different types.

### G. None Type (`NoneType`)

`None` represents the absence of a value.

Example:

```
result = None

print(result)
print(type(result))
```

Output:

```
None
<class 'NoneType'>
```

It is commonly used when a value has not been assigned or a function has no meaningful result to return.

## 7. Mutable and Immutable Data Types

Python objects can be classified according to whether their contents can be changed after creation.

### Mutable Data Types

Mutable objects can be modified after creation.

Examples:

- List
    
- Dictionary
    
- Set
    

Example:

```
tools = ["Nmap", "Wireshark"]

tools.append("Burp Suite")

print(tools)
```

Output:

```
['Nmap', 'Wireshark', 'Burp Suite']
```

The existing list object is modified.

### Immutable Data Types

Immutable objects cannot be modified after creation.

Examples:

- Integer
    
- Float
    
- Boolean
    
- String
    
- Tuple
    
- Range
    
- Bytes
    
- Frozen set
    

Example:

```
name = "Python"

# This would raise a TypeError:
# name[0] = "J"
```

You can create a new string, but you cannot change an individual character in the existing string.

### Comparison

|Mutable|Immutable|
|---|---|
|Can be modified after creation|Cannot be modified after creation|
|List|Tuple|
|Dictionary|String|
|Set|Integer|
||Float|
||Boolean|

**Important:** A tuple is immutable, but it can contain a mutable object such as a list. The list inside it may still be modified.

## 8. Type Conversion

Type conversion means converting a value from one data type to another.

Python provides built-in conversion functions.

|Function|Purpose|
|---|---|
|`int()`|Converts compatible values to an integer|
|`float()`|Converts compatible values to a float|
|`str()`|Converts an object to its string representation|
|`bool()`|Converts an object to a Boolean value|
|`list()`|Creates a list|
|`tuple()`|Creates a tuple|
|`set()`|Creates a set|
|`dict()`|Creates a dictionary from suitable key-value data|

Example:

```
number = "100"

converted_number = int(number)

print(converted_number)
print(type(converted_number))
```

Output:

```
100
<class 'int'>
```

### Implicit Type Conversion

Python sometimes converts compatible numeric types automatically.

Example:

```
a = 10
b = 2.5

result = a + b

print(result)
print(type(result))
```

Output:

```
12.5
<class 'float'>
```

### Explicit Type Conversion

The programmer manually converts the value.

Example:

```
age = "18"

age = int(age)

print(age + 2)
```

Output:

```
20
```

## 9. Variable Scope

Scope determines where a variable can be accessed.

Python commonly uses four scope levels:

1. Local
    
2. Enclosing
    
3. Global
    
4. Built-in
    

This is known as the LEGB rule.

### A. Local Scope

A variable created inside a function is local to that function.

```
def display():
    message = "Hello"
    print(message)

display()
```

### B. Global Scope

A variable created outside functions has global scope within its module.

```
username = "student"

def display():
    print(username)

display()
```

### C. Enclosing Scope

A variable in an outer function can be accessed by an inner function.

```
def outer():
    message = "ROOTLOG"

    def inner():
        print(message)

    inner()

outer()
```

### D. Built-in Scope

Python provides built-in names such as:

- `print()`
    
- `len()`
    
- `type()`
    
- `range()`
    

These names are available without importing a module.

Detailed topic: [[Scope and Lifetime]]

## 10. Constants in Python

A constant is a value intended to remain unchanged throughout a program.

Python does not enforce constant variables through special declaration syntax.

By convention, constants are written using uppercase names.

Example:

```
MAX_ATTEMPTS = 5
DEFAULT_PORT = 443
APPLICATION_NAME = "ROOTLOG"

print(MAX_ATTEMPTS)
```

The uppercase naming convention communicates that these values should not be reassigned.

## 11. Variable Identity and References

Python variables refer to objects rather than directly storing values in the same way as some lower-level languages.

The built-in `id()` function returns an object's identity during its lifetime.

Example:

```
a = [10, 20, 30]
b = a

print(a is b)
```

Output:

```
True
```

Both names refer to the same list object.

Changing the list through one name affects what is observed through the other name.

```
b.append(40)

print(a)
```

Output:

```
[10, 20, 30, 40]
```

This is important when working with mutable objects.

## 12. Data Types in Cybersecurity

Understanding data types is useful when writing security applications.

### A. IP Addresses

IP addresses are commonly represented as strings when processing text input.

```
ip_address = "192.168.1.10"

print(type(ip_address))
```

For actual IP address validation and manipulation, Python provides the `ipaddress` module.

```
import ipaddress

address = ipaddress.ip_address("192.168.1.10")

print(address.is_private)
```

### B. Port Numbers

Port numbers are usually represented as integers.

```
port = 443

print(type(port))
```

### C. Log Records

A log record may contain different data types.

```
log = {
    "username": "student",
    "status": "FAILED",
    "attempts": 3,
    "verified": False
}

print(log)
```

### D. File Hashes

Cryptographic hash values are commonly represented as hexadecimal strings.

```
import hashlib

data = b"ROOTLOG"

file_hash = hashlib.sha256(data).hexdigest()

print(file_hash)
```

### E. Network Data

Network applications may work with:

- Strings
    
- Integers
    
- Bytes
    
- Lists
    
- Dictionaries
    
- Tuples
    

The `bytes` type is particularly important when handling raw binary data.

## 13. Common Errors

### A. TypeError

Occurs when an operation is not supported between the supplied types.

```
# This raises TypeError:
# result = "10" + 5
```

Correct:

```
result = int("10") + 5

print(result)
```

### B. ValueError

Occurs when a function receives a value of the correct general type but cannot process its contents.

```
# This raises ValueError:
# age = int("hello")
```

### C. NameError

Occurs when Python tries to access a name that has not been defined.

```
# This raises NameError:
# print(username)
```

### D. Mutable Object Mistake

Assigning a list to another variable does not automatically create an independent copy.

```
a = [1, 2, 3]
b = a

b.append(4)

print(a)
```

Output:

```
[1, 2, 3, 4]
```

To create a shallow copy:

```
b = a.copy()
```

## 14. Practical Exercises

### Exercise 1: Variable Creation

Create variables for:

- Student name
    
- Age
    
- Course
    
- Percentage
    
- Enrollment status
    

Print their values and data types.

### Exercise 2: Type Conversion

Ask the user to enter two numbers as input.

Convert both values to integers and display their sum.

### Exercise 3: Mutable and Immutable

Create:

- One list
    
- One tuple
    
- One string
    

Try modifying each object and observe the results.

Identify which objects are mutable and which are immutable.

### Exercise 4: Cybersecurity Log Record

Create a dictionary containing:

```
event = {
    "username": "student",
    "ip_address": "192.168.1.10",
    "port": 22,
    "status": "FAILED",
    "attempts": 3
}
```

Print each key and its value.

Also print the data type of each value.

### Exercise 5: IP Address Validation

Use Python's `ipaddress` module to validate an IP address.

```
import ipaddress

ip = input("Enter an IP address: ")

try:
    address = ipaddress.ip_address(ip)
    print("Valid IP address:", address)
except ValueError:
    print("Invalid IP address")
```

Test it with:

- `192.168.1.10`
    
- `256.1.1.1`
    

## 15. Key Takeaways

- Variables are names that refer to objects.
    
- Python uses dynamic typing.
    
- `type()` identifies an object's type.
    
- `isinstance()` checks whether an object belongs to a type.
    
- Python provides numeric, Boolean, string, sequence, set, dictionary, and None types.
    
- Lists, dictionaries, and sets are mutable.
    
- Integers, floats, strings, and tuples are immutable.
    
- Type conversion can be implicit or explicit.
    
- Variable scope determines where a name can be accessed.
    
- Python uses naming conventions for constants.
    
- Understanding data types is essential for cybersecurity programming.
    

## 16. Related Topics

- [[Introduction to Python]]
    
- [[Python Syntax]]
    
- [[Variables and Constants]]
    
- [[Data Types]]
    
- [[Type Conversion]]
    
- [[Operators]]
    
- [[Input and Output]]
    
- [[Lists]]
    
- [[Tuples]]
    
- [[Dictionaries]]
    
- [[Sets]]
    
- [[Scope and Lifetime]]
    
- [[Python for Cybersecurity]]