> Learn how JavaScript stores, organizes, accesses, and manipulates collections of data using arrays and objects.

## 1. Introduction

JavaScript provides two important data structures for organizing information:

- **Arrays:** Store ordered collections of values.
    
- **Objects:** Store data as key-value pairs.
    

Both are used extensively in web development, APIs, automation, and cybersecurity tools.

Example:

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

const student = {
    name: "Alex",
    age: 20,
    course: "Cybersecurity"
};
```

---

## 2. JavaScript Arrays

An array is an ordered collection of values stored in a single variable.

Arrays can contain different data types.

```
const data = ["Alex", 20, true, 3.14];

console.log(data);
```

### 2.1 Creating Arrays

Using array literals:

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];
```

Using the Array constructor:

```
const numbers = new Array(10, 20, 30);
```

Array literals are generally preferred because they are simpler and less ambiguous.

### 2.2 Accessing Array Elements

Array indexing starts at `0`.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

console.log(tools[0]); // Nmap
console.log(tools[1]); // Wireshark
console.log(tools[2]); // Burp Suite
```

Accessing an index that does not exist normally returns `undefined`.

### 2.3 Array Length

The `length` property returns the number of elements.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

console.log(tools.length); // 3
```

### 2.4 Updating Array Elements

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

tools[1] = "Metasploit";

console.log(tools);
```

Output:

```
["Nmap", "Metasploit", "Burp Suite"]
```

A `const` array can still have its elements changed. `const` prevents reassignment of the variable, not modification of the array.

---

## 3. Common Array Methods

JavaScript provides built-in methods to manipulate arrays.

### 3.1 push()

Adds an element to the end.

```
const tools = ["Nmap", "Wireshark"];

tools.push("Burp Suite");

console.log(tools);
```

### 3.2 pop()

Removes the last element and returns it.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

const removed = tools.pop();

console.log(removed);
console.log(tools);
```

### 3.3 unshift()

Adds an element to the beginning.

```
const numbers = [20, 30];

numbers.unshift(10);

console.log(numbers);
```

### 3.4 shift()

Removes the first element.

```
const numbers = [10, 20, 30];

numbers.shift();

console.log(numbers);
```

### 3.5 includes()

Checks whether an array contains a value.

```
const tools = ["Nmap", "Wireshark"];

console.log(tools.includes("Nmap")); // true
```

### 3.6 indexOf()

Returns the first index of a value, or `-1` if it is not found.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

console.log(tools.indexOf("Wireshark")); // 1
```

### 3.7 slice()

Returns a portion of an array without modifying the original array.

The ending index is excluded.

```
const numbers = [10, 20, 30, 40, 50];

const result = numbers.slice(1, 4);

console.log(result);  // [20, 30, 40]
console.log(numbers); // Original remains unchanged
```

### 3.8 splice()

Adds, removes, or replaces elements in the original array.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

tools.splice(1, 1);

console.log(tools);
```

Here:

- `1` is the starting index.
    
- The second `1` is the number of elements to remove.
    

Adding an element:

```
const tools = ["Nmap", "Burp Suite"];

tools.splice(1, 0, "Wireshark");

console.log(tools);
```

### 3.9 join()

Combines array elements into a string.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

console.log(tools.join(", "));
```

Output:

```
Nmap, Wireshark, Burp Suite
```

### 3.10 concat()

Combines arrays and returns a new array.

```
const first = [10, 20];
const second = [30, 40];

const combined = first.concat(second);

console.log(combined);
```

### 3.11 reverse()

Reverses the order of elements in the original array.

```
const numbers = [10, 20, 30];

numbers.reverse();

console.log(numbers);
```

### 3.12 sort()

Sorts array elements. By default, values are sorted as strings.

```
const numbers = [100, 5, 20, 3];

numbers.sort();

console.log(numbers);
```

For numeric ascending order, use a comparison function:

```
const numbers = [100, 5, 20, 3];

numbers.sort((a, b) => a - b);

console.log(numbers);
```

For descending order:

```
numbers.sort((a, b) => b - a);
```

**Important:** `sort()` and `reverse()` modify the original array.

---

## 4. Iterating Through Arrays

Iteration means accessing array elements one by one.

### 4.1 Using a for Loop

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

for (let i = 0; i < tools.length; i++) {
    console.log(tools[i]);
}
```

### 4.2 Using for...of

A simpler way to access array values.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

for (const tool of tools) {
    console.log(tool);
}
```

### 4.3 Using forEach()

Executes a function for each array element.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

tools.forEach(function(tool) {
    console.log(tool);
});
```

Using an arrow function:

```
tools.forEach(tool => console.log(tool));
```

`forEach()` is useful for performing an action on each element. It does not create a transformed array.

---

## 5. Higher-Order Array Methods

Higher-order array methods accept functions as arguments or return functions.

They are frequently used in modern JavaScript.

### 5.1 map()

Creates a new array by transforming every element.

```
const numbers = [1, 2, 3, 4];

const doubled = numbers.map(number => number * 2);

console.log(doubled);
```

Output:

```
[2, 4, 6, 8]
```

### 5.2 filter()

Creates a new array containing elements that satisfy a condition.

```
const numbers = [10, 15, 20, 25, 30];

const result = numbers.filter(number => number > 20);

console.log(result);
```

Output:

```
[25, 30]
```

### 5.3 reduce()

Processes array elements and combines them into a single accumulated result.

```
const numbers = [10, 20, 30, 40];

const total = numbers.reduce((sum, number) => {
    return sum + number;
}, 0);

console.log(total); // 100
```

The initial value `0` is the starting accumulator.

### 5.4 find()

Returns the first element that satisfies a condition.

```
const numbers = [10, 20, 30, 40];

const result = numbers.find(number => number > 20);

console.log(result); // 30
```

If no element matches, it returns `undefined`.

### 5.5 some()

Returns `true` if at least one element satisfies a condition.

```
const numbers = [10, 20, 30];

console.log(numbers.some(number => number > 25)); // true
```

### 5.6 every()

Returns `true` only if every element satisfies a condition.

```
const numbers = [10, 20, 30];

console.log(numbers.every(number => number > 5)); // true
```

### Comparison

|Method|Purpose|Return value|
|---|---|---|
|`forEach()`|Perform an action for each element|`undefined`|
|`map()`|Transform elements|New array|
|`filter()`|Select matching elements|New array|
|`reduce()`|Accumulate values|Single accumulated result|
|`find()`|Find first matching element|Element or `undefined`|
|`some()`|Check whether at least one matches|Boolean|
|`every()`|Check whether all match|Boolean|

---

## 6. Array Destructuring

Destructuring extracts values from arrays into separate variables.

```
const tools = ["Nmap", "Wireshark", "Burp Suite"];

const [first, second, third] = tools;

console.log(first);
console.log(second);
console.log(third);
```

Skipping elements:

```
const numbers = [10, 20, 30];

const [first, , third] = numbers;

console.log(first); // 10
console.log(third); // 30
```

### Spread Syntax

The spread operator (`...`) expands array elements.

```
const first = [10, 20];
const second = [30, 40];

const combined = [...first, ...second];

console.log(combined);
```

It can also create a shallow copy:

```
const original = [10, 20, 30];

const copy = [...original];
```

A shallow copy does not independently copy nested objects.

---

## 7. JavaScript Objects

An object is a collection of properties stored as key-value pairs.

Each property contains:

- Key: The property name.
    
- Value: The data associated with that key.
    

Example:

```
const student = {
    name: "Alex",
    age: 20,
    course: "Cybersecurity"
};

console.log(student);
```

### 7.1 Accessing Object Properties

**Dot notation:**

```
console.log(student.name);
```

**Bracket notation:**

```
console.log(student["age"]);
```

Bracket notation is useful when the property name is stored in a variable or contains special characters.

```
const property = "course";

console.log(student[property]);
```

### 7.2 Adding Properties

```
const student = {
    name: "Alex"
};

student.age = 20;
student.course = "Cybersecurity";

console.log(student);
```

### 7.3 Updating Properties

```
student.age = 21;

console.log(student.age);
```

### 7.4 Deleting Properties

```
delete student.course;

console.log(student);
```

### 7.5 Nested Objects

Objects can contain other objects.

```
const student = {
    name: "Alex",
    course: "Cybersecurity",
    address: {
        city: "Mumbai",
        country: "India"
    }
};

console.log(student.address.city);
```

### 7.6 Object Methods

A method is a function stored as an object property.

```
const student = {
    name: "Alex",

    introduce: function() {
        console.log("My name is " + this.name);
    }
};

student.introduce();
```

The `this` keyword refers to the object that the method is called on in this example.

A shorter method syntax is:

```
const student = {
    name: "Alex",

    introduce() {
        console.log(`My name is ${this.name}`);
    }
};
```

**Important:** Arrow functions do not create their own `this`. Avoid using them as object methods when you expect `this` to refer to that object.

### 7.7 Object Property Shorthand

When a variable name matches the property name, shorthand syntax can be used.

```
const name = "Alex";
const age = 20;

const student = {
    name,
    age
};

console.log(student);
```

---

## 8. Useful Object Methods

### 8.1 Object.keys()

Returns an array of an object's own enumerable property names.

```
const student = {
    name: "Alex",
    age: 20,
    course: "Cybersecurity"
};

console.log(Object.keys(student));
```

### 8.2 Object.values()

Returns an array of property values.

```
console.log(Object.values(student));
```

### 8.3 Object.entries()

Returns an array of key-value pairs.

```
console.log(Object.entries(student));
```

### 8.4 Object.hasOwn()

Checks whether an object directly contains a specified property.

```
console.log(Object.hasOwn(student, "name")); // true
console.log(Object.hasOwn(student, "marks")); // false
```

This is useful when checking properties on objects received from external sources.

### 8.5 Optional Chaining

Optional chaining (`?.`) safely accesses a nested property when an intermediate value may be `null` or `undefined`.

```
const student = {
    name: "Alex"
};

console.log(student.address?.city);
```

Output:

```
undefined
```

Without optional chaining, accessing `student.address.city` would cause an error because `address` does not exist.

---

## 9. Object Destructuring and Spread

### 9.1 Object Destructuring

Extracts properties into variables.

```
const student = {
    name: "Alex",
    age: 20,
    course: "Cybersecurity"
};

const { name, age } = student;

console.log(name);
console.log(age);
```

Renaming a variable:

```
const { name: studentName } = student;

console.log(studentName);
```

### 9.2 Object Spread

The spread operator copies enumerable own properties into a new object.

```
const student = {
    name: "Alex",
    age: 20
};

const updatedStudent = {
    ...student,
    course: "Cybersecurity"
};

console.log(updatedStudent);
```

### 9.3 Shallow Copy

A shallow copy copies only the top-level properties. Nested objects remain shared references.

```
const original = {
    name: "Alex",
    address: {
        city: "Mumbai"
    }
};

const copy = { ...original };

copy.name = "Sam";
copy.address.city = "Delhi";

console.log(original.name); // Alex
console.log(original.address.city); // Delhi
```

The nested address changed in the original because both objects refer to the same nested object.

For supported structured data, `structuredClone()` can create a deep copy:

```
const deepCopy = structuredClone(original);
```

It does not support every possible JavaScript value, such as functions.

---

## 10. Arrays and Objects: Reference Behaviour

Arrays and objects are reference types.

When assigned to another variable, the reference is copied rather than creating an independent copy.

```
const first = [10, 20, 30];

const second = first;

second.push(40);

console.log(first);
```

Output:

```
[10, 20, 30, 40]
```

Both variables refer to the same array.

To create a shallow array copy:

```
const first = [10, 20, 30];

const second = [...first];

second.push(40);

console.log(first);  // [10, 20, 30]
console.log(second); // [10, 20, 30, 40]
```

Remember:

- Assignment copies a reference.
    
- Spread creates a shallow copy.
    
- `structuredClone()` can create a deep copy of supported structured data.
    

---

## 11. JSON and JavaScript Objects

JSON stands for JavaScript Object Notation.

It is a text-based format used to exchange structured data between applications.

Example JSON:

```
{
    "name": "Alex",
    "age": 20,
    "course": "Cybersecurity"
}
```

JSON looks similar to a JavaScript object, but it is a text format with stricter syntax.

### 11.1 JSON.stringify()

Converts a JavaScript value into a JSON string.

```
const student = {
    name: "Alex",
    age: 20
};

const jsonData = JSON.stringify(student);

console.log(jsonData);
```

### 11.2 JSON.parse()

Converts valid JSON text into a JavaScript value.

```
const jsonData = '{"name":"Alex","age":20}';

const student = JSON.parse(jsonData);

console.log(student.name);
```

### Important JSON Limitations

JSON does not directly represent:

- Functions
    
- `undefined`
    
- Symbols
    
- Circular object references
    

For example, object properties with `undefined` values are generally omitted during `JSON.stringify()`.

`JSON.parse()` parses JSON data; it does not execute it as JavaScript code. However, data from external sources must still be validated before an application trusts or uses it.

---

## 12. Other JavaScript Collections

### 12.1 Set

A `Set` stores unique values.

```
const numbers = new Set([10, 20, 20, 30]);

console.log(numbers);
```

Duplicate values are stored only once.

Common methods:

```
const tools = new Set();

tools.add("Nmap");
tools.add("Wireshark");

console.log(tools.has("Nmap"));

tools.delete("Nmap");

console.log(tools.size);
```

### 12.2 Map

A `Map` stores key-value pairs. Its keys can be values of different types, including objects.

```
const user = new Map();

user.set("name", "Alex");
user.set("age", 20);

console.log(user.get("name"));
console.log(user.has("age"));
```

Use:

- Arrays for ordered collections.
    
- Objects for structured properties.
    
- Sets for unique values.
    
- Maps for flexible key-value collections.
    

---

## 13. Security Considerations

Arrays and objects are frequently used to process user input, API responses, and application data. Incorrect handling can introduce security vulnerabilities.

### 13.1 Never Trust External Data

Data received from users or APIs must be validated.

```
const userInput = {
    age: "twenty"
};

if (typeof userInput.age !== "number") {
    console.log("Invalid age");
}
```

Real applications need more complete validation, including acceptable ranges and required fields.

### 13.2 Prototype Pollution

JavaScript objects can inherit properties through their prototype chain.

Prototype pollution is a vulnerability in which attacker-controlled property names or object data modify an object's prototype, potentially affecting other parts of an application.

Be careful when merging untrusted objects or assigning untrusted keys.

Use own-property checks when checking whether a property belongs directly to an object:

```
const data = {
    username: "Alex"
};

console.log(Object.hasOwn(data, "username"));
```

For dictionaries with arbitrary user-controlled keys, consider using `Map` or an object created with `Object.create(null)`, alongside appropriate validation.

### 13.3 Avoid Unsafe HTML Insertion

Do not insert untrusted strings into the DOM using `innerHTML` without proper sanitization.

```
// Risky when userInput contains untrusted HTML
element.innerHTML = userInput;
```

For plain text, use:

```
element.textContent = userInput;
```

This helps prevent HTML injection and cross-site scripting in this context.

### 13.4 Protect Sensitive Data

Do not store passwords, API secrets, or private credentials in frontend JavaScript objects or arrays.

Frontend code is accessible to users who can inspect the application.

---

## 14. Practical Lab

### Lab 1: Working with Arrays

Create an array of cybersecurity tools.

```
const tools = [
    "Nmap",
    "Wireshark",
    "Burp Suite",
    "Metasploit",
    "Gobuster"
];

console.log("Total tools:", tools.length);

tools.push("Nikto");

console.log(tools);
```

### Lab 2: Filtering Array Data

Find tools whose names contain the letter `o`.

```
const tools = [
    "Nmap",
    "Wireshark",
    "Burp Suite",
    "Metasploit",
    "Gobuster"
];

const result = tools.filter(tool =>
    tool.toLowerCase().includes("o")
);

console.log(result);
```

### Lab 3: Working with Objects

Create a student object.

```
const student = {
    name: "Alex",
    age: 20,
    course: "Cybersecurity",
    skills: ["Python", "Linux", "Networking"]
};

console.log(student.name);
console.log(student.skills[0]);

student.age = 21;

student.skills.push("Nmap");

console.log(student);
```

### Lab 4: JSON Conversion

Convert an object into JSON and then parse it back.

```
const student = {
    name: "Alex",
    course: "Cybersecurity"
};

const jsonData = JSON.stringify(student);

console.log("JSON:", jsonData);

const restoredData = JSON.parse(jsonData);

console.log("Name:", restoredData.name);
```

### Lab 5: Mini Project — Cybersecurity Tool Inventory

Create an inventory using an array of objects.

```
const inventory = [
    {
        name: "Nmap",
        category: "Network Scanning",
        platform: "Linux"
    },
    {
        name: "Wireshark",
        category: "Packet Analysis",
        platform: "Windows"
    },
    {
        name: "Burp Suite",
        category: "Web Security",
        platform: "Linux"
    }
];

// Display all tools
inventory.forEach(tool => {
    console.log(tool.name, "-", tool.category);
});

// Find Linux tools
const linuxTools = inventory.filter(tool =>
    tool.platform === "Linux"
);

console.log("Linux tools:", linuxTools);

// Extract tool names
const toolNames = inventory.map(tool => tool.name);

console.log("Tool names:", toolNames);
```

---

## 15. Key Points to Remember

1. Arrays store ordered collections of values.
    
2. Array indexing starts at zero.
    
3. Objects store information as key-value pairs.
    
4. `push()` adds an element to the end of an array.
    
5. `pop()` removes the last element.
    
6. `slice()` returns a portion without changing the original array.
    
7. `splice()` modifies the original array.
    
8. `map()` transforms elements.
    
9. `filter()` selects matching elements.
    
10. `reduce()` combines elements into an accumulated result.
    
11. `Object.keys()` returns property names.
    
12. `Object.values()` returns property values.
    
13. `JSON.stringify()` converts a value into JSON text.
    
14. `JSON.parse()` converts JSON text into a JavaScript value.
    
15. Arrays and objects are reference types.
    

## 16. Quick Revision

|Concept|Meaning|
|---|---|
|Array|Ordered collection of values|
|Object|Collection of key-value pairs|
|Index|Position of an array element|
|`length`|Number of array elements|
|`push()`|Add element at the end|
|`pop()`|Remove last element|
|`map()`|Transform array elements|
|`filter()`|Select matching elements|
|`reduce()`|Accumulate array values|
|`find()`|Find first matching element|
|`Set`|Collection of unique values|
|`Map`|Collection of key-value pairs|
|JSON|Text format for data exchange|

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Variables and Data Types]]
    
- [[JavaScript Operators]]
    
- [[JavaScript Control Flow]]
    
- [[JavaScript Functions]]
    
- [[JavaScript DOM]]
    
- [[JavaScript Events]]
    
- [[JavaScript Asynchronous Programming]]
    
- [[JavaScript Fetch API]]
    
- [[Introduction to Secure Coding]]
    
- [[Cross-Site Scripting Prevention]]