> Understand how JavaScript operators perform calculations, compare values, assign data, and evaluate logical conditions.

## 1. What Are Operators?

Operators are symbols or keywords used to perform operations on values and variables.

Example:

```
let a = 10;
let b = 5;

console.log(a + b);
```

Output:

```
15
```

Here:

- `a` and `b` are operands.
    
- `+` is an operator.
    
- `a + b` is an expression.
    

## 2. Types of JavaScript Operators

JavaScript supports several categories of operators:

1. Arithmetic operators
    
2. Assignment operators
    
3. Comparison operators
    
4. Logical operators
    
5. String operators
    
6. Unary operators
    
7. Bitwise operators
    
8. Conditional (ternary) operator
    
9. Nullish coalescing operator
    
10. Optional chaining operator
    
11. Type operators
    

## 3. Arithmetic Operators

Arithmetic operators perform mathematical calculations.

|Operator|Name|Example|Result|
|---|---|---|---|
|`+`|Addition|`10 + 5`|`15`|
|`-`|Subtraction|`10 - 5`|`5`|
|`*`|Multiplication|`10 * 5`|`50`|
|`/`|Division|`10 / 5`|`2`|
|`%`|Modulus|`10 % 3`|`1`|
|`**`|Exponentiation|`2 ** 3`|`8`|

### Example

```
let a = 20;
let b = 6;

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(a / b);
console.log(a % b);
console.log(a ** 2);
```

Output:

```
26
14
120
3.3333333333333335
2
400
```

### Modulus Operator

The modulus operator returns the remainder after division.

```
console.log(10 % 2);
console.log(10 % 3);
```

Output:

```
0
1
```

Common use: checking whether a number is even or odd.

```
let number = 7;

if (number % 2 === 0) {
    console.log("Even");
} else {
    console.log("Odd");
}
```

## 4. Assignment Operators

Assignment operators assign values to variables.

|Operator|Example|Equivalent|
|---|---|---|
|`=`|`x = 10`|Assign 10|
|`+=`|`x += 5`|`x = x + 5`|
|`-=`|`x -= 5`|`x = x - 5`|
|`*=`|`x *= 5`|`x = x * 5`|
|`/=`|`x /= 5`|`x = x / 5`|
|`%=`|`x %= 5`|`x = x % 5`|
|`**=`|`x **= 2`|`x = x ** 2`|

Example:

```
let score = 10;

score += 5;
console.log(score);

score *= 2;
console.log(score);

score -= 4;
console.log(score);
```

Output:

```
15
30
26
```

## 5. Comparison Operators

Comparison operators compare two values and return a Boolean result (`true` or `false`).

|Operator|Meaning|Example|
|---|---|---|
|`==`|Equal after possible type conversion|`5 == "5"`|
|`===`|Strict equality|`5 === 5`|
|`!=`|Not equal after possible type conversion|`5 != "6"`|
|`!==`|Strict inequality|`5 !== "5"`|
|`>`|Greater than|`10 > 5`|
|`<`|Less than|`5 < 10`|
|`>=`|Greater than or equal|`10 >= 10`|
|`<=`|Less than or equal|`5 <= 10`|

### Example

```
let a = 10;
let b = 5;

console.log(a > b);
console.log(a < b);
console.log(a === b);
console.log(a !== b);
```

Output:

```
true
false
false
true
```

### Strict vs Loose Equality

```
console.log(10 == "10");
console.log(10 === "10");
```

Output:

```
true
false
```

Explanation:

- `==` allows type conversion before comparison.
    
- `===` compares without converting between different types.
    

**Best practice:** Prefer `===` and `!==` for predictable comparisons.

## 6. Logical Operators

Logical operators combine or reverse Boolean conditions.

### A. AND (`&&`)

Returns a truthy or falsy operand according to logical AND evaluation. When used with Boolean conditions, the result behaves like AND.

Both conditions must be truthy for the overall expression to be truthy.

```
let age = 20;
let hasID = true;

console.log(age >= 18 && hasID);
```

Output:

```
true
```

### B. OR (`||`)

Returns the first truthy operand, or the last operand if none is truthy.

At least one condition must be truthy for the overall expression to be truthy.

```
let isAdmin = false;
let isModerator = true;

console.log(isAdmin || isModerator);
```

Output:

```
true
```

### C. NOT (`!`)

Reverses the Boolean interpretation of a value.

```
let isLoggedIn = false;

console.log(!isLoggedIn);
```

Output:

```
true
```

### Comparison

|Operator|Meaning|
|---|---|
|`&&`|Logical AND|
|`||`|Logical OR|
|`!`|Logical NOT|

## 7. Short-Circuit Evaluation

JavaScript logical operators use short-circuit evaluation.

This means the second operand may not be evaluated if the first operand already determines the result.

### AND Example

```
let isLoggedIn = false;

isLoggedIn && console.log("Welcome");
```

The message is not printed because the first operand is falsy.

### OR Example

```
let username = "";

let displayName = username || "Guest";

console.log(displayName);
```

Output:

```
Guest
```

The `||` operator returns the first truthy operand.

**Important:** Logical operators do not always return Boolean values. They can return one of their original operands.

## 8. String Operators

The `+` operator can concatenate strings.

Example:

```
let firstName = "Mohit";
let lastName = "Kharwar";

let fullName = firstName + " " + lastName;

console.log(fullName);
```

Output:

```
Mohit Kharwar
```

The `+=` operator can also append text.

```
let message = "Hello";

message += " Student";

console.log(message);
```

Output:

```
Hello Student
```

## 9. Unary Operators

Unary operators operate on a single operand.

### A. Increment (`++`)

Increases a numeric value by one.

```
let count = 5;

count++;

console.log(count);
```

Output:

```
6
```

### B. Decrement (`--`)

Decreases a numeric value by one.

```
let count = 5;

count--;

console.log(count);
```

Output:

```
4
```

### C. Unary Plus (`+`)

Attempts to convert a value into a number.

```
let value = "25";

console.log(+value);
```

Output:

```
25
```

### D. Unary Minus (`-`)

Converts a value to a number and negates it.

```
let value = 25;

console.log(-value);
```

Output:

```
-25
```

### Prefix and Postfix

```
let a = 5;

console.log(++a);
```

Output:

```
6
```

The prefix operator increments before returning the value.

```
let b = 5;

console.log(b++);
console.log(b);
```

Output:

```
5
6
```

The postfix operator returns the original value before incrementing it.

## 10. Conditional (Ternary) Operator

The ternary operator is a compact way to choose between two expressions based on a condition.

Syntax:

```
condition ? expressionIfTrue : expressionIfFalse;
```

Example:

```
let age = 20;

let result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

Output:

```
Adult
```

It is useful for simple conditional assignments. For complex logic, use `if...else`.

## 11. Nullish Coalescing Operator (`??`)

The nullish coalescing operator returns the right-hand value only when the left-hand value is `null` or `undefined`.

Example:

```
let username = null;

let displayName = username ?? "Guest";

console.log(displayName);
```

Output:

```
Guest
```

Compare it with `||`:

```
console.log(0 || 100);
console.log(0 ?? 100);
```

Output:

```
100
0
```

Explanation:

- `||` uses the fallback when the left value is falsy.
    
- `??` uses the fallback only when the left value is `null` or `undefined`.
    

## 12. Optional Chaining Operator (`?.`)

Optional chaining safely accesses a property or method when an intermediate value may be `null` or `undefined`.

Example:

```
let student = {
    name: "Mohit"
};

console.log(student.address?.city);
```

Output:

```
undefined
```

Without optional chaining, trying to access a property of an undefined or null intermediate value would normally cause a `TypeError`.

Optional chaining does not replace proper validation of application data.

## 13. Bitwise Operators

Bitwise operators work with the binary representation of numbers.

Common operators:

|Operator|Name|
|---|---|
|`&`|AND|
|`|`|OR|
|`^`|XOR|
|`~`|NOT|
|`<<`|Left shift|
|`>>`|Sign-propagating right shift|
|`>>>`|Zero-fill right shift|

Example:

```
let a = 5;
let b = 3;

console.log(a & b);
console.log(a | b);
console.log(a ^ b);
```

Output:

```
1
7
6
```

Binary representation:

```
5 = 0101
3 = 0011

AND = 0001 = 1
OR  = 0111 = 7
XOR = 0110 = 6
```

Bitwise operations can be useful in low-level programming, flags, and binary data processing.

JavaScript's standard bitwise operators convert Number operands to 32-bit integers. BigInt has separate bitwise behaviour.

## 14. Type Operators

JavaScript provides operators that help inspect or test types and objects.

### A. typeof

Returns a string indicating the type of a value.

```
let value = 100;

console.log(typeof value);
```

Output:

```
number
```

### B. instanceof

Checks whether an object is an instance of a particular constructor's prototype chain.

```
let tools = ["Nmap", "Wireshark"];

console.log(tools instanceof Array);
```

Output:

```
true
```

`instanceof` is useful for checking object relationships, but it is not a universal type-checking solution.

## 15. Operator Precedence

Operator precedence determines the order in which operations are evaluated.

Example:

```
let result = 10 + 5 * 2;

console.log(result);
```

Output:

```
20
```

Multiplication is performed before addition.

Using parentheses changes the evaluation order:

```
let result = (10 + 5) * 2;

console.log(result);
```

Output:

```
30
```

**Best practice:** Use parentheses when an expression could be difficult to understand.

## 16. Operator Precedence Reference

A simplified order from higher to lower precedence:

|Category|Operators|
|---|---|
|Grouping|`()`|
|Member access|`.`, `[]`, `?.`|
|Unary|`!`, `+`, `-`, `typeof`, `++`, `--`|
|Exponentiation|`**`|
|Multiplication|`*`, `/`, `%`|
|Addition|`+`, `-`|
|Comparison|`<`, `>`, `<=`, `>=`, `instanceof`|
|Equality|`==`, `===`, `!=`, `!==`|
|Logical AND|`&&`|
|Logical OR|`||`|
|Nullish coalescing|`??`|
|Conditional|`?:`|
|Assignment|`=`, `+=`, `-=`, etc.|

This is a simplified reference, not a complete precedence table. Some operators have special associativity and grouping rules.

## 17. JavaScript Operators in Cybersecurity

Operators are important in security-sensitive application logic.

### A. Authentication Conditions

Example:

```
let isAuthenticated = true;
let hasPermission = false;

if (isAuthenticated && hasPermission) {
    console.log("Access granted");
} else {
    console.log("Access denied");
}
```

Authentication and authorization must be enforced on the server, not only in frontend JavaScript.

### B. Input Validation

```
let age = 20;

if (Number.isFinite(age) && age >= 18) {
    console.log("Valid age");
}
```

This checks that the value is a finite number and meets the minimum requirement.

### C. Type Coercion Risks

Loose equality and automatic type conversion can create unexpected logic.

```
console.log(0 == false);
console.log(0 === false);
```

Output:

```
true
false
```

Use predictable comparisons and validate input types.

### D. Access-Control Mistakes

Incorrect use of logical operators can accidentally allow unauthorized access.

For example, an incorrect OR condition might grant access when only one requirement is satisfied.

Security-sensitive conditions should be reviewed carefully and tested with both allowed and denied cases.

## 18. Practical Lab — JavaScript Operators

### Objective

Practice arithmetic, assignment, comparison, and logical operators.

### Step 1: Create a file

```
operators.js
```

### Step 2: Write the program

```
let a = 20;
let b = 10;

// Arithmetic
console.log("Addition:", a + b);
console.log("Subtraction:", a - b);
console.log("Multiplication:", a * b);
console.log("Division:", a / b);
console.log("Remainder:", a % b);

// Assignment
let score = 50;
score += 10;
console.log("Updated Score:", score);

// Comparison
console.log("Is a greater than b?", a > b);
console.log("Are values equal?", a === b);

// Logical
let isLoggedIn = true;
let isAdmin = false;

console.log("Can access admin panel:", isLoggedIn && isAdmin);

// Ternary
let age = 20;

let status = age >= 18 ? "Adult" : "Minor";

console.log("Status:", status);

// Nullish coalescing
let username = null;

console.log(username ?? "Guest");
```

### Step 3: Run the program

Using Node.js:

```
node operators.js
```

Alternatively, connect the file to an HTML page and inspect the browser console.

### Step 4: Experiment

1. Change the values of `a` and `b`.
    
2. Test the modulus operator with even and odd numbers.
    
3. Compare `==` and `===`.
    
4. Change `isLoggedIn` and `isAdmin`.
    
5. Compare the behaviour of `||` and `??` using `0`, `false`, and `null`.
    
6. Test prefix and postfix increment.
    

### Expected Learning

You should understand how JavaScript performs calculations, comparisons, assignments, and logical evaluations.

## 19. Key Takeaways

- Operators perform operations on values.
    
- Arithmetic operators perform mathematical calculations.
    
- Assignment operators update variables.
    
- Comparison operators return Boolean results.
    
- Logical operators combine conditions.
    
- `===` is generally safer than `==` for predictable comparisons.
    
- Short-circuit evaluation can skip unnecessary expressions.
    
- Ternary, nullish coalescing, and optional chaining simplify certain expressions.
    
- Operator precedence controls evaluation order.
    
- Incorrect logical conditions can introduce security vulnerabilities.
    

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Variables and Data Types]]
    
- [[JavaScript Control Flow]]
    
- [[JavaScript Functions]]
    
- [[Conditional Statements]]
    
- [[Input Validation]]
    
- [[Authentication and Authorization]]
    

---

## My Understanding

Answer in your own words:

1. What are operators?
    
2. What is the difference between arithmetic and assignment operators?
    
3. What is the difference between `==` and `===`?
    
4. How do `&&`, `||`, and `!` work?
    
5. What is short-circuit evaluation?
    
6. What is the difference between prefix and postfix increment?
    
7. What is the ternary operator?
    
8. What is the difference between `||` and `??`?
    
9. What is operator precedence?
    
10. How can incorrect logical conditions create security problems?
    

## Questions & Doubts

Record concepts that need further explanation or practical testing.