> A dictionary is a built-in Python data structure that stores information as key-value pairs. It is useful when data needs to be identified and retrieved using meaningful keys instead of numeric positions.

## 1. What Is a Dictionary?

A Python dictionary is a mutable mapping that stores data in **key-value pairs**.

Each entry contains:

- **Key:** A unique identifier used to access a value.
    
- **Value:** The data associated with that key.
    

Example:

```
student = {
    "name": "Mohit",
    "age": 18,
    "course": "Cybersecurity"
}

print(student)
```

Output:

```
{'name': 'Mohit', 'age': 18, 'course': 'Cybersecurity'}
```

Here:

- `"name"` is a key.
    
- `"Mohit"` is its value.
    
- `"age"` is another key.
    
- `18` is its value.
    

## 2. Characteristics of Dictionaries

1. **Mutable:** Entries can be added, modified, and removed.
    
2. **Unique keys:** A dictionary cannot contain duplicate keys. Assigning an existing key replaces its value.
    
3. **Insertion ordered:** Python 3.7 and later guarantee that dictionaries preserve insertion order.
    
4. **Key-value structure:** Every entry associates a key with a value.
    
5. **Hashable keys:** Keys must be hashable, such as strings, integers, or tuples containing only hashable elements.
    
6. **Flexible values:** Values can be strings, numbers, lists, dictionaries, or other objects.
    

## 3. Creating Dictionaries

### Using Curly Braces

```
student = {
    "name": "Mohit",
    "age": 18,
    "course": "Cybersecurity"
}
```

### Creating an Empty Dictionary

```
student = {}
```

### Using the dict() Constructor

```
student = dict(name="Mohit", age=18)
```

### Dictionary with Different Data Types

```
data = {
    "username": "admin",
    "attempts": 5,
    "active": True,
    "roles": ["student", "analyst"]
}
```

## 4. Accessing Dictionary Values

### Using Square Brackets

```
student = {
    "name": "Mohit",
    "age": 18
}

print(student["name"])
```

Output:

```
Mohit
```

If the requested key does not exist, square-bracket access raises a `KeyError`.

### Using get()

```
print(student.get("name"))
print(student.get("email"))
```

Output:

```
Mohit
None
```

You can also provide a default value:

```
print(student.get("email", "Not available"))
```

Output:

```
Not available
```

**Difference:**

|Method|Missing key|
|---|---|
|`student["email"]`|Raises `KeyError`|
|`student.get("email")`|Returns `None`|
|`student.get("email", "Unknown")`|Returns `"Unknown"`|

## 5. Adding Dictionary Entries

Assign a value to a new key.

```
student = {
    "name": "Mohit"
}

student["age"] = 18
student["course"] = "Cybersecurity"

print(student)
```

Output:

```
{'name': 'Mohit', 'age': 18, 'course': 'Cybersecurity'}
```

## 6. Updating Dictionary Values

Assigning a value to an existing key updates it.

```
student = {
    "name": "Mohit",
    "age": 18
}

student["age"] = 19

print(student)
```

Output:

```
{'name': 'Mohit', 'age': 19}
```

### Using update()

```
student.update({
    "age": 20,
    "course": "Cybersecurity"
})

print(student)
```

`update()` adds new keys and replaces values for existing keys.

## 7. Removing Dictionary Entries

### Using del

```
student = {
    "name": "Mohit",
    "age": 18,
    "course": "Cybersecurity"
}

del student["age"]

print(student)
```

### Using pop()

Removes a specified key and returns its value.

```
age = student.pop("age", None)

print(age)
```

The default argument prevents a `KeyError` if the key is missing.

### Using popitem()

Removes and returns the most recently inserted key-value pair.

```
student = {
    "name": "Mohit",
    "age": 18
}

student.popitem()

print(student)
```

### Using clear()

Removes all entries.

```
student.clear()

print(student)
```

Output:

```
{}
```

## 8. Important Dictionary Methods

|Method|Purpose|
|---|---|
|`keys()`|Returns a view of all keys|
|`values()`|Returns a view of all values|
|`items()`|Returns a view of key-value pairs|
|`get()`|Retrieves a value safely|
|`update()`|Adds or updates entries|
|`pop()`|Removes a specified key|
|`popitem()`|Removes the last inserted pair|
|`clear()`|Removes all entries|
|`copy()`|Creates a shallow copy|
|`setdefault()`|Returns a value or inserts a default if the key is missing|

Example:

```
student = {
    "name": "Mohit",
    "age": 18,
    "course": "Cybersecurity"
}

print(student.keys())
print(student.values())
print(student.items())
```

## 9. Iterating Through Dictionaries

### Iterating Through Keys

```
student = {
    "name": "Mohit",
    "age": 18,
    "course": "Cybersecurity"
}

for key in student:
    print(key)
```

### Iterating Through Values

```
for value in student.values():
    print(value)
```

### Iterating Through Key-Value Pairs

```
for key, value in student.items():
    print(key, ":", value)
```

Output:

```
name : Mohit
age : 18
course : Cybersecurity
```

## 10. Checking Whether a Key Exists

Use the `in` operator.

```
student = {
    "name": "Mohit",
    "age": 18
}

if "name" in student:
    print("Key exists")
else:
    print("Key does not exist")
```

Important: Membership testing checks **keys**, not values.

```
print("name" in student)  # True
print("Mohit" in student) # False
```

To check values:

```
print("Mohit" in student.values())
```

## 11. Nested Dictionaries

A dictionary can contain another dictionary as a value.

```
students = {
    "student1": {
        "name": "Mohit",
        "age": 18
    },
    "student2": {
        "name": "Rahul",
        "age": 19
    }
}

print(students["student1"]["name"])
```

Output:

```
Mohit
```

Nested dictionaries are useful for representing structured records.

## 12. List of Dictionaries

A list can contain multiple dictionaries.

```
students = [
    {"name": "Mohit", "age": 18},
    {"name": "Rahul", "age": 19},
    {"name": "Aman", "age": 20}
]

for student in students:
    print(student["name"])
```

This structure is commonly used when working with collections of records.

## 13. Dictionary Comprehension

Dictionary comprehension creates a dictionary using a compact expression.

Syntax:

```
new_dictionary = {key: value for item in iterable}
```

Example:

```
squares = {
    number: number ** 2
    for number in range(1, 6)
}

print(squares)
```

Output:

```
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

With a condition:

```
even_squares = {
    number: number ** 2
    for number in range(1, 11)
    if number % 2 == 0
}

print(even_squares)
```

## 14. Dictionary Keys and Hashability

Dictionary keys must be hashable.

Valid examples:

```
data = {
    "name": "Mohit",
    10: "Ten",
    (1, 2): "Coordinate"
}
```

Invalid example:

```
data = {
    [1, 2]: "List"
}
```

This raises a `TypeError` because lists are mutable and unhashable.

A tuple can be used as a key only if all its elements are hashable.

## 15. Copying Dictionaries

### Shallow Copy

```
original = {
    "name": "Mohit",
    "skills": ["Python", "Linux"]
}

copied = original.copy()
```

A shallow copy creates a new outer dictionary, but nested mutable objects are still shared.

```
copied["skills"].append("Networking")

print(original["skills"])
```

Output:

```
['Python', 'Linux', 'Networking']
```

For independent copies of nested structures, use `copy.deepcopy()`:

```
import copy

copied = copy.deepcopy(original)
```

## 16. Dictionary Time Complexity

Typical average-case time complexity:

|Operation|Average Time Complexity|
|---|---|
|Access by key|O(1)|
|Insert an entry|O(1)|
|Update an entry|O(1)|
|Delete an entry|O(1)|
|Search for a key|O(1)|
|Iterate through entries|O(n)|

These are average-case expectations, not unconditional guarantees. Hash collisions and implementation details can affect performance.

## 17. Dictionary vs Other Data Structures

|Feature|List|Tuple|Dictionary|Set|
|---|---|---|---|---|
|Stores|Elements|Elements|Key-value pairs|Unique elements|
|Mutable|Yes|No|Yes|Yes|
|Access|Index|Index|Key|No positional indexing|
|Duplicates|Allowed|Allowed|Keys are unique|Not allowed|
|Main use|Ordered collection|Fixed collection|Key-based mapping|Uniqueness and membership|

## 18. Applications in Cybersecurity

Dictionaries are useful in security tools and automation.

### A. Tracking Failed Login Attempts

```
failed_attempts = {
    "192.168.1.10": 5,
    "192.168.1.20": 2,
    "192.168.1.30": 8
}

for ip, attempts in failed_attempts.items():
    if attempts >= 5:
        print(ip, "requires investigation")
```

### B. Counting Security Events

```
events = [
    "login_success",
    "login_failed",
    "login_failed",
    "file_access",
    "login_failed"
]

event_count = {}

for event in events:
    event_count[event] = event_count.get(event, 0) + 1

print(event_count)
```

### C. Storing HTTP Headers

```
headers = {
    "Content-Type": "application/json",
    "User-Agent": "ExampleClient",
    "Authorization": "Bearer example-token"
}
```

Never place real access tokens or credentials in public code or shared notes.

### D. Working with JSON

JSON objects are commonly represented as Python dictionaries after parsing.

```
import json

data = '{"username": "analyst", "role": "student"}'

parsed_data = json.loads(data)

print(parsed_data["username"])
```

## 19. Security Considerations

1. Never store plaintext passwords in dictionaries or application code.
    
2. Use appropriate password hashing mechanisms for password storage.
    
3. Do not treat a dictionary as an authentication or authorization security boundary.
    
4. Validate data received from external sources before processing it.
    
5. Be careful when handling untrusted input that can create excessive memory or processing demands.
    
6. Avoid exposing API tokens, session IDs, and other secrets in logs.
    

## 20. Practical Examples

### Example 1: Student Record

```
student = {
    "name": "Mohit",
    "course": "Cybersecurity",
    "year": 1
}

print("Name:", student["name"])
print("Course:", student["course"])
print("Year:", student["year"])
```

### Example 2: IP Address Event Counter

```
ip_addresses = [
    "192.168.1.10",
    "192.168.1.20",
    "192.168.1.10",
    "192.168.1.30",
    "192.168.1.10"
]

ip_count = {}

for ip in ip_addresses:
    ip_count[ip] = ip_count.get(ip, 0) + 1

for ip, count in ip_count.items():
    print(ip, ":", count)
```

### Example 3: Basic Event Classification

```
events = {
    4624: "Successful Logon",
    4625: "Failed Logon",
    4688: "Process Creation"
}

event_id = 4625

print(events.get(event_id, "Unknown Event"))
```

## 21. Practical Tasks

Complete these tasks using Python:

1. Create a dictionary containing your name, course, and programming skills.
    
2. Add a new key called `college`.
    
3. Update your course value.
    
4. Remove one entry using `pop()`.
    
5. Print all keys, values, and key-value pairs.
    
6. Create a dictionary that counts how many times each IP address appears in a list.
    
7. Build a small log-event counter that counts successful and failed login events.
    

**Challenge:** Modify the log-event counter so that it reports which event type occurred most frequently.

## 22. Key Takeaways

- A dictionary stores data as key-value pairs.
    
- Dictionary keys must be unique and hashable.
    
- Dictionaries are mutable and preserve insertion order in modern Python.
    
- Use square brackets or `get()` to retrieve values.
    
- Use `update()` to add or modify entries.
    
- Use `pop()` or `del` to remove entries.
    
- Use `items()` to iterate through keys and values together.
    
- Dictionaries are widely used in Python automation, JSON processing, and cybersecurity tools.
    

## 23. Related Notes

- [[Introduction to Data Structures]]
    
- [[Lists]]
    
- [[Tuples]]
    
- [[Sets]]
    
- [[Arrays]]
    
- [[Python Data Structures]]
    
- [[Python Programming]]
    
- [[JSON]]
    
- [[Python for Cybersecurity]]
    
- [[Log Analysis with Python]]
    
- [[04 - Programming]]