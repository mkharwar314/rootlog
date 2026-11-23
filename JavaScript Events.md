> Understand how JavaScript responds to user interactions and browser activities to create interactive web applications.

## 1. Introduction to Events

An event is an action or occurrence detected by the browser.

JavaScript can respond to events by executing a function called an **event handler**.

Common examples:

- Clicking a button.
    
- Typing in an input field.
    
- Moving the mouse.
    
- Submitting a form.
    
- Loading a webpage.
    
- Pressing a keyboard key.
    

Example:

```
<button id="myButton">Click Me</button>

<script>
    const button = document.getElementById("myButton");

    button.addEventListener("click", function() {
        console.log("Button clicked!");
    });
</script>
```

When the user clicks the button, JavaScript executes the callback function.

---

## 2. Types of JavaScript Events

### 2.1 Mouse Events

Mouse events occur when a user interacts with a mouse or pointing device.

|Event|Description|
|---|---|
|`click`|Element is clicked|
|`dblclick`|Element is double-clicked|
|`mousedown`|Mouse button is pressed|
|`mouseup`|Mouse button is released|
|`mouseover`|Pointer enters an element or its descendants|
|`mouseout`|Pointer leaves an element or its descendants|
|`mousemove`|Pointer moves|
|`mouseenter`|Pointer enters an element|
|`mouseleave`|Pointer leaves an element|

Example:

```
const button = document.getElementById("myButton");

button.addEventListener("click", function() {
    console.log("Mouse click detected");
});
```

### 2.2 Keyboard Events

Keyboard events occur when a user presses or releases a keyboard key.

|Event|Description|
|---|---|
|`keydown`|A key is pressed|
|`keyup`|A key is released|

Example:

```
document.addEventListener("keydown", function(event) {
    console.log("Key pressed:", event.key);
});
```

The `event.key` property identifies the key associated with the event.

### 2.3 Form Events

Form events occur when users interact with forms.

|Event|Description|
|---|---|
|`submit`|A form is submitted|
|`input`|An input value changes|
|`change`|A value is committed or changed, depending on the control|
|`focus`|An element receives focus|
|`blur`|An element loses focus|
|`reset`|A form is reset|

Example:

```
const username = document.getElementById("username");

username.addEventListener("input", function() {
    console.log(username.value);
});
```

### 2.4 Window and Document Events

|Event|Description|
|---|---|
|`load`|A resource or page finishes loading|
|`DOMContentLoaded`|HTML has been parsed and the DOM is ready|
|`resize`|Browser window size changes|
|`scroll`|Document or element is scrolled|
|`beforeunload`|User is about to leave a document|

Example:

```
document.addEventListener("DOMContentLoaded", function() {
    console.log("DOM is ready");
});
```

---

## 3. Event Handlers

An event handler is a function that executes when a particular event occurs.

JavaScript provides several ways to attach event handlers.

### 3.1 Inline Event Handler

The event is written directly inside HTML.

```
<button onclick="showMessage()">Click Me</button>

<script>
    function showMessage() {
        alert("Hello!");
    }
</script>
```

This approach is simple but generally discouraged because it mixes HTML and JavaScript.

### 3.2 Using DOM Event Properties

An event handler can be assigned to an element property.

```
const button = document.getElementById("myButton");

button.onclick = function() {
    console.log("Button clicked");
};
```

Assigning another function to `onclick` replaces the previous handler.

### 3.3 Using addEventListener()

This is the recommended approach for most event handling.

```
const button = document.getElementById("myButton");

button.addEventListener("click", function() {
    console.log("Button clicked");
});
```

Advantages:

- Separates HTML and JavaScript.
    
- Allows multiple listeners for the same event.
    
- Supports event propagation options.
    
- Makes code easier to maintain.
    

Example with multiple listeners:

```
button.addEventListener("click", function() {
    console.log("First listener");
});

button.addEventListener("click", function() {
    console.log("Second listener");
});
```

Both listeners can execute when the button is clicked.

---

## 4. The Event Object

When an event occurs, the browser provides an event object containing information about it.

Example:

```
document.addEventListener("click", function(event) {
    console.log(event);
});
```

Useful event object properties:

|Property|Description|
|---|---|
|`event.type`|Type of event|
|`event.target`|Original target of the event|
|`event.currentTarget`|Element whose listener is currently executing|
|`event.key`|Keyboard key involved|
|`event.clientX`|Mouse X-coordinate relative to viewport|
|`event.clientY`|Mouse Y-coordinate relative to viewport|
|`event.defaultPrevented`|Indicates whether default action was prevented|

Example:

```
const button = document.getElementById("myButton");

button.addEventListener("click", function(event) {
    console.log("Event:", event.type);
    console.log("Target:", event.target);
    console.log("Current target:", event.currentTarget);
});
```

### target vs currentTarget

- `target`: The element where the event originally occurred.
    
- `currentTarget`: The element whose event listener is currently running.
    

These can be different when events propagate through the DOM.

---

## 5. Event Propagation

Event propagation describes how an event travels through the DOM tree.

There are three important concepts:

1. Capturing phase.
    
2. Target phase.
    
3. Bubbling phase.
    

### 5.1 Capturing Phase

The event travels from the document's outer ancestors toward the target element.

### 5.2 Target Phase

The event reaches the element where it originally occurred.

### 5.3 Bubbling Phase

The event travels back upward through the target's ancestors.

Simplified example:

```
Document
   |
 Parent
   |
 Child  ← Event target
```

During bubbling, the event travels:

```
Child → Parent → Document
```

### Example

HTML:

```
<div id="parent">
    <button id="child">Click Me</button>
</div>
```

JavaScript:

```
const parent = document.getElementById("parent");
const child = document.getElementById("child");

parent.addEventListener("click", function() {
    console.log("Parent clicked");
});

child.addEventListener("click", function() {
    console.log("Child clicked");
});
```

Clicking the button normally produces:

```
Child clicked
Parent clicked
```

The click event bubbles from the button to its parent.

### Enabling Capturing

The third argument to `addEventListener()` can enable capturing.

```
parent.addEventListener("click", function() {
    console.log("Parent capturing");
}, true);
```

The parent listener can execute during the capturing phase, before the event reaches the child.

---

## 6. Controlling Event Propagation

### 6.1 stopPropagation()

Stops the event from continuing through the propagation path.

```
child.addEventListener("click", function(event) {
    event.stopPropagation();

    console.log("Child clicked");
});
```

The parent listener will not receive this click through normal propagation.

### 6.2 stopImmediatePropagation()

Stops further propagation and prevents other listeners on the same element from executing for that event.

Use it carefully because it can interfere with other event handlers.

### 6.3 preventDefault()

Prevents the browser's default action for an event when that action is cancelable.

Example:

```
<a href="https://example.com" id="myLink">Open Website</a>
```

```
const link = document.getElementById("myLink");

link.addEventListener("click", function(event) {
    event.preventDefault();

    console.log("Navigation prevented");
});
```

The browser will not follow the link's default navigation action.

**Important:** `preventDefault()` does not stop event propagation. `stopPropagation()` does not prevent the default browser action.

---

## 7. Event Delegation

Event delegation is a technique in which a parent element handles events from its child elements.

It uses event bubbling.

HTML:

```
<ul id="toolList">
    <li>Nmap</li>
    <li>Wireshark</li>
    <li>Burp Suite</li>
</ul>
```

JavaScript:

```
const list = document.getElementById("toolList");

list.addEventListener("click", function(event) {
    if (event.target.matches("li")) {
        console.log("Selected tool:", event.target.textContent);
    }
});
```

Advantages:

- Reduces the number of event listeners.
    
- Works with dynamically added child elements.
    
- Can simplify event management.
    

However, the handler should check the event target carefully. Events from nested elements may require using `closest()` to find the intended child.

Example:

```
list.addEventListener("click", function(event) {
    const item = event.target.closest("li");

    if (item && list.contains(item)) {
        console.log(item.textContent);
    }
});
```

---

## 8. Removing Event Listeners

The `removeEventListener()` method removes a previously registered event listener.

The function reference must match the function used when registering it.

```
const button = document.getElementById("myButton");

function handleClick() {
    console.log("Button clicked");
}

button.addEventListener("click", handleClick);

button.removeEventListener("click", handleClick);
```

This will not work as expected:

```
button.addEventListener("click", function() {
    console.log("Hello");
});

button.removeEventListener("click", function() {
    console.log("Hello");
});
```

The two anonymous functions are different function objects.

---

## 9. Event Listener Options

`addEventListener()` accepts an optional options object.

Common options:

|Option|Purpose|
|---|---|
|`capture`|Runs listener during capturing|
|`once`|Automatically removes listener after its first execution|
|`passive`|Indicates listener will not call `preventDefault()`|

Example using `once`:

```
button.addEventListener("click", function() {
    console.log("This runs only once");
}, {
    once: true
});
```

Example using `passive`:

```
window.addEventListener("scroll", function() {
    console.log("Page scrolling");
}, {
    passive: true
});
```

A passive listener cannot successfully prevent the event's default action.

---

## 10. Form Event Handling

JavaScript can handle form submissions and validate input.

HTML:

```
<form id="loginForm">
    <input type="text" id="username" placeholder="Username">

    <button type="submit">Submit</button>
</form>
```

JavaScript:

```
const form = document.getElementById("loginForm");
const username = document.getElementById("username");

form.addEventListener("submit", function(event) {
    event.preventDefault();

    if (username.value.trim() === "") {
        console.log("Username is required");
    } else {
        console.log("Submitted:", username.value);
    }
});
```

`preventDefault()` prevents the browser's normal form submission so JavaScript can handle the example locally.

**Security note:** Browser-side validation can be bypassed. The server must independently validate and authorize submitted data.

---

## 11. JavaScript Events and Security

Event handling is important in web application security.

### 11.1 Unsafe Inline Event Handlers

Avoid building event-handler attributes from untrusted strings.

Risky example:

```
element.setAttribute("onclick", userInput);
```

This can introduce script injection vulnerabilities.

Prefer registering a trusted function:

```
element.addEventListener("click", handleClick);
```

### 11.2 Input Validation

Do not assume that keyboard or form events guarantee valid input.

Validate data before using it, and enforce security rules on the server.

### 11.3 Clickjacking Awareness

Clickjacking tricks users into interacting with a webpage element they did not intend to click.

Event handling alone cannot prevent clickjacking. Websites should use appropriate response headers such as:

- `Content-Security-Policy` with `frame-ancestors`.
    
- `X-Frame-Options` where appropriate.
    

### 11.4 Do Not Trust Client-Side Authorization

Hiding a button or blocking a click does not secure a sensitive operation.

Authorization must be checked by the backend for every protected action.

---

## 12. Practical Labs

### Lab 1: Button Click Event

Create an HTML file:

```
<!DOCTYPE html>
<html>
<body>

    <h1 id="heading">Original Text</h1>

    <button id="changeBtn">Change Text</button>

    <script>
        const heading = document.getElementById("heading");
        const button = document.getElementById("changeBtn");

        button.addEventListener("click", function() {
            heading.textContent = "Text Changed!";
        });
    </script>

</body>
</html>
```

Observe how clicking the button changes the heading.

### Lab 2: Keyboard Event

```
<!DOCTYPE html>
<html>
<body>

    <input type="text" id="username" placeholder="Type something">

    <script>
        const input = document.getElementById("username");

        input.addEventListener("keydown", function(event) {
            console.log("Key pressed:", event.key);
        });
    </script>

</body>
</html>
```

Open the browser console and type into the input field.

### Lab 3: Event Delegation

```
<!DOCTYPE html>
<html>
<body>

    <h2>Cybersecurity Tools</h2>

    <ul id="tools">
        <li>Nmap</li>
        <li>Wireshark</li>
        <li>Burp Suite</li>
    </ul>

    <script>
        const tools = document.getElementById("tools");

        tools.addEventListener("click", function(event) {
            if (event.target.matches("li")) {
                console.log("Selected:", event.target.textContent);
            }
        });
    </script>

</body>
</html>
```

Click different list items and observe the console.

### Lab 4: Mini Project — Interactive Tool Selector

Build a webpage that:

1. Displays a list of cybersecurity tools.
    
2. Detects which tool the user clicks.
    
3. Displays the selected tool.
    
4. Uses event delegation.
    
5. Includes a button that clears the selection.
    

Use:

- `addEventListener()`
    
- `event.target`
    
- `textContent`
    
- `preventDefault()` where appropriate
    
- `removeEventListener()` if you add a removable listener
    

---

## 13. Key Points to Remember

1. An event is an action or occurrence detected by the browser.
    
2. An event handler executes when an event occurs.
    
3. `addEventListener()` registers an event listener.
    
4. `removeEventListener()` removes a registered listener.
    
5. The event object contains information about an event.
    
6. `event.target` identifies the original event target.
    
7. `event.currentTarget` identifies the element handling the event.
    
8. Event propagation includes capturing, target, and bubbling phases.
    
9. `stopPropagation()` stops further propagation.
    
10. `preventDefault()` prevents a cancelable default action.
    
11. Event delegation uses bubbling to handle child events through a parent.
    
12. Client-side event handling is not a replacement for server-side security.
    

## 14. Quick Revision

|Concept|Meaning|
|---|---|
|Event|Browser-detected action or occurrence|
|Event handler|Function executed in response to an event|
|`click`|Mouse click event|
|`keydown`|Keyboard key press event|
|`submit`|Form submission event|
|`addEventListener()`|Registers an event listener|
|`removeEventListener()`|Removes an event listener|
|`event.target`|Original event target|
|`event.currentTarget`|Element handling the event|
|Capturing|Event travels toward the target|
|Bubbling|Event travels back through ancestors|
|`preventDefault()`|Prevents default browser behaviour|
|`stopPropagation()`|Stops further event propagation|
|Event delegation|Parent handles child events|

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Functions]]
    
- [[JavaScript Arrays and Objects]]
    
- [[JavaScript DOM]]
    
- [[JavaScript Asynchronous Programming]]
    
- [[JavaScript Fetch API]]
    
- [[Introduction to Secure Coding]]
    
- [[Cross-Site Scripting Prevention]]