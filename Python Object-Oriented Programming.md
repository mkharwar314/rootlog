> Learn how Python uses classes and objects to organize code, represent real-world entities, and build reusable applications.

## 1. What Is Object-Oriented Programming?

**Object-Oriented Programming (OOP)** is a programming paradigm that organizes code around objects rather than only functions and instructions.

An object combines:

- **Data:** Information stored in attributes.
    
- **Behaviour:** Actions implemented through methods.
    

For example, a security application might represent a file using an object containing its filename, size, and hash value.

Python supports four commonly discussed OOP principles:

1. Encapsulation
    
2. Inheritance
    
3. Polymorphism
    
4. Abstraction
    

## 2. Classes and Objects in Python

A **class** is a blueprint used to create objects.

An **object** is an instance of a class.

### Example

```
class Student:
    def display(self):
        print("Cybersecurity Student")


student1 = Student()
student1.display()
```

Output:

```
Cybersecurity Student
```

Explanation:

- `class Student` defines a class.
    
- `student1 = Student()` creates an object.
    
- `display()` is a method.
    
- `student1.display()` calls that method.
    

## 3. The `self` Parameter

`self` refers to the current object.

It allows instance methods to access the object's attributes and other methods.

```
class Student:
    def display(self):
        print("This is a student object")


student1 = Student()
student1.display()
```

Python automatically passes the object as the first argument when an instance method is called.

`self` is a naming convention, not a reserved keyword, but you should follow it.

## 4. The `__init__()` Method

`__init__()` is an initializer method that runs after an object has been created.

It is commonly used to initialize object attributes.

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

**Important distinction:**

- `__new__()` is responsible for creating and returning a new instance.
    
- `__init__()` initializes an already-created instance.
    

For normal application development, you will commonly work with `__init__()`.

## 5. Attributes and Methods

### Attributes

Attributes store information associated with an object or class.

### Methods

Methods are functions defined inside a class.

```
class Computer:
    def __init__(self, brand, ram):
        self.brand = brand
        self.ram = ram

    def show_details(self):
        print(self.brand, self.ram)


computer1 = Computer("ASUS", "16GB")
computer1.show_details()
```

Here:

- `brand` and `ram` are instance attributes.
    
- `show_details()` is an instance method.
    

## 6. Instance Attributes and Class Attributes

### Instance Attributes

Instance attributes belong to individual objects.

```
class Student:
    def __init__(self, name):
        self.name = name
```

Each object can have a different `name`.

### Class Attributes

Class attributes are defined directly inside the class and are shared through the class.

```
class Student:
    college = "ABC College"

    def __init__(self, name):
        self.name = name


student1 = Student("Mohit")
student2 = Student("Rahul")

print(student1.college)
print(student2.college)
```

Output:

```
ABC College
ABC College
```

Use class attributes for data that should be shared. Avoid using mutable class attributes for data that should belong independently to each object.

## 7. Types of Methods

Python commonly uses three method types.

### 7.1 Instance Method

Works with an individual object and receives `self`.

```
class Student:
    def display(self):
        print("Instance method")
```

### 7.2 Class Method

Works with the class and receives `cls`.

Use the `@classmethod` decorator.

```
class Student:
    college = "ABC College"

    @classmethod
    def show_college(cls):
        print(cls.college)


Student.show_college()
```

### 7.3 Static Method

A static method does not automatically receive `self` or `cls`.

Use `@staticmethod` when a function logically belongs to a class but does not need object or class state.

```
class Security:
    @staticmethod
    def is_valid_port(port):
        return 1 <= port <= 65535


print(Security.is_valid_port(443))
```

## 8. Encapsulation

**Encapsulation** means combining data and related methods within a class while controlling how internal state is accessed or modified.

Python uses naming conventions rather than strict private access modifiers.

### Public Attributes

Accessible normally.

```
self.username = "student"
```

### Protected Convention

A single leading underscore indicates that an attribute is intended for internal use.

```
self._status = "active"
```

This is a convention, not enforced access control.

### Name Mangling

A double leading underscore triggers name mangling.

```
class Account:
    def __init__(self):
        self.__balance = 5000
```

Python internally changes the attribute name to reduce accidental name conflicts. It does not make the attribute truly inaccessible.

### Using `@property`

Properties provide controlled access to attributes.

```
class Account:
    def __init__(self, balance):
        self._balance = balance

    @property
    def balance(self):
        return self._balance

    @balance.setter
    def balance(self, value):
        if value < 0:
            raise ValueError("Balance cannot be negative")
        self._balance = value


account = Account(5000)
print(account.balance)

account.balance = 7000
print(account.balance)
```

Properties allow validation without changing the public attribute-style interface.

## 9. Inheritance

**Inheritance** allows one class to reuse and extend the behaviour of another class.

- Parent class: The class being inherited from.
    
- Child class: The class that inherits from the parent.
    

```
class Device:
    def power_on(self):
        print("Device powered on")


class Computer(Device):
    def run_program(self):
        print("Program running")


computer = Computer()
computer.power_on()
computer.run_program()
```

The `Computer` class inherits `power_on()` from `Device`.

### The `super()` Function

`super()` provides access to methods in the next class in the method resolution order.

```
class Device:
    def __init__(self, name):
        self.name = name


class Computer(Device):
    def __init__(self, name, ram):
        super().__init__(name)
        self.ram = ram


computer = Computer("Laptop", "16GB")

print(computer.name)
print(computer.ram)
```

### Method Overriding

A child class can provide its own implementation of an inherited method.

```
class Device:
    def start(self):
        print("Starting device")


class Computer(Device):
    def start(self):
        print("Starting computer")


computer = Computer()
computer.start()
```

Output:

```
Starting computer
```

## 10. Types of Inheritance

Common inheritance structures include:

|Type|Description|
|---|---|
|Single|One child inherits from one parent|
|Multiple|One child inherits from multiple parents|
|Multilevel|A class inherits from a child class|
|Hierarchical|Multiple child classes inherit from one parent|
|Hybrid|A combination of inheritance structures|

### Multiple Inheritance Example

```
class Scanner:
    def scan(self):
        print("Scanning")


class Reporter:
    def report(self):
        print("Generating report")


class SecurityTool(Scanner, Reporter):
    pass


tool = SecurityTool()
tool.scan()
tool.report()
```

Python resolves inherited methods using the **Method Resolution Order (MRO)**.

You can inspect it using:

```
print(SecurityTool.mro())
```

## 11. Polymorphism

**Polymorphism** means that different objects can respond to the same method call in different ways.

```
class Windows:
    def start(self):
        print("Starting Windows")


class Linux:
    def start(self):
        print("Starting Linux")


def boot_system(system):
    system.start()


boot_system(Windows())
boot_system(Linux())
```

The same `boot_system()` function works with different object types.

### Duck Typing

Python often focuses on whether an object supports the required behaviour rather than checking its exact class.

This idea is known as **duck typing**.

If an object provides the required method, it can often be used by the calling code.

## 12. Abstraction

**Abstraction** hides implementation details and exposes the essential behaviour of an object.

Python supports abstraction through the `abc` module and abstract base classes.

```
from abc import ABC, abstractmethod


class Scanner(ABC):

    @abstractmethod
    def scan(self):
        pass


class FileScanner(Scanner):

    def scan(self):
        print("Scanning a file")


scanner = FileScanner()
scanner.scan()
```

A class with an unimplemented abstract method cannot be instantiated until the required method is implemented.

## 13. Special Methods (Dunder Methods)

Special methods are methods with double underscores at the beginning and end of their names.

They allow objects to work with Python's built-in operations.

|Method|Purpose|
|---|---|
|`__init__()`|Initializes an object|
|`__str__()`|Provides a readable string representation|
|`__repr__()`|Provides a developer-oriented representation|
|`__len__()`|Defines behaviour for `len()`|
|`__eq__()`|Defines equality comparison|
|`__add__()`|Defines addition behaviour|

Example:

```
class File:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"File: {self.name}"


file1 = File("report.txt")
print(file1)
```

Output:

```
File: report.txt
```

## 14. Composition vs Inheritance

These are two ways to reuse and organize code.

### Inheritance

Represents an "is-a" relationship.

Example: A `Laptop` is a `Computer`.

### Composition

Represents a "has-a" relationship.

Example: A `Computer` has a `Processor`.

```
class Processor:
    def start(self):
        print("Processor started")


class Computer:
    def __init__(self):
        self.processor = Processor()

    def start(self):
        self.processor.start()


computer = Computer()
computer.start()
```

**Practical guideline:** Prefer composition when an object uses another object's functionality without needing to be a specialized version of it.

## 15. Dataclasses

Python's `dataclasses` module helps create classes mainly used to store data.

```
from dataclasses import dataclass


@dataclass
class Student:
    name: str
    course: str


student = Student("Mohit", "Cybersecurity")

print(student)
```

Dataclasses can automatically generate methods such as `__init__()` and `__repr__()`.

They are useful for structured records and configuration data.

## 16. OOP in Cybersecurity

OOP helps organize cybersecurity tools into reusable components.

For example, a file integrity checker can be represented as a class.

```
import hashlib
from pathlib import Path


class FileIntegrityChecker:

    def calculate_sha256(self, file_path):
        path = Path(file_path)

        if not path.is_file():
            raise FileNotFoundError("File does not exist")

        sha256 = hashlib.sha256()

        with path.open("rb") as file:
            for chunk in iter(lambda: file.read(4096), b""):
                sha256.update(chunk)

        return sha256.hexdigest()


checker = FileIntegrityChecker()

file_hash = checker.calculate_sha256("sample.txt")
print("SHA-256:", file_hash)
```

This example:

- Uses a class to organize file-integrity functionality.
    
- Reads a local file in binary mode.
    
- Processes the file in chunks.
    
- Calculates its SHA-256 hash.
    

The hash can later be compared with a trusted baseline to identify possible file changes. A hash alone does not prove who modified a file or when it was modified.

## 17. Security Considerations When Using OOP

When developing security-related applications:

1. Do not store passwords as plain-text attributes.
    
2. Avoid printing passwords, API keys, or tokens in logs.
    
3. Validate data before using it.
    
4. Handle exceptions without exposing sensitive internal details.
    
5. Use appropriate access controls outside the class when protecting application data.
    
6. Avoid assuming that underscore-prefixed attributes are secure.
    
7. Keep responsibilities separated so individual components can be tested and maintained.
    

**Important:** Encapsulation improves code organization, but it is not a replacement for application security controls.

## 18. Practical Exercises

### Exercise 1 — Create a Student Class

Create a class with:

- `name`
    
- `course`
    
- `year`
    

Add a method that displays the student's information.

### Exercise 2 — Create a Computer Class

Create a class with:

- `brand`
    
- `ram`
    
- `storage`
    

Add a method to display computer specifications.

### Exercise 3 — Practice Inheritance

Create:

- A parent class named `OperatingSystem`.
    
- A child class named `Linux`.
    
- A method named `boot()`.
    

Override the `boot()` method in the child class.

### Exercise 4 — Practice Encapsulation

Create a `BankAccount` class.

Requirements:

- Store the balance internally.
    
- Provide a property to read the balance.
    
- Reject negative balance updates.
    

### Exercise 5 — Build a File Integrity Checker

Extend the example in this note.

Requirements:

- Accept a local file path.
    
- Calculate its SHA-256 hash.
    
- Display the filename and hash.
    
- Handle missing files.
    

Use only files you own or are authorized to examine.

## 19. Key Takeaways

- OOP organizes programs around classes and objects.
    
- Classes define structure; objects are instances of classes.
    
- `self` refers to the current instance.
    
- `__init__()` initializes an object.
    
- Instance attributes belong to individual objects; class attributes belong to the class.
    
- Encapsulation organizes and controls access to internal state.
    
- Inheritance enables code reuse and specialization.
    
- Polymorphism allows different objects to support a common interface.
    
- Abstraction exposes essential behaviour while hiding implementation details.
    
- Composition is often preferable when one object simply uses another.
    
- OOP is useful for building modular cybersecurity tools.
    

## 20. Related Notes

- [[Introduction to OOP]]
    
- [[Classes and Objects]]
    
- [[Constructors]]
    
- [[Encapsulation]]
    
- [[Inheritance]]
    
- [[Polymorphism]]
    
- [[Abstraction]]
    
- [[Python Functions]]
    
- [[Python Data Structures]]
    
- [[Python Exception Handling]]
    
- [[Python for Cybersecurity]]
    
- [[File Integrity Monitoring]]
    
- [[Secure Coding]]