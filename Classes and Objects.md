> Classes and objects are the fundamental building blocks of Object-Oriented Programming (OOP). A class defines the structure and behavior, while an object is an individual instance created from that class.

## 1. What Is a Class?

A class is a blueprint or template used to create objects.

It defines:

- Attributes: Data associated with an object.
    
- Methods: Functions that define an object's behavior.
    

Example:

Imagine designing a blueprint for a car.

The blueprint defines:

- Brand
    
- Model
    
- Colour
    
- Speed
    
- Start method
    
- Stop method
    

The blueprint itself is not a physical car. It describes how individual car objects should be structured.

## 2. What Is an Object?

An object is an instance of a class.

An object contains:

- Identity: What distinguishes it from other objects.
    
- State: The current values of its attributes.
    
- Behavior: The operations it can perform through methods.
    

Example:

```
Class: Car

Objects:
    car1
    car2
    car3
```

Each object belongs to the same class but can have different attribute values.

## 3. Class vs Object

|Feature|Class|Object|
|---|---|---|
|Meaning|Blueprint or template|Instance of a class|
|Purpose|Defines structure and behavior|Represents an individual entity|
|Creation|Defined by the programmer|Created from a class|
|Attributes|Defines available attributes|Holds actual attribute values|
|Example|Car|A specific red car|

Remember:

**Class = Blueprint**

**Object = Actual instance created from the blueprint**

## 4. Creating a Class in Python

Python uses the `class` keyword to define a class.

Syntax:

```
class ClassName:
    # Attributes and methods
    pass
```

Example:

```
class Student:
    pass
```

Here:

- `class` defines a new class.
    
- `Student` is the class name.
    
- `pass` is a placeholder that does nothing.
    

Python class names commonly use PascalCase, such as `StudentRecord`.

## 5. Creating an Object

An object is created by calling the class name like a function.

Example:

```
class Student:
    pass


student1 = Student()
student2 = Student()
```

Here:

- `Student` is the class.
    
- `student1` is an object.
    
- `student2` is another object.
    

Both objects are instances of the same class.

## 6. Attributes

Attributes are variables associated with a class or its objects.

There are two common types.

### A. Instance Attributes

Instance attributes belong to individual objects.

Example:

```
class Student:

    def __init__(self, name, age):
        self.name = name
        self.age = age


student1 = Student("Mohit", 18)
student2 = Student("Rahul", 20)

print(student1.name)
print(student2.name)
```

Output:

```
Mohit
Rahul
```

Each object stores its own values.

### B. Class Attributes

Class attributes are defined directly inside the class and are shared through the class unless an instance overrides the name.

Example:

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

Both objects can access the class attribute.

## 7. What Is self in Python?

`self` refers to the current object instance.

It allows instance methods to access and modify that object's attributes.

Example:

```
class Student:

    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)


student1 = Student("Mohit")

student1.display()
```

Output:

```
Mohit
```

Explanation:

- `self.name` refers to the `name` attribute of the current object.
    
- When `student1.display()` is called, Python passes `student1` as the first argument automatically.
    

`self` is a naming convention in Python, not a reserved keyword. However, using it is the standard practice.

## 8. What Is a Constructor?

A constructor is commonly understood as the mechanism used to initialize an object.

In Python, `__init__()` is the initializer method.

It is automatically called after a new instance has been created.

Example:

```
class Student:

    def __init__(self, name, course):
        self.name = name
        self.course = course


student1 = Student("Mohit", "Cybersecurity")

print(student1.name)
print(student1.course)
```

Output:

```
Mohit
Cybersecurity
```

The initializer assigns the supplied values to the new object's attributes.

Note: Python's actual object-creation method is `__new__()`. The `__init__()` method initializes the created instance.

See [[Constructors]] for more details.

## 9. Instance Methods

Instance methods operate on individual objects.

They take `self` as their first parameter.

Example:

```
class BankAccount:

    def __init__(self, balance):
        self.balance = balance

    def display_balance(self):
        print("Balance:", self.balance)


account1 = BankAccount(5000)

account1.display_balance()
```

Output:

```
Balance: 5000
```

The method accesses the balance belonging to `account1`.

## 10. Class Methods

Class methods operate on the class itself rather than a particular instance.

Python uses the `@classmethod` decorator, and the first parameter is conventionally named `cls`.

Example:

```
class Student:

    college = "ABC College"

    @classmethod
    def change_college(cls, new_college):
        cls.college = new_college


Student.change_college("XYZ College")

print(Student.college)
```

Output:

```
XYZ College
```

Class methods are useful for operations involving class-level data and alternative object-creation methods.

## 11. Static Methods

Static methods are functions placed inside a class namespace that do not automatically receive an instance or class reference.

Python uses the `@staticmethod` decorator.

Example:

```
class Calculator:

    @staticmethod
    def add(a, b):
        return a + b


print(Calculator.add(10, 20))
```

Output:

```
30
```

Static methods are useful when a function is logically related to a class but does not need access to instance or class attributes.

## 12. Instance Method vs Class Method vs Static Method

|Feature|Instance Method|Class Method|Static Method|
|---|---|---|---|
|Decorator|None required|`@classmethod`|`@staticmethod`|
|First parameter|`self`|`cls`|No automatic reference|
|Access instance data|Yes|No direct instance reference|No automatic access|
|Access class data|Yes|Yes|No automatic access|
|Common use|Object behavior|Class-level operations|Related utility functions|

## 13. Modifying Object Attributes

Object attributes can be modified after object creation.

Example:

```
class Student:

    def __init__(self, name, age):
        self.name = name
        self.age = age


student1 = Student("Mohit", 18)

student1.age = 19

print(student1.age)
```

Output:

```
19
```

You can also add an attribute to an individual object dynamically:

```
student1.city = "Mumbai"

print(student1.city)
```

This is allowed for ordinary Python objects, although some classes restrict dynamic attributes.

## 14. Multiple Objects from One Class

A single class can create multiple independent objects.

Example:

```
class Device:

    def __init__(self, name, ip):
        self.name = name
        self.ip = ip

    def display(self):
        print(self.name, self.ip)


device1 = Device("Router", "192.168.1.1")
device2 = Device("Laptop", "192.168.1.10")
device3 = Device("Server", "192.168.1.20")

device1.display()
device2.display()
device3.display()
```

Each object stores its own device information.

## 15. Object Identity and Equality

Two objects can have identical attribute values but still be separate objects.

Example:

```
class Student:

    def __init__(self, name):
        self.name = name


student1 = Student("Mohit")
student2 = Student("Mohit")

print(student1 is student2)
print(student1 == student2)
```

For this class, the output is:

```
False
False
```

Explanation:

- `is` checks whether two references point to the same object.
    
- `==` checks equality according to the class's equality implementation.
    
- By default, ordinary user-defined objects generally use identity-based equality unless equality behavior is customized.
    

## 16. Object-Oriented Programming in Cybersecurity

Classes and objects help organize cybersecurity applications.

Example: Representing a network host.

```
class NetworkHost:

    def __init__(self, ip, hostname):
        self.ip = ip
        self.hostname = hostname

    def display(self):
        print("IP Address:", self.ip)
        print("Hostname:", self.hostname)


host1 = NetworkHost(
    "192.168.1.10",
    "workstation"
)

host1.display()
```

Possible classes in a security application:

```
Security Monitoring System
│
├── NetworkHost
├── SecurityEvent
├── Alert
├── LogAnalyzer
└── ForensicEvidence
```

Each class represents a particular component of the application.

This structure makes it easier to organize, extend, and maintain the code.

## 17. Common Mistakes

1. Forgetting `self` in an instance method.
    
2. Confusing a class with an object.
    
3. Using instance attributes when class attributes are intended.
    
4. Accessing an attribute before it has been initialized.
    
5. Assuming two objects with identical data are the same object.
    
6. Using mutable class attributes when separate per-object data is required.
    

### Example of a Mutable Class Attribute Problem

Incorrect:

```
class Student:

    subjects = []

    def __init__(self, name):
        self.name = name


student1 = Student("Mohit")
student2 = Student("Rahul")

student1.subjects.append("Networking")

print(student2.subjects)
```

Output:

```
['Networking']
```

Both instances refer to the same class-level list.

Correct:

```
class Student:

    def __init__(self, name):
        self.name = name
        self.subjects = []


student1 = Student("Mohit")
student2 = Student("Rahul")

student1.subjects.append("Networking")

print(student2.subjects)
```

Output:

```
[]
```

Each object now has its own list.

## 18. Practical Tasks

Complete these exercises in Python:

1. Create a `Laptop` class with brand, model, and RAM attributes.
    
2. Create three laptop objects with different values.
    
3. Add a method that displays laptop information.
    
4. Create a `NetworkDevice` class with IP address and device type.
    
5. Add an instance method to display device information.
    
6. Add a class attribute named `organization`.
    
7. Create a class method that changes the organization name.
    
8. Create a static method that validates whether a string resembles an IPv4 address. For a complete validator, check all four octets and ensure each is between 0 and 255.
    

**Challenge:** Create a `SecurityEvent` class with event type, source IP, and severity. Create three objects and write a method that displays their information.

## 19. Key Takeaways

- A class is a blueprint for creating objects.
    
- An object is an instance of a class.
    
- Attributes represent data.
    
- Methods represent behavior.
    
- `self` refers to the current instance.
    
- `__init__()` initializes newly created objects.
    
- Instance attributes belong to individual objects.
    
- Class attributes are associated with the class.
    
- Python supports instance methods, class methods, and static methods.
    
- Multiple objects can be created from one class.
    

## 20. Related Notes

- [[Introduction to OOP]]
    
- [[Constructors]]
    
- [[Encapsulation]]
    
- [[Inheritance]]
    
- [[Polymorphism]]
    
- [[Abstraction]]
    
- [[Python Object-Oriented Programming]]
    
- [[04 - Programming]]