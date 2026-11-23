> A hash table is a data structure that stores information using key-value pairs. It uses a hash function to calculate where data should be stored, allowing efficient insertion, searching, and deletion.

## 1. What Is a Hash Table?

A hash table is a data structure that stores data in an organized way using:

- **Key:** Identifies the data.
    
- **Value:** The information associated with the key.
    
- **Hash Function:** Converts a key into a numerical hash value.
    
- **Bucket:** A storage location where entries are placed.
    

Example:

```
          KEY
           |
           v
     Hash Function
           |
           v
      Hash Index
           |
           v
     +-----------+
     |  Bucket 0 |
     +-----------+
     |  Bucket 1 |
     +-----------+
     |  Bucket 2 |
     +-----------+
     |  Bucket 3 |
     +-----------+
```

A hash table uses the calculated hash to determine where an entry should be stored or searched for.

## 2. How Does a Hash Table Work?

Consider storing a student's information:

```
student = {
    "name": "Mohit",
    "age": 18,
    "course": "Cybersecurity"
}
```

When Python processes a dictionary lookup such as:

```
print(student["name"])
```

It uses the key to locate the associated value through its dictionary implementation.

Conceptually, the process is:

1. Provide a key.
    
2. Calculate its hash value.
    
3. Determine a suitable table position.
    
4. Locate the entry.
    
5. Return the associated value.
    

The actual implementation of Python dictionaries is more sophisticated than this simplified model.

## 3. What Is a Hash Function?

A hash function converts an input into a hash value.

Example:

```
def simple_hash(key):
    return sum(ord(character) for character in key)


print(simple_hash("CAT"))
```

Output:

```
216
```

Calculation:

- `C` = 67
    
- `A` = 65
    
- `T` = 84
    

Total:

[  
67 + 65 + 84 = 216  
]

This is only a demonstration. It is not a secure or production-quality hash function.

A good hash-table hash function should:

- Produce consistent results for the same key during its required lifetime.
    
- Distribute keys effectively across available positions.
    
- Be efficient to calculate.
    
- Respect the equality and hashing rules of the programming language.
    

## 4. Hash Index Calculation

A simple hash-table implementation may use modulo to calculate an index.

Formula:

[  
Index = Hash(Key) \bmod TableSize  
]

Example:

```
Hash value = 216
Table size = 10

Index = 216 % 10

Index = 6
```

The key would be assigned to bucket index 6 in this simplified implementation.

## 5. What Is a Hash Collision?

A hash collision occurs when two different keys produce the same hash-table index.

Example:

```
Hash("CAT") = 216
Hash("DOG") = 216
```

Both keys would map to the same index in a table using that hash function and table size.

Collisions are a normal possibility in hash tables because the number of possible keys is generally much larger than the number of available buckets.

## 6. Collision Resolution Techniques

Hash tables use different techniques to handle collisions.

### A. Separate Chaining

Separate chaining stores multiple entries associated with the same bucket.

Example:

```
Bucket 0 -> None

Bucket 1 -> CAT -> DOG -> None

Bucket 2 -> None

Bucket 3 -> BIRD -> None
```

Each bucket can contain a collection of entries.

Advantages:

- Multiple keys can share a bucket.
    
- Implementation is relatively straightforward.
    

Disadvantages:

- Additional memory may be required.
    
- Long chains can slow down searching.
    

### B. Open Addressing

Open addressing stores entries directly within the hash table.

When a collision occurs, the algorithm searches for another available position.

Common methods include:

**1. Linear Probing**

Checks the next available position sequentially.

```
Original index: 3

Check:
3 -> 4 -> 5 -> 6
```

**2. Quadratic Probing**

Checks positions using increasing quadratic offsets.

```
Original index: 3

Check:
3 -> 4 -> 7 -> 12
```

The actual positions depend on the table size and probing formula.

**3. Double Hashing**

Uses a second hash function to determine the probing step size.

This can reduce clustering compared with simple linear probing.

## 7. Load Factor

The load factor measures how full a hash table is.

Formula:

[  
Load\ Factor = \frac{Number\ of\ Entries}{Table\ Capacity}  
]

Example:

```
Number of entries = 7
Table capacity = 10

Load Factor = 7 / 10

Load Factor = 0.7
```

A high load factor can increase collisions and reduce performance, depending on the implementation.

Many hash-table implementations resize their storage when a chosen threshold is reached.

## 8. Rehashing

Rehashing is the process of rebuilding a hash table, usually with a different capacity.

It involves:

1. Creating a larger table.
    
2. Recalculating the positions of existing entries.
    
3. Moving entries into the new table.
    
4. Continuing normal operations.
    

Rehashing helps maintain efficient performance as the number of entries increases.

## 9. Hash Tables in Python

Python dictionaries are implemented using a hash-table-based design.

Example:

```
student = {
    "name": "Mohit",
    "age": 18,
    "course": "Cybersecurity"
}

print(student["name"])
print(student["age"])
```

Output:

```
Mohit
18
```

Python sets also use hash-based storage to maintain unique elements.

Example:

```
tools = {"Nmap", "Wireshark", "Burp Suite"}

tools.add("Nmap")

print(tools)
```

Adding `"Nmap"` again does not create a duplicate.

## 10. The hash() Function in Python

Python provides the built-in `hash()` function.

```
print(hash("Cybersecurity"))
print(hash(100))
print(hash((1, 2, 3)))
```

Important points:

- Hashable objects can be used as dictionary keys or set elements.
    
- Equal objects must have equal hash values.
    
- Hash values are not guaranteed to be unique.
    
- String and bytes hashes are normally randomized between separate Python processes.
    
- Do not use Python's built-in `hash()` as a password hash or persistent identifier.
    

## 11. Hash Table vs Dictionary

|Feature|Hash Table|Python Dictionary|
|---|---|---|
|Concept|General data structure|Python mapping type|
|Storage|Usually key-value entries|Key-value entries|
|Hashing|Uses a hash function|Uses hashing internally|
|Collision handling|Depends on implementation|Managed internally by Python|
|Ordering|Depends on implementation|Insertion order is guaranteed|
|Usage|General programming concept|Directly available in Python|

A Python dictionary is a practical implementation of a hash-table-based mapping, not a separate unrelated data structure.

## 12. Hash Table Time Complexity

Typical expected time complexity:

|Operation|Average Time|Worst Case|
|---|---|---|
|Search|O(1)|O(n)|
|Insert|O(1)|O(n)|
|Delete|O(1)|O(n)|
|Update|O(1)|O(n)|

The expected O(1) performance depends on effective hashing, collision handling, and implementation details.

## 13. Applications of Hash Tables

Hash tables are used in:

1. Database indexing and in-memory lookup structures.
    
2. Caching systems.
    
3. Symbol tables in compilers.
    
4. Counting frequencies.
    
5. Dictionaries and sets.
    
6. Configuration management.
    
7. Searching and retrieving records.
    
8. Session and metadata lookup.
    

## 14. Applications in Cybersecurity

Hash tables are useful in many security-related applications.

### A. Tracking Failed Login Attempts

```
failed_attempts = {
    "192.168.1.10": 5,
    "192.168.1.20": 2,
    "192.168.1.30": 8
}

for ip, attempts in failed_attempts.items():
    if attempts >= 5:
        print("Investigate:", ip)
```

This uses a dictionary to map IP addresses to attempt counts.

### B. File Integrity Monitoring

A hash table can map file paths to previously calculated cryptographic hashes.

```
file_hashes = {
    "system.exe": "example_hash_1",
    "config.ini": "example_hash_2"
}

print(file_hashes["system.exe"])
```

This example demonstrates lookup only. Real integrity monitoring should calculate hashes using a cryptographic algorithm such as SHA-256 and compare them against trusted baselines.

### C. IOC Lookup

Security tools may use hash-based structures to look up known indicators of compromise.

Examples include:

- IP addresses.
    
- Domains.
    
- File hashes.
    
- URLs.
    

### D. Log Analysis

Dictionaries can count event types efficiently.

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

## 15. Hash Tables vs Cryptographic Hashing

These two concepts are related by the word _hash_, but they serve different purposes.

|Feature|Hash Table Hashing|Cryptographic Hashing|
|---|---|---|
|Purpose|Efficient data lookup|Integrity and security applications|
|Main requirement|Good distribution and efficient calculation|Security properties such as collision resistance|
|Output|Used to determine storage location|Fixed-length digest|
|Examples|Python dictionary hashing|SHA-256, SHA-3|
|Security guarantee|No cryptographic guarantee|Designed to provide cryptographic properties|

### Important Security Distinction

A hash-table hash function is not suitable for:

- Password storage.
    
- Digital signatures.
    
- File integrity verification where cryptographic strength is required.
    
- Security-sensitive authentication.
    

For passwords, use dedicated password-hashing algorithms such as Argon2id, scrypt, or bcrypt with appropriate parameters.

For file integrity, use a cryptographic hash such as SHA-256.

See [[Cryptographic Hashing]] for the separate security concept.

## 16. Security Considerations

1. Do not assume that hash values are unique.
    
2. Do not use ordinary hash-table hashing for password storage.
    
3. Use secure cryptographic algorithms for integrity verification.
    
4. Be aware that poorly designed hash functions can create excessive collisions.
    
5. Validate untrusted data before using it as keys.
    
6. Protect sensitive data stored in hash-based collections.
    
7. Do not expose internal hashes as authentication credentials.
    

## 17. Practical Examples

### Example 1: Store User Information

```
users = {
    "user01": {
        "name": "Mohit",
        "role": "student"
    },
    "user02": {
        "name": "Rahul",
        "role": "analyst"
    }
}

print(users["user01"]["name"])
```

### Example 2: Count IP Addresses

```
ips = [
    "192.168.1.10",
    "192.168.1.20",
    "192.168.1.10",
    "192.168.1.30",
    "192.168.1.10"
]

ip_count = {}

for ip in ips:
    ip_count[ip] = ip_count.get(ip, 0) + 1

for ip, count in ip_count.items():
    print(ip, ":", count)
```

### Example 3: Check File Hash Records

```
trusted_hashes = {
    "file1.exe": "abc123",
    "file2.exe": "def456"
}

filename = "file1.exe"
current_hash = "abc123"

if filename in trusted_hashes:
    if trusted_hashes[filename] == current_hash:
        print("Hash matches the stored baseline")
    else:
        print("Hash mismatch: investigate")
else:
    print("File not found in baseline")
```

This is a simplified comparison. A real system must calculate the file's cryptographic hash and protect the baseline from unauthorized modification.

## 18. Practical Tasks

Complete these tasks using Python:

1. Create a dictionary containing five usernames and their roles.
    
2. Retrieve a user's role using the username as a key.
    
3. Add a new user.
    
4. Update an existing user's role.
    
5. Create a program that counts repeated IP addresses.
    
6. Build a dictionary that maps filenames to example SHA-256 digest strings.
    
7. Write a program that compares a current digest with a stored baseline.
    

**Challenge:** Create a small file-integrity record manager that stores filenames and their expected SHA-256 hashes, then checks whether a supplied current hash matches the stored value. Use demonstration data only.

## 19. Key Takeaways

- A hash table stores information using keys and values.
    
- A hash function helps determine where data is stored.
    
- Different keys can produce the same hash-table index.
    
- Collisions can be handled using chaining or open addressing.
    
- Load factor measures how full a hash table is.
    
- Rehashing rebuilds a table when its capacity changes.
    
- Python dictionaries and sets use hash-based storage.
    
- Hash-table hashing is different from cryptographic hashing.
    

## 20. Related Notes

- [[Introduction to Data Structures]]
    
- [[Arrays]]
    
- [[Lists]]
    
- [[Dictionaries]]
    
- [[Sets]]
    
- [[Linked Lists]]
    
- [[Trees and Graphs]]
    
- [[Algorithms]]
    
- [[Python Data Structures]]
    
- [[Cryptographic Hashing]]
    
- [[File Integrity Monitoring]]
    
- [[Log Analysis with Python]]
    
- [[Programming]]