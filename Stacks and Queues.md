> Stacks and queues are linear data structures used to organize and process data. They differ mainly in the order in which elements are added and removed.

## 1. Introduction to Linear Data Structures

A linear data structure stores elements in a sequential arrangement.

Each element is processed according to a defined order.

Common linear data structures include:

- Arrays
    
- Lists
    
- Stacks
    
- Queues
    
- Linked Lists
    

Stacks and queues are important in programming, operating systems, networking, and cybersecurity.

## 2. What Is a Stack?

A stack is a linear data structure that follows the **LIFO (Last In, First Out)** principle.

The element added most recently is the first element removed.

Think of a stack of plates: the last plate placed on top is the first plate removed.

Example:

```
       TOP
    +-------+
    |  30   |  <- Last inserted
    +-------+
    |  20   |
    +-------+
    |  10   |
    +-------+
```

If we remove an element, `30` is removed first.

## 3. Stack Operations

The main stack operations are:

|Operation|Purpose|
|---|---|
|`push()`|Adds an element|
|`pop()`|Removes the top element|
|`peek()`|Returns the top element without removing it|
|`is_empty()`|Checks whether the stack is empty|
|`size()`|Returns the number of elements|

### A. Push

Adds an element to the top.

```
Before: [10, 20]
Push: 30
After: [10, 20, 30]
```

### B. Pop

Removes the top element.

```
Before: [10, 20, 30]
Pop: 30
After: [10, 20]
```

### C. Peek

Returns the top element without removing it.

```
Stack: [10, 20, 30]
Peek: 30
Stack remains unchanged.
```

## 4. Implementing a Stack Using Python Lists

Python lists can implement a basic stack.

```
stack = []

# Push elements
stack.append(10)
stack.append(20)
stack.append(30)

print("Stack:", stack)

# Pop an element
removed = stack.pop()

print("Removed:", removed)
print("Updated Stack:", stack)

# Peek
if stack:
    print("Top element:", stack[-1])
```

Output:

```
Stack: [10, 20, 30]
Removed: 30
Updated Stack: [10, 20]
Top element: 20
```

Here:

- `append()` performs push.
    
- `pop()` performs pop.
    
- `stack[-1]` accesses the top element.
    

## 5. Stack Underflow and Overflow

### Stack Underflow

Underflow occurs when a program attempts to remove an element from an empty stack.

Example:

```
stack = []

stack.pop()
```

This raises an `IndexError`.

Prevent it by checking whether the stack is empty:

```
if stack:
    stack.pop()
else:
    print("Stack is empty")
```

### Stack Overflow

Overflow occurs when an attempt is made to insert an element into a stack whose capacity has been reached.

A Python list normally grows dynamically, so a simple list-based stack does not have a fixed capacity. However, bounded stacks and fixed-size implementations can experience overflow.

## 6. Stack Implementation Using a Class

A class allows us to define stack operations in one reusable structure.

```
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        if self.is_empty():
            return "Stack is empty"

        return self.items.pop()

    def peek(self):
        if self.is_empty():
            return "Stack is empty"

        return self.items[-1]

    def is_empty(self):
        return len(self.items) == 0

    def size(self):
        return len(self.items)


stack = Stack()

stack.push(10)
stack.push(20)
stack.push(30)

print(stack.peek())
print(stack.pop())
print(stack.size())
```

Output:

```
30
30
2
```

## 7. What Is a Queue?

A queue is a linear data structure that follows the **FIFO (First In, First Out)** principle.

The element added first is the first element removed.

Think of a line of people waiting at a ticket counter.

Example:

```
FRONT                         REAR
  |                             |
  v                             v
+------+    +------+    +------+
|  10  | -> |  20  | -> |  30  |
+------+    +------+    +------+

First inserted: 10
First removed:  10
```

## 8. Queue Operations

|Operation|Purpose|
|---|---|
|`enqueue()`|Adds an element to the rear|
|`dequeue()`|Removes an element from the front|
|`front()`|Returns the first element|
|`rear()`|Returns the last element|
|`is_empty()`|Checks whether the queue is empty|
|`size()`|Returns the number of elements|

### A. Enqueue

Adds an element to the rear.

```
Before: [10, 20]
Enqueue: 30
After: [10, 20, 30]
```

### B. Dequeue

Removes the front element.

```
Before: [10, 20, 30]
Dequeue: 10
After: [20, 30]
```

### C. Front

Returns the first element without removing it.

```
Queue: [10, 20, 30]
Front: 10
```

## 9. Implementing a Queue Using Python

Python's `collections.deque` is suitable for implementing an efficient queue.

```
from collections import deque

queue = deque()

# Enqueue
queue.append(10)
queue.append(20)
queue.append(30)

print("Queue:", queue)

# Dequeue
removed = queue.popleft()

print("Removed:", removed)
print("Updated Queue:", queue)

# Front
if queue:
    print("Front element:", queue[0])
```

Output:

```
Queue: deque([10, 20, 30])
Removed: 10
Updated Queue: deque([20, 30])
Front element: 20
```

Why use `deque`?

Removing the first element from a Python list using `pop(0)` requires shifting the remaining elements. This takes O(n) time.

A `deque` supports efficient insertion and removal at both ends, typically O(1) per operation.

## 10. Queue Implementation Using a Class

```
from collections import deque

class Queue:
    def __init__(self):
        self.items = deque()

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        if self.is_empty():
            return "Queue is empty"

        return self.items.popleft()

    def front(self):
        if self.is_empty():
            return "Queue is empty"

        return self.items[0]

    def is_empty(self):
        return len(self.items) == 0

    def size(self):
        return len(self.items)


queue = Queue()

queue.enqueue(10)
queue.enqueue(20)
queue.enqueue(30)

print(queue.front())
print(queue.dequeue())
print(queue.size())
```

Output:

```
10
10
2
```

## 11. Types of Queues

### A. Simple Queue

Follows FIFO.

Elements are added at the rear and removed from the front.

### B. Circular Queue

The last position connects logically to the first position.

It allows available space in a fixed-size array to be reused.

```
       +-----+
       |  10 |
       +-----+
      /       \
 +-----+     +-----+
 |  40 |     |  20 |
 +-----+     +-----+
      \       /
       +-----+
       |  30 |
       +-----+
```

### C. Priority Queue

Elements are processed according to priority rather than simply their insertion order.

For example, a high-priority task may be processed before a low-priority task.

Python provides `heapq` for implementing a priority queue.

```
import heapq

tasks = []

heapq.heappush(tasks, (3, "Low priority"))
heapq.heappush(tasks, (1, "High priority"))
heapq.heappush(tasks, (2, "Medium priority"))

print(heapq.heappop(tasks))
```

Output:

```
(1, 'High priority')
```

With this tuple arrangement, a smaller numeric value represents a higher priority.

### D. Double-Ended Queue (Deque)

A deque allows insertion and removal from both ends.

```
from collections import deque

items = deque([10, 20, 30])

items.appendleft(5)
items.append(40)

print(items)

items.popleft()
items.pop()

print(items)
```

## 12. Stack vs Queue

|Feature|Stack|Queue|
|---|---|---|
|Principle|LIFO|FIFO|
|Insertion|Top|Rear|
|Removal|Top|Front|
|Main operations|Push, Pop|Enqueue, Dequeue|
|Example|Stack of plates|Waiting line|
|Python implementation|List or deque|deque|

## 13. Time Complexity

Typical time complexity for common implementations:

|Operation|Stack using list|Queue using deque|
|---|---|---|
|Insert|O(1) amortized|O(1)|
|Remove|O(1)|O(1)|
|Peek / Front|O(1)|O(1)|
|Check empty|O(1)|O(1)|
|Search|O(n)|O(n)|

Amortized O(1) means that an operation is constant time on average over a sequence of operations, even if occasional resizing takes longer.

## 14. Applications of Stacks

Stacks are used in:

1. Function calls and call stacks.
    
2. Undo and redo operations.
    
3. Browser history navigation.
    
4. Expression evaluation.
    
5. Parentheses matching.
    
6. Backtracking algorithms.
    
7. Depth-first search (DFS).
    

### Example: Checking Balanced Parentheses

```
def balanced_parentheses(expression):
    stack = []

    for character in expression:
        if character == "(":
            stack.append(character)

        elif character == ")":
            if not stack:
                return False

            stack.pop()

    return len(stack) == 0


print(balanced_parentheses("(a + b)"))
print(balanced_parentheses("(a + b"))
```

Output:

```
True
False
```

This simple implementation checks parentheses only. A more complete version can handle multiple bracket types such as `()`, `{}`, and `[]`.

## 15. Applications of Queues

Queues are used in:

1. CPU scheduling.
    
2. Printer job management.
    
3. Network packet processing.
    
4. Task scheduling.
    
5. Message processing systems.
    
6. Breadth-first search (BFS).
    
7. Request handling in servers.
    

### Example: Processing Security Events

```
from collections import deque

events = deque()

events.append("Successful login")
events.append("Failed login")
events.append("File access")

while events:
    event = events.popleft()
    print("Processing:", event)
```

Output:

```
Processing: Successful login
Processing: Failed login
Processing: File access
```

## 16. Applications in Cybersecurity

### A. Stack in Function Call Analysis

When a program calls another function, information about the current execution is maintained in the call stack.

This helps the program return to the correct execution point.

Stack-related vulnerabilities include:

- Stack-based buffer overflows.
    
- Stack exhaustion.
    
- Incorrect handling of memory.
    

A stack data structure and the program's call stack are related concepts, but they are not identical in every implementation.

### B. Queue in Log Processing

Security systems may receive large numbers of events.

A queue can temporarily hold events before a processing component analyzes them.

```
from collections import deque

log_queue = deque([
    "Login success",
    "Login failed",
    "Privilege change"
])

while log_queue:
    current_event = log_queue.popleft()
    print("Analyzing:", current_event)
```

### C. Queue in Network Systems

Network devices and software may use queues to buffer packets while waiting for processing or transmission.

### D. Stack in Digital Forensics

A stack can help implement depth-first traversal when exploring directory structures or investigating connected objects.

## 17. Security Considerations

1. Validate data before inserting it into queues or stacks.
    
2. Apply appropriate size limits to prevent excessive memory consumption.
    
3. Handle empty-stack and empty-queue conditions.
    
4. Protect sensitive information stored in memory.
    
5. Avoid assuming that processing a queue guarantees events will be processed exactly once; reliability depends on the surrounding system.
    
6. Use appropriate concurrency controls when multiple threads or processes access shared structures.
    

## 18. Practical Tasks

Complete these tasks using Python:

1. Create a stack and insert five numbers.
    
2. Remove two numbers using `pop()`.
    
3. Display the top element without removing it.
    
4. Implement a queue using `collections.deque`.
    
5. Add five tasks to the queue and process them in FIFO order.
    
6. Create a program that checks balanced parentheses.
    
7. Create a simple security-event processing queue.
    

**Challenge:** Build a small program that receives security events and processes them in the order they arrive. Display each event and the number of events remaining in the queue.

## 19. Key Takeaways

- A stack follows LIFO.
    
- A queue follows FIFO.
    
- `append()` and `pop()` can implement a basic stack using a Python list.
    
- `collections.deque` is suitable for efficient queue operations.
    
- A circular queue reuses available space.
    
- A priority queue processes elements according to priority.
    
- Stacks and queues are widely used in operating systems, algorithms, networking, and cybersecurity.
    

## 20. Related Notes

- [[Introduction to Data Structures]]
    
- [[Arrays]]
    
- [[Lists]]
    
- [[Tuples]]
    
- [[Dictionaries]]
    
- [[Sets]]
    
- [[Linked Lists]]
    
- [[Trees and Graphs]]
    
- [[Python Data Structures]]
    
- [[Algorithms]]
    
- [[Python for Cybersecurity]]
    
- [[04 - Programming]]