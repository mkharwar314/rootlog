> Understand C++ fundamentals, its relationship with C, its programming features, and its applications in software development and cybersecurity.

## 1. What Is C++?

**C++** is a general-purpose, compiled programming language developed by **Bjarne Stroustrup** at Bell Laboratories.

It was originally designed as an extension of the C programming language, introducing object-oriented programming and other abstractions.

C++ supports multiple programming paradigms, including:

- Procedural programming
    
- Object-oriented programming
    
- Generic programming
    
- Functional programming techniques
    

C++ is widely used for developing high-performance software.

## 2. History of C++

- Developed by Bjarne Stroustrup.
    
- Development began around 1979.
    
- Originally called **C with Classes**.
    
- Renamed C++ in 1983.
    
- First standardized as ISO C++ in 1998.
    
- Continues to evolve through newer standards.
    

The `++` operator in C represents incrementing a value, symbolically suggesting an advancement beyond C.

## 3. Features of C++

Important features include:

|Feature|Explanation|
|---|---|
|Object-Oriented Programming|Supports classes and objects|
|High Performance|Allows efficient, low-level programming|
|Portability|Programs can be compiled on different platforms|
|Reusability|Supports reusable classes and functions|
|Generic Programming|Supports templates|
|Memory Management|Supports dynamic memory allocation|
|Standard Library|Provides containers, algorithms, and utilities|
|Multi-Paradigm|Supports different programming approaches|

## 4. Applications of C++

C++ is used in many areas:

- Operating systems and system software.
    
- Game engines and game development.
    
- Embedded systems.
    
- Desktop applications.
    
- Browsers and rendering engines.
    
- Database systems.
    
- High-performance computing.
    
- Financial software.
    
- Cybersecurity tools.
    

Examples of technologies with substantial C++ code include Unreal Engine, parts of Chromium, and various system utilities.

## 5. C vs C++

C and C++ are related languages, but they are not identical.

|Feature|C|C++|
|---|---|---|
|Programming style|Primarily procedural|Multi-paradigm|
|Classes and objects|Not built in|Supported|
|Inheritance|Not built in|Supported|
|Polymorphism|Not built in|Supported|
|Function overloading|Not supported|Supported|
|Templates|Not supported|Supported|
|Standard library|C standard library|C++ standard library|
|Memory management|`malloc()` and `free()`|`new` and `delete`, plus other techniques|
|Exception handling|No built-in C++-style exceptions|Supported|

**Important:** Modern C++ also supports procedural programming. It is not limited to object-oriented programming.

## 6. Setting Up a C++ Environment

To write and run C++ programs, you need:

1. A text editor or IDE.
    
2. A C++ compiler.
    
3. A terminal or command prompt.
    

Popular C++ compilers include:

- GCC / G++
    
- Clang
    
- Microsoft Visual C++ compiler (MSVC)
    

On Kali Linux, install GCC and G++ using:

```
sudo apt update
sudo apt install build-essential
```

Check the compiler:

```
g++ --version
```

On Windows, you can use a MinGW-w64 toolchain or Microsoft Visual Studio with the C++ workload installed.

## 7. First C++ Program

Create a file named:

`hello.cpp`

```
#include <iostream>

int main() {
    std::cout << "Hello, C++!" << std::endl;

    return 0;
}
```

**Output:**

```
Hello, C++!
```

### Understanding the Program

|Code|Purpose|
|---|---|
|`#include <iostream>`|Includes input/output facilities|
|`int main()`|Program entry point|
|`std::cout`|Displays output|
|`std::endl`|Inserts a newline and flushes the output stream|
|`return 0;`|Indicates successful program termination|

## 8. Compiling and Running C++ Programs

C++ is generally compiled before execution.

### Compile

```
g++ hello.cpp -o hello
```

### Run on Linux

```
./hello
```

### Run on Windows

```
hello.exe
```

The compiler translates the source code into an executable program.

## 9. Basic C++ Input and Output

C++ uses stream-based input and output.

### Output Using cout

```
#include <iostream>

int main() {
    std::cout << "Learning C++" << std::endl;

    return 0;
}
```

### Input Using cin

```
#include <iostream>

int main() {
    int age;

    std::cout << "Enter your age: ";
    std::cin >> age;

    std::cout << "Age: " << age << std::endl;

    return 0;
}
```

### Reading a Full Line

```
#include <iostream>
#include <string>

int main() {
    std::string name;

    std::cout << "Enter your full name: ";
    std::getline(std::cin, name);

    std::cout << "Name: " << name << std::endl;

    return 0;
}
```

`std::getline()` reads a line, including spaces, until a newline is encountered.

## 10. Basic Data Types in C++

C++ provides several built-in data types.

|Data Type|Purpose|Example|
|---|---|---|
|`int`|Integer values|`int age = 20;`|
|`float`|Single-precision floating-point|`float price = 10.5f;`|
|`double`|Double-precision floating-point|`double value = 20.55;`|
|`char`|Character|`char grade = 'A';`|
|`bool`|Boolean value|`bool active = true;`|
|`void`|No value|`void display();`|

C++ also supports user-defined types such as classes, structures, enumerations, and unions.

## 11. Variables and Constants

Variables store data that can change during program execution.

```
int number = 100;
number = 200;
```

Constants represent values that should not be modified through that variable.

```
const double PI = 3.14159;
```

Attempting to modify a `const` variable produces a compilation error.

## 12. Operators in C++

C++ supports several categories of operators.

|Category|Examples|
|---|---|
|Arithmetic|`+`, `-`, `*`, `/`, `%`|
|Relational|`==`, `!=`, `>`, `<`|
|Logical|`&&`, `||`,` !`|
|Assignment|`=`, `+=`, `-=`, `*=`|
|Increment/Decrement|`++`, `--`|
|Bitwise|`&`, `|`,` ^`,` ~`,` <<`,` >>`|

Example:

```
#include <iostream>

int main() {
    int a = 10;
    int b = 5;

    std::cout << a + b << std::endl;
    std::cout << a * b << std::endl;

    return 0;
}
```

## 13. Conditional Statements

Conditional statements allow programs to make decisions.

### if Statement

```
#include <iostream>

int main() {
    int age = 20;

    if (age >= 18) {
        std::cout << "Adult";
    }

    return 0;
}
```

### if-else Statement

```
#include <iostream>

int main() {
    int number = 7;

    if (number % 2 == 0) {
        std::cout << "Even";
    } else {
        std::cout << "Odd";
    }

    return 0;
}
```

## 14. Loops in C++

Loops execute a block of code repeatedly.

### for Loop

```
for (int i = 1; i <= 5; i++) {
    std::cout << i << std::endl;
}
```

### while Loop

```
int i = 1;

while (i <= 5) {
    std::cout << i << std::endl;
    i++;
}
```

### do-while Loop

```
int i = 1;

do {
    std::cout << i << std::endl;
    i++;
} while (i <= 5);
```

## 15. Functions in C++

Functions organize programs into reusable blocks of code.

```
#include <iostream>

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(10, 20);

    std::cout << result << std::endl;

    return 0;
}
```

C++ supports function overloading, which allows multiple functions to share a name when their parameter lists differ appropriately.

## 16. Object-Oriented Programming in C++

C++ supports object-oriented programming through:

- Classes
    
- Objects
    
- Encapsulation
    
- Inheritance
    
- Polymorphism
    
- Abstraction
    

Example:

```
#include <iostream>
#include <string>

class Student {
public:
    std::string name;

    void display() {
        std::cout << name << std::endl;
    }
};

int main() {
    Student student;

    student.name = "Alex";
    student.display();

    return 0;
}
```

A class defines a type, while an object is an instance of that type.

These concepts are covered in more detail in [[C++ Classes and Objects]].

## 17. Memory Management in C++

C++ supports dynamic memory allocation.

### Using new

```
int *ptr = new int(100);
```

### Using delete

```
delete ptr;
ptr = nullptr;
```

For arrays:

```
int *numbers = new int[5];

delete[] numbers;
numbers = nullptr;
```

**Important:** C++ also provides safer resource-management techniques, including standard library containers and smart pointers. Prefer these over manual `new` and `delete` in most modern C++ application code.

## 18. C++ Standard Library

The C++ Standard Library provides reusable components.

Some commonly used headers:

|Header|Purpose|
|---|---|
|`<iostream>`|Input and output|
|`<string>`|String handling|
|`<vector>`|Dynamic arrays|
|`<algorithm>`|Common algorithms|
|`<map>`|Key-value containers|
|`<set>`|Unique-element containers|
|`<memory>`|Smart pointers|
|`<fstream>`|File handling|

Example using `vector`:

```
#include <iostream>
#include <vector>

int main() {
    std::vector<int> numbers = {10, 20, 30};

    for (int number : numbers) {
        std::cout << number << " ";
    }

    return 0;
}
```

## 19. C++ and Cybersecurity

C++ is relevant to cybersecurity because it is used in software that interacts closely with system resources.

Applications include:

- Security tool development.
    
- Network programming.
    
- Malware analysis.
    
- Reverse engineering.
    
- Operating system components.
    
- Digital forensics tools.
    
- Performance-critical security software.
    

### Important Security Topics

- Memory safety.
    
- Buffer overflow prevention.
    
- Pointer validation.
    
- Secure resource management.
    
- Input validation.
    
- Integer overflow.
    
- Safe file handling.
    

Understanding C++ helps security researchers analyze applications that use native compiled code.

## 20. Best Practices

1. Use meaningful variable and function names.
    
2. Initialize variables before reading their values.
    
3. Prefer `std::string` over manually managed character arrays when appropriate.
    
4. Prefer standard library containers such as `std::vector`.
    
5. Avoid unnecessary manual memory allocation.
    
6. Use smart pointers when dynamic ownership is needed.
    
7. Validate user input.
    
8. Compile with warnings enabled.
    
9. Test programs with different inputs.
    
10. Understand memory ownership and object lifetimes.
    

Example compiler command with useful warnings:

```
g++ -Wall -Wextra -Wpedantic hello.cpp -o hello
```

## 21. Practical Exercises

Write C++ programs to perform these tasks:

1. Display `Hello, C++!`.
    
2. Accept two integers and calculate their sum.
    
3. Check whether a number is even or odd.
    
4. Find the largest of three numbers.
    
5. Print numbers from 1 to 10 using a loop.
    
6. Create a function that calculates the square of a number.
    
7. Create a `Student` class with a name and a display function.
    
8. Store five integers in a `std::vector` and display them.
    

## 22. Key Takeaways

- C++ is a general-purpose, compiled, multi-paradigm programming language.
    
- It was developed by Bjarne Stroustrup.
    
- C++ evolved from C but is not simply another name for C.
    
- It supports procedural, object-oriented, and generic programming.
    
- `std::cout` displays output.
    
- `std::cin` reads formatted input.
    
- Functions improve code organization and reusability.
    
- Classes and objects support object-oriented programming.
    
- C++ provides dynamic memory management and standard library containers.
    
- C++ is widely used in systems programming and cybersecurity.
    

## 23. Related Notes

- [[Introduction to C]]
    
- [[C Variables and Data Types]]
    
- [[C Functions]]
    
- [[C Pointers]]
    
- [[C Memory Management]]
    
- [[Introduction to OOP]]
    
- [[C++ Classes and Objects]]
    
- [[C++ Memory Management]]
    
- [[Introduction to Secure Coding]]