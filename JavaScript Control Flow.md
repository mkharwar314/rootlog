> Understand how JavaScript controls the order of program execution using conditions, loops, branching, and iteration.

## 1. What Is Control Flow?

Control flow determines the order in which statements are executed in a program.

By default, JavaScript executes statements from top to bottom.

However, control-flow statements allow a program to:

- Make decisions.
    
- Execute code conditionally.
    
- Repeat instructions.
    
- Skip specific iterations.
    
- Stop loops.
    
- Handle multiple possible conditions.
    

### Example

```
let age = 20;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

Output:

```
Adult
```

The program checks the condition and executes the appropriate block.

## 2. Types of Control Flow

JavaScript control flow can be divided into three major categories.

|Type|Purpose|
|---|---|
|Sequential|Executes statements in order|
|Selection|Chooses between different execution paths|
|Iteration|Repeats a block of code|

### Sequential Control Flow

Statements execute one after another.

```
console.log("Step 1");
console.log("Step 2");
console.log("Step 3");
```

### Selection Control Flow

The program chooses which code to execute based on a condition.

Examples:

- `if`
    
- `if...else`
    
- `else if`
    
- `switch`
    
- Ternary operator
    

### Iteration Control Flow

The program repeats instructions.

Examples:

- `for`
    
- `while`
    
- `do...while`
    
- `for...of`
    
- `for...in`
    

## 3. Conditional Statements

Conditional statements execute code depending on whether a condition evaluates to truthy or falsy.

### A. if Statement

Executes a block when the condition is truthy.

```
let age = 20;

if (age >= 18) {
    console.log("You are an adult");
}
```

Output:

```
You are an adult
```

### B. if...else Statement

Executes one block when the condition is truthy and another when it is falsy.

```
let age = 16;

if (age >= 18) {
    console.log("Eligible");
} else {
    console.log("Not eligible");
}
```

Output:

```
Not eligible
```

### C. else if Statement

Checks multiple conditions in sequence.

```
let marks = 75;

if (marks >= 90) {
    console.log("Grade A");
} else if (marks >= 75) {
    console.log("Grade B");
} else if (marks >= 50) {
    console.log("Grade C");
} else {
    console.log("Fail");
}
```

Output:

```
Grade B
```

JavaScript evaluates the conditions from top to bottom. Once a matching branch is found, the remaining branches are skipped.

### D. Nested if Statements

An `if` statement can be placed inside another conditional block.

```
let age = 20;
let hasID = true;

if (age >= 18) {
    if (hasID) {
        console.log("Entry permitted");
    } else {
        console.log("ID required");
    }
} else {
    console.log("Entry denied");
}
```

Nested conditions are useful when decisions depend on multiple stages.

## 4. switch Statement

The `switch` statement selects a block based on the value of an expression.

Example:

```
let day = 3;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    default:
        console.log("Invalid day");
}
```

Output:

```
Wednesday
```

### Important Components

|Component|Purpose|
|---|---|
|`switch`|Starts the selection statement|
|`case`|Defines a possible matching value|
|`break`|Exits the switch block|
|`default`|Executes when no case matches|

### Why Is break Important?

Without `break`, execution can continue into subsequent cases. This behaviour is called fall-through.

Example:

```
let value = 1;

switch (value) {
    case 1:
        console.log("One");

    case 2:
        console.log("Two");
}
```

Output:

```
One
Two
```

Use `break` when fall-through is not intentional.

## 5. Ternary Operator

The ternary operator is a compact alternative to a simple `if...else` statement.

Syntax:

```
condition ? valueIfTrue : valueIfFalse;
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

Use it for simple decisions. Avoid deeply nested ternary expressions because they can make code difficult to read.

## 6. Loops in JavaScript

Loops repeat a block of code while a particular iteration condition is satisfied.

JavaScript provides several loop types.

|Loop|Description|
|---|---|
|`for`|Repeats code using initialization, condition, and update|
|`while`|Repeats while a condition is truthy|
|`do...while`|Executes at least once before checking the condition|
|`for...of`|Iterates over iterable values|
|`for...in`|Iterates over enumerable property keys|

### A. for Loop

A `for` loop is useful when the number of iterations is known or controlled by a counter.

Syntax:

```
for (initialization; condition; update) {
    // Code
}
```

Example:

```
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Output:

```
1
2
3
4
5
```

Execution stages:

1. Initialization runs once.
    
2. Condition is checked.
    
3. If truthy, the loop body executes.
    
4. Update runs.
    
5. The condition is checked again.
    

### B. while Loop

A `while` loop repeats as long as its condition remains truthy.

Example:

```
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```

Output:

```
1
2
3
4
5
```

If the condition is initially falsy, the loop body does not execute.

### C. do...while Loop

A `do...while` loop executes its body before checking the condition.

Example:

```
let i = 1;

do {
    console.log(i);
    i++;
} while (i <= 5);
```

Output:

```
1
2
3
4
5
```

Even if the condition is initially falsy, the body executes once.

### D. for...of Loop

The `for...of` loop iterates over values from an iterable, such as an array or string.

Example:

```
let tools = ["Nmap", "Wireshark", "Burp Suite"];

for (let tool of tools) {
    console.log(tool);
}
```

Output:

```
Nmap
Wireshark
Burp Suite
```

### E. for...in Loop

The `for...in` loop iterates over enumerable property keys of an object.

Example:

```
let student = {
    name: "Mohit",
    age: 18,
    course: "Cybersecurity"
};

for (let key in student) {
    console.log(key, student[key]);
}
```

Output:

```
name Mohit
age 18
course Cybersecurity
```

**Important distinction:**

- Use `for...of` when you need values from an iterable.
    
- Use `for...in` when you need enumerable property keys.
    
- Avoid using `for...in` as the normal way to iterate through arrays.
    

## 7. break Statement

The `break` statement immediately terminates the nearest enclosing loop or `switch` statement.

Example:

```
for (let i = 1; i <= 10; i++) {
    if (i === 5) {
        break;
    }

    console.log(i);
}
```

Output:

```
1
2
3
4
```

When `i` becomes 5, the loop terminates.

## 8. continue Statement

The `continue` statement skips the remaining statements in the current loop iteration and proceeds to the next iteration.

Example:

```
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

Output:

```
1
2
4
5
```

The value 3 is skipped.

### break vs continue

|Feature|break|continue|
|---|---|---|
|Purpose|Terminates the loop|Skips the current iteration|
|Further iterations|Stop|Continue|
|Common use|Stop when a target is found|Skip unwanted values|

Related note: [[Break and Continue]].

## 9. Nested Loops

A nested loop is a loop placed inside another loop.

Example:

```
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 2; j++) {
        console.log(i, j);
    }
}
```

Output:

```
1 1
1 2
2 1
2 2
3 1
3 2
```

The inner loop completes its iterations for every iteration of the outer loop.

Nested loops are useful for:

- Working with matrices.
    
- Processing tables.
    
- Generating patterns.
    
- Comparing elements.
    

However, nested loops can increase execution time, especially when processing large datasets.

Related note: [[Nested Loops]].

## 10. Loop Control and Infinite Loops

An infinite loop continues executing because its termination condition is never reached.

Example:

```
while (true) {
    console.log("Running...");
}
```

This loop has no natural stopping condition.

Infinite loops may be intentional in certain applications, but accidental infinite loops can cause:

- High CPU usage.
    
- Unresponsive applications.
    
- Browser tab freezing.
    
- Service disruption.
    

### Safe Loop Design

1. Define a clear termination condition.
    
2. Update the loop variable correctly.
    
3. Avoid unnecessary nested loops.
    
4. Test loops with small inputs first.
    
5. Use a maximum iteration limit where appropriate.
    

Example:

```
let count = 0;

while (count < 5) {
    console.log(count);
    count++;
}
```

## 11. Control Flow and Asynchronous JavaScript

JavaScript also supports asynchronous operations.

For example, a network request may take time to complete. JavaScript can continue handling other work while waiting for the result.

Example:

```
console.log("Start");

setTimeout(() => {
    console.log("Delayed message");
}, 1000);

console.log("End");
```

Typical output:

```
Start
End
Delayed message
```

The callback passed to `setTimeout()` runs after the specified delay has elapsed and the event loop can process it.

This is a basic example of asynchronous execution.

Detailed concepts are covered in [[JavaScript Asynchronous Programming]].

## 12. JavaScript Control Flow in Cybersecurity

Control flow is important when implementing security-sensitive logic.

### A. Authentication Checks

Example:

```
let isAuthenticated = true;

if (isAuthenticated) {
    console.log("User authenticated");
} else {
    console.log("Authentication required");
}
```

This demonstrates conditional logic only. Real authentication must be implemented and verified securely on the server.

### B. Authorization Checks

Example:

```
let role = "admin";

if (role === "admin") {
    console.log("Admin feature available");
} else {
    console.log("Access denied");
}
```

In a real application, users must not be allowed to grant themselves privileged roles through client-side code.

The server must independently verify permissions for protected operations.

### C. Input Validation

```
let age = 20;

if (Number.isFinite(age) && age >= 18) {
    console.log("Input accepted");
} else {
    console.log("Invalid input");
}
```

This is a basic validation example. Applications must also validate security-sensitive input on the server.

### D. Denial of Service Risks

Poorly controlled loops can consume excessive resources.

Developers should avoid unbounded processing and implement suitable resource limits.

## 13. Practical Lab — JavaScript Control Flow

### Objective

Create a program that uses conditions, loops, and control-flow statements.

### Step 1: Create a file

```
control-flow.js
```

### Step 2: Write the program

```
// Conditional statement
let marks = 82;

if (marks >= 90) {
    console.log("Grade A");
} else if (marks >= 75) {
    console.log("Grade B");
} else if (marks >= 50) {
    console.log("Grade C");
} else {
    console.log("Fail");
}

// For loop
console.log("Counting:");

for (let i = 1; i <= 5; i++) {
    console.log(i);
}

// Continue example
console.log("Odd numbers:");

for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        continue;
    }

    console.log(i);
}

// Break example
console.log("Stop at 4:");

for (let i = 1; i <= 10; i++) {
    if (i === 4) {
        break;
    }

    console.log(i);
}

// Switch example
let role = "student";

switch (role) {
    case "admin":
        console.log("Administrator");
        break;

    case "student":
        console.log("Student");
        break;

    default:
        console.log("Unknown role");
}
```

### Step 3: Run the program

Using Node.js:

```
node control-flow.js
```

### Step 4: Experiment

1. Change the marks and observe the grade.
    
2. Change the loop limit from 5 to 10.
    
3. Modify the `continue` condition to skip odd numbers.
    
4. Change the `break` condition to stop at 7.
    
5. Change the role to `admin`.
    
6. Write a `while` loop that prints numbers from 1 to 10.
    

### Expected Learning

After completing this lab, you should understand:

- Sequential execution.
    
- Conditional statements.
    
- `switch` statements.
    
- Different types of loops.
    
- `break` and `continue`.
    
- Nested loops.
    
- Basic asynchronous execution.
    
- Security implications of incorrect control flow.
    

## 14. Key Takeaways

- Control flow determines the execution order of a program.
    
- Conditional statements allow decision-making.
    
- `switch` handles multiple possible cases.
    
- Loops repeat instructions.
    
- `for...of` iterates over iterable values.
    
- `for...in` iterates over enumerable property keys.
    
- `break` terminates a loop.
    
- `continue` skips the current iteration.
    
- Infinite loops can cause resource exhaustion.
    
- Security-sensitive decisions must be enforced on the server.
    

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Variables and Data Types]]
    
- [[JavaScript Operators]]
    
- [[Conditional Statements]]
    
- [[Loops]]
    
- [[Break and Continue]]
    
- [[Nested Loops]]
    
- [[JavaScript Functions]]
    
- [[JavaScript Asynchronous Programming]]
    
- [[Input Validation]]
    
- [[Authentication and Authorization]]
    

---

## My Understanding

Answer in your own words:

1. What is control flow?
    
2. What are the three major categories of control flow?
    
3. What is the difference between `if...else` and `switch`?
    
4. What is the difference between `for` and `while`?
    
5. What is the difference between `for...of` and `for...in`?
    
6. What is the difference between `break` and `continue`?
    
7. What is a nested loop?
    
8. What causes an infinite loop?
    
9. How can poorly designed loops affect system performance?
    
10. Why should authorization checks be enforced on the server?
    

## Questions & Doubts

Record concepts that need further explanation or practical testing.