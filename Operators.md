> Understand how operators perform calculations, compare values, make decisions, and manipulate data in programming.

## 1. Introduction

An operator is a symbol or keyword that performs an operation on one or more values.

The values on which operators work are called **operands**.

Example:

```
result = 10 + 20
```

Here:

- `10` is an operand.   
- `20` is an operand.
- `+` is an operator.
- `result` stores the calculated value.

Output:

```
30
```

Operators are essential for:

- Mathematical calculations.
- Comparing values.
- Making decisions.
- Controlling program execution.
- Manipulating binary data.
- Checking conditions.

## 2. Types of Operators

Common operator categories include:

1. Arithmetic operators.
2. Assignment operators.
3. Comparison operators.
4. Logical operators.
5. Bitwise operators.
6. Membership operators.
7. Identity operators.

The exact operators available depend on the programming language.

## 3. Arithmetic Operators

Arithmetic operators perform mathematical calculations.

|Operator|Name|Example|Result|
|---|---|---|---|
|`+`|Addition|`10 + 5`|`15`|
|`-`|Subtraction|`10 - 5`|`5`|
|`*`|Multiplication|`10 * 5`|`50`|
|`/`|Division|`10 / 5`|`2.0`|
|`//`|Floor division|`11 // 5`|`2`|
|`%`|Modulus|`11 % 5`|`1`|
|`**`|Exponentiation|`2 ** 3`|`8`|

### 3.1 Addition

Adds two values.

```
a = 10
b = 20

print(a + b)
```

Output:

```
30
```

### 3.2 Subtraction

Subtracts one value from another.

```
a = 50
b = 20

print(a - b)
```

Output:

```
30
```

### 3.3 Multiplication

Multiplies two values.

```
length = 10
width = 5

area = length * width

print(area)
```

Output:

```
50
```

### 3.4 Division

Divides one value by another.

```
print(10 / 2)
```

Output:

```
5.0
```

In Python, `/` performs true division and normally produces a floating-point result.

### 3.5 Floor Division

Returns the quotient rounded down to the nearest integer.

```
print(11 // 5)
```

Output:

```
2
```

### 3.6 Modulus

Returns the remainder after division.

```
print(11 % 5)
```

Output:

```
1
```

Common uses:

- Checking whether a number is even or odd.
- Repeating operations at intervals.
- Working with cyclic values.

Example:

```
number = 10

if number % 2 == 0:
    print("Even number")
```

### 3.7 Exponentiation

Raises a number to a power.

```
print(2 ** 4)
```

Output:

```
16
```

## 4. Assignment Operators

Assignment operators assign or update values stored through variables.

|Operator|Example|Equivalent Expression|
|---|---|---|
|`=`|`x = 10`|Assign 10 to x|
|`+=`|`x += 5`|`x = x + 5`|
|`-=`|`x -= 5`|`x = x - 5`|
|`*=`|`x *= 5`|`x = x * 5`|
|`/=`|`x /= 5`|`x = x / 5`|
|`//=`|`x //= 5`|`x = x // 5`|
|`%=`|`x %= 5`|`x = x % 5`|
|`**=`|`x **= 2`|`x = x ** 2`|

Example:

```
balance = 1000

balance += 500

print(balance)
```

Output:

```
1500
```

**Important:** Assignment (`=`) is different from comparison (`==`).

## 5. Comparison Operators

Comparison operators compare two values and produce a Boolean result.

|Operator|Meaning|Example|
|---|---|---|
|`==`|Equal to|`10 == 10`|
|`!=`|Not equal to|`10 != 5`|
|`>`|Greater than|`10 > 5`|
|`<`|Less than|`5 < 10`|
|`>=`|Greater than or equal to|`10 >= 10`|
|`<=`|Less than or equal to|`5 <= 10`|

Example:

```
age = 20

print(age >= 18)
```

Output:

```
True
```

### 5.1 Practical Example

```
failed_attempts = 3
maximum_attempts = 5

print(failed_attempts < maximum_attempts)
```

Output:

```
True
```

Comparison operators are commonly used in:

- Authentication checks.
- Access-control decisions.
- Input validation.
- Security monitoring.
- Threshold detection.

## 6. Logical Operators

Logical operators combine or reverse Boolean conditions.

Python provides three main logical operators:

|Operator|Meaning|
|---|---|
|`and`|True when both conditions are true|
|`or`|True when at least one condition is true|
|`not`|Reverses the Boolean result|

### 6.1 AND Operator

Both conditions must be true.

```
username_valid = True
password_valid = True

if username_valid and password_valid:
    print("Login successful")
```

Output:

```
Login successful
```

Truth table:

|A|B|A and B|
|---|---|---|
|True|True|True|
|True|False|False|
|False|True|False|
|False|False|False|

### 6.2 OR Operator

At least one condition must be true.

```
is_admin = False
is_moderator = True

if is_admin or is_moderator:
    print("Access granted")
```

Truth table:

|A|B|A or B|
|---|---|---|
|True|True|True|
|True|False|True|
|False|True|True|
|False|False|False|

### 6.3 NOT Operator

Reverses a Boolean value.

```
is_locked = False

print(not is_locked)
```

Output:

```
True
```

Truth table:

|A|not A|
|---|---|
|True|False|
|False|True|

**Security note:** Logical conditions must be designed carefully. A mistake in an authentication or authorization condition can accidentally grant access to unauthorized users.

## 7. Bitwise Operators

Bitwise operators perform operations on individual bits of integer values.

They are useful in:

- Low-level programming.
- Networking.
- Cryptography implementations.
- File formats.
- Permission flags.
- Hardware programming.

Consider two binary values:

```
A = 5 = 0101
B = 3 = 0011
```

### 7.1 Bitwise AND (`&`)

A bit becomes 1 only when both corresponding bits are 1.

```
print(5 & 3)
```

Binary:

```
0101
0011
----
0001
```

Result:

```
1
```

### 7.2 Bitwise OR (`|`)

A bit becomes 1 when at least one corresponding bit is 1.

```
print(5 | 3)
```

Binary:

```
0101
0011
----
0111
```

Result:

```
7
```

### 7.3 Bitwise XOR (`^`)

A bit becomes 1 when the corresponding bits are different.

```
print(5 ^ 3)
```

Binary:

```
0101
0011
----
0110
```

Result:

```
6
```

### 7.4 Bitwise NOT (`~`)

In Python, bitwise NOT inverts the integer's bits according to its signed integer representation.

```
print(~5)
```

Output:

```
-6
```

For Python integers:

[  
\sim x = -x - 1  
]

### 7.5 Left Shift (`<<`)

Shifts bits to the left.

```
print(5 << 1)
```

Binary:

```
0101 -> 1010
```

Result:

```
10
```

### 7.6 Right Shift (`>>`)

Shifts bits to the right.

```
print(5 >> 1)
```

Binary:

```
0101 -> 0010
```

Result:

```
2
```

**Important:** Bitwise behavior can depend on the language's integer representation and rules. Python uses arbitrary-precision signed integers, so its behavior differs from fixed-width integer types in C.

## 8. Membership Operators

Membership operators check whether a value exists in a collection.

Python provides:

- `in`
- `not in`

Example:

```
ports = [22, 80, 443]

print(80 in ports)
print(3306 not in ports)
```

Output:

```
True
True
```

Common uses:

- Checking whether a username exists.
- Searching a list of ports.
- Checking whether a value appears in a dataset.
- Validating input against allowed values.

Example:

```
allowed_users = ["admin", "analyst", "student"]

username = "analyst"

if username in allowed_users:
    print("User found")
```

Membership checks alone should not be treated as a complete authentication or authorization mechanism.

## 9. Identity Operators

Identity operators check whether two references point to the same object.

Python provides:

- `is`
- `is not`

Example:

```
a = None

print(a is None)
```

Output:

```
True
```

### Equality vs Identity

These concepts are different.

**Equality (**`**==**`**)** checks whether two values are equal.

**Identity (**`**is**`**)** checks whether two references point to the same object.

Example:

```
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)
print(a is b)
```

Output:

```
True
False
```

The lists contain equal values, but they are separate objects.

Use `is` for identity checks, especially comparisons with `None`, rather than using it as a replacement for `==`.

## 10. Operator Precedence

Operator precedence determines the order in which parts of an expression are evaluated.

Example:

```
result = 10 + 5 * 2

print(result)
```

Output:

```
20
```

Multiplication is evaluated before addition.

Using parentheses changes the evaluation order:

```
result = (10 + 5) * 2

print(result)
```

Output:

```
30
```

### Common Python Precedence Order

From higher to lower precedence:

|Priority|Operators|
|---|---|
|1|Parentheses and grouping|
|2|Exponentiation `**`|
|3|Unary `+`, `-`, `~`|
|4|`*`, `/`, `//`, `%`|
|5|`+`, `-`|
|6|Shifts `<<`, `>>`|
|7|Bitwise `&`|
|8|Bitwise `^`|
|9|Bitwise `|`|
|10|Comparisons, membership, identity|
|11|`not`|
|12|`and`|
|13|`or`|

Use parentheses when an expression might be difficult to understand.

## 11. Operators in Different Languages

Operators may look similar across languages, but their behavior and available forms can differ.

|Operation|Python|C|JavaScript|
|---|---|---|---|
|Addition|`+`|`+`|`+`|
|Assignment|`=`|`=`|`=`|
|Equality|`==`|`==`|`==`|
|Strict equality|No separate operator|No separate operator|`===`|
|Logical AND|`and`|`&&`|`&&`|
|Logical OR|`or`|`||`|`||`|
|Logical NOT|`not`|`!`|`!`|
|Bitwise AND|`&`|`&`|`&`|
|Bitwise OR|`|`|`|`|`|`|
|Bitwise XOR|`^`|`^`|`^`|

JavaScript has both loose equality (`==`) and strict equality (`===`). Prefer strict equality in most application code when type coercion is not intended.

## 12. Operators in Cybersecurity

Operators are used in many cybersecurity-related programs.

### 12.1 Login Validation

```
username_valid = True
password_valid = True

if username_valid and password_valid:
    print("Authentication successful")
else:
    print("Authentication failed")
```

This demonstrates Boolean logic. A real authentication system must verify credentials securely rather than relying on hardcoded Boolean values.

### 12.2 Failed Login Monitoring

```
failed_attempts = 6
threshold = 5

if failed_attempts > threshold:
    print("Investigate suspicious activity")
```

Comparison operators help identify values that exceed defined thresholds.

### 12.3 Port Checking

```
port = 443

if port in [80, 443, 8080]:
    print("Port is in the configured list")
```

Membership operators help check values against collections.

### 12.4 Permission Flags

Bitwise operators can be used to work with permission flags.

For example, in a system using bit flags:

```
READ = 1
WRITE = 2
EXECUTE = 4

permissions = READ | WRITE

print(permissions & READ != 0)
print(permissions & EXECUTE != 0)
```

Output:

```
True
False
```

This demonstrates how individual permissions can be represented and checked using bits.

## 13. Common Mistakes

|Mistake|Explanation|
|---|---|
|Using `=` instead of `==`|Assignment is not comparison|
|Confusing `and` with `or`|They produce different logical results|
|Ignoring operator precedence|Expressions may produce unexpected results|
|Confusing `is` with `==`|Identity and equality are different|
|Mixing strings and numbers|Operations may fail or behave differently|
|Misunderstanding bitwise operators|They operate on bits, not ordinary Boolean conditions|
|Forgetting division by zero|Can produce runtime errors|
|Writing unclear conditions|Can introduce security and logic defects|

## 14. Practical Lab

### Lab 1: Arithmetic Operators

Create a file named:

`operators_lab.py`

Add:

```
a = 20
b = 6

print("Addition:", a + b)
print("Subtraction:", a - b)
print("Multiplication:", a * b)
print("Division:", a / b)
print("Floor division:", a // b)
print("Modulus:", a % b)
print("Exponentiation:", a ** b)
```

Run:

```
python operators_lab.py
```

On Kali Linux, use `python3` if required.

### Lab 2: Comparison and Logical Operators

```
failed_attempts = 3
maximum_attempts = 5

print(failed_attempts < maximum_attempts)

is_admin = False
is_authenticated = True

print(is_admin or is_authenticated)
print(is_admin and is_authenticated)
print(not is_admin)
```

Predict the results before running the program.

### Lab 3: Bitwise Operators

```
a = 5
b = 3

print("AND:", a & b)
print("OR:", a | b)
print("XOR:", a ^ b)
print("Left shift:", a << 1)
print("Right shift:", a >> 1)
```

Write the binary representation of `a` and `b` in your notebook.

### Lab 4: Simple Security Condition

```
failed_attempts = 6
account_locked = False

if failed_attempts >= 5 and not account_locked:
    print("Account requires investigation")
else:
    print("No action required")
```

Explain how the comparison and logical operators work together.

## 14. Key Takeaways

- Operators perform operations on values.
- Arithmetic operators perform calculations.
- Assignment operators update variables.
- Comparison operators return Boolean results.
- Logical operators combine conditions.
- Bitwise operators manipulate individual bits.
- Membership operators check collection contents.
- Identity operators compare object identity.
- Operator precedence determines evaluation order.
- Correct operator usage is important for reliable and secure programs.

## 15. Questions for Self-Study

1. What is an operator?
2. What are operands?
3. Explain arithmetic operators with examples.
4. What is the difference between `/` and `//` in Python?
5. What is the purpose of the modulus operator?
6. Explain assignment operators.
7. What is the difference between `=` and `==`?
8. Explain comparison operators.
9. What are logical operators?
10. Explain the truth tables for AND, OR, and NOT.
11. What are bitwise operators?
12. What is the difference between `is` and `==`?
13. What is operator precedence?
14. How are operators used in cybersecurity programs?

## 16. Practical Tasks

1. Write a program that performs all arithmetic operations on two numbers.
2. Write a program that checks whether a number is even or odd.
3. Write a program that checks whether a user meets two conditions before displaying an access message.
4. Use bitwise AND, OR, and XOR on two integers.
5. Create a list of common network ports and check whether port 443 exists.
6. Write a program that identifies when failed login attempts reach a defined threshold.
7. Explain the difference between equality and identity using your own example.

## Related Notes

- [[Introduction to Programming]]
- [[Programming Languages]]
- [[Variables and Constants]]
- [[Data Types]]
- [[Input and Output]]
- [[Conditional Statements]]
- [[Loops]]
- [[Python Operators]]
- [[C Operators and Control Flow]]
- [[JavaScript Operators]]
- [[Secure Programming]]