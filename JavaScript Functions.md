> Understand how functions organize code into reusable blocks, accept input, return results, and support modular application development.

## 1. What Are Functions?

A function is a reusable block of code designed to perform a specific task.

Instead of writing the same code repeatedly, we can define a function once and call it whenever required.

Example:

```
function greet() {
    console.log("Hello, Student!");
}

greet();
```

Output:

```
Hello, Student!
```

Here:

- `function` is the declaration keyword.
    
- `greet` is the function name.
    
- `{}` contains the function body.
    
- `greet()` calls the function.
    

## 2. Why Are Functions Important?

Functions provide several advantages:

1. **Code Reusability:** Write code once and use it multiple times.
    
2. **Modularity:** Divide a large program into smaller parts.
    
3. **Readability:** Make programs easier to understand.
    
4. **Maintainability:** Update one function instead of changing repeated code.
    
5. **Testing:** Individual functions can be tested independently.
    
6. **Abstraction:** Hide implementation details behind a function interface.
    

## 3. Function Declaration

A function declaration defines a named function.

Syntax:

```
function functionName() {
    // Statements
}
```

Example:

```
function showMessage() {
    console.log("Learning JavaScript");
}

showMessage();
```

Output:

```
Learning JavaScript
```

A function declaration is generally hoisted, meaning it can be called before its declaration in the same scope.

Example:

```
greet();

function greet() {
    console.log("Hello!");
}
```

Output:

```
Hello!
```

## 4. Function Parameters and Arguments

Parameters are variables listed in a function definition.

Arguments are the actual values passed when calling the function.

Example:

```
function greet(name) {
    console.log("Hello " + name);
}

greet("Mohit");
```

Output:

```
Hello Mohit
```

Here:

- `name` is a parameter.
    
- `"Mohit"` is an argument.
    

A function can accept multiple parameters.

```
function add(a, b) {
    console.log(a + b);
}

add(10, 20);
```

Output:

```
30
```

## 5. Return Statement

The `return` statement sends a value back from a function.

Example:

```
function add(a, b) {
    return a + b;
}

let result = add(10, 20);

console.log(result);
```

Output:

```
30
```

The returned value can be:

- Stored in a variable.
    
- Passed to another function.
    
- Used in an expression.
    
- Displayed or processed.
    

### Return vs console.log()

|`return`|`console.log()`|
|---|---|
|Sends a value back to the caller|Displays information in the console|
|Can be used by other code|Does not automatically provide a reusable result|
|Ends the current function execution|Does not normally end function execution|

Example:

```
function calculate() {
    console.log("Calculating");
    return 100;
}

let result = calculate();

console.log(result);
```

Output:

```
Calculating
100
```

## 6. Function Expressions

A function expression stores a function in a variable.

Example:

```
const greet = function() {
    console.log("Hello!");
};

greet();
```

Unlike function declarations, function expressions assigned to `const` or `let` cannot be called before the variable initialization is evaluated.

Example:

```
const greet = function() {
    console.log("Hello!");
};
```

The function is available after this assignment executes.

## 7. Arrow Functions

Arrow functions provide a shorter syntax for writing functions.

Example:

```
const greet = () => {
    console.log("Hello!");
};

greet();
```

### Arrow Function with Parameters

```
const add = (a, b) => {
    return a + b;
};

console.log(add(10, 20));
```

Output:

```
30
```

### Short Arrow Function

When the function body contains only a single expression, braces and `return` can be omitted.

```
const multiply = (a, b) => a * b;

console.log(multiply(5, 4));
```

Output:

```
20
```

### Single Parameter

Parentheses around a single parameter can be omitted.

```
const square = number => number * number;

console.log(square(5));
```

Output:

```
25
```

**Important:** Arrow functions do not have their own `this` binding. They inherit `this` from their surrounding lexical context. They also cannot be used as constructors with `new`.

## 8. Default Parameters

Default parameters provide fallback values when an argument is omitted or explicitly passed as `undefined`.

Example:

```
function greet(name = "Guest") {
    console.log("Hello " + name);
}

greet();
greet("Mohit");
```

Output:

```
Hello Guest
Hello Mohit
```

Passing `null` does not trigger the default value.

```
greet(null);
```

This prints `Hello null`.

## 9. Rest Parameters

Rest parameters allow a function to accept multiple arguments as an array.

Example:

```
function addAll(...numbers) {
    let total = 0;

    for (let number of numbers) {
        total += number;
    }

    return total;
}

console.log(addAll(10, 20, 30));
```

Output:

```
60
```

The rest parameter must be the last parameter in the function definition.

## 10. Scope Inside Functions

Scope determines where variables can be accessed.

Example:

```
function test() {
    let message = "Hello";
    console.log(message);
}

test();
```

The variable `message` is local to the function.

Trying to access it outside the function causes a `ReferenceError`.

### Global Variables

```
let username = "Mohit";

function showUser() {
    console.log(username);
}

showUser();
```

The function can access `username` because it is declared in an outer scope.

**Best practice:** Avoid unnecessary global variables because they can create naming conflicts and make programs harder to maintain.

## 11. Anonymous Functions

An anonymous function is a function without its own name.

Example:

```
const greet = function() {
    console.log("Hello!");
};

greet();
```

Anonymous functions are commonly used as:

- Function expressions.
    
- Callback functions.
    
- Event handlers.
    

## 12. Callback Functions

A callback is a function passed to another function as an argument so that it can be called later.

Example:

```
function processUser(name, callback) {
    console.log("Processing " + name);

    callback();
}

function completed() {
    console.log("Processing completed");
}

processUser("Mohit", completed);
```

Output:

```
Processing Mohit
Processing completed
```

Callbacks are commonly used in:

- Event handling.
    
- Timers.
    
- Asynchronous operations.
    
- Array methods.
    

## 13. Higher-Order Functions

A higher-order function is a function that accepts another function as an argument, returns a function, or does both.

Example:

```
function calculate(a, b, operation) {
    return operation(a, b);
}

function add(x, y) {
    return x + y;
}

console.log(calculate(10, 20, add));
```

Output:

```
30
```

JavaScript functions are first-class values. They can be assigned to variables, passed as arguments, and returned from other functions.

## 14. Immediately Invoked Function Expression (IIFE)

An IIFE is a function expression that executes immediately after it is created.

Example:

```
(function() {
    console.log("Executed immediately");
})();
```

Output:

```
Executed immediately
```

IIFEs were historically used to create private scopes and avoid polluting the global namespace.

Modern JavaScript also provides block scope and modules for organizing code.

## 15. Recursive Functions

A recursive function calls itself to solve a problem.

Example:

```
function countdown(number) {
    if (number <= 0) {
        return;
    }

    console.log(number);

    countdown(number - 1);
}

countdown(5);
```

Output:

```
5
4
3
2
1
```

A recursive function needs a base case to stop recursion.

Without a suitable stopping condition, recursion may continue until the runtime encounters a stack limit.

Related note: [[Recursion]].

## 16. Built-in Functions

JavaScript provides built-in functions and methods for common tasks.

Examples:

```
console.log(Number("100"));
console.log(String(500));
console.log(Boolean(1));
console.log(parseInt("25", 10));
console.log(Math.max(10, 20, 30));
```

Output:

```
100
500
true
25
30
```

Some commonly used built-in objects include:

- `Math`
    
- `JSON`
    
- `Date`
    
- `Number`
    
- `String`
    
- `Array`
    
- `Object`
    

## 17. Function Hoisting

Function declarations are hoisted, which means they can generally be called before their declaration.

Example:

```
greet();

function greet() {
    console.log("Hello!");
}
```

Output:

```
Hello!
```

However, function expressions assigned to variables behave differently.

```
greet();

const greet = function() {
    console.log("Hello!");
};
```

This causes a `ReferenceError` because the `const` variable cannot be accessed before initialization.

**Important:** Hoisting does not mean all declarations can be safely used before their source-code position.

## 18. JavaScript Functions in Cybersecurity

Functions are important in security-sensitive application development.

### A. Input Validation

Functions can centralize input validation.

```
function isValidAge(age) {
    return Number.isInteger(age) && age >= 18;
}

console.log(isValidAge(20));
console.log(isValidAge(15));
```

Output:

```
true
false
```

This is a basic example. Real applications must validate security-sensitive input on the server as well.

### B. Authentication Logic

Functions can organize authentication-related operations.

```
function checkLoginStatus(isAuthenticated) {
    if (isAuthenticated === true) {
        return "Authenticated";
    }

    return "Authentication required";
}

console.log(checkLoginStatus(true));
```

This only demonstrates program structure. It does not implement secure authentication.

### C. Code Reuse and Security

Reusable security functions help reduce inconsistent implementations.

For example, a shared validation function can be used wherever the same input rules are required.

However, client-side security functions cannot enforce access control against users who can modify browser code.

### D. Avoid Unsafe Code Execution

Avoid using `eval()` to execute untrusted input.

```
// Avoid this pattern:
eval(userInput);
```

Executing untrusted strings as JavaScript can create serious code-execution vulnerabilities.

## 19. Practical Lab — JavaScript Functions

### Objective

Create reusable functions for calculations, validation, and displaying messages.

### Step 1: Create a file

```
functions.js
```

### Step 2: Write the program

```
// Greeting function
function greet(name) {
    return `Hello, ${name}!`;
}

console.log(greet("Mohit"));

// Addition function
function add(a, b) {
    return a + b;
}

console.log("Addition:", add(10, 20));

// Multiplication using an arrow function
const multiply = (a, b) => a * b;

console.log("Multiplication:", multiply(5, 4));

// Default parameter
function welcome(name = "Guest") {
    console.log(`Welcome, ${name}`);
}

welcome();
welcome("Mohit");

// Validation function
function isValidAge(age) {
    return Number.isInteger(age) && age >= 18;
}

console.log("Age 20:", isValidAge(20));
console.log("Age 15:", isValidAge(15));

// Callback function
function processTask(callback) {
    console.log("Task started");
    callback();
}

processTask(() => {
    console.log("Task completed");
});
```

### Step 3: Run the program

Using Node.js:

```
node functions.js
```

### Step 4: Experiment

1. Create a function that subtracts two numbers.
    
2. Create a function that calculates the square of a number.
    
3. Create an arrow function that calculates the average of three numbers.
    
4. Create a function that checks whether a number is even.
    
5. Modify the greeting function to use a default parameter.
    
6. Create a callback that prints a completion message.
    

### Expected Learning

After completing this lab, you should understand:

- Function declarations.
    
- Function expressions.
    
- Parameters and arguments.
    
- Return values.
    
- Arrow functions.
    
- Default and rest parameters.
    
- Scope.
    
- Callbacks.
    
- Higher-order functions.
    
- Basic function security considerations.
    

## 20. Key Takeaways

- Functions are reusable blocks of code.
    
- Parameters receive input and arguments provide actual values.
    
- `return` sends a result back to the caller.
    
- Function expressions store functions in variables.
    
- Arrow functions provide concise syntax.
    
- Callbacks allow functions to be passed into other functions.
    
- Higher-order functions work with other functions.
    
- Recursive functions call themselves.
    
- Function declarations and function expressions have different hoisting behaviour.
    
- Well-designed functions improve code organization and maintainability.
    

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Variables and Data Types]]
    
- [[JavaScript Operators]]
    
- [[JavaScript Control Flow]]
    
- [[JavaScript Arrays and Objects]]
    
- [[JavaScript Asynchronous Programming]]
    
- [[Recursion]]
    
- [[Modules and Libraries]]
    
- [[Input Validation]]
    
- [[Introduction to Secure Coding]]
    

---

## My Understanding

Answer in your own words:

1. What is a function?
    
2. Why are functions important?
    
3. What is the difference between parameters and arguments?
    
4. What is the difference between `return` and `console.log()`?
    
5. What is a function expression?
    
6. What is an arrow function?
    
7. What is a callback function?
    
8. What is a higher-order function?
    
9. What is an IIFE?
    
10. What is function hoisting?
    
11. Why should untrusted input never be passed to `eval()`?
    

## Questions & Doubts

Record concepts that need further explanation or practical testing.