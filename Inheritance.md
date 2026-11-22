> Inheritance is an Object-Oriented Programming (OOP) principle that allows one class to acquire attributes and methods from another class. It promotes code reuse and helps establish relationships between classes.

## 1. What Is Inheritance?

Inheritance allows a new class to reuse and extend the functionality of an existing class.

For example, consider an animal classification system.

```
             Animal
                |
       -----------------
       |               |
      Dog             Cat
```

Here:

- `Animal` is the parent class.
    
- `Dog` is a child class.
    
- `Cat` is another child class.
    

Both child classes can inherit common behavior from the parent class.

## 2. Why Is Inheritance Used?

Inheritance helps developers:

1. Reuse existing code.
    
2. Reduce unnecessary code duplication.
    
3. Organize related classes.
    
4. Extend existing functionality.
    
5. Create hierarchical relationships.
    
6. Maintain consistent behavior across related classes.
    

Instead of implementing the same methods repeatedly, common functionality can be placed in a parent class.

## 3. Important Inheritance Terminology

|Term|Meaning|
|---|---|
|Parent Class|Class whose features are inherited|
|Base Class|Another name for a parent class|
|Superclass|Another name for a parent class|
|Child Class|Class that inherits from another class|
|Derived Class|Another name for a child class|
|Subclass|Another name for a child class|
|Method Overriding|Redefining an inherited method in a child class|

## 4. Basic Inheritance in Python

Python uses parentheses after the child class name to specify its parent class.

Syntax:

```
class Parent:
    # Parent attributes and methods
    pass


class Child(Parent):
    # Child attributes and methods
    pass
```

Example:

```
class Animal:

    def eat(self):
        print("Animal is eating")


class Dog(Animal):

    def bark(self):
        print("Dog is barking")


dog1 = Dog()

dog1.eat()
dog1.bark()
```

Output:

```
Animal is eating
Dog is barking
```

Explanation:

- `Animal` defines the `eat()` method.
    
- `Dog` inherits from `Animal`.
    
- `Dog` also defines its own `bark()` method.
    
- The `dog1` object can use both methods.
    

## 5. Types of Inheritance

Inheritance is commonly classified into five types:

1. Single Inheritance
    
2. Multiple Inheritance
    
3. Multilevel Inheritance
    
4. Hierarchical Inheritance
    
5. Hybrid Inheritance
    

### A. Single Inheritance

Single inheritance occurs when one child class inherits from one parent class.

Structure:

```
Parent
   |
 Child
```

Example:

```
class Vehicle:

    def start(self):
        print("Vehicle started")


class Car(Vehicle):

    def drive(self):
        print("Car is moving")


car1 = Car()

car1.start()
car1.drive()
```

Output:

```
Vehicle started
Car is moving
```

Use case: A `Car` class inherits common vehicle functionality.

### B. Multiple Inheritance

Multiple inheritance occurs when one child class inherits from more than one parent class.

Structure:

```
Parent1       Parent2
    \           /
       Child
```

Example:

```
class Camera:

    def take_photo(self):
        print("Photo captured")


class Phone:

    def make_call(self):
        print("Calling...")


class Smartphone(Camera, Phone):
    pass


device = Smartphone()

device.take_photo()
device.make_call()
```

Output:

```
Photo captured
Calling...
```

The `Smartphone` class inherits functionality from both parent classes.

### C. Multilevel Inheritance

Multilevel inheritance occurs when a class inherits from another child class, forming a chain.

Structure:

```
Grandparent
     |
   Parent
     |
    Child
```

Example:

```
class Animal:

    def eat(self):
        print("Eating")


class Dog(Animal):

    def bark(self):
        print("Barking")


class Puppy(Dog):

    def play(self):
        print("Playing")


puppy1 = Puppy()

puppy1.eat()
puppy1.bark()
puppy1.play()
```

Output:

```
Eating
Barking
Playing
```

The `Puppy` class can access inherited methods from both `Dog` and `Animal`.

### D. Hierarchical Inheritance

Hierarchical inheritance occurs when multiple child classes inherit from the same parent class.

Structure:

```
          Parent
         /      \
      Child1   Child2
```

Example:

```
class Animal:

    def eat(self):
        print("Animal is eating")


class Dog(Animal):

    def bark(self):
        print("Dog is barking")


class Cat(Animal):

    def meow(self):
        print("Cat is meowing")


dog = Dog()
cat = Cat()

dog.eat()
dog.bark()

cat.eat()
cat.meow()
```

Both child classes inherit the common `eat()` method.

### E. Hybrid Inheritance

Hybrid inheritance combines two or more inheritance patterns.

Example:

```
          Animal
         /      \
       Dog      Cat
         \      /
         PetAnimal
```

Python can represent hybrid inheritance using multiple and multilevel inheritance structures.

However, complicated inheritance hierarchies can become difficult to maintain.

## 6. Method Overriding

Method overriding occurs when a child class provides its own implementation of a method inherited from its parent class.

Example:

```
class Animal:

    def sound(self):
        print("Animal makes a sound")


class Dog(Animal):

    def sound(self):
        print("Dog barks")


animal = Animal()
dog = Dog()

animal.sound()
dog.sound()
```

Output:

```
Animal makes a sound
Dog barks
```

The `Dog` class overrides the inherited `sound()` method.

Method overriding is an important mechanism used to achieve runtime polymorphism in many OOP languages.

## 7. The super() Function

Python provides `super()` to access methods from a parent class according to the method resolution order.

Example:

```
class Animal:

    def __init__(self, name):
        self.name = name


class Dog(Animal):

    def __init__(self, name, breed):
        super().__init__(name)
        self.breed = breed


dog1 = Dog("Bruno", "Labrador")

print(dog1.name)
print(dog1.breed)
```

Output:

```
Bruno
Labrador
```

Explanation:

- `Dog` inherits from `Animal`.
    
- The child class defines its own initializer.
    
- `super().__init__(name)` invokes the parent initializer through Python's method resolution order.
    
- The child class initializes its additional `breed` attribute.
    

`super()` is especially important when working with multiple inheritance and cooperative class design.

## 8. Method Resolution Order (MRO)

Method Resolution Order determines the order in which Python searches classes for methods and attributes.

This is particularly important in multiple inheritance.

Example:

```
class A:

    def show(self):
        print("Class A")


class B(A):

    def show(self):
        print("Class B")


class C(A):

    def show(self):
        print("Class C")


class D(B, C):
    pass


obj = D()

obj.show()

print(D.mro())
```

Output begins with:

```
Class B
```

Python follows its method resolution order to decide which implementation is selected.

The MRO can also be inspected using:

```
print(D.__mro__)
```

Python uses the C3 linearization algorithm to calculate the MRO.

## 9. Inheritance vs Composition

Inheritance is not always the best way to reuse functionality.

Composition is another important design approach.

### Inheritance

Represents an **is-a** relationship.

Example:

```
Dog is an Animal.
```

### Composition

Represents a **has-a** relationship.

Example:

```
Car has an Engine.
```

Python composition example:

```
class Engine:

    def start(self):
        print("Engine started")


class Car:

    def __init__(self):
        self.engine = Engine()

    def start_car(self):
        self.engine.start()


car1 = Car()

car1.start_car()
```

Output:

```
Engine started
```

Here, the `Car` object contains an `Engine` object.

Use inheritance when there is a genuine subtype relationship. Use composition when one object needs to use another object's functionality.

## 10. Advantages of Inheritance

1. **Code Reusability:** Existing methods can be reused.
    
2. **Reduced Duplication:** Common functionality can be implemented once.
    
3. **Extensibility:** Child classes can add new behavior.
    
4. **Maintainability:** Shared behavior can be updated in a parent class.
    
5. **Polymorphism:** Different child classes can implement common interfaces.
    

## 11. Disadvantages of Inheritance

1. **Tight Coupling:** Child classes depend on parent-class behavior.
    
2. **Complexity:** Deep inheritance hierarchies can become difficult to understand.
    
3. **Fragile Base Class Problem:** Changes in a parent class may unexpectedly affect child classes.
    
4. **Unnecessary Reuse:** Inheritance can create confusing relationships when used only to reuse code.
    
5. **Multiple Inheritance Complexity:** Method resolution can become difficult to reason about.
    

Inheritance should represent a meaningful relationship, not simply be used to avoid writing repeated code.

## 12. Inheritance in Different Programming Languages

### Python

```
class Animal:
    def eat(self):
        print("Eating")


class Dog(Animal):
    def bark(self):
        print("Barking")
```

### Java

```
class Animal {

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }
}
```

Java classes support single inheritance of classes, but multiple inheritance of class implementations is not supported. Java supports multiple interfaces.

### C++

```
#include <iostream>
using namespace std;

class Animal {

public:
    void eat() {
        cout << "Eating" << endl;
    }
};

class Dog : public Animal {

public:
    void bark() {
        cout << "Barking" << endl;
    }
};

int main() {

    Dog dog1;

    dog1.eat();
    dog1.bark();

    return 0;
}
```

C++ supports multiple inheritance of classes.

## 13. Inheritance in Cybersecurity

Inheritance can help organize security applications.

For example, a security monitoring system may contain a common event class and specialized event types.

```
             SecurityEvent
              /         \
       LoginEvent    NetworkEvent
```

Example:

```
class SecurityEvent:

    def __init__(self, source_ip, severity):
        self.source_ip = source_ip
        self.severity = severity


class LoginEvent(SecurityEvent):

    def __init__(self, source_ip, severity, username):
        super().__init__(source_ip, severity)
        self.username = username

    def display(self):
        print("Login Event")
        print("Source IP:", self.source_ip)
        print("Username:", self.username)
        print("Severity:", self.severity)


event1 = LoginEvent(
    "192.168.1.50",
    "High",
    "student"
)

event1.display()
```

Possible uses:

- Different security event types.
    
- Network device models.
    
- Forensic evidence categories.
    
- Security alert classifications.
    
- Authentication mechanisms.
    

A good design should avoid inheriting from classes that do not represent a genuine subtype relationship.

## 14. Common Mistakes

### Mistake 1: Forgetting to Inherit

Incorrect:

```
class Dog:
    pass
```

Correct:

```
class Dog(Animal):
    pass
```

### Mistake 2: Incorrect Parent Initializer Call

When a child class defines its own `__init__()`, the parent initializer is not automatically called.

Use `super()` when the parent initialization is required.

### Mistake 3: Confusing Overriding with Overloading

- Overriding: A child class provides a new implementation of an inherited method.
    
- Overloading: Multiple methods or constructors share a name but accept different parameter lists. Support varies by language.
    

### Mistake 4: Overusing Inheritance

Do not create inheritance relationships just to reuse a few methods. Consider composition or ordinary functions when they provide a simpler design.

## 15. Practical Tasks

Complete these exercises in Python:

1. Create a parent class named `Vehicle`.
    
2. Create a child class named `Car`.
    
3. Add a method to the parent class and access it through the child.
    
4. Create two parent classes named `Camera` and `Phone`.
    
5. Create a `Smartphone` class that inherits from both.
    
6. Create a multilevel inheritance example using `Animal`, `Dog`, and `Puppy`.
    
7. Override a method in a child class.
    
8. Use `super()` to initialize parent-class attributes.
    
9. Inspect the MRO of a class with multiple inheritance.
    

**Challenge:** Build a small cybersecurity event hierarchy with a common `SecurityEvent` parent class and child classes for `LoginEvent` and `NetworkEvent`. Give each child class its own relevant attributes and display method.

## 16. Key Takeaways

- Inheritance allows a class to acquire functionality from another class.
    
- Parent classes provide shared attributes and methods.
    
- Child classes can extend or override inherited behavior.
    
- Python supports single, multiple, multilevel, hierarchical, and hybrid inheritance patterns.
    
- `super()` accesses parent behavior through the MRO.
    
- MRO determines the method lookup order.
    
- Composition is an alternative to inheritance.
    
- Inheritance should represent a genuine relationship between classes.
    

## 17. Related Notes

- [[Introduction to OOP]]
    
- [[Classes and Objects]]
    
- [[Constructors]]
    
- [[Encapsulation]]
    
- [[Polymorphism]]
    
- [[Abstraction]]
    
- [[Python Object-Oriented Programming]]
    
- [[04 - Programming]]