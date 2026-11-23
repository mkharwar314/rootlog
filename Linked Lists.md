> A linked list is a linear data structure in which elements are stored in separate nodes. Each node contains data and a reference to another node, allowing elements to be connected without requiring contiguous memory locations.

## 1. What Is a Linked List?

A linked list is a collection of nodes connected through references (links).

Each node generally contains:

- **Data:** The value stored in the node.
    
- **Next:** A reference to the next node.
    

Unlike arrays, linked-list elements do not need to occupy consecutive memory locations.

Example:

```
HEAD
 |
 v
+------+------+
|  10  |   o---->
+------+------+
               |
               v
        +------+------+
        |  20  |   o---->
        +------+------+
                       |
                       v
                +------+------+
                |  30  | None |
                +------+------+
```

The final node points to `None`, indicating the end of the list.

## 2. Characteristics of Linked Lists

1. **Dynamic size:** Nodes can be added or removed during execution.
    
2. **Non-contiguous storage:** Nodes do not need to occupy adjacent memory locations.
    
3. **Sequential access:** Nodes are normally accessed by traversing from the head.
    
4. **References:** Each node stores a reference to another node.
    
5. **Flexible insertion and deletion:** Nodes can be connected or disconnected by changing references.
    
6. **Additional memory:** Each node requires memory for its data and references.
    

## 3. Components of a Linked List

|Component|Description|
|---|---|
|Node|Basic unit containing data and references|
|Head|Reference to the first node|
|Tail|Reference to the last node, when maintained|
|Next|Reference to the next node|
|None|Indicates that no next node exists|

Example:

```
HEAD                         TAIL
 |                             |
 v                             v
[10 | next] -> [20 | next] -> [30 | None]
```

## 4. Types of Linked Lists

There are several types of linked lists.

### A. Singly Linked List

Each node points to the next node.

```
HEAD
 |
 v
[10] -> [20] -> [30] -> None
```

Characteristics:

- Traversal is normally forward only.
    
- Each node stores one next reference.
    
- Requires less reference storage than a doubly linked list.
    

### B. Doubly Linked List

Each node contains references to both the previous and next nodes.

```
None <- [10] <-> [20] <-> [30] -> None
```

Characteristics:

- Supports forward and backward traversal.
    
- Requires additional memory for previous references.
    
- Insertion and deletion can be convenient when the relevant node is already known.
    

### C. Circular Singly Linked List

The final node points back to the first node.

```
       +--------------------+
       |                    |
       v                    |
HEAD -> [10] -> [20] -> [30]
```

Characteristics:

- No `None` reference at the end of the circular chain.
    
- Traversal can continue cyclically.
    
- Requires careful stopping conditions to avoid infinite loops.
    

### D. Circular Doubly Linked List

Each node has previous and next references, and the first and last nodes are connected.

```
       +-----------------------+
       |                       |
       v                       |
     [10] <-> [20] <-> [30]
       ^                       |
       |                       v
       +-----------------------+
```

## 5. Creating a Node in Python

Python does not have a built-in linked-list type, but we can implement one using classes.

```
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


first = Node(10)
second = Node(20)
third = Node(30)

first.next = second
second.next = third

print(first.data)
print(first.next.data)
print(first.next.next.data)
```

Output:

```
10
20
30
```

Explanation:

- `first`, `second`, and `third` are node objects.
    
- Each node stores a value in `data`.
    
- The `next` attribute connects one node to another.
    

## 6. Traversing a Linked List

Traversal means visiting each node from the head to the end.

```
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


first = Node(10)
second = Node(20)
third = Node(30)

first.next = second
second.next = third

current = first

while current is not None:
    print(current.data)
    current = current.next
```

Output:

```
10
20
30
```

The traversal process:

1. Start at the head.
    
2. Read the current node's data.
    
3. Move to the next node.
    
4. Continue until the reference is `None`.
    

## 7. Inserting Nodes

### A. Insertion at the Beginning

A new node becomes the head.

```
new_node.next = head
head = new_node
```

Example:

```
Before:
HEAD -> [20] -> [30] -> None

Insert 10:

After:
HEAD -> [10] -> [20] -> [30] -> None
```

### B. Insertion at the End

The final node points to the new node.

```
Before:
HEAD -> [10] -> [20] -> None

Insert 30:

After:
HEAD -> [10] -> [20] -> [30] -> None
```

Without a tail reference, we must traverse the list to find the final node.

### C. Insertion After a Given Node

Suppose a new node must be inserted after the node containing `20`.

```
Before:
[10] -> [20] -> [40]

Insert 30:

After:
[10] -> [20] -> [30] -> [40]
```

The new node's next reference must be updated before changing the previous node's next reference.

## 8. Deleting Nodes

### A. Deleting the First Node

Move the head to the second node.

```
Before:
HEAD -> [10] -> [20] -> [30]

Delete 10:

After:
HEAD -> [20] -> [30]
```

### B. Deleting the Last Node

Find the second-last node and set its next reference to `None`.

```
Before:
[10] -> [20] -> [30] -> None

Delete 30:

After:
[10] -> [20] -> None
```

### C. Deleting a Specific Node

Find the node before the target node and connect it to the target's next node.

```
Before:
[10] -> [20] -> [30] -> [40]

Delete 30:

After:
[10] -> [20] -> [40]
```

## 9. Complete Singly Linked List Implementation

The following implementation supports insertion, deletion, searching, and displaying nodes.

```
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self):
        self.head = None

    def insert_at_end(self, data):
        new_node = Node(data)

        if self.head is None:
            self.head = new_node
            return

        current = self.head

        while current.next is not None:
            current = current.next

        current.next = new_node

    def insert_at_beginning(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def delete(self, data):
        if self.head is None:
            return

        if self.head.data == data:
            self.head = self.head.next
            return

        current = self.head

        while current.next is not None:
            if current.next.data == data:
                current.next = current.next.next
                return

            current = current.next

    def search(self, data):
        current = self.head

        while current is not None:
            if current.data == data:
                return True

            current = current.next

        return False

    def display(self):
        current = self.head

        while current is not None:
            print(current.data, end=" -> ")
            current = current.next

        print("None")


linked_list = LinkedList()

linked_list.insert_at_end(10)
linked_list.insert_at_end(20)
linked_list.insert_at_end(30)

linked_list.insert_at_beginning(5)

linked_list.display()

linked_list.delete(20)

linked_list.display()

print(linked_list.search(30))
```

Output:

```
5 -> 10 -> 20 -> 30 -> None
5 -> 10 -> 30 -> None
True
```

## 10. Linked List vs Array

|Feature|Array|Linked List|
|---|---|---|
|Storage|Elements stored in an indexed sequence|Nodes connected by references|
|Access|Direct indexed access|Sequential traversal|
|Random access|O(1) for ordinary array indexing|O(n)|
|Insertion at beginning|Usually O(n) for shifting elements|O(1) when updating the head|
|Deletion at beginning|Usually O(n) for shifting elements|O(1) when updating the head|
|Memory|Usually lower per element|Additional reference storage|
|Cache locality|Generally better|Generally poorer|

Python lists are dynamic arrays, not linked lists. Their behavior should not be confused with a linked-list implementation.

## 11. Time Complexity

For a basic singly linked list:

|Operation|Time Complexity|
|---|---|
|Access by position|O(n)|
|Search|O(n)|
|Insert at beginning|O(1)|
|Insert at end without tail|O(n)|
|Insert at end with tail|O(1)|
|Delete at beginning|O(1)|
|Delete a value by searching|O(n)|
|Traverse entire list|O(n)|

If the node to be modified is already known, insertion or deletion can often be O(1), assuming the necessary references are available.

## 12. Applications of Linked Lists

Linked lists are useful in different areas of computer science.

1. Implementing stacks and queues.
    
2. Managing playlists.
    
3. Browser navigation.
    
4. Memory management structures.
    
5. Implementing hash-table collision chains.
    
6. Representing certain graph structures.
    
7. Maintaining sequences where frequent insertions and deletions are required.
    

## 13. Applications in Cybersecurity

### A. Managing Security Events

A linked list can represent a sequence of events that are added dynamically.

### B. Memory Management

Operating systems and runtime systems may use linked structures to track memory blocks or other resources.

### C. Hash Table Collision Handling

Some hash-table implementations use linked lists or other structures to store entries that map to the same hash-table bucket.

### D. Digital Forensics

Linked structures can be used to represent connected records or objects during data analysis.

A linked list is a general data structure; using one does not automatically make a security tool faster or more secure.

## 14. Security Considerations

1. Check for empty lists before accessing or deleting nodes.
    
2. Avoid creating accidental cycles in a singly linked list.
    
3. Use correct references when inserting or deleting nodes.
    
4. Avoid infinite loops during traversal.
    
5. Validate input before inserting data into a list.
    
6. Be aware of memory consumption when processing large collections.
    
7. In low-level languages such as C and C++, incorrect pointer handling can cause memory corruption, dangling pointers, and use-after-free vulnerabilities.
    

## 15. Practical Examples

### Example 1: Create and Display a Linked List

```
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


head = Node("Nmap")
head.next = Node("Wireshark")
head.next.next = Node("Burp Suite")

current = head

while current:
    print(current.data)
    current = current.next
```

### Example 2: Count Nodes

```
def count_nodes(head):
    count = 0
    current = head

    while current is not None:
        count += 1
        current = current.next

    return count
```

### Example 3: Reverse a Singly Linked List

```
def reverse_list(head):
    previous = None
    current = head

    while current is not None:
        next_node = current.next
        current.next = previous
        previous = current
        current = next_node

    return previous
```

This algorithm reverses the links without creating a second list.

## 16. Practical Tasks

Complete these tasks using Python:

1. Create a `Node` class with `data` and `next` attributes.
    
2. Connect three nodes to form a singly linked list.
    
3. Traverse the list and print all values.
    
4. Insert a node at the beginning.
    
5. Insert a node at the end.
    
6. Delete a node containing a specified value.
    
7. Search for a value in the linked list.
    
8. Count the total number of nodes.
    
9. Reverse the linked list.
    

**Challenge:** Create a linked list that stores security event names. Add five events, remove one event, and display the remaining events in order.

## 17. Key Takeaways

- A linked list consists of connected nodes.
    
- Each node stores data and one or more references.
    
- The head points to the first node.
    
- Singly linked lists support forward traversal.
    
- Doubly linked lists support forward and backward traversal.
    
- Circular linked lists connect the final node back to the beginning.
    
- Linked lists provide efficient insertion and deletion when the relevant position or node is already known.
    
- Accessing an arbitrary position requires traversal and takes O(n) time.
    

## 18. Related Notes

- [[Introduction to Data Structures]]
    
- [[Arrays]]
    
- [[Lists]]
    
- [[Tuples]]
    
- [[Dictionaries]]
    
- [[Sets]]
    
- [[Stacks and Queues]]
    
- [[Trees and Graphs]]
    
- [[Hash Tables]]
    
- [[Algorithms]]
    
- [[Python Data Structures]]
    
- [[Programming]]