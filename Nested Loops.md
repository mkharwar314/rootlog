> Understand how loops work inside other loops, how to control their execution, and how to analyze their time complexity.

## 1. What Are Nested Loops?

A **nested loop** is a loop placed inside another loop.

The loop containing another loop is called the **outer loop**, while the loop inside it is called the **inner loop**.

The inner loop executes completely for each iteration of the outer loop.

Nested loops are useful when working with:

- Tables and grids
    
- Matrices and two-dimensional arrays
    
- Pattern printing
    
- Comparing multiple values
    
- Processing structured datasets
    

## 2. How Nested Loops Work

Consider this structure:

```
for i in range(3):
    for j in range(2):
        print(i, j)
```

Execution:

|Outer loop (`i`)|Inner loop (`j`)|
|---|---|
|0|0|
|0|1|
|1|0|
|1|1|
|2|0|
|2|1|

Output:

```
0 0
0 1
1 0
1 1
2 0
2 1
```

**Important:** The inner loop runs twice for every iteration of the outer loop.

Total executions of the inner loop body:

`3 × 2 = 6`

## 3. Nested Loops in Python

### Basic Syntax

```
for outer_variable in sequence:
    for inner_variable in sequence:
        # Code to execute
```

Example:

```
for i in range(1, 4):
    for j in range(1, 3):
        print("Outer:", i, "Inner:", j)
```

### Example 1: Multiplication Grid

```
for i in range(1, 4):
    for j in range(1, 4):
        print(i * j, end=" ")
    print()
```

Output:

```
1 2 3
2 4 6
3 6 9
```

The inner loop prints values in one row. The outer loop creates the next row.

### Example 2: Printing a Pattern

```
for i in range(1, 5):
    for j in range(i):
        print("*", end="")
    print()
```

Output:

```
*
**
***
****
```

Explanation:

- The outer loop controls the number of rows.
    
- The inner loop controls how many stars appear in each row.
    
- `print()` moves the cursor to the next line.
    

### Example 3: Iterating Through a Matrix

A matrix is a rectangular arrangement of values in rows and columns.

```
matrix = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

for row in matrix:
    for value in row:
        print(value, end=" ")
    print()
```

Output:

```
10 20 30
40 50 60
70 80 90
```

The outer loop selects each row. The inner loop processes each value in that row.

## 4. Nested Loops in C

Example:

```
#include <stdio.h>

int main() {
    for (int i = 1; i <= 3; i++) {
        for (int j = 1; j <= 2; j++) {
            printf("%d %d\n", i, j);
        }
    }

    return 0;
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

The inner loop completes before the outer loop moves to its next iteration.

## 5. Nested Loops in JavaScript

Example:

```
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 2; j++) {
        console.log(i, j);
    }
}
```

The execution follows the same nested-loop principle used in Python and C.

## 6. Break and Continue in Nested Loops

`break` and `continue` can be used inside nested loops.

However, they normally affect only the **nearest enclosing loop**.

### Using Break

```
for i in range(1, 4):
    for j in range(1, 4):
        if j == 2:
            break
        print(i, j)
```

Output:

```
1 1
2 1
3 1
```

When `j == 2`, the inner loop terminates. The outer loop continues with its next iteration.

### Using Continue

```
for i in range(1, 4):
    for j in range(1, 4):
        if j == 2:
            continue
        print(i, j)
```

Output:

```
1 1
1 3
2 1
2 3
3 1
3 3
```

When `j == 2`, the current inner-loop iteration is skipped. The inner loop then continues.

**Remember:** A `break` inside the inner loop does not automatically terminate the outer loop. Exiting multiple loop levels requires additional control logic.

## 7. Nested Loops and Time Complexity

Nested loops can increase the number of operations performed by a program.

Consider:

```
for i in range(n):
    for j in range(n):
        print(i, j)
```

The outer loop runs `n` times.

For every outer iteration, the inner loop also runs `n` times.

Total operations:

`n × n = n²`

Time complexity: **O(n²)**

### Different Loop Sizes

```
for i in range(n):
    for j in range(m):
        print(i, j)
```

Time complexity: **O(n × m)**

### Important Distinction

Not every nested loop has O(n²) complexity.

For example:

```
for i in range(n):
    for j in range(5):
        print(i, j)
```

The inner loop always runs five times.

Time complexity: **O(n)**

Always analyze how many times each loop actually executes.

## 8. Nested Loops in Cybersecurity

Nested loops are useful in cybersecurity programming when processing structured data.

### Example 1: Comparing IP Addresses

```
internal_ips = ["192.168.1.10", "192.168.1.20"]
logged_ips = ["192.168.1.20", "192.168.1.30"]

for internal_ip in internal_ips:
    for logged_ip in logged_ips:
        if internal_ip == logged_ip:
            print("Matching IP:", internal_ip)
```

Output:

```
Matching IP: 192.168.1.20
```

This demonstrates comparing two small datasets.

### Example 2: Comparing Log Events

Suppose two lists contain usernames from different log sources.

```
source_a = ["admin", "student", "guest"]
source_b = ["guest", "user1", "admin"]

for user_a in source_a:
    for user_b in source_b:
        if user_a == user_b:
            print("Matching account:", user_a)
```

Output:

```
Matching account: admin
Matching account: guest
```

This technique can help compare small datasets during log analysis.

For large datasets, nested comparisons can become inefficient. Consider sets, dictionaries, sorting, or other more efficient approaches when appropriate.

## 9. Common Mistakes

1. **Incorrect indentation:** Python uses indentation to define the loop structure.
    
2. **Confusing loop variables:** Use meaningful names such as `row` and `column`.
    
3. **Misunderstanding break:** `break` normally exits only the nearest enclosing loop.
    
4. **Missing newline:** Forgetting `print()` after a row can produce unexpected output.
    
5. **Ignoring complexity:** Large nested loops can make programs slow.
    
6. **Unnecessary nesting:** Sometimes a single loop or a more suitable data structure is enough.
    

## 10. Key Takeaways

- A nested loop is a loop inside another loop.
    
- The outer loop controls the execution of the inner loop.
    
- The inner loop completes its iterations before the outer loop advances.
    
- Nested loops are useful for matrices, grids, patterns, and dataset comparisons.
    
- `break` and `continue` normally affect the nearest enclosing loop.
    
- Two loops with `n` iterations each generally produce O(n²) work.
    
- Nested loops should be designed carefully when processing large datasets.
    

## 11. Questions and Doubts

Use this section to record questions you encounter while studying nested loops.

- When should I use nested loops?
    
- How does execution flow through two loops?
    
- Why can nested loops become inefficient?
    
- How can I reduce unnecessary nested-loop operations?
    

## 12. Practical Tasks

Complete these programs yourself:

1. Print a multiplication grid from 1 to 5.
    
2. Print a right-angled triangle using stars.
    
3. Print a 5 × 5 number grid.
    
4. Calculate the sum of all values in a two-dimensional list.
    
5. Compare two small lists of IP addresses and print matching addresses.
    
6. Modify a nested loop using `break` and observe which loop terminates.
    

**Practical rule:** Predict the output before running each program. Then execute it and compare your prediction with the actual result.