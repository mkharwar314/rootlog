> Understand how C programs use, allocate, manage, and release memory during execution.

## 1. What Is Memory Management?

Memory management is the process of allocating, using, organizing, and releasing computer memory while a program runs.

In C, programmers have significant control over memory management.

Poor memory management can cause:

- Memory leaks.
    
- Buffer overflows.
    
- Program crashes.
    
- Data corruption.
    
- Security vulnerabilities.
    

## 2. Understanding Program Memory

A running C program commonly uses several memory regions.

|Memory Region|Purpose|
|---|---|
|Code / Text|Stores executable instructions|
|Data|Stores initialized global and static variables|
|BSS|Stores zero-initialized and uninitialized global and static variables|
|Heap|Supports dynamic memory allocation|
|Stack|Stores function call information and automatic local variables|

Conceptual memory layout:

```
+--------------------------+
|          Stack           |
|   Local variables        |
|   Function call data     |
|            ↓             |
+--------------------------+
|                          |
|       Free Space         |
|                          |
+--------------------------+
|            ↑             |
|           Heap           |
|   Dynamic allocations    |
+--------------------------+
|           BSS            |
|  Zero-initialized data   |
+--------------------------+
|           Data           |
|  Initialized data        |
+--------------------------+
|       Code / Text        |
|  Program instructions    |
+--------------------------+
```

This is a simplified conceptual diagram. Actual memory layouts depend on the operating system, compiler, executable format, and runtime environment.

## 3. Stack Memory

The stack is used for function calls and automatic storage.

Local variables with automatic storage duration are commonly stored on the stack.

Example:

```
#include <stdio.h>

void display() {
    int number = 100;

    printf("%d\n", number);
}

int main() {
    display();

    return 0;
}
```

When `display()` is called, its local variable exists during the function's execution.

After the function returns, the variable's lifetime ends.

### Characteristics

- Automatically managed.
    
- Commonly used for local variables.
    
- Used for function call information.
    
- Generally efficient.
    
- Has limited available capacity.
    

**Important:** The C language specifies object lifetimes and storage duration, not that every automatic variable must physically reside on a hardware stack. Stack allocation is a common implementation.

## 4. Heap Memory

The heap is used for dynamic memory allocation.

Unlike ordinary local variables, dynamically allocated memory can remain available after the function that allocated it returns, until it is released.

Example:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = malloc(sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    *ptr = 100;

    printf("%d\n", *ptr);

    free(ptr);

    return 0;
}
```

### Characteristics

- Allocated dynamically.
    
- Managed explicitly by the programmer.
    
- Can support variable-sized data structures.
    
- Must be released when no longer needed.
    
- Incorrect handling can cause memory errors.
    

## 5. Static and Global Memory

Global and static variables have static storage duration.

Their lifetime extends throughout program execution.

### Global Variable

```
#include <stdio.h>

int number = 100;

int main() {
    printf("%d\n", number);

    return 0;
}
```

### Static Variable

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

**Output:**

```
1
2
3
```

The static local variable retains its value between function calls.

## 6. Static vs Automatic vs Dynamic Storage

|Feature|Automatic|Static|Allocated|
|---|---|---|---|
|Typical example|Local variable|Global/static variable|`malloc()`|
|Lifetime|Enclosing block execution|Entire program execution|Until released|
|Management|Automatic|Automatic|Programmer-managed|
|Common use|Temporary data|Persistent program state|Variable-sized data|

## 7. Dynamic Memory Allocation

Dynamic memory allocation allows a program to request memory during execution.

C provides four commonly used functions in `stdlib.h`:

1. `malloc()`
    
2. `calloc()`
    
3. `realloc()`
    
4. `free()`
    

## 8. malloc()

`malloc()` allocates a specified number of bytes.

Syntax:

```
pointer = malloc(size);
```

Example:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = malloc(5 * sizeof *ptr);

    if (ptr == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    for (int i = 0; i < 5; i++) {
        ptr[i] = (i + 1) * 10;
    }

    for (int i = 0; i < 5; i++) {
        printf("%d ", ptr[i]);
    }

    free(ptr);

    return 0;
}
```

**Output:**

```
10 20 30 40 50
```

Important:

- `malloc()` returns a pointer to allocated memory or NULL if allocation fails.
    
- The allocated memory is uninitialized.
    
- Check the returned pointer before using it.
    
- Release the allocation using `free()` when it is no longer needed.
    

## 9. calloc()

`calloc()` allocates memory for multiple elements and initializes all allocated bytes to zero.

Syntax:

```
pointer = calloc(number_of_elements, size_of_each_element);
```

Example:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = calloc(5, sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    for (int i = 0; i < 5; i++) {
        printf("%d ", ptr[i]);
    }

    free(ptr);

    return 0;
}
```

**Output on typical systems:**

```
0 0 0 0 0
```

For an array of integers, all-zero bytes represent integer zero on modern conventional systems.

## 10. malloc() vs calloc()

|Feature|malloc()|calloc()|
|---|---|---|
|Full form|Memory Allocation|Contiguous Allocation|
|Arguments|One|Two|
|Allocation|Specified number of bytes|Number of elements × element size|
|Initial contents|Uninitialized|All bytes initialized to zero|
|Typical use|General allocation|Allocating arrays with zeroed storage|

## 11. realloc()

`realloc()` changes the size of an existing dynamically allocated memory block.

Syntax:

```
new_pointer = realloc(old_pointer, new_size);
```

Example:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = malloc(3 * sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    ptr[0] = 10;
    ptr[1] = 20;
    ptr[2] = 30;

    int *temp = realloc(ptr, 5 * sizeof *ptr);

    if (temp == NULL) {
        free(ptr);
        return 1;
    }

    ptr = temp;

    ptr[3] = 40;
    ptr[4] = 50;

    for (int i = 0; i < 5; i++) {
        printf("%d ", ptr[i]);
    }

    free(ptr);

    return 0;
}
```

**Output:**

```
10 20 30 40 50
```

Important:

- `realloc()` may move the allocation to a different memory location.
    
- Existing data is preserved up to the smaller of the old and new sizes.
    
- Newly added memory is uninitialized.
    
- If resizing fails for a nonzero requested size, the original allocation remains valid.
    
- A temporary pointer prevents losing the original allocation when resizing fails.
    

## 12. free()

`free()` releases dynamically allocated memory.

Syntax:

```
free(pointer);
```

Example:

```
#include <stdlib.h>

int main() {
    int *ptr = malloc(sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    *ptr = 100;

    free(ptr);
    ptr = NULL;

    return 0;
}
```

After releasing memory, do not access the released allocation through that pointer.

Setting the pointer to NULL is a useful defensive practice, but it does not change other pointers that may still refer to the same allocation.

## 13. Memory Leak

A memory leak occurs when dynamically allocated memory is not released and the program loses the ability to access it.

Example:

```
#include <stdlib.h>

int main() {
    int *ptr = malloc(sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    ptr = NULL;

    return 0;
}
```

The allocated memory is no longer reachable through `ptr`, but it was never released.

This is a memory leak.

### Prevention

- Track every successful allocation.
    
- Release memory when it is no longer required.
    
- Use clear ownership rules.
    
- Check all error paths.
    
- Use memory analysis tools.
    

## 14. Dangling Pointers

A dangling pointer refers to an object whose lifetime has ended or to memory that has been released.

Example:

```
#include <stdlib.h>

int main() {
    int *ptr = malloc(sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    *ptr = 50;

    free(ptr);

    /* ptr is now dangling */

    return 0;
}
```

Using `*ptr` after `free(ptr)` causes undefined behavior.

A simple precaution:

```
free(ptr);
ptr = NULL;
```

Remember that setting one pointer to NULL does not update other aliases.

## 15. Buffer Overflow

A buffer overflow occurs when a program writes beyond the allocated boundaries of a buffer.

Example:

```
#include <stdio.h>

int main() {
    int numbers[3] = {10, 20, 30};

    numbers[5] = 100;

    return 0;
}
```

The array contains only three elements, so valid indexes are `0`, `1`, and `2`.

Writing to index `5` causes undefined behavior.

### Possible Consequences

- Program crashes.
    
- Memory corruption.
    
- Unexpected program behavior.
    
- Potential security compromise.
    

## 16. Use-After-Free

Use-after-free occurs when a program accesses memory after it has been released.

Example of incorrect code:

```
#include <stdlib.h>

int main() {
    int *ptr = malloc(sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    *ptr = 100;

    free(ptr);

    /* Incorrect: accessing released memory */
    /* printf("%d", *ptr); */

    return 0;
}
```

This is a serious memory-safety error.

## 17. Double Free

Double free occurs when the same allocation is released more than once.

Incorrect example:

```
int *ptr = malloc(sizeof *ptr);

if (ptr != NULL) {
    free(ptr);
    free(ptr);
}
```

The second `free()` is invalid because the allocation has already been released.

Correct approach:

```
free(ptr);
ptr = NULL;
```

Calling `free(NULL)` is safe.

## 18. Memory Management and Cybersecurity

Memory management is a major topic in systems security.

Many software vulnerabilities originate from incorrect memory handling.

|Vulnerability|Description|
|---|---|
|Buffer Overflow|Writing beyond a buffer|
|Use-After-Free|Accessing released memory|
|Double Free|Releasing the same allocation twice|
|Memory Leak|Failing to release allocated memory|
|NULL Pointer Dereference|Accessing memory through NULL|
|Out-of-Bounds Read|Reading outside valid memory|
|Out-of-Bounds Write|Writing outside valid memory|

These issues can cause crashes, information disclosure, or in some circumstances, code execution.

## 19. Memory Debugging Tools

Several tools help identify memory-related errors.

### A. AddressSanitizer

AddressSanitizer detects many memory errors during program execution.

Compile with GCC:

```
gcc -g -fsanitize=address -fno-omit-frame-pointer program.c -o program
```

Run:

```
./program
```

It can detect issues such as:

- Heap buffer overflows.
    
- Stack buffer overflows.
    
- Use-after-free.
    
- Some memory leaks, depending on platform support.
    

### B. Valgrind

Valgrind is a memory debugging and profiling tool commonly used on Linux.

Run:

```
valgrind --leak-check=full ./program
```

It can help identify:

- Memory leaks.
    
- Invalid memory reads.
    
- Invalid memory writes.
    
- Incorrect memory deallocation.
    

### C. GDB

GDB is a debugger used to inspect program execution.

Start a debugging session:

```
gcc -g program.c -o program
gdb ./program
```

Useful commands:

```
break main
run
next
step
print variable_name
backtrace
quit
```

## 20. Best Practices for Memory Management

1. Initialize pointers before using them.
    
2. Check allocation results.
    
3. Use `sizeof *ptr` when allocating memory for the pointed-to type.
    
4. Check array boundaries.
    
5. Release dynamically allocated memory.
    
6. Avoid accessing released memory.
    
7. Avoid double-free errors.
    
8. Use temporary pointers with `realloc()`.
    
9. Keep track of memory ownership.
    
10. Use debugging tools during development.
    

## 21. Practical Exercises

Write C programs to perform these tasks:

1. Allocate memory for one integer using `malloc()`.
    
2. Allocate memory for five integers using `calloc()`.
    
3. Resize an allocated array using `realloc()`.
    
4. Store and display five numbers using dynamic memory.
    
5. Release allocated memory using `free()`.
    
6. Write a program that safely handles allocation failure.
    
7. Compile a program using AddressSanitizer.
    
8. Create a small program with a deliberate memory leak and inspect it using Valgrind, if available.
    

## 22. Key Takeaways

- Memory management controls how programs use memory.
    
- Stack memory commonly supports function calls and automatic variables.
    
- Heap memory supports dynamic allocation.
    
- Global and static variables have static storage duration.
    
- `malloc()` allocates uninitialized memory.
    
- `calloc()` allocates zero-initialized storage.
    
- `realloc()` changes the size of an allocation.
    
- `free()` releases allocated memory.
    
- Memory leaks, dangling pointers, and buffer overflows are important memory-management problems.
    
- AddressSanitizer, Valgrind, and GDB help debug memory-related errors.
    

## 23. Related Notes

- [[Introduction to C]]
    
- [[C Variables and Data Types]]
    
- [[C Functions]]
    
- [[C Arrays and Strings]]
    
- [[C Pointers]]
    
- [[Introduction to Data Structures]]
    
- [[Introduction to Secure Coding]]