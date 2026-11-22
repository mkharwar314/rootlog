> Understand how data is organized, stored, accessed, and modified so programs can process information efficiently.

## 1. What Are Data Structures?

A **data structure** is a way of organizing and storing data in a computer so that it can be accessed, modified, and processed efficiently.

Programs often work with large amounts of information. Without proper organization, managing that information becomes difficult.

Data structures help programmers:

- Store multiple values.
    
- Organize related information.
    
- Search for specific data.
    
- Insert and delete elements.
    
- Process information efficiently.
    
- Build complex applications.
    

### Example

Suppose you want to store the marks of five students.

Without a data structure, you might create separate variables:

```
mark1 = 75
mark2 = 82
mark3 = 90
mark4 = 68
mark5 = 88
```

Using a list:

```
marks = [75, 82, 90, 68, 88]
```

The list makes it easier to access and process all five values.

## 2. Why Are Data Structures Important?

Data structures influence the performance and design of software.

Consider a program that stores thousands of usernames.

It may need to:

- Find a particular username.
    
- Add a new username.
    
- Remove an existing username.
    
- Check whether a username already exists.
    

The choice of data structure affects how efficiently these operations can be performed.

### Main Advantages

1. **Organization:** Keeps data structured.
    
2. **Efficiency:** Can reduce processing time.
    
3. **Reusability:** Supports reusable algorithms.
    
4. **Scalability:** Helps applications manage growing datasets.
    
5. **Maintainability:** Makes complex programs easier to develop and understand.
    

## 3. Types of Data Structures

Data structures can be classified in different ways.

### A. Primitive Data Structures

Primitive data types are basic types provided by a programming language.

Examples:

- Integer
    
- Float
    
- Character
    
- Boolean
    

Example:

```
age = 18
price = 99.5
name = "Student"
is_active = True
```

### B. Non-Primitive Data Structures

Non-primitive data structures organize collections of values.

Examples:

- Arrays
    
- Linked lists
    
- Stacks
    
- Queues
    
- Trees
    
- Graphs
    
- Hash tables
    

These structures can store and manage larger collections of information.

## 4. Linear Data Structures

A **linear data structure** organizes elements in a sequence.

Each element has a logical position in the sequence.

Common examples include:

|Data Structure|Description|
|---|---|
|Array|Stores elements in indexed positions|
|Linked List|Stores elements in connected nodes|
|Stack|Follows Last In, First Out|
|Queue|Follows First In, First Out|

### Example: Linear Organization

```
10 → 20 → 30 → 40 → 50
```

The elements are arranged sequentially.

## 5. Non-Linear Data Structures

A **non-linear data structure** organizes data in hierarchical or interconnected relationships rather than a single sequence.

Common examples include:

- Trees
    
- Graphs
    

### Example: Tree

```
        A
       / \
      B   C
     / \
    D   E
```

A tree contains nodes connected through parent-child relationships.

### Example: Graph

```
A ----- B
|       |
|       |
C ----- D
```

A graph contains vertices and edges representing relationships.

## 6. Static and Dynamic Data Structures

### A. Static Data Structures

A static data structure has a fixed size or capacity determined when it is created.

Example: A fixed-size array in C.

```
int numbers[5] = {10, 20, 30, 40, 50};
```

This array has space for five integers.

### B. Dynamic Data Structures

Dynamic data structures can grow or shrink during program execution.

Examples:

- Linked lists
    
- Dynamic arrays
    
- Trees
    
- Graphs
    

Python lists are dynamically resizable.

```
numbers = [10, 20, 30]

numbers.append(40)

print(numbers)
```

Output:

```
[10, 20, 30, 40]
```

**Important:** Static versus dynamic describes size or allocation behavior. Linear versus non-linear describes how elements are logically organized. These are different classification dimensions.

## 7. Common Operations on Data Structures

Most data structures support several fundamental operations.

|Operation|Meaning|
|---|---|
|Traversal|Visiting elements|
|Insertion|Adding an element|
|Deletion|Removing an element|
|Searching|Finding an element|
|Sorting|Arranging elements|
|Updating|Modifying an element|
|Accessing|Retrieving an element|

### Example

```
numbers = [10, 20, 30]

# Insertion
numbers.append(40)

# Accessing
print(numbers[0])

# Updating
numbers[1] = 25

# Deletion
numbers.remove(30)

# Traversal
for number in numbers:
    print(number)
```

## 8. Introduction to Time Complexity

Time complexity describes how the number of operations performed by an algorithm grows as the input size increases.

It is commonly expressed using **Big O notation**.

Examples:

|Complexity|Name|General Meaning|
|---|---|---|
|O(1)|Constant|Does not grow with input size|
|O(log n)|Logarithmic|Grows slowly as input increases|
|O(n)|Linear|Grows proportionally to input size|
|O(n log n)|Linearithmic|Common in efficient sorting algorithms|
|O(n²)|Quadratic|Often occurs with two nested loops|

### Example: Linear Search

```
numbers = [10, 20, 30, 40, 50]

target = 40

for number in numbers:
    if number == target:
        print("Found")
        break
```

In the worst case, the algorithm may examine every element.

Its time complexity is O(n).

## 9. Data Structures in Cybersecurity

Data structures are widely used in cybersecurity tools and applications.

### A. Hash Tables

Hash tables support efficient key-based lookups.

They can be used for:

- Storing user account information.
    
- Tracking IP addresses.
    
- Maintaining lookup tables.
    
- Caching security information.
    

### B. Lists and Arrays

Lists and arrays can store:

- Network scan results.
    
- Log entries.
    
- File paths.
    
- Suspicious indicators.
    

### C. Queues

Queues are useful for:

- Processing incoming log events.
    
- Handling network packets.
    
- Scheduling security tasks.
    
- Managing background jobs.
    

### D. Trees

Trees can represent:

- File-system structures.
    
- Directory hierarchies.
    
- Certificate relationships.
    
- Parsing structures.
    

### E. Graphs

Graphs can represent:

- Network connections.
    
- Relationships between user accounts.
    
- Attack paths.
    
- Dependencies between software components.
    

## 10. Choosing the Right Data Structure

The best data structure depends on what the program needs to do.

|Requirement|Possible Data Structure|
|---|---|
|Store an ordered collection|Array or List|
|Fast key-based lookup|Hash Table|
|Track recent items|Stack|
|Process tasks in arrival order|Queue|
|Represent hierarchical information|Tree|
|Represent network relationships|Graph|

No single data structure is best for every problem.

Consider:

- How much data must be stored?
    
- How frequently will data be searched?
    
- How often will elements be inserted or deleted?
    
- Does the order of elements matter?
    
- Is the data hierarchical or interconnected?
    

## 11. Common Mistakes

|Mistake|Explanation|
|---|---|
|Choosing a structure without considering operations|Can reduce performance|
|Confusing arrays and linked lists|They have different storage and access behavior|
|Ignoring memory usage|Some structures require additional memory|
|Using nested loops unnecessarily|Can increase time complexity|
|Assuming every lookup is O(1)|Performance depends on the structure and implementation|
|Ignoring edge cases|Empty collections and duplicate values can cause errors|

## 12. Key Takeaways

- A data structure organizes and stores information.
    
- Primitive types represent basic values.
    
- Non-primitive structures manage collections of data.
    
- Linear structures organize elements sequentially.
    
- Non-linear structures represent hierarchical or interconnected relationships.
    
- Static and dynamic describe size or allocation behavior.
    
- Common operations include insertion, deletion, searching, and traversal.
    
- Big O notation helps describe algorithm efficiency.
    
- Choosing the right data structure is important when developing security tools.
    

## 13. Practical Tasks

### Task 1 — Create a List

Create a Python list containing five IP addresses.

```
ip_addresses = [
    "192.168.1.1",
    "192.168.1.2",
    "192.168.1.3",
    "10.0.0.1",
    "10.0.0.2"
]

print(ip_addresses)
```

### Task 2 — Search for an IP Address

Write a program that checks whether a given IP address exists in your list.

### Task 3 — Modify a Collection

Write a program that:

1. Creates a list of five usernames.
    
2. Adds a new username.
    
3. Removes one username.
    
4. Displays the updated list.
    

### Challenge — Suspicious IP Tracker

Create a program that stores suspicious IP addresses and:

1. Adds new addresses.
    
2. Checks whether an address already exists.
    
3. Removes an address.
    
4. Displays all stored addresses.
    

For this exercise, use sample addresses only.

## 14. Questions & Doubts

Use this section to record:

- What is a data structure?
    
- What is the difference between linear and non-linear structures?
    
- What is the difference between static and dynamic structures?
    
- Why is time complexity important?
    
- Which data structure is suitable for storing network connections?
    

## Related Notes

- [[Programming Fundamentals]]
    
- [[Data Structures]]
    
- [[Arrays]]
    
- [[Lists]]
    
- [[Stacks and Queues]]
    
- [[Trees and Graphs]]
    
- [[Hash Tables]]
    
- [[Algorithms]]
    
- [[Time and Space Complexity]]
    
- [[Python for Cybersecurity]]