> Understand what JavaScript is, where it runs, how it interacts with web pages, and why it is important in modern software development and cybersecurity.

## 1. What Is JavaScript?

JavaScript (JS) is a high-level, general-purpose programming language primarily used to create interactive and dynamic web applications.

It allows developers to add functionality to websites, such as:

- Responding to button clicks.
    
- Validating forms.
    
- Updating webpage content dynamically.
    
- Communicating with web servers.
    
- Creating interactive applications.
    
- Building server-side applications.
    

### Example

```
console.log("Hello, World!");
```

Output:

```
Hello, World!
```

JavaScript is one of the core technologies of web development:

|Technology|Purpose|
|---|---|
|HTML|Defines webpage structure|
|CSS|Controls webpage appearance|
|JavaScript|Adds functionality and interactivity|

## 2. History of JavaScript

JavaScript was created by Brendan Eich in 1995 while working at Netscape.

Important milestones:

- **1995:** JavaScript was created.
    
- **1997:** ECMAScript standardization began.
    
- **2009:** Node.js enabled JavaScript outside browsers.
    
- **2015:** ECMAScript 6 (ES6) introduced major language improvements.
    
- **Today:** JavaScript is widely used in frontend, backend, and application development.
    

### What Is ECMAScript?

ECMAScript is the language specification that defines how JavaScript should work.

JavaScript implementations follow the ECMAScript standard and may provide additional environment-specific features.

## 3. Features of JavaScript

Important characteristics:

1. **High-level:** Provides abstractions that simplify programming.
    
2. **Dynamically typed:** Variable types do not need to be declared explicitly.
    
3. **Multi-paradigm:** Supports procedural, object-oriented, and functional programming.
    
4. **Event-driven:** Can respond to events such as clicks and keyboard input.
    
5. **Asynchronous:** Supports operations that can complete without blocking the main execution flow.
    
6. **Cross-platform:** Runs in different browsers and other supported environments.
    
7. **Prototype-based:** Uses prototypes as a fundamental inheritance mechanism.
    

## 4. Where Does JavaScript Run?

JavaScript runs inside an execution environment called a runtime.

Two major environments are:

### A. Browser Environment

Modern browsers contain JavaScript engines that execute JavaScript code.

Examples:

- Chrome uses V8.
    
- Firefox uses SpiderMonkey.
    
- Safari uses JavaScriptCore.
    

Browser JavaScript can interact with webpage elements through the Document Object Model (DOM).

### B. Node.js Environment

Node.js allows JavaScript to execute outside a web browser.

It is commonly used for:

- Backend development.
    
- REST APIs.
    
- Automation.
    
- Command-line applications.
    
- Development tools.
    

**Important:** JavaScript is the language. Node.js is a runtime environment that executes JavaScript outside the browser.

## 5. JavaScript vs Java

JavaScript and Java are different programming languages despite having similar names.

|Feature|JavaScript|Java|
|---|---|---|
|Typing|Dynamically typed|Statically typed|
|Execution|JavaScript runtime|JVM|
|Common use|Web development|Enterprise and Android-related development|
|Object model|Prototype-based|Class-based|
|File extension|`.js`|`.java`|

## 6. Adding JavaScript to HTML

JavaScript can be added to an HTML document in different ways.

### A. Internal JavaScript

JavaScript is written inside a `<script>` element.

```
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Example</title>
</head>
<body>

    <h1>My First JavaScript Program</h1>

    <script>
        console.log("JavaScript is running!");
    </script>

</body>
</html>
```

### B. External JavaScript

JavaScript can be stored in a separate `.js` file.

**index.html**

```
<!DOCTYPE html>
<html>
<head>
    <title>External JavaScript</title>
    <script src="script.js" defer></script>
</head>
<body>

    <h1>Learning JavaScript</h1>

</body>
</html>
```

**script.js**

```
console.log("External JavaScript is working!");
```

The `defer` attribute tells the browser to download the script while parsing HTML and execute it after HTML parsing is complete.

### C. Async and Defer

|Attribute|Behaviour|
|---|---|
|`defer`|Executes after HTML parsing, preserving the order of deferred scripts|
|`async`|Executes as soon as downloading finishes; execution order is not guaranteed|

Both attributes are generally used with external scripts.

## 7. JavaScript Syntax

Syntax refers to the rules used to write valid JavaScript code.

Example:

```
let username = "Mohit";
let age = 18;

console.log(username);
console.log(age);
```

Important syntax rules:

- JavaScript is case-sensitive.
    
- Statements are commonly written on separate lines.
    
- Semicolons are optional in many situations because of Automatic Semicolon Insertion (ASI), but using them consistently can improve clarity.
    
- Code blocks are enclosed in curly braces `{}`.
    
- Strings can use single quotes, double quotes, or backticks.
    

### Comments

Comments explain code and are ignored during normal execution.

Single-line comment:

```
// This is a single-line comment
```

Multi-line comment:

```
/*
This is a
multi-line comment
*/
```

## 8. Variables in JavaScript

Variables store values that a program can use.

JavaScript provides three variable declaration keywords:

|Keyword|Scope|Reassignment|Redeclaration in same scope|
|---|---|---|---|
|`var`|Function or global|Yes|Yes|
|`let`|Block|Yes|No|
|`const`|Block|No reassignment|No|

Example:

```
let username = "Mohit";
const country = "India";

username = "Rahul";

console.log(username);
console.log(country);
```

Recommended practice:

- Prefer `const` when a variable will not be reassigned.
    
- Use `let` when reassignment is required.
    
- Avoid `var` in modern JavaScript unless there is a specific reason to use it.
    

**Important:** A `const` object or array can still have its internal properties or elements modified. `const` prevents reassignment of the variable binding, not mutation of the object.

## 9. JavaScript Data Types

JavaScript has primitive and non-primitive data types.

### A. Primitive Data Types

|Data Type|Description|Example|
|---|---|---|
|String|Text|`"Hello"`|
|Number|Integers and floating-point numbers|`25`, `10.5`|
|BigInt|Large integers|`123456789n`|
|Boolean|True or false|`true`|
|Undefined|Declared but not assigned a value|`undefined`|
|Null|Intentional absence of a value|`null`|
|Symbol|Unique identifiers|`Symbol("id")`|

JavaScript's `Number` type uses IEEE 754 double-precision floating-point representation.

This means some decimal calculations may produce unexpected precision results.

Example:

```
console.log(0.1 + 0.2);
```

Possible output:

```
0.30000000000000004
```

### B. Non-Primitive Data Types

Objects are used to store collections and more complex structures.

Examples:

```
let student = {
    name: "Mohit",
    age: 18
};

let languages = ["Python", "JavaScript", "C"];
```

Arrays and functions are also objects in JavaScript.

## 10. Checking Data Types

The `typeof` operator returns a string describing the type of a value.

Example:

```
console.log(typeof "Hello");
console.log(typeof 25);
console.log(typeof true);
console.log(typeof undefined);
```

Output:

```
string
number
boolean
undefined
```

One important JavaScript behaviour:

```
console.log(typeof null);
```

Output:

```
object
```

This is a historical JavaScript quirk. It does not mean that `null` is actually an object.

## 11. Operators

Operators perform operations on values.

Common categories:

|Operator Type|Examples|
|---|---|
|Arithmetic|`+`, `-`, `*`, `/`, `%`|
|Assignment|`=`, `+=`, `-=`|
|Comparison|`>`, `<`, `>=`, `<=`|
|Equality|`==`, `===`, `!=`, `!==`|
|Logical|`&&`, `||`,` !`|

Example:

```
let a = 10;
let b = 5;

console.log(a + b);
console.log(a > b);
console.log(a === b);
```

### Strict vs Loose Equality

```
console.log(5 == "5");
console.log(5 === "5");
```

Output:

```
true
false
```

- `==` compares values after possible type conversion.
    
- `===` compares values without performing that type conversion.
    

Prefer strict equality (`===`) in most application code.

## 12. Type Conversion and Type Coercion

JavaScript can convert values from one type to another.

### Explicit Type Conversion

The programmer performs the conversion.

```
let number = Number("100");

console.log(number);
console.log(typeof number);
```

Output:

```
100
number
```

### Implicit Type Coercion

JavaScript automatically converts values in certain operations.

```
let result = "10" + 5;

console.log(result);
```

Output:

```
105
```

The number `5` is converted to a string during concatenation.

Unexpected type coercion can introduce programming errors and security problems.

## 13. Input and Output

JavaScript provides different ways to receive input and display output.

### Console Output

```
console.log("Hello");
console.error("An error occurred");
console.warn("Warning message");
```

### Browser Alert

```
alert("Welcome!");
```

### Browser Input

```
let username = prompt("Enter your name:");

console.log(username);
```

`alert()` and `prompt()` are simple browser features useful for demonstrations, but they are generally not suitable for production application interfaces.

## 14. Basic Control Flow

Control flow determines the order in which statements execute.

### Conditional Statement

```
let age = 18;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

### Loop

```
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Detailed topics are covered in:

- [[Conditional Statements]]
    
- [[Loops]]
    
- [[Break and Continue]]
    
- [[Nested Loops]]
    

## 15. Introduction to Functions

A function is a reusable block of code designed to perform a task.

Example:

```
function greet() {
    console.log("Hello, Student!");
}

greet();
```

Functions help organize code and reduce repetition.

JavaScript also supports arrow functions:

```
const greet = () => {
    console.log("Hello!");
};

greet();
```

Detailed concepts are covered in [[JavaScript Functions]].

## 16. Introduction to Arrays and Objects

### Array

An array stores multiple values in an ordered collection.

```
let tools = ["Nmap", "Wireshark", "Burp Suite"];

console.log(tools[0]);
```

Output:

```
Nmap
```

### Object

An object stores information using key-value pairs.

```
let student = {
    name: "Mohit",
    course: "Cybersecurity"
};

console.log(student.name);
```

Output:

```
Mohit
```

Detailed concepts are covered in [[JavaScript Arrays and Objects]].

## 17. Errors and Debugging

An error is a problem that prevents code from behaving as intended.

Common JavaScript error categories:

|Error|Meaning|
|---|---|
|SyntaxError|Code does not follow valid syntax|
|ReferenceError|Accessing an unavailable variable or reference|
|TypeError|An operation is performed on an incompatible value|
|RangeError|A value is outside an allowed range|

Example:

```
console.log(username);
```

If `username` has not been declared in the accessible scope, JavaScript may produce a `ReferenceError`.

### Debugging Tools

- `console.log()` for inspecting values.
    
- Browser Developer Tools.
    
- JavaScript debugger and breakpoints.
    
- Node.js debugging tools.
    

## 18. JavaScript and Cybersecurity

JavaScript is important in cybersecurity because it runs in browsers and is commonly used in web applications.

Security topics related to JavaScript include:

### A. Cross-Site Scripting (XSS)

XSS occurs when an attacker causes malicious script content to execute in another user's browser.

### B. Client-Side Validation Bypass

Validation performed only in the browser can be modified or bypassed by users.

Important validation must also be performed on the server.

### C. DOM-Based Vulnerabilities

Unsafe handling of webpage content can introduce DOM-based XSS vulnerabilities.

### D. Insecure Use of eval()

The `eval()` function executes JavaScript code represented as a string.

Executing untrusted input through `eval()` can lead to code execution vulnerabilities.

Avoid using it when safer alternatives exist.

### E. Sensitive Data Exposure

Never treat frontend JavaScript as a secure place to store:

- API secrets.
    
- Private keys.
    
- Database credentials.
    
- Authentication secrets.
    

Client-side code can be inspected by users.

### Security Best Practices

1. Treat user input as untrusted.
    
2. Avoid unsafe DOM operations.
    
3. Avoid executing untrusted strings as code.
    
4. Use secure authentication and session management.
    
5. Validate input on the server.
    
6. Keep dependencies updated.
    
7. Never expose server-side secrets in frontend code.
    

Related topics:

- [[Introduction to Secure Coding]]
    
- [[Cross-Site Scripting Prevention]]
    
- [[Input Validation]]
    
- [[Authentication and Authorization]]
    

## 19. Practical Lab — Your First JavaScript Program

### Objective

Create a basic HTML webpage connected to an external JavaScript file.

### Step 1: Create a project directory

Create a directory named:

```
JavaScript-Basics
```

Inside it, create:

```
JavaScript-Basics/
├── index.html
└── script.js
```

### Step 2: Write the HTML file

**index.html**

```
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Basics</title>
    <script src="script.js" defer></script>
</head>
<body>

    <h1>My First JavaScript Program</h1>
    <p>Open the browser console to see the output.</p>

</body>
</html>
```

### Step 3: Write the JavaScript file

**script.js**

```
const studentName = "Mohit";
let age = 18;

console.log("Welcome to JavaScript!");
console.log("Student:", studentName);
console.log("Age:", age);

let number1 = 20;
let number2 = 10;

console.log("Addition:", number1 + number2);
console.log("Subtraction:", number1 - number2);
console.log("Multiplication:", number1 * number2);
console.log("Division:", number1 / number2);
```

### Step 4: Run the program

1. Open `index.html` in a browser.
    
2. Open Developer Tools using `F12`.
    
3. Select the **Console** tab.
    
4. Observe the output.
    

### Step 5: Experiment

Modify the program:

- Change the student name.
    
- Change the age.
    
- Add two more numbers.
    
- Display their multiplication.
    
- Check the data type of each variable using `typeof`.
    

### Expected Learning

After completing this lab, you should be able to:

- Explain what JavaScript is.
    
- Identify where JavaScript executes.
    
- Connect JavaScript with HTML.
    
- Declare basic variables.
    
- Identify common data types.
    
- Use console output.
    
- Perform basic operations.
    

## 20. Key Takeaways

- JavaScript adds functionality and interactivity to applications.
    
- It runs in browsers and environments such as Node.js.
    
- ECMAScript defines the language specification.
    
- JavaScript supports primitive and object data types.
    
- `let`, `const`, and `var` have different scoping and reassignment rules.
    
- JavaScript supports functions, arrays, objects, and asynchronous operations.
    
- Browser JavaScript is an important part of web application security.
    
- Client-side validation cannot replace server-side validation.
    

## Related Notes

- [[Programming Languages]]
    
- [[Introduction to HTML]]
    
- [[Introduction to CSS]]
    
- [[JavaScript Variables and Data Types]]
    
- [[JavaScript Operators]]
    
- [[JavaScript Control Flow]]
    
- [[JavaScript Functions]]
    
- [[Introduction to Secure Coding]]
    
- [[Cross-Site Scripting Prevention]]
    

---

## My Understanding

Write in your own words:

1. What is JavaScript?
    
2. What is the difference between JavaScript and Java?
    
3. What is ECMAScript?
    
4. Where can JavaScript execute?
    
5. What is the difference between `let`, `const`, and `var`?
    
6. What are primitive and non-primitive data types?
    
7. Why is JavaScript important in web security?
    

## Questions & Doubts

Record concepts that need further explanation or practical testing.