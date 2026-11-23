> Understand how a function can call itself to solve a problem by breaking it into smaller subproblems.

## 1. What Is Recursion?

**Recursion** is a programming technique in which a function calls itself to solve a problem.

Instead of solving the entire problem in one operation, a recursive function breaks it into smaller versions of the same problem.

Example:

```
def countdown(number):
    if number == 0:
        print("Finished")
        return

    print(number)
    countdown(number - 1)

countdown(5)
```

Output:

```
5
4
3
2
1
Finished
```

The function keeps calling itself with a smaller number until it reaches the stopping condition.

## 2. Two Important Parts of Recursion

Every correctly designed recursive function needs two important components.

### A. Base Case

The **base case** is the condition that stops recursion.

Without a base case, a recursive function may continue calling itself until the program encounters a recursion-depth error or another resource limit.

Example:

```
if number == 0:
    return
```

### B. Recursive Case

The **recursive case** is the part where the function calls itself with a smaller or simpler input.

Example:

```
countdown(number - 1)
```

**Remember:**

- Base case = Stop condition.
    
- Recursive case = Function calls itself.
    

## 3. How Recursion Works

Consider:

```
def countdown(n):
    if n == 0:
        return

    print(n)
    countdown(n - 1)

countdown(3)
```

Execution:

1. `countdown(3)` prints `3`.
    
2. It calls `countdown(2)`.
    
3. `countdown(2)` prints `2`.
    
4. It calls `countdown(1)`.
    
5. `countdown(1)` prints `1`.
    
6. It calls `countdown(0)`.
    
7. The base case executes and returns.
    

Output:

```
3
2
1
```

Each function call waits for the next recursive call to finish before continuing after that call.

## 4. The Call Stack

The **call stack** is a memory structure that tracks active function calls.

When a function calls another function, information about the current call is stored on the stack.

Recursive functions create multiple active function calls.

Example:

```
def show(n):
    if n == 0:
        return

    print("Entering:", n)
    show(n - 1)
    print("Returning:", n)

show(3)
```

Output:

```
Entering: 3
Entering: 2
Entering: 1
Returning: 1
Returning: 2
Returning: 3
```

Explanation:

- Function calls move deeper into the call stack.
    
- The base case stops further recursive calls.
    
- The functions then return in reverse order.
    

This is why the output has two different phases.

## 5. Factorial Using Recursion

The factorial of a positive integer is the product of all positive integers up to that number.

For example:

`5! = 5 × 4 × 3 × 2 × 1 = 120`

Mathematically:

- `0! = 1`
    
- `n! = n × (n - 1)!` for positive integers.
    

Python implementation:

```
def factorial(n):
    if n < 0:
        raise ValueError("Factorial is not defined for negative integers")

    if n == 0 or n == 1:
        return 1

    return n * factorial(n - 1)

print(factorial(5))
```

Output:

```
120
```

The recursive calls are:

```
factorial(5)
5 * factorial(4)
5 * 4 * factorial(3)
5 * 4 * 3 * factorial(2)
5 * 4 * 3 * 2 * factorial(1)
```

The base case returns `1`, allowing the pending multiplications to complete.

## 6. Fibonacci Sequence Using Recursion

The Fibonacci sequence is a series in which each number is the sum of the previous two numbers.

Example:

```
0, 1, 1, 2, 3, 5, 8, 13, 21
```

Recursive implementation:

```
def fibonacci(n):
    if n < 0:
        raise ValueError("Enter a non-negative integer")

    if n == 0:
        return 0

    if n == 1:
        return 1

    return fibonacci(n - 1) + fibonacci(n - 2)

for i in range(7):
    print(fibonacci(i))
```

Output:

```
0
1
1
2
3
5
8
```

**Performance warning:** This basic recursive implementation repeats many calculations. Its time complexity is exponential, approximately O(2ⁿ). For larger inputs, use an iterative solution or memoization.

## 7. Recursion vs Iteration

Iteration uses loops to repeat instructions. Recursion uses function calls.

|Feature|Recursion|Iteration|
|---|---|---|
|Repetition|Function calls itself|Loop repeats|
|Stopping condition|Base case|Loop condition|
|Memory usage|Uses call stack|Often uses less auxiliary memory|
|Code structure|Can be concise for recursive problems|Often simpler for repetitive operations|
|Risk|Stack overflow or recursion-depth errors|Infinite loops|

Example using iteration:

```
def countdown(n):
    while n > 0:
        print(n)
        n -= 1

    print("Finished")

countdown(5)
```

The same task can be performed without recursive calls.

## 8. Recursion in C

C supports recursive functions.

Example:

```
#include <stdio.h>

int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    }

    return n * factorial(n - 1);
}

int main() {
    printf("%d\n", factorial(5));
    return 0;
}
```

Output:

```
120
```

Each recursive call creates another active function call.

For production code, consider input validation and integer overflow. A factorial can exceed the range of a C integer type quickly.

## 9. Recursion in JavaScript

JavaScript also supports recursive functions.

Example:

```
function factorial(n) {
    if (n < 0) {
        throw new Error("Negative numbers are not supported");
    }

    if (n === 0 || n === 1) {
        return 1;
    }

    return n * factorial(n - 1);
}

console.log(factorial(5));
```

Output:

```
120
```

JavaScript engines impose practical limits on recursive call depth. Excessive recursion can result in a stack overflow error.

## 10. Recursion in Cybersecurity

Recursion can be useful when working with hierarchical or nested data.

### Example 1: Searching Nested Directories

A directory can contain files and other directories.

A recursive approach can process each directory and its subdirectories.

Conceptual example:

```
from pathlib import Path

def list_files(directory):
    for item in Path(directory).iterdir():
        if item.is_dir():
            list_files(item)
        else:
            print(item)

list_files("sample_directory")
```

This example recursively lists files in a directory tree.

Only run it on directories you are authorized to inspect. For production tools, also handle permission errors, symbolic links, and possible directory cycles.

### Example 2: Processing Nested Data

Security tools often process JSON data containing nested objects.

```
def display_values(data):
    if isinstance(data, dict):
        for value in data.values():
            display_values(value)

    elif isinstance(data, list):
        for item in data:
            display_values(item)

    else:
        print(data)

sample = {
    "user": "admin",
    "events": ["login", "logout"],
    "details": {
        "status": "failed"
    }
}

display_values(sample)
```

This recursively visits values inside nested dictionaries and lists.

### Example 3: Understanding Recursive Analysis

Recursion can help with:

- Processing directory structures.
    
- Traversing trees.
    
- Examining nested JSON objects.
    
- Walking hierarchical event data.
    
- Analyzing nested configuration structures.
    

## 11. Common Mistakes

1. Forgetting to define a base case.
    
2. Writing a recursive call that does not move toward the base case.
    
3. Using the wrong stopping condition.
    
4. Creating too many recursive calls.
    
5. Ignoring the memory used by the call stack.
    
6. Using recursion when a simple loop would be more efficient.
    
7. Not considering repeated calculations.
    

## 12. Key Takeaways

- Recursion occurs when a function calls itself.
    
- Every recursive function needs a base case.
    
- The recursive case reduces the problem toward the base case.
    
- Recursive calls are tracked using the call stack.
    
- Recursion can make hierarchical problems easier to express.
    
- Recursion and iteration are alternative approaches to repetition.
    
- Excessive recursion can cause stack overflow or recursion-depth errors.
    
- Recursion is useful in directory traversal and nested-data processing.
    

## 13. Questions and Doubts

- What is recursion?
    
- What is the purpose of a base case?
    
- What is a recursive case?
    
- How does the call stack work?
    
- What is the difference between recursion and iteration?
    
- Why can recursive Fibonacci implementations be inefficient?
    

## 14. Practical Tasks

Complete these tasks in Python:

1. Create a recursive countdown function.
    
2. Create a recursive function that calculates the sum of numbers from 1 to n.
    
3. Create a recursive factorial function.
    
4. Create a recursive function that calculates the nth Fibonacci number.
    
5. Create a recursive function that traverses a small nested dictionary.
    
6. Compare a recursive countdown with an iterative countdown.
    

**Challenge:** Create a recursive directory-listing program that examines a test directory containing multiple subdirectories. Print each file's path and explain how the recursive calls work.