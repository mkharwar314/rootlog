# I> Object-Oriented Programming (OOP) is a programming approach that organizes software around objects containing data and methods. It helps developers build modular, reusable, and maintainable applications.

## 1. What Is Object-Oriented Programming?

Object-Oriented Programming is a programming paradigm in which programs are designed using **classes and objects**.

An object represents an entity with:

- **Attributes:** Data or properties describing the object.
    
- **Methods:** Functions that define the object's behavior.
    

Example:

Imagine a car.

Attributes:

- Brand
    
- Model
    
- Colour
    
- Speed
    

Methods:

- Start
    
- Stop
    
- Accelerate
    
- Brake
    

A car object combines its data and behavior into one logical unit.

## 2. What Is a Programming Paradigm?

A programming paradigm is a style or approach used to design and organize programs.

Common programming paradigms include:

|Paradigm|Description|
|---|---|
|Procedural Programming|Organizes programs around procedures and functions.|
|Object-Oriented Programming|Organizes programs around objects and classes.|
|Functional Programming|Uses functions and emphasizes expressions and data transformations.|
|Logic Programming|Uses logical rules and relationships to solve problems.|

OOP is widely used in application development, software engineering, game development, and enterprise systems.

## 3. Classes and Objects

Classes and objects are the foundation of OOP.

### Class

A class is a blueprint or template used to create objects.

It defines the attributes and methods that its objects can have.

### Object

An object is an instance of a class.

For example:

```
Class: Car

Objects:
- Car 1
- Car 2
- Car 3
```

Each object can have different attribute values while sharing the structure defined by the class.

See [[Classes and Objects]] for a detailed explanation.

## 4. Example of OOP in Python

```
class Student:

    def __init__(self, name, course):
        self.name = name
        self.course = course

    def display(self):
        print("Name:", self.name)
        print("Course:", self.course)


student1 = Student("Mohit", "Cybersecurity")

student1.display()
```

Output:

```
Name: Mohit
Course: Cybersecurity
```

Explanation:

- `class Student` defines a class.
    
- `__init__()` initializes an object's attributes.
    
- `self` refers to the current instance.
    
- `name` and `course` are instance attributes.
    
- `display()` is an instance method.
    
- `student1` is an object of the `Student` class.
    

## 5. Four Main Pillars of OOP

OOP is commonly explained through four fundamental principles:

1. Encapsulation
    
2. Inheritance
    
3. Polymorphism
    
4. Abstraction
    

### A. Encapsulation

Encapsulation combines data and related methods inside a class while controlling how internal data is accessed or modified.

Example:

```
class BankAccount:

    def __init__(self, balance):
        self.__balance = balance

    def get_balance(self):
        return self.__balance


account = BankAccount(5000)

print(account.get_balance())
```

Output:

```
5000
```

Here, `__balance` uses Python's name-mangling convention. It discourages direct access but is not a strict security boundary.

Benefits:

- Organizes related data and behavior.
    
- Controls access through methods and properties.
    
- Reduces unintended modifications.
    

See [[Encapsulation]].

### B. Inheritance

Inheritance allows one class to derive attributes and methods from another class.

Example:

```
class Animal:

    def eat(self):
        print("Animal is eating")


class Dog(Animal):

    def bark(self):
        print("Dog is barking")


dog = Dog()

dog.eat()
dog.bark()
```

Output:

```
Animal is eating
Dog is barking
```

Here:

- `Animal` is the parent class.
    
- `Dog` is the child class.
    
- `Dog` inherits the `eat()` method.
    

Benefits:

- Code reuse.
    
- Easier extension of existing classes.
    
- Clear relationships between related types.
    

See [[Inheritance]].

### C. Polymorphism

Polymorphism means that different objects can respond to the same operation in different ways.

Example:

```
class Cat:

    def sound(self):
        print("Meow")


class Dog:

    def sound(self):
        print("Bark")


animals = [Cat(), Dog()]

for animal in animals:
    animal.sound()
```

Output:

```
Meow
Bark
```

Both objects provide a `sound()` method, but each behaves differently.

Benefits:

- Flexible code.
    
- Easier extension.
    
- Common interfaces for different implementations.
    

See [[Polymorphism]].

### D. Abstraction

Abstraction hides unnecessary implementation details and exposes the essential operations of an object.

Example:

When using an ATM, you can withdraw money without knowing how the ATM communicates with the banking server internally.

Python supports abstraction through abstract base classes.

```
from abc import ABC, abstractmethod


class Payment(ABC):

    @abstractmethod
    def pay(self, amount):
        pass


class UPI(Payment):

    def pay(self, amount):
        print("Paid:", amount)


payment = UPI()
payment.pay(500)
```

Output:

```
Paid: 500
```

The `Payment` class defines an abstract operation. The `UPI` class provides its implementation.

Benefits:

- Reduces unnecessary complexity.
    
- Defines common interfaces.
    
- Separates what an object does from how it does it.
    

See [[Abstraction]].

## 6. Important OOP Terminology

|Term|Meaning|
|---|---|
|Class|Blueprint for creating objects.|
|Object|Instance of a class.|
|Attribute|Data associated with an object or class.|
|Method|Function defined inside a class.|
|Constructor|Mechanism used to initialize an object.|
|Instance|An individual object created from a class.|
|Inheritance|Deriving a class from another class.|
|Encapsulation|Bundling data and methods with controlled access.|
|Polymorphism|Different objects responding to the same interface.|
|Abstraction|Exposing essential behavior while hiding implementation details.|

## 7. Advantages of OOP

1. **Code Reusability:** Existing classes can be reused through composition and inheritance.
    
2. **Modularity:** Programs can be divided into independent classes.
    
3. **Maintainability:** Related functionality can be organized together.
    
4. **Scalability:** New classes and behavior can be added as requirements grow.
    
5. **Data Organization:** Attributes and methods are grouped logically.
    
6. **Extensibility:** Different implementations can follow common interfaces.
    

## 8. Disadvantages of OOP

1. **Complexity:** Poorly designed class structures can make programs difficult to understand.
    
2. **Overengineering:** Simple problems may become unnecessarily complicated.
    
3. **Memory Overhead:** Objects and their associated structures can require additional memory.
    
4. **Learning Curve:** Understanding inheritance, abstraction, and object relationships takes practice.
    
5. **Tight Coupling:** Poor class design can make components heavily dependent on each other.
    

OOP is useful, but it is not automatically the best choice for every problem.

## 9. OOP vs Procedural Programming

|Feature|OOP|Procedural Programming|
|---|---|---|
|Organization|Classes and objects|Functions and procedures|
|Main focus|Objects and their behavior|Steps and operations|
|Data handling|Often grouped with methods|Commonly passed between functions|
|Reusability|Classes, composition, inheritance|Functions and modules|
|Suitable for|Complex object-based systems|Many task-oriented programs|
|Examples|Java, C++, Python|C, procedural Python|

Python supports both procedural and object-oriented programming.

C is primarily procedural, while C++ supports both procedural and object-oriented programming.

## 10. Real-World Applications of OOP

OOP is commonly used in:

- Banking applications.
    
- Inventory management systems.
    
- Hospital management systems.
    
- E-commerce platforms.
    
- Desktop applications.
    
- Game development.
    
- Enterprise software.
    
- Mobile application development.
    

For example, a banking application may contain:

```
Banking System
│
├── Customer
├── BankAccount
├── Transaction
├── Loan
└── Payment
```

Each class represents a different concept within the system.

## 11. OOP in Cybersecurity

OOP is useful when developing security tools and applications.

### A. User Authentication

A program can represent users through a `User` class containing account-related attributes and authentication methods.

### B. Security Monitoring

A monitoring application can use separate classes for:

- Log files.
    
- Events.
    
- Alerts.
    
- Detection rules.
    

### C. Network Scanning

A network-scanning application can organize hosts, ports, and scan results into separate classes.

### D. Digital Forensics

A forensic application can represent:

- Evidence files.
    
- Hash records.
    
- Investigators.
    
- Forensic reports.
    

### Example: Basic Security Event Class

```
class SecurityEvent:

    def __init__(self, event_type, source_ip):
        self.event_type = event_type
        self.source_ip = source_ip

    def display(self):
        print("Event:", self.event_type)
        print("Source IP:", self.source_ip)


event = SecurityEvent(
    "Failed Login",
    "192.168.1.50"
)

event.display()
```

This example organizes security event information into an object. It is a basic demonstration, not a complete detection system.

## 12. When Should You Use OOP?

OOP is useful when:

- Your application contains multiple related entities.
    
- You need reusable components.
    
- You want to organize complex application logic.
    
- Different objects share common behavior.
    
- Your project needs to grow over time.
    

Procedural programming may be simpler when:

- The task is small.
    
- The program performs a straightforward sequence of operations.
    
- A class structure would add unnecessary complexity.
    

Choose the programming approach based on the problem, not just the popularity of a paradigm.

## 13. Practical Tasks

Complete these exercises in Python:

1. Create a `Student` class with `name`, `age`, and `course` attributes.
    
2. Create two objects from the `Student` class.
    
3. Add a method that displays student information.
    
4. Create a `BankAccount` class with deposit and withdrawal methods.
    
5. Create an `Animal` parent class and two child classes.
    
6. Demonstrate polymorphism using a common method.
    
7. Create an abstract `SecurityTool` class and implement it in a child class.
    

**Challenge:** Design a simple cybersecurity monitoring system using OOP. Create classes for `SecurityEvent`, `Alert`, and `LogAnalyzer`. Keep the implementation simple and focus on understanding how objects interact.

## 14. Key Takeaways

- OOP is a programming paradigm based on classes and objects.
    
- Classes define structure and behavior.
    
- Objects are instances of classes.
    
- Attributes store information.
    
- Methods define behavior.
    
- The four main OOP principles are encapsulation, inheritance, polymorphism, and abstraction.
    
- OOP promotes modularity and code reuse.
    
- OOP is useful for building maintainable applications and cybersecurity tools.
    

## 15. Related Notes

- [[Programming Languages]]
    
- [[Introduction to Functions]]
    
- [[Modules and Libraries]]
    
- [[Classes and Objects]]
    
- [[Constructors]]
    
- [[Encapsulation]]
    
- [[Inheritance]]
    
- [[Polymorphism]]
    
- [[Abstraction]]
    
- [[Python Object-Oriented Programming]]
    
- [[04 - Programming]]