> Understand how classes and objects organize data and functions into reusable structures using object-oriented programming.

## 1. What Is a Class?

A **class** is a user-defined data type that acts as a blueprint for creating objects.

It defines:

- Data members (variables).
    
- Member functions (functions).
    
- Access permissions.
    
- Object behavior.
    

Example:

```
class Student {
public:
    string name;
    int age;
};
```

Here, `Student` is a class containing two data members.

## 2. What Is an Object?

An **object** is an instance of a class.

A class defines the structure, while an object represents an actual instance containing its own data.

Example:

```
#include <iostream>
#include <string>

class Student {
public:
    std::string name;
    int age;
};

int main() {
    Student s1;

    s1.name = "Alex";
    s1.age = 20;

    std::cout << s1.name << std::endl;
    std::cout << s1.age << std::endl;

    return 0;
}
```

**Output:**

```
Alex
20
```

Here:

- `Student` is the class.
    
- `s1` is the object.
    
- `name` and `age` are data members.
    

## 3. Class Syntax

General syntax:

```
class ClassName {
    access_specifier:

        // Data members

        // Member functions
};
```

Example:

```
class Car {
public:
    std::string brand;
    int speed;

    void display() {
        std::cout << brand << " " << speed;
    }
};
```

Important: A class definition ends with a semicolon.

## 4. Creating Multiple Objects

A single class can create multiple objects.

```
#include <iostream>
#include <string>

class Student {
public:
    std::string name;
    int age;
};

int main() {
    Student s1;
    Student s2;

    s1.name = "Alex";
    s1.age = 20;

    s2.name = "Rahul";
    s2.age = 21;

    std::cout << s1.name << std::endl;
    std::cout << s2.name << std::endl;

    return 0;
}
```

Each object has its own instance data.

## 5. Data Members and Member Functions

### Data Members

Variables declared inside a class are called data members.

```
class Employee {
public:
    int id;
    std::string name;
};
```

### Member Functions

Functions declared inside a class are called member functions.

```
class Calculator {
public:
    int add(int a, int b) {
        return a + b;
    }
};
```

Calling the function:

```
Calculator c;

std::cout << c.add(10, 20);
```

Output:

```
30
```

## 6. Access Specifiers

Access specifiers control how class members can be accessed.

C++ provides three main access specifiers.

|Access Specifier|Accessibility|
|---|---|
|`public`|Accessible from outside the class through an object|
|`private`|Accessible only from the class and its friends|
|`protected`|Accessible from the class, its friends, and derived classes|

### A. Public

```
class Student {
public:
    int age;
};
```

The variable can be accessed through an object.

```
Student s;
s.age = 20;
```

### B. Private

```
class Student {
private:
    int age;
};
```

The variable cannot be accessed directly from outside the class.

### C. Protected

```
class Parent {
protected:
    int value;
};
```

The member can be accessed by derived classes, subject to the rules of inheritance.

**Important:** Class members are private by default in C++.

## 7. Encapsulation in Classes

Encapsulation means combining data and related functions inside a class while controlling access to the internal data.

Example:

```
#include <iostream>

class BankAccount {
private:
    double balance = 0;

public:
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    double getBalance() {
        return balance;
    }
};

int main() {
    BankAccount account;

    account.deposit(1000);

    std::cout << account.getBalance();

    return 0;
}
```

**Output:**

```
1000
```

The balance is private, so external code cannot directly modify it.

This allows the class to enforce rules before changing its internal state.

## 8. Constructors

A constructor is a special member function that initializes an object when it is created.

It:

- Has the same name as the class.
    
- Has no return type.
    
- Is called automatically during object initialization.
    

Example:

```
#include <iostream>

class Student {
public:
    Student() {
        std::cout << "Object created";
    }
};

int main() {
    Student s;

    return 0;
}
```

**Output:**

```
Object created
```

Constructors are explained in more detail in [[Constructors]].

## 9. Member Functions Outside the Class

Member functions can be declared inside a class and defined outside it using the scope resolution operator `::`.

Example:

```
#include <iostream>

class Calculator {
public:
    int add(int a, int b);
};

int Calculator::add(int a, int b) {
    return a + b;
}

int main() {
    Calculator c;

    std::cout << c.add(10, 20);

    return 0;
}
```

Output:

```
30
```

The `::` operator identifies which class the function belongs to.

## 10. The this Pointer

The `this` pointer is available inside non-static member functions.

It points to the current object.

Example:

```
#include <iostream>

class Student {
private:
    int age;

public:
    void setAge(int age) {
        this->age = age;
    }

    int getAge() {
        return this->age;
    }
};

int main() {
    Student s;

    s.setAge(20);

    std::cout << s.getAge();

    return 0;
}
```

Output:

```
20
```

Here:

- `age` refers to the function parameter.
    
- `this->age` refers to the current object's data member.
    

## 11. Static Members

A static data member belongs to the class rather than to each individual object.

All objects of that class share the same static data member.

Example:

```
#include <iostream>

class Student {
public:
    static int count;

    Student() {
        count++;
    }
};

int Student::count = 0;

int main() {
    Student s1;
    Student s2;
    Student s3;

    std::cout << Student::count;

    return 0;
}
```

Output:

```
3
```

A static member function can be called using the class name and does not have a `this` pointer.

## 12. Constant Member Functions

A member function declared with `const` promises not to modify the object's ordinary non-mutable data members.

Example:

```
#include <iostream>

class Student {
private:
    int age = 20;

public:
    int getAge() const {
        return age;
    }
};
```

This is useful for functions that only read object state.

## 13. Objects and Memory

Each object has its own storage for non-static data members.

Example:

```
class Student {
public:
    int age;
};
```

Creating objects:

```
Student s1;
Student s2;
```

Conceptually:

```
Class: Student
       |
       +------------------+
       |                  |
       v                  v
    Object s1          Object s2
    age = 20           age = 21
```

Static data members are shared at the class level rather than stored separately in each object.

## 14. Class vs Structure

C++ supports both `class` and `struct`.

|Feature|class|struct|
|---|---|---|
|Default member access|private|public|
|Default inheritance access|private|public|
|Supports member functions|Yes|Yes|
|Supports constructors|Yes|Yes|
|Supports inheritance|Yes|Yes|

Example:

```
struct Point {
    int x;
    int y;
};

class Employee {
    int id;
};
```

Both are capable of representing complex user-defined types.

## 15. Object Initialization

Objects can be initialized in several ways.

### Default Initialization

```
Student s1;
```

### Direct Initialization

```
Student s2(20);
```

This requires a suitable constructor.

### Brace Initialization

```
Student s3{20};
```

Brace initialization is useful because it can prevent certain unintended narrowing conversions.

The exact initialization behavior depends on the constructors and members defined by the class.

## 16. Relationship Between Classes and Objects

|Class|Object|
|---|---|
|Blueprint or type definition|Instance of a class|
|Defines data and behavior|Contains instance data|
|Defines the structure|Uses the structure|
|Example: `Student`|Example: `s1`|

Think of a class as a blueprint for a house and an object as an actual house constructed using that blueprint.

## 17. Classes and Cybersecurity

Classes are important in secure software development.

They can help organize security-related functionality.

Examples include:

- User authentication classes.
    
- Permission management classes.
    
- Secure file handling classes.
    
- Network connection classes.
    
- Encryption interface classes.
    
- Logging and auditing classes.
    

### Security Considerations

1. Keep sensitive data private where appropriate.
    
2. Validate inputs before modifying object state.
    
3. Enforce authorization checks in sensitive operations.
    
4. Avoid exposing internal implementation details unnecessarily.
    
5. Manage resources safely.
    
6. Do not assume that private members alone provide complete security.
    

**Important:** Access specifiers are language-level access controls, not a substitute for application security or operating-system permissions.

## 18. Practical Exercises

Write C++ programs to perform these tasks:

1. Create a `Student` class with name and age.
    
2. Create three objects of the same class.
    
3. Create a `Car` class with brand and speed.
    
4. Add a member function that displays object information.
    
5. Create a class with private data members.
    
6. Use public setter and getter functions.
    
7. Create a `BankAccount` class with deposit and balance functions.
    
8. Create a static member that counts the number of objects.
    
9. Create a constant member function.
    
10. Define a member function outside the class using `::`.
    

## 19. Key Takeaways

- A class is a user-defined type and blueprint for objects.
    
- An object is an instance of a class.
    
- Data members store object information.
    
- Member functions define object behavior.
    
- Access specifiers control member accessibility.
    
- Encapsulation combines data and related behavior.
    
- Constructors initialize objects.
    
- The `this` pointer refers to the current object.
    
- Static members belong to the class rather than individual instances.
    
- C++ classes are fundamental to object-oriented programming.
    

## 20. Related Notes

- [[Introduction to C++]]
    
- [[Introduction to OOP]]
    
- [[Classes and Objects]]
    
- [[Constructors]]
    
- [[Encapsulation]]
    
- [[Inheritance]]
    
- [[Polymorphism]]
    
- [[Abstraction]]
    
- [[C++ Memory Management]]
    
- [[Introduction to Secure Coding]]