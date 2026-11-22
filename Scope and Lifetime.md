 > Understand where variables can be accessed in a program and how long they remain available in memory.

## 1. What Is Variable Scope?

**Scope** defines the region of a program where a variable can be accessed.

A variable may be accessible:

- Throughout a program.
    
- Only inside a function.
    
- Only inside a particular block or module, depending on the language.
    

Understanding scope helps prevent naming conflicts and unexpected changes to variables.

## 2. What Is Variable Lifetime?

**Lifetime** refers to how long a variable or object exists during program execution.

Scope and lifetime are related, but they are not the same.

|Scope|Lifetime|
|---|---|
|Where a variable can be accessed|How long a variable or object exists|
|Concerned with visibility|Concerned with existence|
|Depends on language rules|Depends on storage and object-management rules|

A variable can have limited visibility while the object it references remains alive elsewhere.

## 3. Types of Scope

### A. Local Scope

A variable created inside a function is generally local to that function.

Example:

```
def show_message():
    message = "Hello ROOTLOG"
    print(message)

show_message()
```

Output:

```
Hello ROOTLOG
```

The variable `message` is local to `show_message()`.

Trying to access it outside the function normally causes a `NameError`:

```
def show_message():
    message = "Hello"

show_message()

print(message)
```

The variable is not accessible from the global scope.

### B. Global Scope

A variable defined at the module level is called a global variable.

Example:

```
project = "ROOTLOG"

def show_project():
    print(project)

show_project()
print(project)
```

Output:

```
ROOTLOG
ROOTLOG
```

The function can read the global variable.

### C. Enclosing Scope

Python supports nested functions.

A variable defined in an outer function can be accessed by an inner function.

Example:

```
def outer():
    message = "Outer function"

    def inner():
        print(message)

    inner()

outer()
```

Output:

```
Outer function
```

The variable `message` belongs to the enclosing function.

### D. Built-in Scope

Python provides built-in names that are available without defining them yourself.

Examples:

```
print("Hello")
length = len("Cybersecurity")
maximum = max(10, 20, 30)
```

Here:

- `print()` is a built-in function.
    
- `len()` is a built-in function.
    
- `max()` is a built-in function.
    

## 4. Python LEGB Rule

Python searches for variable names using the **LEGB rule**.

LEGB stands for:

1. **Local:** Inside the current function.
    
2. **Enclosing:** Inside the surrounding function.
    
3. **Global:** At the module level.
    
4. **Built-in:** Names provided by Python.
    

Example:

```
name = "Global"

def outer():
    name = "Enclosing"

    def inner():
        name = "Local"
        print(name)

    inner()

outer()
```

Output:

```
Local
```

Python finds the name in the local scope first.

## 5. The Global Keyword in Python

The `global` keyword allows a function to reassign a variable defined at module level.

Example:

```
count = 0

def update_count():
    global count
    count = count + 1

update_count()

print(count)
```

Output:

```
1
```

Without `global`, assigning to `count` inside the function would make it a local variable.

**Best practice:** Avoid unnecessary global-variable modification. Passing values through function parameters and return values often makes programs easier to test and maintain.

## 6. The Nonlocal Keyword in Python

The `nonlocal` keyword allows an inner function to reassign a variable belonging to its nearest enclosing function scope.

Example:

```
def outer():
    count = 0

    def inner():
        nonlocal count
        count += 1

    inner()
    print(count)

outer()
```

Output:

```
1
```

`nonlocal` does not refer to a module-level global variable.

## 7. Variable Scope in C

C uses block scope for variables declared inside blocks.

Example:

```
#include <stdio.h>

int main() {
    int number = 10;

    if (number > 5) {
        int value = 20;
        printf("%d\n", value);
    }

    printf("%d\n", number);

    return 0;
}
```

Output:

```
20
10
```

The variable `value` is accessible inside its block but not outside it.

Trying to access `value` after the `if` block would cause a compilation error.

### Global Variables in C

A variable declared outside all functions has file scope.

```
#include <stdio.h>

int count = 10;

void display() {
    printf("%d\n", count);
}

int main() {
    display();
    return 0;
}
```

Output:

```
10
```

C also has storage-duration concepts such as automatic, static, and allocated storage duration. These affect how long objects exist.

## 8. Variable Scope in JavaScript

JavaScript supports three commonly used declaration keywords.

|Keyword|Scope|Reassignment|
|---|---|---|
|`var`|Function or global scope|Allowed|
|`let`|Block scope|Allowed|
|`const`|Block scope|Not allowed for reassignment|

Example:

```
function testScope() {
    var first = 10;
    let second = 20;
    const third = 30;

    console.log(first, second, third);
}

testScope();
```

Output:

```
10 20 30
```

### Block Scope

```
if (true) {
    let number = 100;
    const value = 200;
}

console.log(number);
```

This causes a `ReferenceError` because `number` is only available inside the block.

**Important:** `const` prevents reassignment of the variable binding. It does not make an object or array deeply immutable.

## 9. Understanding Variable Lifetime

Lifetime describes how long a variable or object remains available.

### Local Variables

In Python, local names are generally available during the execution of their function.

```
def calculate():
    result = 100
    print(result)

calculate()
```

The local name `result` is not accessible outside the function.

However, the object it referenced may continue to exist if another reference to it is retained.

### Global Variables

A module-level variable generally remains available while its module is loaded.

```
project = "ROOTLOG"

def display():
    print(project)

display()
```

### Static Variables in C

A local static variable retains its stored value between function calls.

```
#include <stdio.h>

void counter() {
    static int count = 0;
    count++;

    printf("%d\n", count);
}

int main() {
    counter();
    counter();
    counter();

    return 0;
}
```

Output:

```
1
2
3
```

Unlike an ordinary automatic local variable, `count` is not recreated with an initial value on every function call.

## 10. Scope and Lifetime in Cybersecurity

Understanding scope and lifetime is important when writing security tools.

### Example 1: Avoiding Global Password Storage

Poor design:

```
password = "example-password"

def check_password():
    print(password)
```

This makes the password available at module scope.

A better design is to pass the value only where it is required:

```
def check_password(password):
    return len(password) >= 12
```

This improves control over where the value is used, although it does not automatically guarantee secure memory handling.

### Example 2: Local Log Processing

```
def analyze_log(event):
    status = event.get("status")

    if status == "Failed":
        return "Investigate event"

    return "No alert"

event = {"username": "admin", "status": "Failed"}

print(analyze_log(event))
```

The variable `status` is local to the function.

### Example 3: Avoiding Shared Mutable State

Global mutable data can be modified by multiple parts of a program.

For security-sensitive applications, uncontrolled shared state can create unexpected behavior.

Prefer:

- Clear function inputs.
    
- Clear return values.
    
- Limited shared mutable data.
    
- Explicit state management.
    

## 11. Common Mistakes

1. Trying to access a local variable outside its scope.
    
2. Confusing scope with lifetime.
    
3. Modifying global variables unnecessarily.
    
4. Forgetting the `global` keyword when rebinding a global variable in Python.
    
5. Using `nonlocal` when the intended variable is global.
    
6. Assuming JavaScript `var`, `let`, and `const` have identical scope.
    
7. Assuming a local variable disappearing means every object it referenced is immediately destroyed.
    
8. Using global mutable data without considering its side effects.
    

## 12. Key Takeaways

- Scope determines where a variable can be accessed.
    
- Lifetime determines how long a variable or object exists.
    
- Python uses the LEGB name-resolution rule.
    
- Python supports `global` and `nonlocal`.
    
- C supports block scope and different storage durations.
    
- JavaScript provides `var`, `let`, and `const`.
    
- Limiting unnecessary shared state improves code maintainability.
    
- Scope and lifetime matter when handling sensitive application data.
    

## 13. Questions and Doubts

- What is the difference between scope and lifetime?
    
- What is local scope?
    
- What is global scope?
    
- What does LEGB mean in Python?
    
- What is the difference between `global` and `nonlocal`?
    
- How do `var`, `let`, and `const` differ in JavaScript?
    
- What is a static variable in C?
    

## 14. Practical Tasks

Complete these tasks:

1. Create a function with a local variable and try accessing it outside the function.
    
2. Create a global variable and read it inside a function.
    
3. Modify a global variable using Python's `global` keyword.
    
4. Create nested functions and modify an enclosing variable using `nonlocal`.
    
5. Write a C program using a static local counter.
    
6. Write a JavaScript example demonstrating the difference between `var` and `let`.
    
7. Create a log-analysis function that uses local variables to process an event.
    

**Challenge:** Create a small Python program that processes login events without relying on unnecessary global variables. Pass each event into a function and return its analysis result.