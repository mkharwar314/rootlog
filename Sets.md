> A set is a built-in Python data structure used to store unique elements. It is useful for removing duplicates, performing membership tests, and carrying out mathematical set operations.

## 1. What Is a Set?

A set is an unordered collection of unique elements.

Example:

```
numbers = {10, 20, 30, 40}

print(numbers)
```

Output (order may vary):

```
{10, 20, 30, 40}
```

Sets automatically remove duplicate values.

```
numbers = {10, 20, 20, 30, 30}

print(numbers)
```

Output:

```
{10, 20, 30}
```

## 2. Characteristics of Sets

1. **Unique elements:** Duplicate values are automatically removed.
    
2. **Unordered:** Sets do not guarantee a particular element position.
    
3. **Mutable:** Elements can be added or removed.
    
4. **No indexing:** Elements cannot be accessed using positions such as `set[0]`.
    
5. **Hashable elements:** Elements must be hashable, such as strings, integers, or suitable tuples.
    
6. **Dynamic size:** Elements can be added or removed after creation.
    

## 3. Creating Sets

### Using Curly Braces

```
languages = {"Python", "C", "JavaScript"}

print(languages)
```

### Using set()

```
numbers = set([10, 20, 30, 40])

print(numbers)
```

### Creating an Empty Set

```
empty_set = set()
```

Important:

```
empty_dictionary = {}
empty_set = set()
```

`{}` creates an empty dictionary, not an empty set.

## 4. Removing Duplicate Values

Sets are commonly used to remove duplicates from a collection.

```
numbers = [10, 20, 20, 30, 30, 40]

unique_numbers = set(numbers)

print(unique_numbers)
```

Output (order may vary):

```
{10, 20, 30, 40}
```

To convert it back into a list:

```
unique_list = list(unique_numbers)
```

Note: Converting a list to a set does not preserve the original order.

## 5. Adding Elements

Use `add()` to insert one element.

```
skills = {"Python", "Linux"}

skills.add("Networking")

print(skills)
```

Use `update()` to insert multiple elements from an iterable.

```
skills.update(["Wireshark", "Nmap", "SQL"])

print(skills)
```

Adding an element that already exists does not create a duplicate.

## 6. Removing Elements

### Using remove()

Removes an element.

```
skills = {"Python", "Linux", "Nmap"}

skills.remove("Linux")

print(skills)
```

If the element does not exist, `remove()` raises a `KeyError`.

### Using discard()

```
skills.discard("Java")
```

`discard()` does not raise an error if the element is missing.

### Using pop()

```
skills = {"Python", "Linux", "Nmap"}

removed = skills.pop()

print(removed)
```

`pop()` removes and returns an arbitrary element. Do not assume which element will be removed.

### Using clear()

```
skills.clear()

print(skills)
```

Output:

```
set()
```

## 7. Checking Membership

Use the `in` operator to check whether an element exists.

```
tools = {"Nmap", "Wireshark", "Burp Suite"}

print("Nmap" in tools)
print("Metasploit" in tools)
```

Output:

```
True
False
```

You can also use `not in`:

```
if "Linux" not in tools:
    print("Linux is not in the set")
```

## 8. Set Operations

Sets support mathematical operations that are useful when comparing collections.

### A. Union

Union combines all unique elements from two sets.

Operator: `|`

Method: `union()`

```
A = {1, 2, 3}
B = {3, 4, 5}

print(A | B)
print(A.union(B))
```

Output:

```
{1, 2, 3, 4, 5}
```

### B. Intersection

Intersection returns only elements common to both sets.

Operator: `&`

Method: `intersection()`

```
A = {1, 2, 3}
B = {3, 4, 5}

print(A & B)
print(A.intersection(B))
```

Output:

```
{3}
```

### C. Difference

Difference returns elements present in the first set but not in the second.

Operator: `-`

Method: `difference()`

```
A = {1, 2, 3}
B = {3, 4, 5}

print(A - B)
print(B - A)
```

Output:

```
{1, 2}
{4, 5}
```

The order of the operands matters.

### D. Symmetric Difference

Returns elements that belong to either set, but not both.

Operator: `^`

Method: `symmetric_difference()`

```
A = {1, 2, 3}
B = {3, 4, 5}

print(A ^ B)
```

Output:

```
{1, 2, 4, 5}
```

## 9. Set Comparison Methods

### isdisjoint()

Checks whether two sets have no common elements.

```
A = {1, 2}
B = {3, 4}

print(A.isdisjoint(B))
```

Output:

```
True
```

### issubset()

Checks whether all elements of one set exist in another.

```
A = {1, 2}
B = {1, 2, 3, 4}

print(A.issubset(B))
```

Output:

```
True
```

### issuperset()

Checks whether one set contains all elements of another.

```
A = {1, 2, 3, 4}
B = {1, 2}

print(A.issuperset(B))
```

Output:

```
True
```

## 10. Important Set Methods

|Method|Purpose|
|---|---|
|`add()`|Adds one element|
|`update()`|Adds multiple elements|
|`remove()`|Removes an element; raises `KeyError` if missing|
|`discard()`|Removes an element without raising an error if missing|
|`pop()`|Removes and returns an arbitrary element|
|`clear()`|Removes all elements|
|`union()`|Combines unique elements|
|`intersection()`|Returns common elements|
|`difference()`|Returns elements present only in the first set|
|`symmetric_difference()`|Returns elements not shared by both sets|
|`issubset()`|Checks subset relationship|
|`issuperset()`|Checks superset relationship|
|`isdisjoint()`|Checks whether sets have no common elements|

## 11. Iterating Through Sets

Use a `for` loop to process elements.

```
tools = {"Nmap", "Wireshark", "Burp Suite"}

for tool in tools:
    print(tool)
```

The iteration order is not guaranteed. Do not rely on it for positional operations.

## 12. Set Comprehension

Set comprehension creates a set using a compact expression.

Syntax:

```
new_set = {expression for item in iterable}
```

Example:

```
squares = {number ** 2 for number in range(1, 6)}

print(squares)
```

Output:

```
{1, 4, 9, 16, 25}
```

With a condition:

```
even_numbers = {
    number
    for number in range(1, 11)
    if number % 2 == 0
}

print(even_numbers)
```

Output:

```
{2, 4, 6, 8, 10}
```

## 13. Frozen Sets

A `frozenset` is an immutable version of a set.

```
permissions = frozenset({"read", "write", "execute"})

print(permissions)
```

You cannot add or remove elements from a `frozenset`.

```
permissions.add("admin")
```

This raises an `AttributeError`.

Frozen sets can be used as dictionary keys or as elements of another set because they are hashable.

## 14. Set vs Other Data Structures

|Feature|List|Tuple|Set|Dictionary|
|---|---|---|---|---|
|Stores|Elements|Elements|Unique elements|Key-value pairs|
|Mutable|Yes|No|Yes|Yes|
|Ordered|Yes|Yes|No guaranteed order|Yes, insertion ordered|
|Duplicates|Allowed|Allowed|Not allowed|Keys must be unique|
|Indexing|Yes|Yes|No|Access by key|
|Main use|Ordered collection|Fixed collection|Uniqueness and set operations|Key-based mapping|

## 15. Set Time Complexity

Typical average-case time complexity:

|Operation|Average Time Complexity|
|---|---|
|Add an element|O(1)|
|Remove an element|O(1)|
|Membership test|O(1)|
|Union|O(n + m)|
|Intersection|Depends on set sizes and implementation; commonly O(min(n, m))|
|Difference|Depends on the size of the first set|
|Iteration|O(n)|

Here, `n` and `m` represent the sizes of the involved sets. These are typical expectations, not unconditional guarantees.

## 16. Applications in Cybersecurity

Sets are useful when analyzing unique values and comparing collections of security data.

### A. Finding Unique IP Addresses

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

### B. Comparing Known and Observed Indicators

An indicator of compromise (IOC) may include an IP address, domain, or file hash associated with suspicious activity.

```
known_iocs = {
    "192.0.2.10",
    "malicious.example"
}

observed_indicators = {
    "192.0.2.10",
    "example.com"
}

matches = known_iocs.intersection(observed_indicators)

print(matches)
```

The example uses reserved documentation addresses and domains, not real threat intelligence.

### C. Comparing User Permissions

```
required_permissions = {"read", "write"}

user_permissions = {"read", "write", "execute"}

if required_permissions.issubset(user_permissions):
    print("Required permissions are present")
```

This is only a demonstration of set comparison, not a complete authorization system.

### D. Comparing Network Hosts

```
network_a = {"192.168.1.10", "192.168.1.20"}
network_b = {"192.168.1.20", "192.168.1.30"}

common_hosts = network_a.intersection(network_b)

print(common_hosts)
```

## 17. Security Considerations

1. Validate external data before using it in security analysis.
    
2. Do not assume that an IP address or domain is malicious merely because it appears in a set of indicators.
    
3. Keep threat intelligence sources and timestamps so that indicators can be evaluated in context.
    
4. Do not use a set as a replacement for proper authentication or authorization controls.
    
5. Remember that sets remove duplicates, so they are unsuitable when frequency counts matter. Use a dictionary or `collections.Counter` for counting.
    

## 18. Practical Examples

### Example 1: Remove Duplicate Tools

```
tools = [
    "Nmap",
    "Wireshark",
    "Nmap",
    "Burp Suite",
    "Wireshark"
]

unique_tools = set(tools)

print(unique_tools)
```

### Example 2: Find Common IP Addresses

```
scan_a = {
    "192.168.1.10",
    "192.168.1.20",
    "192.168.1.30"
}

scan_b = {
    "192.168.1.20",
    "192.168.1.30",
    "192.168.1.40"
}

common = scan_a & scan_b

print(common)
```

### Example 3: Find New Hosts

```
old_scan = {
    "192.168.1.10",
    "192.168.1.20"
}

new_scan = {
    "192.168.1.10",
    "192.168.1.20",
    "192.168.1.30"
}

new_hosts = new_scan - old_scan

print(new_hosts)
```

Output:

```
{'192.168.1.30'}
```

## 19. Practical Tasks

Complete these tasks using Python:

1. Create a set containing five programming languages.
    
2. Add two more languages using `add()` and `update()`.
    
3. Remove an element using `discard()`.
    
4. Convert a list containing duplicate IP addresses into a set.
    
5. Create two sets representing hosts found in two network scans.
    
6. Find common hosts using intersection.
    
7. Find newly discovered hosts using difference.
    
8. Use `issubset()` to compare two permission sets.
    

**Challenge:** Given two lists of IP addresses from different network scans, write a program that identifies:

- Hosts present in both scans.
    
- Hosts appearing only in the first scan.
    
- Hosts appearing only in the second scan.
    

## 20. Key Takeaways

- A set stores unique elements.
    
- Sets are mutable and unordered.
    
- Sets do not support indexing.
    
- Use `add()` and `update()` to insert elements.
    
- Use `remove()` or `discard()` to remove elements.
    
- Union combines sets.
    
- Intersection finds common elements.
    
- Difference finds elements present in one set but not another.
    
- Symmetric difference finds elements not shared by both sets.
    
- Sets are useful for deduplication and comparing security data.
    

## 21. Related Notes

- [[Introduction to Data Structures]]
    
- [[Lists]]
    
- [[Tuples]]
    
- [[Dictionaries]]
    
- [[Arrays]]
    
- [[Python Data Structures]]
    
- [[Python for Cybersecurity]]
    
- [[Log Analysis with Python]]
    
- [[Nmap]]
    
- [[Programming]]