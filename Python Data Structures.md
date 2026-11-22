## 1. Introduction

Data structures are ways of organizing, storing, and managing data so that it can be accessed and modified efficiently.

Python provides built-in data structures that help programmers work with collections of information.

The four major built-in collection types are:

1. List
    
2. Tuple
    
3. Set
    
4. Dictionary
    

### Example

```
student = ["Mohit", 18, "Cybersecurity"]

print(student)
```

Output:

```
['Mohit', 18, 'Cybersecurity']
```

Here, a list stores multiple pieces of related information in one variable.

## 2. Why Are Data Structures Important?

Data structures are important because they help programmers:

- Organize large amounts of information.
    
- Store related values together.
    
- Search and retrieve data.
    
- Insert, update, and delete information.
    
- Reduce unnecessary processing.
    
- Build efficient applications.
    

In cybersecurity, data structures are used for storing IP addresses, analyzing logs, tracking users, managing security events, and processing network information.

## 3. Types of Python Data Structures

|Data Structure|Ordered|Mutable|Allows Duplicates|
|---|---|---|---|
|List|Yes|Yes|Yes|
|Tuple|Yes|No|Yes|
|Set|No guaranteed order|Yes|No|
|Dictionary|Yes (insertion order)|Yes|Keys must be unique|

Note: Python dictionaries preserve insertion order in modern Python versions. Sets do not provide a guaranteed positional order.

## 4. Lists

A list is an ordered and mutable collection that can store multiple values.

Lists are created using square brackets `[]`.

Example:

```
tools = ["Nmap", "Wireshark", "Burp Suite"]

print(tools)
```

Output:

```
['Nmap', 'Wireshark', 'Burp Suite']
```

### Accessing List Elements

List indexing starts from zero.

```
tools = ["Nmap", "Wireshark", "Burp Suite"]

print(tools[0])
print(tools[1])
```

Output:

```
Nmap
Wireshark
```

### Modifying List Elements

```
tools = ["Nmap", "Wireshark"]

tools[1] = "Burp Suite"

print(tools)
```

Output:

```
['Nmap', 'Burp Suite']
```

### Common List Methods

|Method|Purpose|
|---|---|
|`append()`|Adds an element at the end|
|`insert()`|Adds an element at a specified position|
|`remove()`|Removes the first matching value|
|`pop()`|Removes and returns an element|
|`sort()`|Sorts the list|
|`reverse()`|Reverses the list|
|`index()`|Finds the position of a value|
|`count()`|Counts occurrences of a value|
|`clear()`|Removes all elements|

Example:

```
ports = [80, 443, 22]

ports.append(8080)
ports.remove(22)

print(ports)
```

Output:

```
[80, 443, 8080]
```

Detailed topic: [[Lists]]

## 5. Tuples

A tuple is an ordered and immutable collection.

Tuples are created using parentheses `()`.

Example:

```
server = ("192.168.1.10", 443, "HTTPS")

print(server)
```

Output:

```
('192.168.1.10', 443, 'HTTPS')
```

### Accessing Tuple Elements

```
server = ("192.168.1.10", 443, "HTTPS")

print(server[0])
print(server[1])
```

Output:

```
192.168.1.10
443
```

### Tuple Immutability

Once a tuple is created, its elements cannot be reassigned.

```
ports = (80, 443, 22)

# This raises TypeError:
# ports[0] = 8080
```

### Tuple Unpacking

```
server = ("192.168.1.10", 443)

ip, port = server

print(ip)
print(port)
```

Output:

```
192.168.1.10
443
```

Detailed topic: [[Tuples]]

## 6. Sets

A set is a mutable collection of unique elements.

Sets are created using curly braces `{}` or the `set()` constructor.

Example:

```
ports = {80, 443, 22, 80}

print(ports)
```

Output contains each value only once:

```
{80, 443, 22}
```

The displayed order may vary.

### Adding Elements

```
ports = {80, 443}

ports.add(8080)

print(ports)
```

### Removing Elements

```
ports = {80, 443, 22}

ports.remove(22)

print(ports)
```

`remove()` raises `KeyError` if the element does not exist. `discard()` does not raise an error for a missing element.

### Set Operations

Sets support mathematical operations.

```
team_a = {"Nmap", "Wireshark", "Burp"}
team_b = {"Burp", "Metasploit", "Nmap"}

print(team_a | team_b)
print(team_a & team_b)
print(team_a - team_b)
```

The operations are:

|Operator|Meaning|
|---|---|
|`|`|Union: elements from both sets|
|`&`|Intersection: common elements|
|`-`|Difference: elements in the first set but not the second|
|`^`|Symmetric difference: elements in either set, but not both|

### Cybersecurity Use Case

Sets can help identify unique IP addresses from logs.

```
ip_addresses = [
    "192.168.1.10",
    "192.168.1.20",
    "192.168.1.10",
    "192.168.1.30"
]

unique_ips = set(ip_addresses)

print(unique_ips)
```

Detailed topic: [[Sets]]

## 7. Dictionaries

A dictionary stores information as key-value pairs.

Dictionaries are created using curly braces `{}`.

Example:

```
student = {
    "name": "Mohit",
    "course": "Cybersecurity",
    "year": 1
}

print(student)
```

### Accessing Values

```
student = {
    "name": "Mohit",
    "course": "Cybersecurity"
}

print(student["name"])
print(student["course"])
```

Output:

```
Mohit
Cybersecurity
```

You can also use `get()` to retrieve a value without raising `KeyError` when a key is missing.

```
print(student.get("age", "Not available"))
```

### Adding and Updating Values

```
student = {
    "name": "Mohit",
    "course": "Cybersecurity"
}

student["year"] = 1
student["course"] = "Computer Science"

print(student)
```

### Removing Values

```
student = {
    "name": "Mohit",
    "course": "Cybersecurity",
    "year": 1
}

student.pop("year")

print(student)
```

### Common Dictionary Methods

|Method|Purpose|
|---|---|
|`keys()`|Returns dictionary keys|
|`values()`|Returns dictionary values|
|`items()`|Returns key-value pairs|
|`get()`|Retrieves a value safely|
|`update()`|Updates dictionary entries|
|`pop()`|Removes a specified key|
|`clear()`|Removes all entries|

Detailed topic: [[Dictionaries]]

## 8. Nested Data Structures

A nested data structure contains another data structure inside it.

Example:

```
users = {
    "user1": {
        "name": "Mohit",
        "role": "Student"
    },
    "user2": {
        "name": "Rahul",
        "role": "Developer"
    }
}

print(users["user1"]["name"])
```

Output:

```
Mohit
```

Nested structures are useful for representing complex information.

## 9. List Comprehensions

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

### List Comprehension With Conditions

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

## 10. Choosing the Right Data Structure

Different problems require different data structures.

|Requirement|Suitable Structure|
|---|---|
|Store an ordered collection that can change|List|
|Store a fixed collection of values|Tuple|
|Store unique values|Set|
|Store key-value information|Dictionary|
|Remove duplicate values|Set|
|Represent structured records|Dictionary|
|Store a sequence of events|List|

Example:

```
# List of security events
events = ["LOGIN", "LOGOUT", "LOGIN"]

# Set of unique IP addresses
ips = {"192.168.1.10", "192.168.1.20"}

# Dictionary containing user details
user = {
    "username": "student",
    "role": "analyst"
}
```

## 11. Basic Data Structure Performance

The time required for operations depends on the data structure, operation, and implementation.

Typical average-case performance:

|Operation|List|Set|Dictionary|
|---|---|---|---|
|Access by index|O(1)|Not supported|Not applicable|
|Search by value/key|O(n)|O(1)|O(1) by key|
|Append or insert|O(1) amortized for append; O(n) for arbitrary insertion|O(1) average for add|O(1) average for insertion|
|Delete by value/key|O(n)|O(1) average|O(1) average by key|

These are typical complexities, not guarantees for every situation. Hash collisions, resizing, and implementation details can affect performance.

Detailed topic: [[Time and Space Complexity]]

## 12. Data Structures in Cybersecurity

Data structures are widely used in security tools.

### A. Storing Network Ports

```
open_ports = [22, 80, 443, 8080]

for port in open_ports:
    print("Open port:", port)
```

### B. Tracking Unique IP Addresses

```
ips = [
    "192.168.1.10",
    "192.168.1.20",
    "192.168.1.10"
]

unique_ips = set(ips)

print(unique_ips)
```

### C. Storing User Information

```
user = {
    "username": "analyst",
    "role": "security",
    "active": True
}

print(user["username"])
```

### D. Counting Security Events

```
events = [
    "LOGIN_FAILED",
    "LOGIN_SUCCESS",
    "LOGIN_FAILED",
    "LOGIN_FAILED"
]

event_counts = {}

for event in events:
    event_counts[event] = event_counts.get(event, 0) + 1

print(event_counts)
```

Output:

```
{
    'LOGIN_FAILED': 3,
    'LOGIN_SUCCESS': 1
}
```

This basic technique can be used to summarize events in a log-analysis program.

## 13. Common Mistakes

### Mistake 1: Accessing an Invalid List Index

```
numbers = [10, 20, 30]

# This raises IndexError:
# print(numbers[5])
```

### Mistake 2: Modifying a Tuple

```
values = (10, 20, 30)

# This raises TypeError:
# values[0] = 100
```

### Mistake 3: Using a Missing Dictionary Key

```
user = {"name": "Mohit"}

# This raises KeyError:
# print(user["age"])

# Safer alternative:
print(user.get("age", "Unknown"))
```

### Mistake 4: Creating an Empty Set Incorrectly

```
empty_set = set()
empty_dictionary = {}

print(type(empty_set))
print(type(empty_dictionary))
```

Output:

```
<class 'set'>
<class 'dict'>
```

An empty pair of curly braces creates a dictionary, not a set.

## 14. Practical Exercises

### Exercise 1: Security Tools List

Create a list containing five cybersecurity tools.

Perform these operations:

1. Display the list.
    
2. Add a new tool.
    
3. Remove one tool.
    
4. Display the final list.
    

### Exercise 2: Unique IP Addresses

Create a list containing duplicate IP addresses.

Convert it into a set and display the unique addresses.

### Exercise 3: User Dictionary

Create a dictionary containing:

- Username
    
- Role
    
- Department
    
- Account status
    

Display each value separately.

### Exercise 4: Event Counter

Create a list containing at least five security events.

Use a dictionary to count how many times each event occurs.

### Exercise 5: Nested Dictionary

Create a dictionary containing information about three users.

Each user should have:

- Username
    
- Role
    
- Active status
    

Access and display the role of the second user.

### Exercise 6: Mini Security Log Analyzer

Create a list of sample log entries:

```
logs = [
    "LOGIN_SUCCESS",
    "LOGIN_FAILED",
    "LOGIN_FAILED",
    "FILE_ACCESS",
    "LOGIN_SUCCESS",
    "LOGIN_FAILED"
]
```

Your program should:

1. Count each event type.
    
2. Store the counts in a dictionary.
    
3. Display the total number of failed logins.
    
4. Display the unique event types using a set.
    

## 15. Key Takeaways

- Data structures organize and manage information.
    
- Lists are ordered and mutable.
    
- Tuples are ordered and immutable.
    
- Sets store unique elements.
    
- Dictionaries store key-value pairs.
    
- Nested structures represent complex information.
    
- List comprehensions provide concise list creation.
    
- Choosing the correct data structure can improve performance.
    
- Cybersecurity applications use data structures for logs, IP addresses, users, and security events.
    

## 16. Related Topics

- [[Introduction to Data Structures]]
    
- [[Arrays]]
    
- [[Strings]]
    
- [[Lists]]
    
- [[Tuples]]
    
- [[Dictionaries]]
    
- [[Sets]]
    
- [[Stacks and Queues]]
    
- [[Linked Lists]]
    
- [[Trees and Graphs]]
    
- [[Hash Tables]]
    
- [[Time and Space Complexity]]
    
- [[Python for Cybersecurity]]
    
- [[Log Analysis with Python]]