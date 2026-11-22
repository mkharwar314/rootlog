> Understand how functions receive information, process input values, and produce reusable results.

## 1. What Are Parameters and Arguments?

Functions often need information to perform a task. This information is passed into a function through **parameters and arguments**.

Although these terms are related, they have different meanings.

- **Parameter:** A variable listed in the function definition.
    
- **Argument:** The actual value supplied when calling the function.
    

Example:

```
def greet(name):
    print("Hello", name)

greet("Mohit")
```

In this example:

- `name` is a parameter.
    
- `"Mohit"` is an argument.
    
- The function receives the value and prints a greeting.
    

Output:

```
Hello Mohit
```

## 2. Function Without Parameters

A function does not always need parameters.

```
def welcome():
    print("Welcome to ROOTLOG")

welcome()
```

Output:

```
Welcome to ROOTLOG
```

The function performs its task without receiving external input.

## 3. Function With One Parameter

A function can receive one parameter.

```
def square(number):
    print(number * number)

square(5)
```

Output:

```
25
```

Here, `number` receives the argument `5`.

## 4. Function With Multiple Parameters

A function can receive multiple parameters.

```
def add(a, b):
    print(a + b)

add(10, 20)
```

Output:

```
30
```

Here:

- `a` receives `10`.
    
- `b` receives `20`.
    

By default, positional arguments are assigned according to their order.

## 5. Types of Function Arguments in Python

Python supports several ways to pass arguments.

### A. Positional Arguments

Values are assigned according to their position.

```
def student(name, age):
    print("Name:", name)
    print("Age:", age)

student("Mohit", 18)
```

Output:

```
Name: Mohit
Age: 18
```

Changing the order changes which parameter receives each value.

### B. Keyword Arguments

Values are passed by explicitly specifying parameter names.

```
def student(name, age):
    print("Name:", name)
    print("Age:", age)

student(age=18, name="Mohit")
```

Output:

```
Name: Mohit
Age: 18
```

Keyword arguments make function calls easier to understand.

### C. Default Arguments

A default argument provides a value that is used when the caller does not supply that argument.

```
def greet(name="Guest"):
    print("Hello", name)

greet()
greet("Mohit")
```

Output:

```
Hello Guest
Hello Mohit
```

The first call uses the default value. The second call supplies a different value.

**Important:** In Python, parameters with default values must generally appear after parameters without default values.

### D. Variable-Length Positional Arguments (`*args`)

Sometimes a function needs to accept an unknown number of positional arguments.

Python provides `*args` for this purpose.

```
def add_numbers(*numbers):
    total = sum(numbers)
    print("Total:", total)

add_numbers(10, 20)
add_numbers(10, 20, 30, 40)
```

Output:

```
Total: 30
Total: 100
```

Inside the function, `numbers` is a tuple.

### E. Variable-Length Keyword Arguments (`**kwargs`)

`**kwargs` allows a function to receive multiple keyword arguments.

```
def display_info(**details):
    for key, value in details.items():
        print(key, ":", value)

display_info(name="Mohit", role="Student", language="Python")
```

Output:

```
name : Mohit
role : Student
language : Python
```

Inside the function, `details` is a dictionary.

## 6. Positional vs Keyword Arguments

|Feature|Positional Arguments|Keyword Arguments|
|---|---|---|
|Assignment|Based on position|Based on parameter name|
|Order|Usually matters|Can be changed|
|Syntax|`function(10, 20)`|`function(a=10, b=20)`|
|Readability|Depends on context|Often clearer|

## 7. Parameters and Arguments in C

C uses parameters in function definitions and arguments in function calls.

```
#include <stdio.h>

void add(int a, int b) {
    printf("Total: %d\n", a + b);
}

int main() {
    add(10, 20);
    return 0;
}
```

Output:

```
Total: 30
```

Here:

- `int a` and `int b` are parameters.
    
- `10` and `20` are arguments.
    

C functions use declared parameter types.

## 8. Parameters and Arguments in JavaScript

JavaScript also supports parameters and arguments.

```
function greet(name) {
    console.log("Hello", name);
}

greet("Mohit");
```

Output:

```
Hello Mohit
```

### Default Parameters in JavaScript

```
function greet(name = "Guest") {
    console.log("Hello", name);
}

greet();
greet("Mohit");
```

### Rest Parameters in JavaScript

The rest parameter (`...`) collects multiple arguments into an array.

```
function addNumbers(...numbers) {
    let total = 0;

    for (let number of numbers) {
        total += number;
    }

    console.log(total);
}

addNumbers(10, 20, 30);
```

Output:

```
60
```

## 9. Argument Passing and Object References

In Python, arguments are passed by object reference semantics: a function receives a reference to an object.

For mutable objects, changes made to the object inside a function can be visible outside the function.

Example:

```
def add_item(items):
    items.append("New Item")

my_list = ["First Item"]

add_item(my_list)

print(my_list)
```

Output:

```
['First Item', 'New Item']
```

The function modifies the same list object.

However, assigning a new object to the parameter does not reassign the caller's variable.

```
def change_value(number):
    number = 100

value = 10
change_value(value)

print(value)
```

Output:

```
10
```

Understanding this distinction is important when working with lists, dictionaries, and other mutable objects.

## 10. Functions in Cybersecurity

Parameters allow security functions to process different inputs without rewriting the same logic.

### Example 1: Hashing Different Strings

```
import hashlib

def calculate_hash(data):
    return hashlib.sha256(data.encode()).hexdigest()

print(calculate_hash("file-one"))
print(calculate_hash("file-two"))
```

The same function processes different input strings.

### Example 2: Processing Log Events

```
def analyze_login(username, status):
    print("Username:", username)
    print("Login status:", status)

analyze_login("admin", "Failed")
analyze_login("student", "Successful")
```

The function can process different usernames and login statuses.

### Example 3: Configurable Threshold

```
def check_failed_logins(count, threshold=5):
    if count >= threshold:
        print("Alert: Failed login threshold reached")
    else:
        print("No alert")

check_failed_logins(3)
check_failed_logins(7)
check_failed_logins(3, threshold=2)
```

The default threshold is 5, but the caller can provide another value.

This is a simplified example, not a complete intrusion detection system.

## 11. Common Mistakes

1. Confusing parameters with arguments.
    
2. Passing the wrong number of arguments.
    
3. Passing values in the wrong positional order.
    
4. Using an incorrect keyword argument name.
    
5. Defining default parameters before required parameters in Python.
    
6. Forgetting that `*args` collects positional arguments into a tuple.
    
7. Forgetting that `**kwargs` collects keyword arguments into a dictionary.
    
8. Modifying a mutable object without understanding the side effects.
    

## 12. Key Takeaways

- Parameters are variables in a function definition.
    
- Arguments are actual values passed during a function call.
    
- Functions can accept zero, one, or multiple arguments.
    
- Python supports positional, keyword, default, `*args`, and `**kwargs` arguments.
    
- C uses declared parameter types.
    
- JavaScript supports default and rest parameters.
    
- Parameters make functions reusable and flexible.
    
- Cybersecurity scripts use parameters to process different files, users, events, and inputs.
    

## 13. Questions and Doubts

- What is the difference between a parameter and an argument?
    
- How do positional and keyword arguments differ?
    
- Why are default arguments useful?
    
- What is the purpose of `*args` and `**kwargs`?
    
- How can mutable arguments affect a function's caller?
    

## 14. Practical Tasks

Complete these tasks in Python:

1. Create a function that accepts a name and prints a greeting.
    
2. Create a function that accepts two numbers and returns their sum.
    
3. Create a function that accepts a name and an age, using a default age value.
    
4. Create a function that accepts any number of integers using `*args` and calculates their sum.
    
5. Create a function that accepts multiple student details using `**kwargs`.
    
6. Create a function that accepts a filename and prints a message indicating that the file is ready for analysis.
    

**Challenge:** Create a function that accepts a list of login attempts and a configurable failure threshold. Display an alert when the number of failed attempts reaches the threshold.