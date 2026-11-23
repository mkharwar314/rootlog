> Understand memory addresses, pointer variables, dereferencing, pointer arithmetic, and how pointers are used in C programming.

## 1. What Is a Pointer?

A **pointer** is a variable that stores the memory address of another variable.

Unlike ordinary variables, which store values directly, pointers store addresses.

### Example

```
#include <stdio.h>

int main() {
    int number = 50;

    int *ptr = &number;

    printf("Value: %d\n", number);
    printf("Address: %p\n", (void *)ptr);

    return 0;
}
```

The output will show:

- The value `50`.
    
- The memory address where `number` is stored.
    

The actual address varies between program executions and systems.

## 2. Address-of Operator (&)

The `&` operator obtains the memory address of a variable.

```
int number = 100;

printf("%p", (void *)&number);
```

Here, `&number` means the address of `number`.

## 3. Dereference Operator (*)

The `*` operator accesses the value stored at the address held by a pointer.

```
#include <stdio.h>

int main() {
    int number = 100;
    int *ptr = &number;

    printf("%d\n", *ptr);

    return 0;
}
```

**Output:**

```
100
```

Here:

- `ptr` stores the address of `number`.
    
- `*ptr` accesses the value at that address.
    

## 4. Pointer Declaration

General syntax:

```
data_type *pointer_name;
```

Examples:

```
int *ptr;
float *ptr;
char *ptr;
double *ptr;
```

The pointer type indicates the type of object it is intended to point to.

For example:

```
int number = 10;
int *ptr = &number;
```

`ptr` is a pointer to an integer.

## 5. Understanding Pointers Visually

Consider:

```
int number = 50;
int *ptr = &number;
```

Conceptual memory representation:

|Variable|Stored value|
|---|---|
|`number`|`50`|
|`ptr`|Address of `number`|

Relationship:

```
ptr
 |
 | stores address
 v
number
 |
 | contains
 v
50
```

The pointer does not contain the integer `50`. It contains the address of the variable that contains `50`.

## 6. Modifying Values Through Pointers

Pointers can modify the original variable through dereferencing.

```
#include <stdio.h>

int main() {
    int number = 10;
    int *ptr = &number;

    *ptr = 99;

    printf("%d\n", number);

    return 0;
}
```

**Output:**

```
99
```

Because `ptr` points to `number`, modifying `*ptr` changes `number`.

## 7. NULL Pointers

A NULL pointer does not point to a valid object or function.

```
int *ptr = NULL;
```

Before dereferencing a pointer, check that it is not NULL when NULL is a possible value.

```
#include <stdio.h>

int main() {
    int *ptr = NULL;

    if (ptr != NULL) {
        printf("%d\n", *ptr);
    } else {
        printf("Pointer is NULL\n");
    }

    return 0;
}
```

**Important:** Dereferencing a NULL pointer causes undefined behavior.

## 8. Pointer Arithmetic

Pointer arithmetic allows movement between elements of an array.

Example:

```
#include <stdio.h>

int main() {
    int numbers[] = {10, 20, 30};

    int *ptr = numbers;

    printf("%d\n", *ptr);

    ptr++;

    printf("%d\n", *ptr);

    return 0;
}
```

**Output:**

```
10
20
```

When an integer pointer is incremented, it moves to the next integer element, not necessarily just one byte.

Pointer arithmetic is only valid within an array object and one position past its final element, subject to the C language rules. A one-past-the-end pointer must not be dereferenced.

## 9. Pointers and Arrays

Array names usually convert to pointers to their first elements in expressions.

```
#include <stdio.h>

int main() {
    int numbers[] = {10, 20, 30};

    int *ptr = numbers;

    for (int i = 0; i < 3; i++) {
        printf("%d\n", *(ptr + i));
    }

    return 0;
}
```

**Output:**

```
10
20
30
```

Remember:

- `numbers` usually converts to `&numbers[0]`.
    
- `*ptr` accesses the first element.
    
- `*(ptr + 1)` accesses the second element.
    

An array and a pointer are related, but they are not the same type.

## 10. Pointers and Functions

Pointers allow functions to modify variables belonging to the caller.

Example:

```
#include <stdio.h>

void changeValue(int *ptr) {
    *ptr = 500;
}

int main() {
    int number = 100;

    changeValue(&number);

    printf("%d\n", number);

    return 0;
}
```

**Output:**

```
500
```

This technique is useful when:

- A function needs to modify caller-owned data.
    
- A function needs to work with arrays.
    
- A function needs to return multiple results through output parameters.
    

C still passes the pointer value by value. The function receives a copy of the address, which can be used to access the original object.

## 11. Pointer to Pointer

A pointer to pointer stores the address of another pointer.

```
#include <stdio.h>

int main() {
    int number = 50;

    int *ptr = &number;
    int **ptr2 = &ptr;

    printf("%d\n", **ptr2);

    return 0;
}
```

**Output:**

```
50
```

Explanation:

- `number` stores `50`.
    
- `ptr` stores the address of `number`.
    
- `ptr2` stores the address of `ptr`.
    
- `**ptr2` accesses the value of `number`.
    

## 12. Void Pointers

A `void *` is a generic object pointer that can hold the address of an object of any type.

```
#include <stdio.h>

int main() {
    int number = 100;

    void *ptr = &number;

    printf("%d\n", *(int *)ptr);

    return 0;
}
```

**Output:**

```
100
```

A `void *` must be converted to an appropriate object pointer type before dereferencing it.

## 13. Constant Pointers and Pointers to Constants

These declarations have different meanings.

### A. Pointer to Constant Data

```
const int *ptr;
```

The pointer can be changed to point elsewhere, but the pointed-to value cannot be modified through this pointer.

### B. Constant Pointer

```
int *const ptr = &number;
```

The pointer cannot be changed to point elsewhere, but the pointed-to value can be modified.

### C. Constant Pointer to Constant Data

```
const int *const ptr = &number;
```

Neither the pointer nor the pointed-to value can be modified through this pointer.

## 14. Function Pointers

A function pointer stores the address of a function.

```
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int (*operation)(int, int) = add;

    printf("%d\n", operation(10, 20));

    return 0;
}
```

**Output:**

```
30
```

Function pointers are used in:

- Callback functions.
    
- Event handling.
    
- Sorting functions.
    
- Operating system interfaces.
    
- Modular program design.
    

## 15. Dynamic Memory and Pointers

Pointers are essential for dynamic memory allocation.

Dynamic memory is allocated during program execution rather than being fixed at compile time.

C provides these functions in `stdlib.h`:

|Function|Purpose|
|---|---|
|`malloc()`|Allocates memory without initializing it|
|`calloc()`|Allocates memory and initializes its bytes to zero|
|`realloc()`|Changes the size of an allocated memory block|
|`free()`|Releases allocated memory|

Example:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = malloc(5 * sizeof *ptr);

    if (ptr == NULL) {
        return 1;
    }

    for (int i = 0; i < 5; i++) {
        ptr[i] = (i + 1) * 10;
    }

    for (int i = 0; i < 5; i++) {
        printf("%d ", ptr[i]);
    }

    free(ptr);
    ptr = NULL;

    return 0;
}
```

**Output:**

```
10 20 30 40 50
```

Important:

- Check whether allocation succeeded.
    
- Do not access memory beyond the allocated size.
    
- Release allocated memory with `free()`.
    
- Do not use a pointer after its memory has been freed.
    

Dynamic memory management is covered in more detail in [[C Memory Management]].

## 16. Common Pointer Errors

### A. Wild Pointer

An uninitialized pointer contains an indeterminate value.

```
int *ptr;
```

Using this pointer before assigning a valid address can cause undefined behavior.

### B. NULL Pointer Dereference

```
int *ptr = NULL;

printf("%d", *ptr);
```

This causes undefined behavior.

### C. Dangling Pointer

A dangling pointer refers to an object whose lifetime has ended or memory that has been released.

```
int *ptr = malloc(sizeof *ptr);

if (ptr != NULL) {
    free(ptr);
    ptr = NULL;
}
```

Setting the pointer to NULL prevents further accidental use through that particular pointer variable. It does not invalidate other copies of the old address.

### D. Memory Leak

A memory leak occurs when dynamically allocated memory is no longer reachable but has not been released.

```
int *ptr = malloc(sizeof *ptr);

/* Missing free(ptr) */
```

### E. Out-of-Bounds Access

Accessing memory outside an array's valid range can corrupt data or crash a program.

## 17. Pointer Security

Pointers are important in cybersecurity because memory-related programming errors can create vulnerabilities.

Common issues include:

|Vulnerability|Explanation|
|---|---|
|Buffer overflow|Writing beyond a buffer's boundaries|
|Use-after-free|Accessing memory after it has been released|
|Double free|Releasing the same allocation more than once|
|NULL pointer dereference|Accessing memory through a NULL pointer|
|Out-of-bounds access|Accessing memory outside valid limits|
|Memory leak|Failing to release allocated memory|

### Secure Programming Practices

- Initialize pointers before using them.
    
- Check pointers before dereferencing when they may be NULL.
    
- Validate array indexes and buffer sizes.
    
- Track dynamically allocated memory carefully.
    
- Avoid using pointers after freeing their memory.
    
- Do not assume that a pointer is valid just because it is non-NULL.
    

## 18. Practical Exercises

Write C programs to perform these tasks:

1. Declare an integer variable and print its address using `&`.
    
2. Create a pointer that stores the address of an integer.
    
3. Access a variable's value using the dereference operator.
    
4. Modify a variable through a pointer.
    
5. Traverse an array using pointer arithmetic.
    
6. Create a function that swaps two integers using pointer parameters.
    
7. Create a pointer to pointer and access the original integer.
    
8. Use a `void *` to access an integer.
    
9. Allocate memory dynamically for five integers and release it.
    
10. Create a function pointer that calls an addition function.
    

## 19. Key Takeaways

- A pointer stores a memory address.
    
- `&` obtains the address of an object.
    
- `*` dereferences a pointer.
    
- Pointer arithmetic moves between elements of an array.
    
- Arrays and pointers are related but are not identical.
    
- C functions can modify caller-owned objects using pointer parameters.
    
- A pointer to pointer stores the address of another pointer.
    
- `void *` is a generic object pointer.
    
- Dynamic memory allocation relies on pointers.
    
- Incorrect pointer handling can cause serious security vulnerabilities.
    

## 20. Related Notes

- [[Introduction to C]]
    
- [[C Variables and Data Types]]
    
- [[C Functions]]
    
- [[C Arrays and Strings]]
    
- [[C Memory Management]]
    
- [[Introduction to Data Structures]]
    
- [[Introduction to Secure Coding]]