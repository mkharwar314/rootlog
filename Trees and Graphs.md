> Trees and graphs are non-linear data structures used to represent hierarchical relationships and complex connections between objects. They are important in algorithms, networking, databases, and cybersecurity.

## 1. Introduction to Non-Linear Data Structures

A non-linear data structure organizes data in relationships rather than a simple sequential arrangement.

Unlike arrays, stacks, and queues, elements are not necessarily processed in a single linear order.

Two important non-linear data structures are:

- **Tree:** Organizes data hierarchically.
    
- **Graph:** Represents relationships and connections between objects.
    

Examples:

- A file system can be represented as a tree.
    
- A computer network can be represented as a graph.
    
- A social network can be represented as a graph.
    

## 2. What Is a Tree?

A tree is a hierarchical data structure made up of nodes connected by edges.

It begins with a special node called the **root**.

Example:

```
             A
           /   \
          B     C
         / \     \
        D   E     F
```

Here:

- `A` is the root node.
    
- `B` and `C` are children of `A`.
    
- `D` and `E` are children of `B`.
    
- `F` is a child of `C`.
    

A tree with `n` nodes has exactly `n - 1` edges.

## 3. Basic Tree Terminology

|Term|Meaning|
|---|---|
|Node|An individual element in a tree|
|Root|The topmost node|
|Edge|Connection between two nodes|
|Parent|A node that has one or more children|
|Child|A node connected below a parent|
|Sibling|Nodes sharing the same parent|
|Leaf|A node with no children|
|Internal Node|A node with at least one child|
|Ancestor|A node located above another node|
|Descendant|A node located below another node|
|Subtree|A node and all its descendants|
|Depth|Number of edges from the root to a node|
|Height|Number of edges on the longest downward path from a node to a leaf|

In the example:

- `A` is the root.
    
- `B` and `C` are siblings.
    
- `D`, `E`, and `F` are leaf nodes.
    
- `A` is an ancestor of `D`.
    

## 4. Types of Trees

### A. General Tree

A general tree allows each node to have any number of children.

```
             A
          /  |  \
         B   C   D
        / \
       E   F
```

### B. Binary Tree

A binary tree is a tree in which each node has at most two children.

The children are called:

- Left child
    
- Right child
    

```
          10
         /  \
        20   30
       / \
      40  50
```

### C. Binary Search Tree (BST)

A Binary Search Tree is a binary tree that follows an ordering rule:

- Values smaller than a node are placed in its left subtree.
    
- Values greater than a node are placed in its right subtree.
    

Example:

```
          50
         /  \
        30   70
       / \   / \
      20 40 60 80
```

For this example, an inorder traversal produces:

```
20, 30, 40, 50, 60, 70, 80
```

This ordering assumes unique values. BST implementations can handle duplicates using additional rules.

### D. Balanced Binary Tree

A balanced binary tree maintains a reasonably controlled height so that operations can remain efficient.

Examples:

- AVL Tree
    
- Red-Black Tree
    

### E. Heap

A heap is a complete binary tree that follows a heap-order property.

Two common types:

**Min Heap:** Each parent is less than or equal to its children.

**Max Heap:** Each parent is greater than or equal to its children.

Example of a min heap:

```
          10
         /  \
        20   30
       / \
      40  50
```

Heaps are commonly used to implement priority queues.

## 5. Tree Traversal

Tree traversal means visiting all nodes in a particular order.

For the following binary tree:

```
          A
         / \
        B   C
       / \
      D   E
```

### A. Preorder Traversal

Order:

**Root → Left → Right**

Output:

```
A, B, D, E, C
```

### B. Inorder Traversal

Order:

**Left → Root → Right**

Output:

```
D, B, E, A, C
```

### C. Postorder Traversal

Order:

**Left → Right → Root**

Output:

```
D, E, B, C, A
```

### D. Level Order Traversal

Visits nodes level by level, usually using a queue.

Output:

```
A, B, C, D, E
```

## 6. Implementing a Binary Tree in Python

```
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None


root = Node("A")

root.left = Node("B")
root.right = Node("C")

root.left.left = Node("D")
root.left.right = Node("E")
```

The tree structure is:

```
          A
         / \
        B   C
       / \
      D   E
```

## 7. Implementing Tree Traversal in Python

Using the binary tree created above:

### Preorder

```
def preorder(node):
    if node is None:
        return

    print(node.data, end=" ")
    preorder(node.left)
    preorder(node.right)


preorder(root)
```

### Inorder

```
def inorder(node):
    if node is None:
        return

    inorder(node.left)
    print(node.data, end=" ")
    inorder(node.right)


inorder(root)
```

### Postorder

```
def postorder(node):
    if node is None:
        return

    postorder(node.left)
    postorder(node.right)
    print(node.data, end=" ")


postorder(root)
```

### Level Order

```
from collections import deque


def level_order(root):
    if root is None:
        return

    queue = deque([root])

    while queue:
        node = queue.popleft()
        print(node.data, end=" ")

        if node.left:
            queue.append(node.left)

        if node.right:
            queue.append(node.right)


level_order(root)
```

## 8. What Is a Graph?

A graph is a non-linear data structure consisting of:

- **Vertices (Nodes):** Objects or entities.
    
- **Edges:** Connections between vertices.
    

A graph is commonly represented as:

[  
G = (V, E)  
]

Where:

- `V` represents the set of vertices.
    
- `E` represents the set of edges.
    

Example:

```
       A -------- B
       |          |
       |          |
       C -------- D
```

Here:

- Vertices: A, B, C, D
    
- Edges: Connections between them.
    

Graphs are useful for representing networks, relationships, and routes.

## 9. Graph Terminology

|Term|Meaning|
|---|---|
|Vertex|A node in a graph|
|Edge|A connection between vertices|
|Adjacent Vertices|Vertices connected by an edge|
|Degree|Number of edges connected to a vertex in an undirected graph|
|Path|Sequence of vertices connected by edges|
|Cycle|A path that returns to its starting vertex|
|Connected Graph|A graph where every vertex can reach every other vertex|
|Weighted Graph|A graph whose edges have associated values or costs|
|Directed Graph|A graph whose edges have directions|
|Undirected Graph|A graph whose edges have no direction|

## 10. Types of Graphs

### A. Undirected Graph

Edges do not have a direction.

```
A -------- B
|          |
|          |
C -------- D
```

If `A` is connected to `B`, the connection works in both directions.

### B. Directed Graph

Edges have directions.

```
A ------> B
|
|
v
C ------> D
```

A connection from `A` to `B` does not automatically mean there is a connection from `B` to `A`.

### C. Weighted Graph

Each edge has a weight, such as distance, cost, or time.

```
A --5-- B
|       |
2       3
|       |
C --4-- D
```

### D. Unweighted Graph

Edges represent connections without an associated numerical weight.

### E. Cyclic Graph

A graph that contains at least one cycle.

### F. Acyclic Graph

A graph without cycles.

A directed acyclic graph is called a **DAG**.

DAGs are useful for representing task dependencies and execution order.

## 11. Graph Representation

Graphs can be represented in multiple ways.

### A. Adjacency Matrix

An adjacency matrix uses a two-dimensional matrix to represent connections.

Example:

```
Graph:

A ----- B
|
|
C
```

Adjacency matrix:

||A|B|C|
|---|---|---|---|
|A|0|1|1|
|B|1|0|0|
|C|1|0|0|

Here:

- `1` means an edge exists.
    
- `0` means no edge exists.
    

For an undirected graph, the matrix is symmetric.

### B. Adjacency List

An adjacency list stores the neighbors of each vertex.

```
graph = {
    "A": ["B", "C"],
    "B": ["A"],
    "C": ["A"]
}

print(graph)
```

This representation is often more memory-efficient for sparse graphs.

## 12. Implementing a Graph in Python

```
graph = {
    "A": ["B", "C"],
    "B": ["A", "D"],
    "C": ["A", "D"],
    "D": ["B", "C"]
}

for vertex, neighbors in graph.items():
    print(vertex, "->", neighbors)
```

Output:

```
A -> ['B', 'C']
B -> ['A', 'D']
C -> ['A', 'D']
D -> ['B', 'C']
```

## 13. Graph Traversal

Graph traversal means visiting vertices while following graph connections.

Two important algorithms are:

### A. Breadth-First Search (BFS)

BFS explores vertices level by level.

It uses a queue.

```
from collections import deque


def bfs(graph, start):
    visited = {start}
    queue = deque([start])

    while queue:
        vertex = queue.popleft()
        print(vertex, end=" ")

        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)


graph = {
    "A": ["B", "C"],
    "B": ["A", "D"],
    "C": ["A", "D"],
    "D": ["B", "C"]
}

bfs(graph, "A")
```

Possible output:

```
A B C D
```

The order can depend on the order of neighbors in the adjacency list.

### B. Depth-First Search (DFS)

DFS explores one path as deeply as possible before backtracking.

It can be implemented using recursion or an explicit stack.

```
def dfs(graph, vertex, visited=None):
    if visited is None:
        visited = set()

    if vertex in visited:
        return

    visited.add(vertex)
    print(vertex, end=" ")

    for neighbor in graph[vertex]:
        dfs(graph, neighbor, visited)


dfs(graph, "A")
```

Possible output:

```
A B D C
```

The order depends on neighbor ordering.

## 14. Tree vs Graph

|Feature|Tree|Graph|
|---|---|---|
|Structure|Hierarchical|General network of connections|
|Root|Usually has one root|No root required|
|Cycles|No cycles|Cycles may exist|
|Connectivity|A non-empty tree is connected|May be connected or disconnected|
|Edges|Exactly n - 1|Can vary|
|Direction|Usually represented hierarchically|Directed or undirected|
|Relationships|Parent-child|General connections|

A tree is a special type of connected, acyclic graph.

## 15. Time Complexity

Typical time complexities depend on the representation and algorithm.

### Tree Operations

|Operation|Typical Complexity|
|---|---|
|Traversal|O(n)|
|Search in an ordinary binary tree|O(n)|
|Search in a balanced BST|O(log n)|
|Search in a balanced BST|O(log n)|
|Search in a skewed BST|O(n)|

### Graph Operations

Using an adjacency-list representation:

|Operation|Complexity|
|---|---|
|BFS traversal|O(V + E)|
|DFS traversal|O(V + E)|
|Store graph|O(V + E)|
|Visit all vertices|O(V)|

Where:

- `V` is the number of vertices.
    
- `E` is the number of edges.
    

An adjacency matrix requires O(V²) storage.

## 16. Applications of Trees

Trees are used in:

1. File system organization.
    
2. Database indexing.
    
3. Syntax trees in compilers.
    
4. Decision-making algorithms.
    
5. Hierarchical data representation.
    
6. Search algorithms.
    
7. DNS hierarchy representation.
    

## 17. Applications of Graphs

Graphs are used in:

1. Computer network topology.
    
2. Social networks.
    
3. Route planning.
    
4. Dependency management.
    
5. Recommendation systems.
    
6. Network routing.
    
7. Relationship analysis.
    

## 18. Applications in Cybersecurity

Trees and graphs are important in security analysis.

### A. Network Mapping

A graph can represent network devices and their connections.

```
Router
  |
  +---- Server
  |
  +---- Workstation
  |
  +---- Firewall
```

Security analysts can use network graphs to understand connectivity and identify unexpected paths.

### B. Attack Path Analysis

Graphs can represent possible paths an attacker might take between systems.

For example:

```
Initial Access
      |
      v
Compromised Workstation
      |
      v
Credential Access
      |
      v
Server Access
```

This is a simplified conceptual example, not a complete attack model.

### C. Active Directory Analysis

An Active Directory environment contains relationships between:

- Users
    
- Groups
    
- Computers
    
- Permissions
    
- Domain resources
    

Graph analysis can help identify privilege relationships and potential attack paths.

### D. Malware Analysis

Trees can represent:

- Process hierarchies.
    
- File system structures.
    
- Registry key hierarchies.
    

Graphs can represent:

- Process relationships.
    
- Network connections.
    
- Function call relationships.
    
- Dependencies between malware components.
    

### E. Digital Forensics

Graphs can help investigators connect events, accounts, devices, files, and network activity.

The relationships must be supported by evidence; a graph alone does not prove that two entities are related.

## 19. Security Considerations

1. Validate graph data received from external sources.
    
2. Avoid infinite traversal by maintaining a visited set.
    
3. Consider memory and processing requirements for very large graphs.
    
4. Protect sensitive network maps and attack-path information.
    
5. Avoid interpreting a possible graph path as proof that an attack occurred.
    
6. Record the source and timestamp of evidence used to construct security graphs.
    

## 20. Practical Examples

### Example 1: Represent a Network

```
network = {
    "Router": ["Firewall", "Switch"],
    "Firewall": ["Router", "Server"],
    "Switch": ["Router", "Workstation"],
    "Server": ["Firewall"],
    "Workstation": ["Switch"]
}

for device, connections in network.items():
    print(device, "connects to", connections)
```

### Example 2: Find Whether a Device Exists

```
network = {
    "Router": ["Firewall", "Switch"],
    "Firewall": ["Router", "Server"],
    "Switch": ["Router", "Workstation"]
}

device = "Server"

if device in network:
    print("Device found")
else:
    print("Device not found")
```

This checks whether the device is a key in the adjacency list, not whether it appears only as a neighbor.

### Example 3: Traverse a Network Using BFS

```
from collections import deque

network = {
    "Router": ["Firewall", "Switch"],
    "Firewall": ["Router", "Server"],
    "Switch": ["Router", "Workstation"],
    "Server": ["Firewall"],
    "Workstation": ["Switch"]
}


def network_scan(graph, start):
    visited = {start}
    queue = deque([start])

    while queue:
        device = queue.popleft()
        print("Visited:", device)

        for neighbor in graph.get(device, []):
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)


network_scan(network, "Router")
```

This is a graph traversal demonstration using an in-memory network model. It does not scan real devices.

## 21. Practical Tasks

Complete these tasks using Python:

1. Create a binary tree with at least five nodes.
    
2. Implement preorder traversal.
    
3. Implement inorder traversal.
    
4. Implement postorder traversal.
    
5. Create a graph representing five network devices.
    
6. Store graph connections using an adjacency list.
    
7. Implement BFS.
    
8. Implement DFS.
    
9. Compare the traversal orders produced by BFS and DFS.
    

**Challenge:** Build a small network topology analyzer that:

- Stores devices and their connections.
    
- Displays all connected devices.
    
- Traverses the network using BFS.
    
- Identifies whether a specified device exists in the graph.
    

## 22. Key Takeaways

- Trees organize data hierarchically.
    
- Graphs represent general relationships and connections.
    
- A tree is a connected, acyclic graph.
    
- Binary trees have at most two children per node.
    
- Binary Search Trees organize values according to an ordering rule.
    
- Preorder, inorder, and postorder are tree traversal methods.
    
- BFS uses a queue.
    
- DFS uses a stack or recursion.
    
- Graphs are important for network mapping and attack-path analysis.
    

## 23. Related Notes

- [[Introduction to Data Structures]]
    
- [[Arrays]]
    
- [[Lists]]
    
- [[Stacks and Queues]]
    
- [[Linked Lists]]
    
- [[Hash Tables]]
    
- [[Algorithms]]
    
- [[Network Architecture]]
    
- [[Network Topologies]]
    
- [[Nmap]]
    
- [[Active Directory]]
    
- [[Digital Forensics]]
    
- [[Python for Cybersecurity]]
    
- [[Programming]]