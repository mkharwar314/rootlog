> Understand how arrays store multiple elements in indexed positions and how they are accessed, modified, and processed.

## 1. What Is an Array?

An **array** is a data structure that stores multiple elements in an ordered collection.

Each element is associated with an index, which identifies its position.

Arrays are commonly used to:

- Store multiple values.
    
- Organize related information.
    
- Access elements using indexes.
    
- Process collections using loops.
    
- Implement other data structures and algorithms.
    

### Example

Imagine storing five student marks.

```
Index:     0    1    2    3    4
Value:    75   82   90   68   88
```

The first element is at index `0`, and the last element is at index `4`.

## 2. Array Indexing

**Indexing** means accessing an element using its position.

Most commonly used programming languages use zero-based indexing for arrays.

Example in Python:

```
marks = [75, 82, 90, 68, 88]

print(marks[0])
print(marks[2])
print(marks[4])
```

Output:

```
75
90
88
```

### Important Points

- First index = `0`
    
- Second index = `1`
    
- Third index = `2`
    
- Last index = `n - 1`
    

Here, `n` represents the number of elements.

Accessing an invalid index may cause an error.

```
marks = [75, 82, 90]

print(marks[5])
```

This raises an `IndexError` because index `5` does not exist.

## 3. Types of Arrays

### A. One-Dimensional Array

A one-dimensional array stores elements in a single sequence.

```
[10, 20, 30, 40, 50]
```

Python example:

```
numbers = [10, 20, 30, 40, 50]

print(numbers[2])
```

### B. Two-Dimensional Array

A two-dimensional array organizes elements into rows and columns.

```
10  20  30
40  50  60
70  80  90
```

Python example:

```
matrix = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

print(matrix[1][2])
```

Output:

```
60
```

The first index selects the row, and the second selects the column.

### C. Multidimensional Array

A multidimensional array has more than two dimensions.

These structures are useful in:

- Scientific computing.
    
- Image processing.
    
- Machine learning.
    
- Mathematical simulations.
    

## 4. Array Operations

Common operations include:

|Operation|Meaning|
|---|---|
|Traversal|Visiting every element|
|Access|Retrieving an element|
|Insertion|Adding an element|
|Deletion|Removing an element|
|Searching|Finding an element|
|Updating|Changing an element|
|Sorting|Arranging elements|

### A. Traversal

Traversal means visiting each element.

```
numbers = [10, 20, 30, 40]

for number in numbers:
    print(number)
```

### B. Accessing

```
numbers = [10, 20, 30, 40]

print(numbers[1])
```

Output:

```
20
```

### C. Updating

```
numbers = [10, 20, 30]

numbers[1] = 99

print(numbers)
```

Output:

```
[10, 99, 30]
```

### D. Insertion

Python lists support insertion at a specified position.

```
numbers = [10, 20, 30]

numbers.insert(1, 15)

print(numbers)
```

Output:

```
[10, 15, 20, 30]
```

### E. Deletion

```
numbers = [10, 20, 30, 40]

numbers.remove(30)

print(numbers)
```

Output:

```
[10, 20, 40]
```

### F. Searching

```
numbers = [10, 20, 30, 40]

target = 30

if target in numbers:
    print("Element found")
else:
    print("Element not found")
```

## 5. Arrays in Different Programming Languages

Array behavior differs between programming languages.

### A. Python

Python's built-in `list` is a dynamic sequence. It is often used like an array, but it is not the same as a traditional fixed-size array.

```
numbers = [10, 20, 30, 40]

print(numbers[0])

numbers.append(50)

print(numbers)
```

Python also provides the `array` module for typed arrays.

```
from array import array

numbers = array('i', [10, 20, 30])

numbers.append(40)

print(numbers)
```

### B. C Programming

C provides fixed-size arrays.

```
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};

    printf("%d\n", numbers[0]);

    return 0;
}
```

Important characteristics:

- The array has a declared element type.
    
- Its size is fixed after creation for this example.
    
- Elements are stored contiguously.
    
- Array indexing begins at zero.
    

### C. JavaScript

JavaScript provides dynamic `Array` objects.

```
let numbers = [10, 20, 30, 40];

console.log(numbers[0]);

numbers.push(50);

console.log(numbers);
```

JavaScript arrays can grow or shrink dynamically.

## 6. Memory Representation

In a traditional array, elements are stored in contiguous memory locations.

Example:

```
Memory addresses

1000 → 10
1004 → 20
1008 → 30
1012 → 40
1016 → 50
```

The addresses are illustrative. Actual memory spacing depends on the element type and platform.

Because elements occupy consecutive locations, an array can calculate an element's address using its index.

For a conventional array:

[  
Address(A[i]) = BaseAddress + (i \times ElementSize)  
]

Where:

- `BaseAddress` is the starting memory address.
    
- `i` is the index.
    
- `ElementSize` is the size of each element in bytes.
    

This is why accessing an array element by index is generally O(1).

## 7. Time Complexity of Array Operations

The following table describes common complexity for a conventional array or dynamic array under typical assumptions.

|Operation|Typical Time Complexity|
|---|---|
|Access by index|O(1)|
|Update by index|O(1)|
|Linear search|O(n)|
|Traversal|O(n)|
|Insert at beginning|O(n)|
|Delete from beginning|O(n)|
|Append to dynamic array|Amortized O(1)|

**Why does insertion at the beginning take O(n)?**

Existing elements usually need to be shifted to make space.

**Why is append amortized O(1)?**

A dynamic array sometimes needs to allocate a larger storage area and copy existing elements. However, across many append operations, the average cost per append is generally constant.

## 8. Advantages of Arrays

1. Fast access using indexes.
    
2. Simple structure and implementation.
    
3. Efficient traversal.
    
4. Contiguous storage in traditional arrays improves memory locality.
    
5. Useful for implementing other algorithms and data structures.
    

## 9. Disadvantages of Arrays

1. Traditional fixed-size arrays cannot grow beyond their allocated capacity.
    
2. Inserting elements in the middle may require shifting.
    
3. Deleting elements may require shifting.
    
4. Searching an unsorted array generally takes O(n).
    
5. Some languages restrict array elements to a single declared type.
    

## 10. Arrays in Cybersecurity

Arrays are useful in many security-related programs.

### A. IP Address Collection

```
ip_addresses = [
    "192.168.1.10",
    "192.168.1.20",
    "10.0.0.5"
]

for ip in ip_addresses:
    print(ip)
```

This example stores sample IP addresses.

### B. Failed Login Attempts

```
failed_attempts = [2, 5, 1, 8, 3]

for attempts in failed_attempts:
    if attempts >= 5:
        print("Review this account")
```

This is a simplified demonstration, not a complete detection system.

### C. File Hash Collection

```
hashes = [
    "abc123",
    "def456",
    "ghi789"
]

for file_hash in hashes:
    print(file_hash)
```

A real integrity-monitoring application would calculate and validate actual cryptographic hashes.

### D. Network Scan Results

An array or list can store:

- Discovered IP addresses.
    
- Open ports.
    
- Service names.
    
- Scan results.
    

## 11. Common Array Errors

|Error|Explanation|
|---|---|
|Index out of range|Accessing a position that does not exist|
|Incorrect index|Using the wrong element position|
|Off-by-one error|Incorrect loop boundary|
|Uninitialized values|Reading values before assigning them in languages where this is possible|
|Incorrect dimensions|Accessing a multidimensional array incorrectly|

Example of an off-by-one error:

```
numbers = [10, 20, 30]

for i in range(0, 4):
    print(numbers[i])
```

The loop tries to access index `3`, which does not exist.

Correct version:

```
numbers = [10, 20, 30]

for i in range(len(numbers)):
    print(numbers[i])
```

## 12. Key Takeaways

- An array stores multiple elements in an ordered collection.
    
- Array indexing commonly begins at zero.
    
- One-dimensional arrays use a single index.
    
- Two-dimensional arrays use row and column indexes.
    
- Traditional arrays store elements in contiguous memory.
    
- Access by index is generally O(1).
    
- Searching an unsorted array is generally O(n).
    
- Insertion and deletion can require shifting elements.
    
- Python lists and JavaScript arrays are dynamic, while C arrays commonly have fixed declared sizes.
    

## 13. Practical Tasks

### Task 1 — Store Student Marks

Create a Python list containing marks of five students.

Print:

- All marks.
    
- First student's marks.
    
- Last student's marks.
    

### Task 2 — Find the Highest Mark

Write a program that finds the highest value in an array without using the built-in `max()` function.

### Task 3 — Search for an IP Address

Create a list of five sample IP addresses.

Ask the user to enter an IP address and check whether it exists in the list.

### Challenge — Failed Login Analyzer

Create a program that:

1. Stores failed login counts for five sample accounts.
    
2. Finds the highest failed login count.
    
3. Calculates the total failed login count.
    
4. Displays accounts with five or more failed attempts.
    

Use sample data only. A real detection system needs additional context before deciding whether activity is malicious.

## 14. Questions & Doubts

Use this section to record:

- Why does array indexing begin at zero in many languages?
    
- Why is accessing an array element generally O(1)?
    
- What is the difference between an array and a Python list?
    
- Why can insertion at the beginning require O(n)?
    
- What is a multidimensional array?
    

## Related Notes

- [[Introduction to Data Structures]]
    
- [[Lists]]
    
- [[Strings]]
    
- [[Stacks and Queues]]
    
- [[Linked Lists]]
    
- [[Trees and Graphs]]
    
- [[Hash Tables]]
    
- [[Algorithms]]
    
- [[Time and Space Complexity]]
    
- [[Python Programming]]
    
- [[C Programming]]