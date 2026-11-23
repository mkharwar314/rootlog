> Understand how C stores collections of data and represents text using character arrays.

## 1. What Is an Array?

An **array** is a collection of elements of the same data type stored in contiguous memory locations.

Instead of declaring multiple variables separately, we can store related values in one array.

### Example

```
#include <stdio.h>

int main() {
    int marks[5] = {80, 75, 90, 85, 95};

    printf("%d\n", marks[0]);
    printf("%d\n", marks[1]);

    return 0;
}
```

**Output:**

```
80
75
```

Here:

- `int` is the data type.
    
- `marks` is the array name.
    
- `5` is the number of elements.
    
- `{80, 75, 90, 85, 95}` contains the array values.
    

## 2. Array Indexing

Each array element has an index.

In C, array indexing starts at **0**, not 1.

For an array containing five elements:

|Index|Value|
|---|---|
|0|80|
|1|75|
|2|90|
|3|85|
|4|95|

Access an element using:

```
marks[2]
```

This accesses the third element.

**Important:** Accessing an array outside its valid bounds causes undefined behavior.

For an array of five elements, valid indexes are `0` through `4`.

## 3. Declaring and Initializing Arrays

### Declaration

```
int numbers[5];
```

This declares an array of five integers. Its elements are uninitialized if it is an automatic local array.

### Initialization

```
int numbers[5] = {10, 20, 30, 40, 50};
```

### Partial Initialization

```
int numbers[5] = {10, 20};
```

The remaining elements are initialized to zero.

Result:

```
10 20 0 0 0
```

### Automatic Size Calculation

```
int numbers[] = {10, 20, 30};
```

The compiler determines the number of elements from the initializer.

## 4. Accessing and Modifying Array Elements

Use an index to read or update an element.

```
#include <stdio.h>

int main() {
    int numbers[3] = {10, 20, 30};

    numbers[1] = 100;

    printf("%d\n", numbers[1]);

    return 0;
}
```

**Output:**

```
100
```

## 5. Traversing an Array

Traversing means visiting each element of an array.

A `for` loop is commonly used.

```
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }

    return 0;
}
```

**Output:**

```
10 20 30 40 50
```

## 6. Common Array Operations

### A. Finding the Sum

```
#include <stdio.h>

int main() {
    int numbers[] = {10, 20, 30, 40, 50};
    int sum = 0;

    for (int i = 0; i < 5; i++) {
        sum += numbers[i];
    }

    printf("Sum: %d\n", sum);

    return 0;
}
```

### B. Finding the Largest Element

```
#include <stdio.h>

int main() {
    int numbers[] = {15, 42, 8, 90, 23};
    int largest = numbers[0];

    for (int i = 1; i < 5; i++) {
        if (numbers[i] > largest) {
            largest = numbers[i];
        }
    }

    printf("Largest: %d\n", largest);

    return 0;
}
```

### C. Searching an Element

```
#include <stdio.h>

int main() {
    int numbers[] = {10, 20, 30, 40, 50};
    int target = 30;
    int found = 0;

    for (int i = 0; i < 5; i++) {
        if (numbers[i] == target) {
            found = 1;
            break;
        }
    }

    if (found) {
        printf("Element found\n");
    } else {
        printf("Element not found\n");
    }

    return 0;
}
```

## 7. Types of Arrays

C supports arrays with different numbers of dimensions.

### A. One-Dimensional Array

Stores elements in a single sequence.

```
int numbers[5] = {1, 2, 3, 4, 5};
```

### B. Two-Dimensional Array

Stores elements in rows and columns.

```
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

Access an element:

```
printf("%d", matrix[1][2]);
```

Output:

```
6
```

### C. Traversing a Two-Dimensional Array

```
#include <stdio.h>

int main() {
    int matrix[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", matrix[i][j]);
        }

        printf("\n");
    }

    return 0;
}
```

**Output:**

```
1 2 3
4 5 6
```

## 8. Memory Representation of Arrays

Array elements are stored in contiguous memory locations.

For example:

```
int numbers[4] = {10, 20, 30, 40};
```

Conceptual memory layout:

|Element|Index|Address (illustrative)|
|---|---|---|
|10|0|1000|
|20|1|1004|
|30|2|1008|
|40|3|1012|

These addresses are illustrative. If an `int` occupies four bytes, consecutive elements are four bytes apart.

The address of an array element can be obtained using:

```
&numbers[0]
&numbers[1]
```

## 9. Array and Pointer Relationship

In most expressions, an array name is converted into a pointer to its first element.

Example:

```
#include <stdio.h>

int main() {
    int numbers[] = {10, 20, 30};

    printf("%d\n", *numbers);
    printf("%d\n", *(numbers + 1));

    return 0;
}
```

**Output:**

```
10
20
```

Important:

- `numbers` usually converts to a pointer to the first element.
    
- `*numbers` accesses the first element.
    
- `*(numbers + 1)` accesses the second element.
    

An array is not itself a pointer. They are different types, even though array-to-pointer conversion occurs in many expressions.

## 10. Passing Arrays to Functions

Arrays can be passed to functions for processing.

```
#include <stdio.h>

void display(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
}

int main() {
    int numbers[] = {10, 20, 30, 40};

    display(numbers, 4);

    return 0;
}
```

Important:

- The function receives access to the original array elements.
    
- Changes made through the parameter can modify those elements.
    
- The array length is not automatically passed.
    
- Pass the length separately.
    

## 11. What Is a String in C?

A **string** in C is a sequence of characters terminated by a special null character:

```
\0
```

C does not have a built-in string data type like some other languages.

Instead, strings are represented using character arrays.

Example:

```
char name[] = "Mohit";
```

The actual array contains:

```
M  o  h  i  t  \0
```

The null terminator marks the end of the string.

## 12. Declaring and Initializing Strings

### Using a String Literal

```
char name[] = "Mohit";
```

The compiler automatically includes the terminating null character.

### Using Individual Characters

```
char name[] = {'M', 'o', 'h', 'i', 't', '\0'};
```

### Specifying Array Size

```
char name[20] = "Mohit";
```

The remaining elements are initialized to zero.

**Important:** A character array must have enough space for all characters plus the terminating `\0`.

## 13. Reading Strings

### Using scanf()

```
#include <stdio.h>

int main() {
    char name[30];

    printf("Enter your name: ");
    scanf("%29s", name);

    printf("Name: %s\n", name);

    return 0;
}
```

`%29s` limits the input to 29 characters, leaving room for the null terminator.

However, `scanf("%s", ...)` stops at whitespace, so it cannot read a complete sentence.

### Using fgets()

```
#include <stdio.h>

int main() {
    char sentence[100];

    printf("Enter a sentence: ");
    if (fgets(sentence, sizeof(sentence), stdin) != NULL) {
        printf("%s", sentence);
    }

    return 0;
}
```

`fgets()` can read spaces and limits the number of characters read based on the buffer size.

It may also store the newline character if there is room.

## 14. String Library Functions

The `string.h` header provides commonly used string functions.

|Function|Purpose|
|---|---|
|`strlen()`|Calculates string length|
|`strcpy()`|Copies a string|
|`strcat()`|Appends one string to another|
|`strcmp()`|Compares two strings|
|`strchr()`|Finds a character|
|`strstr()`|Finds a substring|

### A. strlen()

Returns the number of characters before the null terminator.

```
#include <stdio.h>
#include <string.h>

int main() {
    char name[] = "Cyber";

    printf("%zu\n", strlen(name));

    return 0;
}
```

Output:

```
5
```

### B. strcpy()

Copies a source string into a destination array.

```
#include <stdio.h>
#include <string.h>

int main() {
    char source[] = "Hello";
    char destination[20];

    strcpy(destination, source);

    printf("%s\n", destination);

    return 0;
}
```

The destination must have enough space for the source string and its null terminator.

### C. strcat()

Appends one string to another.

```
#include <stdio.h>
#include <string.h>

int main() {
    char first[30] = "Cyber";
    char second[] = "Security";

    strcat(first, second);

    printf("%s\n", first);

    return 0;
}
```

Output:

```
CyberSecurity
```

The destination must have enough unused capacity for the appended characters and null terminator.

### D. strcmp()

Compares two strings.

```
#include <stdio.h>
#include <string.h>

int main() {
    char first[] = "hello";
    char second[] = "hello";

    if (strcmp(first, second) == 0) {
        printf("Strings are equal\n");
    } else {
        printf("Strings are different\n");
    }

    return 0;
}
```

Output:

```
Strings are equal
```

`strcmp()` returns:

- `0` when strings are equal.
    
- A negative value when the first string compares less than the second.
    
- A positive value when the first string compares greater than the second.
    

## 15. Difference Between Character and String

|Character|String|
|---|---|
|Represents one character|Represents a sequence of characters|
|Usually stored in `char`|Stored in a character array|
|Uses single quotes|Uses double quotes|
|Example: `'A'`|Example: `"Hello"`|
|Does not require a null terminator by itself|Must end with `\0` to be a valid C string|

## 16. Common Array and String Errors

### A. Array Out-of-Bounds Access

```
int numbers[3] = {10, 20, 30};

printf("%d", numbers[5]);
```

Index `5` is outside the valid range.

This causes undefined behavior.

### B. Buffer Overflow

```
char name[5] = "Cyber";
```

This is incorrect because `"Cyber"` needs six bytes: five characters and one null terminator.

Correct:

```
char name[6] = "Cyber";
```

### C. Missing Null Terminator

```
char name[3] = {'C', 'A', 'T'};
```

This is not a valid null-terminated C string. Passing it to string functions can cause out-of-bounds reads.

### D. Modifying a String Literal

```
char *name = "Cyber";
```

Do not modify the characters through `name`. Modifying a string literal causes undefined behavior.

If modification is required:

```
char name[] = "Cyber";
name[0] = 'c';
```

## 17. Security Considerations

Arrays and strings are important in application security because incorrect memory handling can introduce vulnerabilities.

### A. Buffer Overflow

A buffer overflow occurs when a program writes beyond the allocated memory of a buffer.

Possible consequences include:

- Program crashes.
    
- Data corruption.
    
- Memory corruption.
    
- Potential security compromise.
    

### B. Input Validation

Validate user input before storing or processing it.

### C. Bounds Checking

Always ensure that array indexes remain within valid limits.

### D. Safe String Handling

Use functions and techniques that account for destination buffer capacity.

Remember: a function is not automatically safe simply because its name contains `safe`. Correct buffer sizing and validation are still necessary.

### E. Avoid Unsafe Functions

Avoid `gets()`. It cannot limit input length and was removed from the C standard.

## 18. Practical Exercises

Write C programs to perform these tasks:

1. Declare an integer array and display all its elements.
    
2. Calculate the sum and average of array elements.
    
3. Find the largest and smallest elements in an array.
    
4. Search for a number using linear search.
    
5. Reverse an array.
    
6. Create a two-dimensional matrix and display it.
    
7. Read a name using `fgets()`.
    
8. Calculate string length without using `strlen()`.
    
9. Compare two strings using `strcmp()`.
    
10. Create a function that accepts an array and returns its sum.
    

## 19. Key Takeaways

- Arrays store multiple elements of the same data type.
    
- Array indexing starts at zero.
    
- Array elements occupy contiguous memory locations.
    
- C supports one-dimensional and multidimensional arrays.
    
- Array names often convert to pointers to their first elements.
    
- Array lengths must generally be passed separately to functions.
    
- C strings are character arrays terminated by `\0`.
    
- `string.h` provides common string-handling functions.
    
- Array bounds and string buffer sizes must be checked carefully.
    
- Incorrect memory handling can lead to serious security vulnerabilities.
    

## 20. Related Notes

- [[Introduction to C]]
    
- [[C Variables and Data Types]]
    
- [[C Functions]]
    
- [[C Pointers]]
    
- [[C Memory Management]]
    
- [[Introduction to Data Structures]]
    
- [[Introduction to Secure Coding]]