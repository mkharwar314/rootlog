> Learn how to use loops and nested loops to generate structured output such as triangles, pyramids, number patterns, and grids.

## 1. What Is Pattern Programming?

Pattern programming is the process of creating structured output using programming statements, especially loops and nested loops.

Patterns can contain:

- Stars (`*`)
    
- Numbers (`1, 2, 3`)
    
- Letters (`A, B, C`)
    
- Spaces
    
- Combinations of characters
    

Pattern programming helps develop:

- Logical thinking
    
- Loop control
    
- Nested-loop understanding
    
- Problem-solving skills
    
- Output formatting skills
    

## 2. Understanding Rows and Columns

Most patterns are organized into rows and columns.

For example:

```
* * *
* * *
* * *
```

This pattern contains:

- 3 rows
    
- 3 columns
    
- 9 stars
    

In pattern programming:

- The outer loop usually controls rows.
    
- The inner loop usually controls columns.
    
- `print()` or newline characters move output to the next row.
    

## 3. Basic Star Patterns in Python

### Pattern 1: Square Pattern

```
for i in range(3):
    for j in range(3):
        print("*", end=" ")
    print()
```

Output:

```
* * *
* * *
* * *
```

Explanation:

- Outer loop runs 3 times.
    
- Inner loop prints 3 stars per row.
    
- `print()` moves to the next line.
    

### Pattern 2: Right-Angled Triangle

```
for i in range(1, 5):
    for j in range(i):
        print("*", end=" ")
    print()
```

Output:

```
*
* *
* * *
* * * *
```

The number of stars increases with each row.

### Pattern 3: Inverted Triangle

```
for i in range(4, 0, -1):
    for j in range(i):
        print("*", end=" ")
    print()
```

Output:

```
* * * *
* * *
* *
*
```

The number of stars decreases with each row.

### Pattern 4: Pyramid Pattern

```
rows = 4

for i in range(1, rows + 1):
    for space in range(rows - i):
        print(" ", end="")
    for star in range(2 * i - 1):
        print("*", end="")
    print()
```

Output:

```
   *
  ***
 *****
*******
```

Explanation:

- The first inner loop prints leading spaces.
    
- The second inner loop prints stars.
    
- Each row contains two more stars than the previous row.
    

## 4. Number Patterns

Pattern programming is not limited to symbols. Numbers can also be arranged into patterns.

### Pattern 1: Increasing Numbers

```
for i in range(1, 5):
    for j in range(1, i + 1):
        print(j, end=" ")
    print()
```

Output:

```
1
1 2
1 2 3
1 2 3 4
```

### Pattern 2: Repeated Row Numbers

```
for i in range(1, 5):
    for j in range(i):
        print(i, end=" ")
    print()
```

Output:

```
1
2 2
3 3 3
4 4 4 4
```

### Pattern 3: Continuous Numbers

```
number = 1

for i in range(1, 4):
    for j in range(i):
        print(number, end=" ")
        number += 1
    print()
```

Output:

```
1
2 3
4 5 6
```

The variable `number` keeps its value across rows because it is initialized before the loops.

## 5. Alphabet Patterns

Characters can also be used to create patterns.

```
for i in range(1, 5):
    for j in range(i):
        print(chr(64 + i), end=" ")
    print()
```

Output:

```
A
B B
C C C
D D D D
```

Explanation:

- `chr()` converts a numeric character code into a character.
    
- In this example, 65 represents `A`, 66 represents `B`, and so on.
    

## 6. Understanding Spaces and Alignment

Spaces are important when creating centered patterns.

Consider:

```
   *
  * *
 * * *
* * * *
```

The spaces at the beginning of each row align the stars.

A pattern may require multiple inner loops:

1. One loop for spaces.
    
2. Another loop for symbols.
    

Always identify what each loop is responsible for before writing the code.

## 7. Pattern Programming in C

Example: Right-angled triangle.

```
#include <stdio.h>

int main() {
    int rows = 4;

    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }

    return 0;
}
```

Output:

```
*
* *
* * *
* * * *
```

In C:

- `printf("* ")` prints a symbol on the current line.
    
- `printf("\n")` moves to the next line.
    

## 8. Pattern Programming in JavaScript

Example: Number triangle.

```
for (let i = 1; i <= 4; i++) {
    let row = "";

    for (let j = 1; j <= i; j++) {
        row += j + " ";
    }

    console.log(row);
}
```

Output:

```
1
1 2
1 2 3
1 2 3 4
```

Here, the inner loop builds a string, and the outer loop prints each completed row.

## 9. How to Solve Pattern Problems

Follow this process:

1. **Observe the pattern:** Count rows, columns, spaces, and symbols.
    
2. **Identify the outer loop:** Determine how many rows are required.
    
3. **Identify the inner loop:** Determine what must be printed in each row.
    
4. **Find the relationship:** Check how the number of symbols or spaces changes.
    
5. **Write the code:** Translate the relationship into loop conditions.
    
6. **Dry-run:** Trace the first few iterations manually.
    
7. **Test:** Run the program and compare its output with the expected pattern.
    

Do not memorize every pattern program. Understand how the number of spaces and symbols changes from row to row.

## 10. Common Mistakes

1. Incorrect loop boundaries.
    
2. Missing or incorrect indentation in Python.
    
3. Forgetting to move to the next line.
    
4. Printing the wrong number of spaces.
    
5. Initializing a counter inside the wrong loop.
    
6. Confusing the row variable with the column variable.
    
7. Using complicated nested loops when a simpler solution is possible.
    

## 11. Key Takeaways

- Pattern programming uses loops to generate structured output.
    
- The outer loop usually controls rows.
    
- Inner loops control symbols, numbers, or spaces.
    
- Multiple inner loops can be used to create complex patterns.
    
- Dry-running helps identify incorrect loop conditions.
    
- Understanding the pattern is more important than memorizing code.
    

## 12. Questions and Doubts

- How does the outer loop control rows?
    
- Why are multiple inner loops sometimes needed?
    
- How are spaces used to center a pattern?
    
- How can I convert a visual pattern into loop conditions?
    

## 13. Practical Tasks

Write these programs in Python without copying the examples:

1. Print a 5 × 5 square of stars.
    
2. Print an inverted right-angled triangle with 5 rows.
    
3. Print a number triangle:
    

```
1
2 3
4 5 6
7 8 9 10
```

4. Print an alphabet triangle:
    

```
A
A B
A B C
A B C D
```

5. Print a centered pyramid with 5 rows.
    
6. Create your own pattern and explain the role of each loop.
    

**Challenge:** Write one pattern program in Python and then convert it into C or JavaScript.