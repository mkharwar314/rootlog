> Understand how C++ manages memory, allocates resources dynamically, and prevents memory-related errors.

## 1. What Is Memory Management?

Memory management is the process of allocating, using, and releasing memory during program execution.

C++ provides several ways to manage memory:

- Automatic storage for local variables.
    
- Static storage for global and static variables.
    
- Dynamic memory allocation.
    
- Standard library containers.
    
- Smart pointers.
    

Good memory management improves:

- Program stability.
    
- Performance.
    
- Resource utilization.
    
- Security.
    
- Maintainability.
    

## 2. Memory Layout of a C++ Program

A running C++ program commonly uses several memory regions.

|Memory Region|Purpose|
|---|---|
|Code / Text|Stores executable instructions|
|Data|Stores initialized global and static variables|
|BSS|Stores zero-initialized global and static variables|
|Heap|Supports dynamic memory allocation|
|Stack|Commonly supports function calls and automatic variables|

Conceptual layout:

```
+--------------------------+
|          Stack           |
|   Local variables        |
|   Function call data     |
|            ↓             |
+--------------------------+
|                          |
|       Free Space         |
|                          |
+--------------------------+
|            ↑             |
|           Heap           |
|   Dynamic allocations    |
+--------------------------+
|           BSS            |
|  Zero-initialized data   |
+--------------------------+
|           Data           |
|  Initialized data        |
+--------------------------+
|       Code / Text        |
|  Program instructions    |
+--------------------------+
```

This is a simplified conceptual diagram. Actual memory layouts depend on the operating system, compiler, executable format, and runtime.

## 3. Stack Memory

Stack memory commonly stores:

- Local variables with automatic storage duration.
    
- Function call information.
    
- Function parameters and temporary data, depending on the implementation.
    

Example:

```
#include <iostream>

void display() {
    int number = 100;

    std::cout << number << std::endl;
}

int main() {
    display();

    return 0;
}
```

The local variable `number` exists during the execution of `display()`.

After the function returns, its lifetime ends.

### Characteristics

- Automatic lifetime management.
    
- Commonly efficient.
    
- Useful for temporary variables.
    
- Limited available capacity.
    

## 4. Heap Memory

The heap supports dynamic memory allocation.

Unlike ordinary local variables, dynamically allocated objects can remain alive beyond the function that created them.

Their lifetime continues until they are destroyed or their storage is released.

Example:

```
#include <iostream>

int main() {
    int *ptr = new int(100);

    std::cout << *ptr << std::endl;

    delete ptr;
    ptr = nullptr;

    return 0;
}
```

### Characteristics

- Dynamic allocation.
    
- Flexible object lifetime.
    
- Requires proper resource management.
    
- Can introduce memory leaks and other errors.
    

## 5. Static Storage Duration

Global variables and static variables have static storage duration.

Their lifetime extends throughout program execution.

Example:

```
#include <iostream>

void counter() {
    static int count = 0;

    count++;

    std::cout << count << std::endl;
}

int main() {
    counter();
    counter();
    counter();

    return 0;
}
```

**Output:**

```
1
2
3
```

The static variable retains its value between function calls.

## 6. Dynamic Memory Allocation in C++

C++ provides two traditional operators for dynamic memory management:

- `new`
    
- `delete`
    

These operators create and destroy dynamically allocated objects.

## 7. The new Operator

The `new` operator allocates storage and initializes an object.

Syntax:

```
data_type *pointer = new data_type;
```

Example:

```
#include <iostream>

int main() {
    int *ptr = new int;

    *ptr = 50;

    std::cout << *ptr << std::endl;

    delete ptr;

    return 0;
}
```

**Output:**

```
50
```

### Initializing During Allocation

```
int *ptr = new int(100);
```

The allocated integer is initialized to `100`.

By default, an ordinary throwing `new` expression reports allocation failure by throwing `std::bad_alloc`.

## 8. The delete Operator

The `delete` operator destroys an object created using an ordinary `new` expression and releases its storage.

Example:

```
int *ptr = new int(100);

delete ptr;
ptr = nullptr;
```

Important:

- Release each allocation exactly once.
    
- Do not access an object after its lifetime ends.
    
- Do not use `delete` on memory that was not obtained through a compatible `new` expression.
    
- Do not use `delete` for memory allocated by `malloc()`.
    

## 9. Dynamic Memory Allocation for Arrays

C++ supports dynamic allocation of arrays using `new[]`.

Example:

```
#include <iostream>

int main() {
    int *numbers = new int[5];

    for (int i = 0; i < 5; i++) {
        numbers[i] = (i + 1) * 10;
    }

    for (int i = 0; i < 5; i++) {
        std::cout << numbers[i] << " ";
    }

    delete[] numbers;
    numbers = nullptr;

    return 0;
}
```

**Output:**

```
10 20 30 40 50
```

Important:

- `new[]` allocates an array.
    
- `delete[]` releases an array.
    
- Use the matching allocation and deallocation forms.
    

## 10. new vs delete

|new|delete|
|---|---|
|Allocates storage|Releases storage|
|Creates an object|Ends the object's lifetime|
|Returns a typed pointer|Does not return a value|
|Can throw `std::bad_alloc`|Must receive a compatible pointer|

For arrays:

```
int *arr = new int[5];

delete[] arr;
```

## 11. new vs malloc()

C++ also supports the C allocation functions through the C standard library.

However, `new` and `malloc()` are not interchangeable.

|Feature|new|malloc()|
|---|---|---|
|Language|C++|C library function|
|Returns|Typed pointer|`void *`|
|Object construction|Performs initialization and construction|Does not call C++ constructors|
|Failure|Normally throws `std::bad_alloc`|Returns NULL|
|Release|`delete`|`free()`|
|Arrays|Supports `new[]`|Allocates raw storage|

Example using `new`:

```
int *ptr = new int(100);

delete ptr;
```

Example using `malloc()`:

```
#include <cstdlib>

int *ptr = static_cast<int *>(std::malloc(sizeof(int)));

if (ptr != nullptr) {
    *ptr = 100;

    std::free(ptr);
}
```

Never release memory allocated with `new` using `free()`, or memory allocated with `malloc()` using `delete`.

## 12. Memory Leaks

A memory leak occurs when dynamically allocated memory is not released and the program loses access to it.

Example:

```
int main() {
    int *ptr = new int(100);

    ptr = nullptr;

    return 0;
}
```

The allocation is lost because the pointer is overwritten without releasing the memory.

### Prevention

- Track dynamically allocated resources.
    
- Release allocations when no longer needed.
    
- Prefer automatic resource management.
    
- Use smart pointers.
    
- Check error paths.
    

## 13. Dangling Pointers

A dangling pointer refers to an object whose lifetime has ended or to storage that has been released.

Example:

```
int *ptr = new int(100);

delete ptr;

// ptr is now dangling
ptr = nullptr;
```

Using the pointer after deletion causes undefined behavior.

Setting the pointer to `nullptr` helps prevent accidental use through that pointer variable.

It does not update other pointers that may refer to the same object.

## 14. Smart Pointers

Modern C++ provides **smart pointers** to manage dynamically allocated objects automatically.

They are defined in the `<memory>` header.

The three commonly discussed smart pointer types are:

1. `unique_ptr`
    
2. `shared_ptr`
    
3. `weak_ptr`
    

### A. unique_ptr

`std::unique_ptr` provides exclusive ownership of an object.

Only one `unique_ptr` owns the object at a time.

Example:

```
#include <iostream>
#include <memory>

int main() {
    std::unique_ptr<int> ptr =
        std::make_unique<int>(100);

    std::cout << *ptr << std::endl;

    return 0;
}
```

When `ptr` goes out of scope, the allocated object is automatically destroyed.

### Characteristics

- Exclusive ownership.
    
- Cannot be copied.
    
- Can be moved.
    
- Automatically releases its resource.
    

### B. shared_ptr

`std::shared_ptr` allows multiple smart pointers to share ownership of an object.

The object is destroyed when the last owning `shared_ptr` is destroyed or reset.

Example:

```
#include <iostream>
#include <memory>

int main() {
    std::shared_ptr<int> ptr1 =
        std::make_shared<int>(100);

    std::shared_ptr<int> ptr2 = ptr1;

    std::cout << *ptr1 << std::endl;
    std::cout << ptr1.use_count() << std::endl;

    return 0;
}
```

**Output:**

```
100
2
```

### Characteristics

- Shared ownership.
    
- Uses reference counting.
    
- Automatically releases the object when ownership ends.
    
- Cyclic ownership can prevent automatic cleanup.
    

### C. weak_ptr

`std::weak_ptr` observes an object managed by `shared_ptr` without increasing its reference count.

It is useful for avoiding ownership cycles.

Example:

```
#include <iostream>
#include <memory>

int main() {
    std::shared_ptr<int> shared =
        std::make_shared<int>(100);

    std::weak_ptr<int> weak = shared;

    if (auto locked = weak.lock()) {
        std::cout << *locked << std::endl;
    }

    return 0;
}
```

`lock()` returns a `shared_ptr` if the object still exists; otherwise, it returns an empty `shared_ptr`.

## 15. Smart Pointer Comparison

|Feature|unique_ptr|shared_ptr|weak_ptr|
|---|---|---|---|
|Ownership|Exclusive|Shared|Non-owning|
|Reference counting|No|Yes|Does not increase ownership count|
|Copyable|No|Yes|Yes|
|Automatic cleanup|Yes|Yes|Does not own the object|
|Common use|Single ownership|Shared ownership|Observing shared objects|

**Recommendation:** Prefer `std::unique_ptr` when ownership is exclusive. Use `std::shared_ptr` only when shared ownership is actually required.

## 16. RAII (Resource Acquisition Is Initialization)

RAII is a C++ resource-management technique.

It connects resource ownership to object lifetime.

When an object is created, it acquires a resource. When the object is destroyed, it releases that resource.

Resources can include:

- Dynamically allocated memory.
    
- File handles.
    
- Network connections.
    
- Locks and synchronization objects.
    

Example:

```
#include <iostream>
#include <fstream>

int main() {
    std::ofstream file("example.txt");

    if (file.is_open()) {
        file << "Learning C++ memory management";
    }

    return 0;
}
```

The file stream automatically closes the file when the object goes out of scope.

RAII reduces the need for manual cleanup and helps make programs safer.

## 17. Stack vs Heap

|Feature|Stack|Heap|
|---|---|---|
|Common use|Automatic local objects|Dynamic objects|
|Lifetime|Usually tied to scope|Controlled by ownership and destruction|
|Management|Automatic|Explicit or managed through RAII|
|Flexibility|Less flexible|More flexible|
|Common risk|Stack exhaustion|Leaks and lifetime errors|

## 18. Memory Management Errors in C++

### A. Memory Leak

Allocated memory is not released.

### B. Use-After-Free

A program accesses an object after its lifetime has ended.

### C. Double Delete

The same allocation is deleted more than once.

```
int *ptr = new int(100);

delete ptr;

// Incorrect: deleting the same allocation again
// delete ptr;
```

### D. Mismatched Allocation and Deallocation

Incorrect:

```
int *ptr = new int[5];

// Incorrect: should use delete[]
// delete ptr;
```

Correct:

```
delete[] ptr;
```

### E. Buffer Overflow

Writing outside the valid boundaries of an array or buffer.

### F. Resource Leak

A program fails to release resources such as files, sockets, or locks.

## 19. C++ Memory Management and Cybersecurity

Memory-management errors can create serious software vulnerabilities.

|Vulnerability|Description|
|---|---|
|Buffer Overflow|Writing beyond allocated memory|
|Use-After-Free|Accessing an object after its lifetime ends|
|Double Free / Delete|Releasing the same allocation more than once|
|Memory Leak|Failing to release memory|
|Out-of-Bounds Access|Accessing memory outside valid limits|
|Dangling Pointer|Using a pointer after its target is no longer valid|

### Secure Development Practices

1. Prefer standard library containers over raw dynamic arrays.
    
2. Use smart pointers for dynamic ownership.
    
3. Follow RAII principles.
    
4. Validate input and buffer sizes.
    
5. Avoid unnecessary raw pointer ownership.
    
6. Keep object lifetimes clear.
    
7. Use sanitizers during testing.
    
8. Handle exceptions safely.
    

## 20. Memory Debugging Tools

### A. AddressSanitizer

AddressSanitizer detects many memory errors during execution.

Compile using GCC:

```
g++ -g -fsanitize=address -fno-omit-frame-pointer program.cpp -o program
```

Run:

```
./program
```

It can detect:

- Heap buffer overflows.
    
- Stack buffer overflows.
    
- Use-after-free.
    
- Some memory leaks, depending on platform support.
    

### B. Valgrind

Valgrind can identify memory-management problems on supported Linux systems.

Run:

```
valgrind --leak-check=full ./program
```

It can help detect:

- Memory leaks.
    
- Invalid memory access.
    
- Uninitialized memory usage.
    
- Incorrect memory deallocation.
    

### C. GDB

GDB helps inspect program execution.

Compile:

```
g++ -g program.cpp -o program
```

Start debugging:

```
gdb ./program
```

Useful commands:

```
break main
run
next
step
print variable_name
backtrace
quit
```

## 21. Best Practices

1. Prefer automatic objects when possible.
    
2. Prefer standard library containers such as `std::vector`.
    
3. Use `std::string` for ordinary text handling.
    
4. Use `std::unique_ptr` for exclusive dynamic ownership.
    
5. Use `std::shared_ptr` only when shared ownership is needed.
    
6. Avoid manual `new` and `delete` when a standard library solution is suitable.
    
7. Never access objects after their lifetime ends.
    
8. Match allocation and deallocation correctly.
    
9. Handle exceptions and error paths.
    
10. Test with memory debugging tools.
    

## 22. Practical Exercises

Write C++ programs to perform these tasks:

1. Allocate one integer using `new` and release it using `delete`.
    
2. Allocate an array of five integers using `new[]`.
    
3. Display the array and release it using `delete[]`.
    
4. Create a `unique_ptr` using `std::make_unique`.
    
5. Create two `shared_ptr` objects that share ownership.
    
6. Create a `weak_ptr` and access the object using `lock()`.
    
7. Use `std::vector` to store five integers.
    
8. Use `std::string` to store and display a sentence.
    
9. Write a program that uses an `std::ofstream` object.
    
10. Compile a program using AddressSanitizer.
    

## 23. Key Takeaways

- Memory management controls how programs allocate and release memory.
    
- Stack memory commonly supports automatic variables and function calls.
    
- Heap memory supports dynamic allocation.
    
- `new` creates dynamically allocated objects.
    
- `delete` destroys individual dynamically allocated objects.
    
- `new[]` and `delete[]` are used for dynamic arrays.
    
- Smart pointers automate ownership and cleanup.
    
- RAII connects resource management to object lifetime.
    
- `unique_ptr` provides exclusive ownership.
    
- `shared_ptr` provides shared ownership.
    
- `weak_ptr` observes shared objects without owning them.
    
- Memory errors can create serious cybersecurity vulnerabilities.
    

## 24. Related Notes

- [[Introduction to C++]]
    
- [[C++ Classes and Objects]]
    
- [[Constructors]]
    
- [[C Memory Management]]
    
- [[C Pointers]]
    
- [[Introduction to Secure Coding]]
    
- [[C++ Programming Labs]]