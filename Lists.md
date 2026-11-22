> Understand how lists store, organize, access, modify, and process collections of elements.

## 1. What Is a List?

A **list** is an ordered collection of elements that can store multiple values in a single variable.

In Python, lists are:

- Ordered: Elements maintain their sequence.
    
- Mutable: Elements can be changed.
    
- Dynamic: Elements can be added or removed.
    
- Indexed: Elements can be accessed using positions.
    
- Flexible: They can store different data types.
    

Example:

```
students = ["Mohit", "Rahul", "Amit"]

print(students)
```

Output:

```
['Mohit', 'Rahul', 'Amit']
```

## 2. Creating Lists

Lists are created using square brackets `[]`.

### A. List of Integers

```
numbers = [10, 20, 30, 40, 50]

print(numbers)
```

### B. List of Strings

```
names = ["Mohit", "Rahul", "Amit"]

print(names)
```

### C. Mixed Data Types

Python lists can contain different data types.

```
data = ["Mohit", 18, 85.5, True]

print(data)
```

### D. Empty List

```
items = []

print(items)
```

You can also use the `list()` constructor:

```
numbers = list((10, 20, 30))

print(numbers)
```

## 3. Accessing List Elements

Lists use zero-based indexing.

Example:

```
students = ["Mohit", "Rahul", "Amit", "Priya"]

print(students[0])
print(students[2])
```

Output:

```
Mohit
Amit
```

### Negative Indexing

Python supports negative indexing.

```
students = ["Mohit", "Rahul", "Amit", "Priya"]

print(students[-1])
print(students[-2])
```

Output:

```
Priya
Amit
```

`-1` represents the last element.

## 4. List Slicing

Slicing extracts a portion of a list.

Syntax:

```
list_name[start:end:step]
```

Example:

```
numbers = [10, 20, 30, 40, 50, 60]

print(numbers[1:4])
```

Output:

```
[20, 30, 40]
```

Other examples:

```
numbers = [10, 20, 30, 40, 50]

print(numbers[:3])
print(numbers[2:])
print(numbers[::2])
print(numbers[::-1])
```

## 5. Modifying List Elements

Python lists are mutable, meaning their elements can be changed after creation.

Example:

```
numbers = [10, 20, 30]

numbers[1] = 99

print(numbers)
```

Output:

```
[10, 99, 30]
```

You can also modify multiple elements using slicing:

```
numbers = [10, 20, 30, 40]

numbers[1:3] = [99, 88]

print(numbers)
```

Output:

```
[10, 99, 88, 40]
```

## 6. Adding Elements to Lists

Python provides several methods for adding elements.

### A. append()

Adds one element to the end of the list.

```
numbers = [10, 20, 30]

numbers.append(40)

print(numbers)
```

Output:

```
[10, 20, 30, 40]
```

### B. insert()

Adds an element at a specified position.

```
numbers = [10, 20, 30]

numbers.insert(1, 15)

print(numbers)
```

Output:

```
[10, 15, 20, 30]
```

### C. extend()

Adds elements from another iterable.

```
numbers = [10, 20]

numbers.extend([30, 40, 50])

print(numbers)
```

Output:

```
[10, 20, 30, 40, 50]
```

**Difference:**

- `append()` adds its argument as one element.
    
- `extend()` adds each element from the supplied iterable.
    

Example:

```
numbers = [10, 20]

numbers.append([30, 40])

print(numbers)
```

Output:

```
[10, 20, [30, 40]]
```

The nested list remains a single element.

## 7. Removing Elements from Lists

### A. remove()

Removes the first matching value.

```
numbers = [10, 20, 30, 20]

numbers.remove(20)

print(numbers)
```

Output:

```
[10, 30, 20]
```

### B. pop()

Removes and returns an element.

```
numbers = [10, 20, 30]

removed = numbers.pop()

print(removed)
print(numbers)
```

Output:

```
30
[10, 20]
```

You can also specify an index:

```
numbers = [10, 20, 30]

numbers.pop(1)

print(numbers)
```

### C. clear()

Removes all elements.

```
numbers = [10, 20, 30]

numbers.clear()

print(numbers)
```

Output:

```
[]
```

### D. del Statement

Deletes an element or a slice.

```
numbers = [10, 20, 30, 40]

del numbers[1]

print(numbers)
```

Output:

```
[10, 30, 40]
```

## 8. Searching in Lists

The `in` operator checks whether an element exists.

```
users = ["admin", "student", "guest"]

if "admin" in users:
    print("User found")
else:
    print("User not found")
```

The `index()` method returns the position of the first matching element.

```
users = ["admin", "student", "guest"]

print(users.index("student"))
```

Output:

```
1
```

If the value does not exist, `index()` raises a `ValueError`.

## 9. Useful List Functions and Methods

|Function or Method|Purpose|
|---|---|
|`len()`|Returns the number of elements|
|`max()`|Returns the largest element|
|`min()`|Returns the smallest element|
|`sum()`|Adds numeric elements|
|`sorted()`|Returns a new sorted list|
|`sort()`|Sorts the original list|
|`reverse()`|Reverses the original list|
|`count()`|Counts occurrences|
|`copy()`|Creates a shallow copy|

Examples:

```
numbers = [40, 10, 30, 20]

print(len(numbers))
print(max(numbers))
print(min(numbers))
print(sum(numbers))
```

Sorting:

```
numbers = [40, 10, 30, 20]

numbers.sort()

print(numbers)
```

Output:

```
[10, 20, 30, 40]
```

Using `sorted()`:

```
numbers = [40, 10, 30, 20]

result = sorted(numbers)

print(result)
print(numbers)
```

`sorted()` returns a new sorted list without changing the original list.

## 10. Traversing a List

Traversal means visiting each element.

### A. Using a for Loop

```
users = ["admin", "student", "guest"]

for user in users:
    print(user)
```

### B. Using an Index

```
users = ["admin", "student", "guest"]

for i in range(len(users)):
    print(users[i])
```

### C. Using enumerate()

`enumerate()` provides both the index and the value.

```
users = ["admin", "student", "guest"]

for index, user in enumerate(users):
    print(index, user)
```

## 11. Nested Lists

A list can contain other lists.

Example:

```
students = [
    ["Mohit", 85],
    ["Rahul", 90],
    ["Amit", 78]
]

print(students[0])
print(students[0][1])
```

Output:

```
['Mohit', 85]
85
```

Nested lists can represent:

- Tables.
    
- Matrices.
    
- Student records.
    
- Structured datasets.
    

## 12. List Comprehension

List comprehension provides a concise way to create lists.

Example:

```
numbers = [1, 2, 3, 4, 5]

squares = [number ** 2 for number in numbers]

print(squares)
```

Output:

```
[1, 4, 9, 16, 25]
```

With a condition:

```
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = [
    number for number in numbers
    if number % 2 == 0
]

print(even_numbers)
```

Output:

```
[2, 4, 6]
```

List comprehensions are useful for transforming and filtering data.

## 13. Copying Lists

Assigning one list variable to another does not create an independent copy.

Example:

```
first = [10, 20, 30]

second = first

second.append(40)

print(first)
print(second)
```

Both variables refer to the same list.

To create a shallow copy:

```
first = [10, 20, 30]

second = first.copy()

second.append(40)

print(first)
print(second)
```

Output:

```
[10, 20, 30]
[10, 20, 30, 40]
```

For nested lists, a shallow copy still shares references to inner objects. A deep copy may be needed when independent nested structures are required.

## 14. List Time Complexity

Typical time complexity for Python lists:

|Operation|Typical Complexity|
|---|---|
|Access by index|O(1)|
|Update by index|O(1)|
|Append|Amortized O(1)|
|Insert at beginning|O(n)|
|Insert in middle|O(n)|
|Remove by value|O(n)|
|Search by value|O(n)|
|Traversal|O(n)|
|Sorting|O(n log n)|

These are typical costs; exact behavior can depend on the operation and input.

## 15. Lists in Cybersecurity

Lists are useful for storing and processing security-related information.

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

### B. Failed Login Records

```
failed_attempts = [2, 5, 1, 8, 3]

for attempts in failed_attempts:
    if attempts >= 5:
        print("Review account activity:", attempts)
```

This is a simplified example. Real detection requires account identity, timestamps, and other context.

### C. Suspicious File Names

```
suspicious_files = [
    "unknown.exe",
    "payload.bin",
    "sample.js"
]

for file_name in suspicious_files:
    print(file_name)
```

A filename alone does not prove that a file is malicious.

### D. Port Collection

```
open_ports = [22, 80, 443, 8080]

for port in open_ports:
    print("Open port:", port)
```

These examples use sample data, not actual scan results.

## 16. Common List Errors

|Error|Explanation|
|---|---|
|IndexError|Accessing an index that does not exist|
|ValueError|Removing or searching for a missing value using methods that require it to exist|
|Unexpected nested list|Using `append()` when `extend()` was intended|
|Shared references|Assigning one list variable to another|
|Modifying while iterating|Can cause elements to be skipped or processing to behave unexpectedly|
|Incorrect sorting assumptions|`sort()` modifies the original list|

## 17. Key Takeaways

- A list stores multiple elements in an ordered collection.
    
- Python lists are mutable and dynamic.
    
- Indexing starts at zero.
    
- Slicing extracts a portion of a list.
    
- `append()`, `insert()`, and `extend()` add elements.
    
- `remove()`, `pop()`, `clear()`, and `del` remove elements.
    
- List comprehension creates lists concisely.
    
- Lists can contain nested lists and mixed data types.
    
- List operations have different time complexities.
    
- Lists are useful for log analysis and security automation.
    

## 18. Practical Tasks

### Task 1 — Student Records

Create a list containing five student names.

Perform these operations:

1. Display all names.
    
2. Add a new student.
    
3. Remove one student.
    
4. Sort the list.
    
5. Display the final list.
    

### Task 2 — IP Address Manager

Create a program that stores sample IP addresses.

Allow the user to:

1. Add an IP address.
    
2. Search for an IP address.
    
3. Remove an IP address.
    
4. Display all stored addresses.
    

### Task 3 — Failed Login Analyzer

Create a list of failed login counts:

```
failed_attempts = [2, 5, 1, 8, 3, 6]
```

Calculate:

- Total failed attempts.
    
- Highest failed attempt count.
    
- Number of entries with five or more failures.
    

### Challenge — Simple Security Indicator Manager

Create a program that manages sample indicators of compromise (IOCs).

The program should:

- Store indicators in a list.
    
- Add new indicators.
    
- Prevent duplicate entries.
    
- Search for an indicator.
    
- Remove an indicator.
    
- Display all indicators.
    

For a real security platform, use appropriate validation and consider a set for efficient membership checks.

## 19. Questions & Doubts

Use this section to record:

- What is a Python list?
    
- Why are lists mutable?
    
- What is the difference between `append()` and `extend()`?
    
- What is the difference between `remove()` and `pop()`?
    
- What is list comprehension?
    
- What is the difference between a shallow copy and a deep copy?
    

## Related Notes

- [[Introduction to Data Structures]]
    
- [[Arrays]]
    
- [[Strings]]
    
- [[Tuples]]
    
- [[Dictionaries]]
    
- [[Sets]]
    
- [[Stacks and Queues]]
    
- [[Linked Lists]]
    
- [[Python Programming]]
    
- [[Python Data Structures]]
    
- [[Python for Cybersecurity]]