> Encapsulation is an Object-Oriented Programming (OOP) principle that combines data and the methods that operate on that data inside a class while controlling how the internal state is accessed or modified.

## 1. What Is Encapsulation?

Encapsulation means organizing related data and methods into a single unit, usually a class, and controlling access to the internal data.

Consider a bank account.

It contains:

- Account holder name.
    
- Account number.
    
- Account balance.
    
- Deposit operation.
    
- Withdrawal operation.
    

A user should not be able to change the account balance through arbitrary operations that bypass the account's rules.

Instead, the class provides methods that control how the balance changes.

Example:

```
class BankAccount:

    def __init__(self, balance):
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount

    def display_balance(self):
        print("Balance:", self.balance)


account = BankAccount(5000)

account.deposit(1000)
account.display_balance()
```

Output:

```
Balance: 6000
```

The class groups account data and related operations together.

## 2. Why Is Encapsulation Important?

Encapsulation helps to:

1. Organize data and methods.
    
2. Control how object attributes are modified.
    
3. Reduce accidental changes to internal state.
    
4. Improve code maintainability.
    
5. Separate internal implementation from public interfaces.
    
6. Enforce application rules through controlled operations.
    

Without appropriate control, different parts of a program may modify important data in unexpected ways.

## 3. Access Modifiers

Access modifiers describe how class members can be accessed.

Common access levels in OOP include:

1. Public
    
2. Protected
    
3. Private
    

Their exact behavior depends on the programming language.

### A. Public Members

Public members can be accessed from outside the class.

Example:

```
class Student:

    def __init__(self, name):
        self.name = name


student1 = Student("Mohit")

print(student1.name)
```

Output:

```
Mohit
```

Here, `name` is a public instance attribute.

### B. Protected Members

Protected members are intended for use inside the class and its subclasses.

In Python, a single leading underscore indicates that an attribute is intended for internal use.

Example:

```
class Student:

    def __init__(self, name):
        self._name = name


student1 = Student("Mohit")

print(student1._name)
```

Output:

```
Mohit
```

Python does not enforce protected access. The underscore is a convention that communicates intended usage.

### C. Private Members

In Python, a double leading underscore triggers name mangling.

Example:

```
class Student:

    def __init__(self, name):
        self.__name = name


student1 = Student("Mohit")
```

Direct access using `student1.__name` normally raises an `AttributeError`.

However, this is not strict privacy or a security boundary. Name mangling changes the attribute name internally and helps avoid accidental access and naming conflicts.

## 4. Access Modifiers in Python

|Access Level|Naming Convention|Intended Access|
|---|---|---|
|Public|`name`|Anywhere|
|Protected|`_name`|Internal use and subclasses|
|Private|`__name`|Internal use through the mangled name|

Remember:

- Public: No leading underscore.
    
- Protected: One leading underscore.
    
- Private: Two leading underscores.
    

These are Python conventions and mechanisms, not equivalent to strict access control in languages such as Java or C++.

## 5. Implementing Encapsulation in Python

Consider a bank account where the balance should be changed only through controlled operations.

```
class BankAccount:

    def __init__(self, balance):
        if balance < 0:
            raise ValueError("Initial balance cannot be negative")

        self.__balance = balance

    def deposit(self, amount):
        if amount <= 0:
            print("Invalid deposit amount")
            return

        self.__balance += amount
        print("Deposit successful")

    def withdraw(self, amount):
        if amount <= 0:
            print("Invalid withdrawal amount")
            return

        if amount > self.__balance:
            print("Insufficient balance")
            return

        self.__balance -= amount
        print("Withdrawal successful")

    def get_balance(self):
        return self.__balance


account = BankAccount(5000)

account.deposit(1000)
account.withdraw(2000)

print("Balance:", account.get_balance())
```

Output:

```
Deposit successful
Withdrawal successful
Balance: 4000
```

Explanation:

- `__balance` is an attribute using name mangling.
    
- `deposit()` controls how money is added.
    
- `withdraw()` checks whether a withdrawal is valid.
    
- `get_balance()` provides a controlled way to read the balance.
    

The important principle is that the class enforces rules through its methods.

## 6. Getters and Setters

Getters and setters are methods used to retrieve and modify attribute values.

### Getter

A getter returns an attribute value.

### Setter

A setter modifies an attribute after applying required validation.

Example:

```
class Student:

    def __init__(self, age):
        self.__age = age

    def get_age(self):
        return self.__age

    def set_age(self, age):
        if age > 0:
            self.__age = age
        else:
            print("Invalid age")


student1 = Student(18)

print(student1.get_age())

student1.set_age(19)

print(student1.get_age())
```

Output:

```
18
19
```

Getters and setters allow validation to be centralized instead of repeating it throughout the application.

## 7. Python Properties

Python provides the `@property` decorator to expose controlled attribute access using attribute-style syntax.

Example:

```
class Student:

    def __init__(self, age):
        self.__age = age

    @property
    def age(self):
        return self.__age

    @age.setter
    def age(self, value):
        if value <= 0:
            raise ValueError("Age must be positive")

        self.__age = value


student1 = Student(18)

print(student1.age)

student1.age = 19

print(student1.age)
```

Output:

```
18
19
```

Explanation:

- `@property` defines a getter.
    
- `@age.setter` defines controlled assignment.
    
- Invalid values are rejected.
    

Properties are a common Pythonic way to implement controlled attribute access.

## 8. Encapsulation vs Data Hiding

These concepts are related but not identical.

|Feature|Encapsulation|Data Hiding|
|---|---|---|
|Meaning|Combines data and related methods|Restricts or discourages direct access to internal data|
|Purpose|Organizes and controls object behavior|Protects internal implementation from unintended access|
|Scope|Broader OOP principle|One technique associated with encapsulation|
|Example|A BankAccount class|A name-mangled balance attribute|

Encapsulation is the broader concept. Data hiding is one way to support it.

## 9. Advantages of Encapsulation

1. **Controlled Access:** Important attributes can be modified through defined methods.
    
2. **Data Integrity:** Validation can prevent invalid object states.
    
3. **Maintainability:** Internal implementation can change without changing the public interface.
    
4. **Modularity:** Related functionality stays inside the same class.
    
5. **Reduced Coupling:** Other components can interact through a defined interface.
    
6. **Reusability:** Encapsulated classes can be reused in different programs.
    

## 10. Disadvantages of Encapsulation

1. **Additional Code:** Getters, setters, and validation methods can increase code length.
    
2. **Complexity:** Excessive access restrictions can make simple programs harder to understand.
    
3. **Performance Overhead:** Additional method calls may introduce small overhead.
    
4. **Poor Design Risk:** Unnecessary restrictions can make classes difficult to use.
    

Encapsulation should be applied where it improves design and protects important object invariants.

## 11. Encapsulation in Different Programming Languages

### Python

Python uses naming conventions, name mangling, and properties.

```
class Account:

    def __init__(self):
        self.__balance = 1000

    @property
    def balance(self):
        return self.__balance
```

### Java

Java provides explicit access modifiers such as `private`, `protected`, and `public`.

```
class BankAccount {

    private double balance = 1000;

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
}
```

### C++

C++ provides access specifiers such as `private`, `protected`, and `public`.

```
#include <iostream>
using namespace std;

class BankAccount {

private:
    int balance = 1000;

public:
    int getBalance() {
        return balance;
    }

    void deposit(int amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
};

int main() {

    BankAccount account;

    account.deposit(500);

    cout << account.getBalance();

    return 0;
}
```

## 12. Encapsulation in Cybersecurity

Encapsulation is useful when building security-related applications because it helps enforce application rules and organize sensitive operations.

### A. Password Management

A user-account class can provide methods for password verification without exposing stored password hashes through its public interface.

### B. Access Control

A class can control permission changes through defined methods.

### C. Security Event Management

A security event object can validate event attributes before accepting them.

### D. Digital Forensics

An evidence-management class can control how evidence metadata is modified.

Example:

```
class SecurityEvent:

    def __init__(self, event_type, severity):
        self.__event_type = event_type
        self.__severity = severity

    def get_event(self):
        return {
            "event_type": self.__event_type,
            "severity": self.__severity
        }


event = SecurityEvent("Failed Login", "High")

print(event.get_event())
```

Output:

```
{'event_type': 'Failed Login', 'severity': 'High'}
```

This organizes event information behind a method-based interface.

**Security limitation:** Python name mangling does not protect secrets against a malicious user who can inspect or execute code inside the same process. Real security requires appropriate authentication, authorization, isolation, and secret-management controls.

## 13. Common Mistakes

### Mistake 1: Assuming Double Underscores Make Data Completely Private

Incorrect assumption:

```
student1.__name
```

A double underscore triggers name mangling, not cryptographic protection or strict privacy.

### Mistake 2: Allowing Invalid Data

Incorrect:

```
class Student:

    def __init__(self, age):
        self.__age = age
```

This accepts any value, including negative ages.

Better:

```
class Student:

    def __init__(self, age):
        if age <= 0:
            raise ValueError("Age must be positive")

        self.__age = age
```

### Mistake 3: Using Setters Without Validation

A setter that accepts every possible value does not enforce meaningful constraints.

### Mistake 4: Confusing Encapsulation with Encryption

Encapsulation organizes and controls access to program data.

Encryption transforms data using a cryptographic algorithm and key.

They solve different problems.

## 14. Practical Tasks

Complete these exercises in Python:

1. Create a `Student` class with a private `__age` attribute.
    
2. Create a getter to retrieve the age.
    
3. Create a setter that rejects zero and negative ages.
    
4. Create a `BankAccount` class with a private balance.
    
5. Add deposit and withdrawal methods with validation.
    
6. Create a `SecurityEvent` class with controlled access to its severity.
    
7. Use `@property` to expose a validated attribute.
    

**Challenge:** Create a simple user-account class that stores a username and a password hash. Provide a method to verify a supplied password using a dedicated password-hashing library. Do not store plaintext passwords or use Python's built-in `hash()` for password storage.

## 15. Key Takeaways

- Encapsulation combines data and related methods within a class.
    
- It provides controlled access to an object's internal state.
    
- Public, protected, and private access conventions vary by language.
    
- Python uses underscores and name mangling rather than strict private access.
    
- Getters and setters can control attribute access.
    
- Python properties provide a convenient interface for validation.
    
- Encapsulation improves organization and maintainability.
    
- Encapsulation alone does not provide security against malicious code running in the same process.
    

## 16. Related Notes

- [[Introduction to OOP]]
    
- [[Classes and Objects]]
    
- [[Constructors]]
    
- [[Inheritance]]
    
- [[Polymorphism]]
    
- [[Abstraction]]
    
- [[Python Object-Oriented Programming]]
    
- [[Programming]]