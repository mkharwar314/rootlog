> Understand how JavaScript stores information, represents different types of values, and handles type conversion.

## 1. What Are Variables?

A variable is a named storage reference used to hold a value that a program can access and manipulate.

Example:

```
let username = "Mohit";
let age = 18;

console.log(username);
console.log(age);
```

Output:

```
Mohit
18
```

Here:

- `username` is a variable containing a string.
    
- `age` is a variable containing a number.
    
- `let` declares the variables.
    

## 2. Declaring Variables

JavaScript provides three main variable declaration keywords:

1. `var`
    
2. `let`
    
3. `const`
    

### A. var

`var` is the older way of declaring variables.

```
var name = "Mohit";

name = "Rahul";

console.log(name);
```

Output:

```
Rahul
```

Characteristics:

- Function-scoped or globally scoped.
    
- Can be reassigned.
    
- Can be redeclared in the same scope.
    
- Can be accessed before its declaration in some circumstances because of hoisting, but its initial value is `undefined`.
    

### B. let

`let` is used when a variable needs to be reassigned.

```
let age = 18;

age = 19;

console.log(age);
```

Output:

```
19
```

Characteristics:

- Block-scoped.
    
- Can be reassigned.
    
- Cannot be redeclared in the same scope.
    
- Cannot be accessed before its declaration is evaluated.
    

### C. const

`const` is used when a variable binding should not be reassigned.

```
const country = "India";

console.log(country);
```

Trying to reassign it causes a `TypeError`.

```
const country = "India";

country = "Japan";
```

Characteristics:

- Block-scoped.
    
- Cannot be reassigned.
    
- Cannot be redeclared in the same scope.
    
- Must be initialized when declared.
    

### Comparison

|Feature|var|let|const|
|---|---|---|---|
|Scope|Function/global|Block|Block|
|Reassignment|Yes|Yes|No|
|Redeclaration in same scope|Yes|No|No|
|Must initialize immediately|No|No|Yes|

**Best practice:** Prefer `const` by default. Use `let` when reassignment is necessary. Avoid `var` in modern JavaScript unless required by a particular codebase.

## 3. Scope of Variables

Scope determines where a variable can be accessed.

### A. Global Scope

A variable declared at the top level of a script is generally accessible throughout that script.

```
const website = "example.com";

function showWebsite() {
    console.log(website);
}

showWebsite();
```

### B. Function Scope

Variables declared with `var` inside a function are accessible within that function.

```
function test() {
    var message = "Hello";
    console.log(message);
}

test();
```

The variable `message` cannot be accessed outside the function.

### C. Block Scope

Variables declared with `let` and `const` inside a block are accessible only within that block.

```
if (true) {
    let age = 18;
    const name = "Mohit";

    console.log(age);
    console.log(name);
}
```

Accessing `age` or `name` outside the block causes a `ReferenceError`.

## 4. Variable Naming Rules

JavaScript variable names must follow certain rules.

Valid examples:

```
let username = "Mohit";
let userAge = 18;
let _count = 10;
let $price = 500;
let user1 = "Rahul";
```

Invalid examples:

```
let 1user = "Mohit";
let user-name = "Rahul";
let let = 10;
```

Rules:

1. Names cannot begin with a number.
    
2. Names can contain letters, digits, `_`, and `$`.
    
3. Names cannot contain spaces.
    
4. Reserved keywords cannot be used as variable names.
    
5. JavaScript is case-sensitive.
    

For example:

```
let username = "Mohit";
let UserName = "Rahul";

console.log(username);
console.log(UserName);
```

These are two different variables.

## 5. What Are Data Types?

A data type describes the kind of value a variable holds.

JavaScript is dynamically typed, meaning a variable can hold values of different types at different times.

Example:

```
let value = 100;

console.log(typeof value);

value = "Hello";

console.log(typeof value);
```

Output:

```
number
string
```

## 6. Primitive Data Types

JavaScript has seven primitive data types.

### A. String

A string represents text.

```
let username = "Mohit";
let city = 'Mumbai';
let message = `Welcome`;
```

Strings can use:

- Single quotes: `'Hello'`
    
- Double quotes: `"Hello"`
    
- Backticks: `` `Hello` ``
    

Template literals allow expressions to be embedded inside strings.

```
let name = "Mohit";
let age = 18;

console.log(`My name is ${name} and I am ${age} years old.`);
```

### B. Number

The `number` type represents integers and floating-point numbers.

```
let age = 18;
let price = 99.50;

console.log(typeof age);
console.log(typeof price);
```

JavaScript uses IEEE 754 double-precision floating-point numbers.

Special numeric values include:

- `Infinity`
    
- `-Infinity`
    
- `NaN`
    

Example:

```
console.log(10 / 0);
console.log("hello" * 5);
```

Output:

```
Infinity
NaN
```

`NaN` means Not-a-Number. Its type is still `number`.

```
console.log(typeof NaN);
```

Output:

```
number
```

Use `Number.isNaN()` when checking whether a value is specifically `NaN`.

### C. BigInt

`BigInt` represents integers larger than the safe integer range of the JavaScript `Number` type.

```
let largeNumber = 123456789012345678901234567890n;

console.log(largeNumber);
console.log(typeof largeNumber);
```

The `n` suffix indicates a BigInt literal.

### D. Boolean

A Boolean represents one of two values:

- `true`
    
- `false`
    

Example:

```
let isLoggedIn = true;
let isAdmin = false;

console.log(isLoggedIn);
console.log(isAdmin);
```

Booleans are commonly used in conditions and access-control logic.

### E. Undefined

A variable that has been declared but not assigned a value has the value `undefined`.

```
let username;

console.log(username);
console.log(typeof username);
```

Output:

```
undefined
undefined
```

### F. Null

`null` represents an intentional absence of a value.

```
let selectedUser = null;

console.log(selectedUser);
```

It is often used when a value is intentionally empty or unavailable.

Important JavaScript quirk:

```
console.log(typeof null);
```

Output:

```
object
```

This is a historical behaviour of JavaScript. `null` is a primitive value, not an object.

### G. Symbol

A Symbol creates a unique primitive value, often used as a unique object property key.

```
const id1 = Symbol("id");
const id2 = Symbol("id");

console.log(id1 === id2);
```

Output:

```
false
```

Even though both Symbols use the same description, they are unique.

## 7. Non-Primitive Data Types

Objects are used to store collections of values and more complex data.

### A. Object

An object stores data in key-value pairs.

```
let student = {
    name: "Mohit",
    age: 18,
    course: "Cybersecurity"
};

console.log(student.name);
console.log(student.age);
```

### B. Array

An array stores an ordered collection of values.

```
let tools = ["Nmap", "Wireshark", "Burp Suite"];

console.log(tools[0]);
console.log(tools[1]);
```

Array indexing starts from zero.

### C. Function

Functions are callable objects in JavaScript.

```
function greet() {
    console.log("Hello!");
}

greet();
```

The `typeof` operator returns `"function"` for ordinary functions.

## 8. The typeof Operator

The `typeof` operator helps identify the type of a value.

```
console.log(typeof "Hello");
console.log(typeof 100);
console.log(typeof true);
console.log(typeof undefined);
console.log(typeof 100n);
console.log(typeof Symbol("id"));
console.log(typeof {});
console.log(typeof []);
console.log(typeof function () {});
```

Typical output:

```
string
number
boolean
undefined
bigint
symbol
object
object
function
```

Important observations:

- `typeof null` returns `"object"`.
    
- `typeof []` returns `"object"`.
    
- Arrays are objects, not a separate primitive type.
    
- `typeof` is useful, but it does not distinguish every object type.
    

For arrays, use:

```
console.log(Array.isArray([]));
```

Output:

```
true
```

## 9. Type Conversion

Type conversion means changing a value from one data type to another.

### A. String Conversion

Use `String()` to convert a value into a string.

```
let age = 18;

let result = String(age);

console.log(result);
console.log(typeof result);
```

Output:

```
18
string
```

### B. Number Conversion

Use `Number()` to convert a value into a number.

```
let value = "250";

let result = Number(value);

console.log(result);
console.log(typeof result);
```

Output:

```
250
number
```

Invalid numeric text converts to `NaN`.

```
console.log(Number("hello"));
```

Output:

```
NaN
```

### C. Boolean Conversion

Use `Boolean()` to convert a value into a Boolean.

```
console.log(Boolean(1));
console.log(Boolean(0));
console.log(Boolean(""));
console.log(Boolean("Hello"));
```

Output:

```
true
false
false
true
```

## 10. Truthy and Falsy Values

JavaScript converts values to Booleans when they are evaluated in Boolean contexts, such as conditions.

### Common Falsy Values

- `false`
    
- `0`
    
- `-0`
    
- `0n`
    
- `""`
    
- `null`
    
- `undefined`
    
- `NaN`
    

Most other values are truthy, including:

- `"0"`
    
- `"false"`
    
- `[]`
    
- `{}`
    

Example:

```
let username = "";

if (username) {
    console.log("Username exists");
} else {
    console.log("Username is empty");
}
```

Output:

```
Username is empty
```

**Security relevance:** Incorrect assumptions about truthy and falsy values can cause validation and authorization logic errors.

## 11. Type Coercion

Type coercion occurs when JavaScript automatically converts a value from one type to another during an operation.

Example:

```
console.log("10" + 5);
console.log("10" - 5);
```

Output:

```
105
5
```

Explanation:

- With `+`, JavaScript performs string concatenation in this example.
    
- With `-`, JavaScript converts the string to a number.
    

To avoid unexpected behaviour, use explicit conversions when appropriate.

## 12. Equality and Data Types

JavaScript provides two main equality comparison operators.

### Loose Equality (`==`)

Allows type conversion before comparison.

```
console.log(10 == "10");
```

Output:

```
true
```

### Strict Equality (`===`)

Compares values without converting between different types.

```
console.log(10 === "10");
```

Output:

```
false
```

Use strict equality in most situations to reduce unexpected type-conversion behaviour.

## 13. Mutability: Primitive Values vs Objects

Primitive values are immutable. This means their value cannot be changed in place.

Objects and arrays are mutable, meaning their contents can be modified.

Example:

```
const student = {
    name: "Mohit"
};

student.name = "Rahul";

console.log(student.name);
```

Output:

```
Rahul
```

This works because the object is modified, not reassigned.

However:

```
const student = {
    name: "Mohit"
};

student = {
    name: "Rahul"
};
```

This causes a `TypeError` because the `const` binding cannot be reassigned.

## 14. JavaScript Variables and Cybersecurity

Understanding variables and data types is important for application security.

### A. Input Validation

Applications must validate data before using it.

Example:

```
const age = Number("18");

if (!Number.isFinite(age)) {
    console.log("Invalid age");
} else {
    console.log("Valid numeric input");
}
```

### B. Type Confusion

Unexpected type conversion can produce incorrect application behaviour.

Security-sensitive code should validate types and values explicitly.

### C. Authentication Logic

Boolean conditions and comparisons are frequently used in authentication and authorization.

Incorrect conditions can result in access-control vulnerabilities.

### D. Sensitive Information

Do not store passwords, private keys, or secret API credentials in frontend JavaScript.

Browser code is accessible to users and can be inspected.

## 15. Practical Lab — Variables and Data Types

### Objective

Create a JavaScript program that declares variables, identifies their data types, and performs type conversion.

### Step 1: Create a JavaScript file

Create:

```
variables.js
```

### Step 2: Write the program

```
const studentName = "Mohit";
let age = 18;
let isStudent = true;
let selectedCourse = null;

console.log("Student:", studentName);
console.log("Age:", age);
console.log("Is Student:", isStudent);
console.log("Selected Course:", selectedCourse);

console.log("Name Type:", typeof studentName);
console.log("Age Type:", typeof age);
console.log("Boolean Type:", typeof isStudent);
console.log("Null Type:", typeof selectedCourse);

// Type conversion
let marks = "85";

let convertedMarks = Number(marks);

console.log("Original:", marks);
console.log("Converted:", convertedMarks);
console.log("Converted Type:", typeof convertedMarks);
```

### Step 3: Run the program

If Node.js is installed, open a terminal in the directory and run:

```
node variables.js
```

Alternatively, include the JavaScript file in an HTML page and inspect the browser console.

### Step 4: Experiment

1. Change `age` from a number to a string.
    
2. Check the result of `typeof`.
    
3. Convert `"500"` into a number.
    
4. Convert `"hello"` into a number.
    
5. Test `Boolean(0)` and `Boolean("0")`.
    
6. Try modifying a `const` object property.
    
7. Try reassigning a `const` variable and observe the error.
    

### Expected Learning

After completing this lab, you should understand:

- Variable declaration.
    
- Difference between `var`, `let`, and `const`.
    
- Variable scope.
    
- Primitive and non-primitive data types.
    
- Type checking.
    
- Type conversion and coercion.
    
- Truthy and falsy values.
    
- Mutability.
    

## 16. Key Takeaways

- Variables store values that programs can use.
    
- JavaScript provides `var`, `let`, and `const`.
    
- JavaScript is dynamically typed.
    
- There are seven primitive data types.
    
- Objects, arrays, and functions are non-primitive values.
    
- `typeof` helps identify data types but has some limitations.
    
- Type conversion can be explicit or implicit.
    
- Strict equality (`===`) avoids many unexpected conversion behaviours.
    
- Understanding types is important for writing secure application logic.
    

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Operators]]
    
- [[JavaScript Control Flow]]
    
- [[JavaScript Functions]]
    
- [[JavaScript Arrays and Objects]]
    
- [[JavaScript DOM]]
    
- [[Input Validation]]
    
- [[Cross-Site Scripting Prevention]]
    

---

## My Understanding

Answer in your own words:

1. What is a variable?
    
2. What is the difference between `var`, `let`, and `const`?
    
3. What is variable scope?
    
4. What are the seven primitive data types?
    
5. What is the difference between `null` and `undefined`?
    
6. What is type coercion?
    
7. What is the difference between `==` and `===`?
    
8. Why does `typeof null` return `"object"`?
    
9. What is the difference between mutable and immutable values?
    

## Questions & Doubts

Record any concepts that need further explanation or practical testing.