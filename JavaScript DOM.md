> Understand how JavaScript interacts with HTML documents, accesses webpage elements, changes content, and creates dynamic web interfaces.

## 1. Introduction to DOM

DOM stands for **Document Object Model**.

The DOM is a programming interface that represents an HTML document as a tree of objects.

JavaScript uses the DOM to:

- Access HTML elements.
    
- Change text and HTML content.
    
- Modify CSS styles.
    
- Add or remove elements.
    
- Read user input.
    
- Create dynamic webpages.
    

Example HTML:

```
<!DOCTYPE html>
<html>
<head>
    <title>DOM Example</title>
</head>
<body>
    <h1 id="heading">Hello World</h1>
</body>
</html>
```

JavaScript can access the heading through the DOM:

```
const heading = document.getElementById("heading");

console.log(heading.textContent);
```

Output:

```
Hello World
```

---

## 2. DOM Tree Structure

The browser converts an HTML document into a tree-like structure.

Example:

```
<html>
    <body>
        <h1>Welcome</h1>
        <p>Learning JavaScript</p>
    </body>
</html>
```

Simplified DOM tree:

```
Document
└── html
    └── body
        ├── h1
        │   └── "Welcome"
        └── p
            └── "Learning JavaScript"
```

Important DOM concepts:

|Concept|Meaning|
|---|---|
|Document|Represents the entire HTML document|
|Element|An HTML element such as `h1` or `p`|
|Node|A unit in the DOM tree|
|Text node|Text inside an element|
|Parent|Node containing another node|
|Child|Node contained inside another node|
|Sibling|Node sharing the same parent|

---

## 3. Accessing HTML Elements

JavaScript provides several methods to select elements.

### 3.1 getElementById()

Selects an element using its ID.

```
const heading = document.getElementById("heading");
```

### 3.2 getElementsByClassName()

Selects elements using a class name.

```
const items = document.getElementsByClassName("item");

console.log(items);
```

Returns a live HTMLCollection.

### 3.3 getElementsByTagName()

Selects elements using their HTML tag name.

```
const paragraphs = document.getElementsByTagName("p");

console.log(paragraphs);
```

Also returns a live HTMLCollection.

### 3.4 querySelector()

Selects the first element matching a CSS selector.

```
const heading = document.querySelector("#heading");

const firstItem = document.querySelector(".item");

const paragraph = document.querySelector("p");
```

### 3.5 querySelectorAll()

Selects all elements matching a CSS selector.

```
const items = document.querySelectorAll(".item");

console.log(items);
```

Returns a static NodeList.

### Comparison

|Method|Selection|Return|
|---|---|---|
|`getElementById()`|ID|Element or `null`|
|`getElementsByClassName()`|Class|Live HTMLCollection|
|`getElementsByTagName()`|Tag|Live HTMLCollection|
|`querySelector()`|CSS selector|First matching element or `null`|
|`querySelectorAll()`|CSS selector|Static NodeList|

---

## 4. Changing HTML Content

JavaScript can modify the content of HTML elements.

### 4.1 textContent

Gets or changes the text content.

```
const heading = document.getElementById("heading");

heading.textContent = "Welcome to JavaScript";
```

### 4.2 innerHTML

Gets or changes the HTML markup inside an element.

```
const container = document.getElementById("container");

container.innerHTML = "<h2>New Heading</h2>";
```

**Security warning:** Never insert untrusted user input directly into `innerHTML`. It can execute attacker-controlled HTML or scripts and lead to cross-site scripting (XSS).

For plain text, prefer:

```
container.textContent = userInput;
```

### 4.3 innerText

Gets or changes rendered text.

```
const heading = document.getElementById("heading");

heading.innerText = "Updated Text";
```

`innerText` considers rendered visibility, while `textContent` works with the text content of the DOM.

---

## 5. Changing CSS Styles

JavaScript can modify an element's inline CSS styles.

```
<h1 id="heading">Hello World</h1>
```

```
const heading = document.getElementById("heading");

heading.style.color = "blue";
heading.style.backgroundColor = "lightgray";
heading.style.fontSize = "30px";
```

CSS property names written in JavaScript generally use camelCase.

For example:

- `background-color` becomes `backgroundColor`.
    
- `font-size` becomes `fontSize`.
    
- `margin-top` becomes `marginTop`.
    

### Using classList

Instead of changing many inline styles, use CSS classes.

HTML:

```
<h1 id="heading">Hello World</h1>
```

CSS:

```
.highlight {
    color: blue;
    background-color: lightgray;
}
```

JavaScript:

```
const heading = document.getElementById("heading");

heading.classList.add("highlight");
```

Useful methods:

|Method|Purpose|
|---|---|
|`add()`|Adds a class|
|`remove()`|Removes a class|
|`toggle()`|Adds or removes a class|
|`contains()`|Checks whether a class exists|
|`replace()`|Replaces one class with another|

Example:

```
heading.classList.toggle("highlight");
```

---

## 6. Creating and Removing Elements

JavaScript can create new HTML elements dynamically.

### 6.1 createElement()

Creates a new HTML element.

```
const paragraph = document.createElement("p");

paragraph.textContent = "This paragraph was created using JavaScript.";
```

### 6.2 appendChild()

Adds an element as the last child of another element.

```
const container = document.getElementById("container");

container.appendChild(paragraph);
```

### 6.3 append()

Adds one or more nodes or strings.

```
container.append("New content");
```

### 6.4 remove()

Removes an element from the DOM.

```
paragraph.remove();
```

### 6.5 prepend()

Adds content at the beginning of an element.

```
container.prepend(paragraph);
```

### 6.6 insertBefore()

Inserts a node before another child node.

```
const newItem = document.createElement("li");

newItem.textContent = "New Item";

const list = document.getElementById("list");

list.insertBefore(newItem, list.firstElementChild);
```

---

## 7. DOM Traversal

DOM traversal means moving between related elements and nodes.

Example HTML:

```
<div id="parent">
    <p id="child">Hello</p>
</div>
```

JavaScript:

```
const child = document.getElementById("child");

console.log(child.parentElement);
console.log(child.children);
console.log(child.nextElementSibling);
console.log(child.previousElementSibling);
```

Important properties:

|Property|Purpose|
|---|---|
|`parentElement`|Gets the parent element|
|`children`|Gets child elements|
|`firstElementChild`|Gets the first child element|
|`lastElementChild`|Gets the last child element|
|`nextElementSibling`|Gets the next sibling element|
|`previousElementSibling`|Gets the previous sibling element|

---

## 8. Working with HTML Attributes

Attributes provide additional information about HTML elements.

Example:

```
<img id="photo" src="image.jpg" alt="Sample Image">
```

### 8.1 getAttribute()

Reads an attribute value.

```
const image = document.getElementById("photo");

console.log(image.getAttribute("src"));
```

### 8.2 setAttribute()

Sets or updates an attribute.

```
image.setAttribute("alt", "Cybersecurity illustration");
```

### 8.3 removeAttribute()

Removes an attribute.

```
image.removeAttribute("alt");
```

### 8.4 hasAttribute()

Checks whether an attribute exists.

```
console.log(image.hasAttribute("src"));
```

---

## 9. Working with Forms and Input Fields

JavaScript can access and process user input through HTML forms.

Example HTML:

```
<input type="text" id="username" placeholder="Enter username">

<button id="submitBtn">Submit</button>

<p id="output"></p>
```

JavaScript:

```
const username = document.getElementById("username");
const button = document.getElementById("submitBtn");
const output = document.getElementById("output");

button.addEventListener("click", function() {
    output.textContent = "Welcome, " + username.value;
});
```

The `.value` property retrieves the current value of an input field.

**Important:** Client-side validation improves usability, but it is not a security boundary. A user can bypass browser-side checks. Applications must validate input on the server as well.

---

## 10. DOM and JavaScript Security

The DOM is an important area of web application security.

Incorrect DOM manipulation can introduce vulnerabilities.

### 10.1 DOM-Based Cross-Site Scripting

DOM-based XSS occurs when attacker-controlled data is processed by client-side JavaScript and inserted into the page in an unsafe way.

Risky example:

```
const input = location.hash.substring(1);

document.getElementById("output").innerHTML = input;
```

If the input contains malicious HTML, it may be interpreted as markup.

Safer example for displaying plain text:

```
const input = location.hash.substring(1);

document.getElementById("output").textContent = input;
```

### 10.2 Dangerous DOM Sinks

Be careful when using:

- `innerHTML`
    
- `outerHTML`
    
- `insertAdjacentHTML()`
    
- `document.write()`
    
- Event-handler attributes such as `onclick` when constructed from untrusted strings.
    

These APIs are not always unsafe, but inserting untrusted data into them without proper handling can create vulnerabilities.

### 10.3 Safe DOM Practices

1. Use `textContent` for plain text.
    
2. Avoid inserting untrusted data as HTML.
    
3. Validate data according to its expected format.
    
4. Use trusted sanitization libraries when HTML input is genuinely required.
    
5. Do not rely only on client-side validation.
    
6. Keep security-sensitive operations on the server.
    

---

## 11. Practical Lab

### Lab 1: Select and Modify Elements

Create an HTML file:

```
<!DOCTYPE html>
<html>
<head>
    <title>DOM Lab</title>
</head>
<body>

    <h1 id="heading">Original Heading</h1>

    <script>
        const heading = document.getElementById("heading");

        heading.textContent = "DOM Manipulation Lab";

        heading.style.color = "blue";
    </script>

</body>
</html>
```

Open the file in your browser and observe the changes.

### Lab 2: Create Elements Dynamically

```
<!DOCTYPE html>
<html>
<body>

    <ul id="tools"></ul>

    <script>
        const tools = ["Nmap", "Wireshark", "Burp Suite"];

        const list = document.getElementById("tools");

        tools.forEach(tool => {
            const item = document.createElement("li");

            item.textContent = tool;

            list.appendChild(item);
        });
    </script>

</body>
</html>
```

Observe how JavaScript creates list items dynamically.

### Lab 3: Build a Simple User Input Interface

```
<!DOCTYPE html>
<html>
<body>

    <h2>Username Checker</h2>

    <input type="text" id="username" placeholder="Enter username">

    <button id="check">Check</button>

    <p id="result"></p>

    <script>
        const username = document.getElementById("username");
        const button = document.getElementById("check");
        const result = document.getElementById("result");

        button.addEventListener("click", function() {
            if (username.value.trim() === "") {
                result.textContent = "Please enter a username.";
            } else {
                result.textContent = "Username entered: " + username.value;
            }
        });
    </script>

</body>
</html>
```

### Lab 4: Mini Project — Cybersecurity Tool List

Build a webpage that:

1. Displays a list of cybersecurity tools.
    
2. Adds a new tool using an input field.
    
3. Removes a selected tool.
    
4. Changes the heading when a button is clicked.
    

Use:

- `getElementById()`
    
- `createElement()`
    
- `appendChild()`
    
- `remove()`
    
- `addEventListener()`
    
- `textContent`
    

Do not use `innerHTML` to insert user-provided tool names.

---

## 12. Key Points to Remember

1. DOM stands for Document Object Model.
    
2. The DOM represents an HTML document as a tree of nodes.
    
3. JavaScript uses the DOM to interact with webpages.
    
4. `getElementById()` selects an element by ID.
    
5. `querySelector()` selects the first matching CSS selector.
    
6. `querySelectorAll()` selects all matching elements.
    
7. `textContent` reads or changes text.
    
8. `innerHTML` reads or changes HTML markup.
    
9. `classList` manages CSS classes.
    
10. `createElement()` creates new elements.
    
11. `appendChild()` adds an element to another element.
    
12. `remove()` removes an element.
    
13. `getAttribute()` reads an attribute.
    
14. `setAttribute()` changes an attribute.
    
15. Unsafe DOM manipulation can introduce DOM-based XSS.
    

## 13. Quick Revision

|Term|Meaning|
|---|---|
|DOM|Document Object Model|
|Node|Unit in the DOM tree|
|Element|HTML element represented in the DOM|
|Selector|Method of finding elements|
|`textContent`|Gets or sets text|
|`innerHTML`|Gets or sets HTML markup|
|`classList`|Manages element classes|
|`createElement()`|Creates an HTML element|
|`appendChild()`|Adds a child node|
|`remove()`|Removes an element|
|`getAttribute()`|Reads an attribute|
|`setAttribute()`|Sets an attribute|
|DOM XSS|XSS caused by unsafe client-side DOM handling|

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Variables and Data Types]]
    
- [[JavaScript Functions]]
    
- [[JavaScript Arrays and Objects]]
    
- [[JavaScript Events]]
    
- [[JavaScript Asynchronous Programming]]
    
- [[JavaScript Fetch API]]
    
- [[Introduction to Secure Coding]]
    
- [[Cross-Site Scripting Prevention]]