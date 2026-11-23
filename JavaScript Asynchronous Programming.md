> Understand how JavaScript handles operations that take time, allowing applications to remain responsive while waiting for external tasks to complete.

## 1. Introduction to Asynchronous Programming

Asynchronous programming allows JavaScript to start an operation and continue executing other code without waiting for that operation to finish.

Examples of asynchronous operations:

- Fetching data from an API.
    
- Reading files.
    
- Communicating with a server.
    
- Database operations.
    
- Timers and scheduled tasks.
    

### Synchronous vs Asynchronous Programming

**Synchronous programming:** Operations execute one after another. Each operation must finish before the next one proceeds.

```
console.log("First");
console.log("Second");
console.log("Third");
```

Output:

```
First
Second
Third
```

**Asynchronous programming:** An operation can complete later while JavaScript continues executing other code.

```
console.log("First");

setTimeout(() => {
    console.log("Second");
}, 2000);

console.log("Third");
```

Output:

```
First
Third
Second
```

The timer schedules a callback to execute after approximately two seconds. It does not block the remaining synchronous code.

---

## 2. JavaScript Runtime and Event Loop

JavaScript commonly executes application code on a single main thread in a browser environment.

The runtime uses several components to coordinate asynchronous work.

### Important Components

|Component|Purpose|
|---|---|
|Call Stack|Tracks currently executing functions|
|Web APIs|Browser-provided facilities such as timers and networking|
|Callback Queue|Holds callbacks waiting for execution|
|Microtask Queue|Holds microtasks such as Promise callbacks|
|Event Loop|Coordinates execution between the call stack and queues|

### How the Event Loop Works

Consider:

```
console.log("Start");

setTimeout(() => {
    console.log("Timer");
}, 0);

console.log("End");
```

Output:

```
Start
End
Timer
```

Explanation:

1. `console.log("Start")` executes.
    
2. `setTimeout()` schedules a timer callback.
    
3. `console.log("End")` executes.
    
4. The current synchronous code finishes.
    
5. The event loop allows the timer callback to execute when it is ready.
    

A zero-millisecond timer does not mean immediate execution. Its callback still waits until the current synchronous work has completed and the runtime can process it.

---

## 3. Callbacks

A callback is a function passed as an argument to another function.

Callbacks are commonly used to execute code after an operation or event.

### Example

```
function greet(name, callback) {
    console.log("Hello " + name);

    callback();
}

function showMessage() {
    console.log("Welcome to JavaScript");
}

greet("Alex", showMessage);
```

Output:

```
Hello Alex
Welcome to JavaScript
```

### Asynchronous Callback Example

```
console.log("Start");

setTimeout(function() {
    console.log("Task completed");
}, 2000);

console.log("End");
```

The callback executes after the timer completes.

### Advantages of Callbacks

- Simple way to handle events.
    
- Useful for asynchronous operations.
    
- Allow functions to be reused.
    
- Support flexible program behaviour.
    

### Callback Hell

Callback hell occurs when many nested callbacks make code difficult to understand and maintain.

Example:

```
getUser(function(user) {
    getOrders(user.id, function(orders) {
        getPayments(orders[0].id, function(payment) {
            console.log(payment);
        });
    });
});
```

Problems:

- Difficult to read.
    
- Difficult to debug.
    
- Error handling becomes complicated.
    
- Deep nesting reduces maintainability.
    

Promises and async/await provide cleaner alternatives.

---

## 4. Promises

A Promise is a JavaScript object representing the eventual completion or failure of an asynchronous operation.

A Promise can be in one of three states:

|State|Meaning|
|---|---|
|Pending|Operation has not settled|
|Fulfilled|Operation completed successfully|
|Rejected|Operation failed|

Once a Promise is fulfilled or rejected, it is settled and cannot change to another state.

### Creating a Promise

```
const myPromise = new Promise((resolve, reject) => {
    const success = true;

    if (success) {
        resolve("Operation successful");
    } else {
        reject("Operation failed");
    }
});
```

- `resolve()` fulfills the Promise.
    
- `reject()` rejects the Promise.
    

### Handling a Promise with then()

The `then()` method handles successful fulfillment.

```
myPromise.then(result => {
    console.log(result);
});
```

### Handling Errors with catch()

The `catch()` method handles rejection.

```
myPromise.catch(error => {
    console.log(error);
});
```

### Using finally()

The `finally()` method executes after the Promise settles, regardless of whether it fulfilled or rejected.

```
myPromise.finally(() => {
    console.log("Operation finished");
});
```

### Complete Example

```
const myPromise = new Promise((resolve, reject) => {
    const success = true;

    if (success) {
        resolve("Data received");
    } else {
        reject("Unable to receive data");
    }
});

myPromise
    .then(result => {
        console.log(result);
    })
    .catch(error => {
        console.log(error);
    })
    .finally(() => {
        console.log("Request completed");
    });
```

---

## 5. Promise Chaining

Promise chaining allows multiple asynchronous operations to execute in sequence.

```
Promise.resolve(10)
    .then(number => {
        console.log(number);

        return number * 2;
    })
    .then(result => {
        console.log(result);

        return result + 5;
    })
    .then(finalResult => {
        console.log(finalResult);
    })
    .catch(error => {
        console.log(error);
    });
```

Output:

```
10
20
25
```

Each `then()` receives the value returned by the previous handler.

If a handler returns another Promise, the chain waits for that Promise to settle before continuing.

---

## 6. Promise Methods

JavaScript provides methods for working with multiple Promises.

### 6.1 Promise.all()

Waits for all Promises to fulfill.

```
const promise1 = Promise.resolve("Task 1");
const promise2 = Promise.resolve("Task 2");
const promise3 = Promise.resolve("Task 3");

Promise.all([promise1, promise2, promise3])
    .then(results => {
        console.log(results);
    })
    .catch(error => {
        console.log(error);
    });
```

If any input Promise rejects, `Promise.all()` rejects with that reason.

### 6.2 Promise.allSettled()

Waits until every Promise settles, whether fulfilled or rejected.

```
const tasks = [
    Promise.resolve("Success"),
    Promise.reject("Failed")
];

Promise.allSettled(tasks).then(results => {
    console.log(results);
});
```

It returns an array describing the outcome of each Promise.

### 6.3 Promise.race()

Settles with the outcome of the first input Promise to settle.

```
const first = new Promise(resolve => {
    setTimeout(() => resolve("First"), 1000);
});

const second = new Promise(resolve => {
    setTimeout(() => resolve("Second"), 2000);
});

Promise.race([first, second]).then(result => {
    console.log(result);
});
```

Output:

```
First
```

### 6.4 Promise.any()

Fulfills with the first input Promise that fulfills.

```
const tasks = [
    Promise.reject("Error 1"),
    Promise.resolve("Success"),
    Promise.resolve("Another success")
];

Promise.any(tasks).then(result => {
    console.log(result);
});
```

If every input Promise rejects, `Promise.any()` rejects with an `AggregateError`.

### Comparison

|Method|Behaviour|
|---|---|
|`Promise.all()`|Fulfills when all fulfill; rejects when one rejects|
|`Promise.allSettled()`|Waits for every Promise to settle|
|`Promise.race()`|Settles with the first settled Promise|
|`Promise.any()`|Fulfills with the first fulfilled Promise|

---

## 7. Async and Await

`async` and `await` provide a cleaner syntax for working with Promises.

### 7.1 async Keyword

An `async` function always returns a Promise.

```
async function greet() {
    return "Hello";
}

greet().then(message => {
    console.log(message);
});
```

Even though the function returns a normal string, JavaScript wraps that value in a fulfilled Promise.

### 7.2 await Keyword

The `await` keyword pauses the execution of the surrounding async function until the awaited Promise settles.

```
function getData() {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve("Data received");
        }, 2000);
    });
}

async function displayData() {
    const result = await getData();

    console.log(result);
}

displayData();
```

`await` does not block the entire JavaScript runtime. Other tasks can continue while the async function waits.

### 7.3 Error Handling with try...catch

Use `try...catch` to handle errors from awaited Promises.

```
async function getData() {
    try {
        const result = await Promise.reject("Request failed");

        console.log(result);
    } catch (error) {
        console.log("Error:", error);
    }
}

getData();
```

### 7.4 Using finally

```
async function processData() {
    try {
        console.log("Processing data");
    } catch (error) {
        console.log(error);
    } finally {
        console.log("Process finished");
    }
}

processData();
```

### 7.5 Sequential vs Parallel Execution

Sequential execution waits for each operation before starting the next.

```
async function runTasks() {
    const first = await taskOne();
    const second = await taskTwo();

    console.log(first, second);
}
```

Parallel execution starts both operations before waiting for their results.

```
async function runTasks() {
    const [first, second] = await Promise.all([
        taskOne(),
        taskTwo()
    ]);

    console.log(first, second);
}
```

Use parallel execution when operations are independent and can safely run at the same time.

---

## 8. Timers in JavaScript

JavaScript provides timer functions for scheduling code execution.

### 8.1 setTimeout()

Executes a callback after a specified delay.

```
setTimeout(() => {
    console.log("Executed after approximately 2 seconds");
}, 2000);
```

The delay is measured in milliseconds.

### 8.2 clearTimeout()

Cancels a scheduled timeout before it executes.

```
const timer = setTimeout(() => {
    console.log("This will not execute");
}, 3000);

clearTimeout(timer);
```

### 8.3 setInterval()

Repeatedly executes a callback at a specified interval.

```
const timer = setInterval(() => {
    console.log("Running...");
}, 2000);
```

### 8.4 clearInterval()

Stops a repeating interval.

```
const timer = setInterval(() => {
    console.log("Running...");
}, 1000);

setTimeout(() => {
    clearInterval(timer);
    console.log("Interval stopped");
}, 5000);
```

**Important:** Timers schedule callbacks; they do not guarantee execution at an exact time. A busy event loop can delay them.

---

## 9. Microtasks and Macrotasks

JavaScript runtimes use different task queues.

Two important categories are:

**Microtasks:**

- Promise callbacks such as `.then()`, `.catch()`, and `.finally()`.
    
- `queueMicrotask()` callbacks.
    
- Mutation observer callbacks in browsers.
    

**Tasks (often called macrotasks):**

- Timer callbacks such as `setTimeout()`.
    
- Many browser event callbacks.
    
- Other host-scheduled tasks.
    

After the current synchronous code finishes, the runtime generally processes the microtask queue before moving to the next task.

Example:

```
console.log("Start");

setTimeout(() => {
    console.log("Timer");
}, 0);

Promise.resolve().then(() => {
    console.log("Promise");
});

console.log("End");
```

Output:

```
Start
End
Promise
Timer
```

Explanation:

1. Synchronous statements execute first.
    
2. The Promise callback is scheduled as a microtask.
    
3. The timer callback is scheduled as a task.
    
4. After synchronous execution, the microtask runs.
    
5. The timer callback runs when its task is processed.
    

---

## 10. Asynchronous Programming and APIs

Modern applications frequently communicate with remote servers.

JavaScript can use asynchronous operations to request data without blocking the main thread.

Common examples:

- Retrieving user information.
    
- Loading application data.
    
- Checking service availability.
    
- Sending form submissions.
    
- Communicating with backend APIs.
    

The Fetch API provides a Promise-based interface for making HTTP requests.

Example:

```
fetch("https://jsonplaceholder.typicode.com/users/1")
    .then(response => {
        if (!response.ok) {
            throw new Error("HTTP error: " + response.status);
        }

        return response.json();
    })
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.log("Request failed:", error);
    });
```

Detailed Fetch API concepts are covered in:

- [[JavaScript Fetch API]]
    

---

## 11. Common Errors in Asynchronous Programming

### 11.1 Forgetting await

Incorrect:

```
async function getData() {
    const result = fetch("https://example.com");

    console.log(result);
}
```

The variable contains a Promise rather than the completed response.

Correct:

```
async function getData() {
    const result = await fetch("https://example.com");

    console.log(result);
}
```

### 11.2 Missing Error Handling

Network requests can fail.

Use `try...catch` or Promise rejection handlers.

```
async function getData() {
    try {
        const response = await fetch("https://example.com");

        if (!response.ok) {
            throw new Error("HTTP error: " + response.status);
        }

        console.log(response.status);
    } catch (error) {
        console.log("Request failed:", error);
    }
}
```

### 11.3 Sequential Execution When Parallel Is Possible

Unnecessarily waiting for independent operations can increase total execution time.

Consider `Promise.all()` when operations do not depend on one another.

### 11.4 Unhandled Promise Rejections

A rejected Promise without appropriate error handling can produce an unhandled rejection.

Always consider how failures will be handled.

---

## 12. Security Considerations

Asynchronous JavaScript is frequently used in applications that communicate with servers and process external data.

### 12.1 Validate API Responses

Do not automatically trust data received from an API.

Validate:

- Expected data types.
    
- Required properties.
    
- Acceptable values.
    
- Data size and format.
    

### 12.2 Handle Errors Safely

Do not expose sensitive internal information through error messages.

Log appropriate technical details securely on the server and show users safe, understandable messages.

### 12.3 Avoid Hardcoding Secrets

Never place private API keys, passwords, or server credentials in frontend JavaScript.

Browser code can be inspected by users.

### 12.4 Use HTTPS

Use HTTPS to protect data in transit between the client and server.

HTTPS provides transport protection but does not guarantee that the remote server or its returned data is trustworthy.

### 12.5 Handle Timeouts and Cancellation

A request may take too long or no longer be needed.

The `AbortController` API can cancel supported asynchronous operations such as Fetch requests.

Example:

```
const controller = new AbortController();

fetch("https://example.com", {
    signal: controller.signal
})
    .then(response => console.log(response.status))
    .catch(error => {
        if (error.name === "AbortError") {
            console.log("Request cancelled");
        } else {
            console.log("Request failed:", error);
        }
    });

controller.abort();
```

In a real application, call `abort()` when cancellation is actually required, such as when a user leaves a page or changes a search query.

---

## 13. Practical Labs

### Lab 1: Working with setTimeout()

```
console.log("Starting task");

setTimeout(() => {
    console.log("Task completed");
}, 2000);

console.log("Continuing program");
```

Observe the execution order.

### Lab 2: Creating a Promise

```
const task = new Promise((resolve, reject) => {
    const success = true;

    setTimeout(() => {
        if (success) {
            resolve("Task successful");
        } else {
            reject("Task failed");
        }
    }, 2000);
});

task
    .then(result => console.log(result))
    .catch(error => console.log(error));
```

Change `success` to `false` and observe the result.

### Lab 3: Using async and await

```
function getUser() {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve({
                name: "Alex",
                course: "Cybersecurity"
            });
        }, 1500);
    });
}

async function displayUser() {
    const user = await getUser();

    console.log(user.name);
    console.log(user.course);
}

displayUser();
```

### Lab 4: Compare Promise and Timer Execution

```
console.log("Start");

setTimeout(() => {
    console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
    console.log("Promise");
});

console.log("End");
```

Write down the output and explain why it appears in that order.

### Lab 5: Mini Project — Asynchronous Security Status Checker

Create a simulated security status checker.

```
function checkSecurityStatus() {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve({
                firewall: "Enabled",
                antivirus: "Active",
                updates: "Current"
            });
        }, 2000);
    });
}

async function displayStatus() {
    console.log("Checking security status...");

    try {
        const status = await checkSecurityStatus();

        console.log("Firewall:", status.firewall);
        console.log("Antivirus:", status.antivirus);
        console.log("Updates:", status.updates);
    } catch (error) {
        console.log("Unable to retrieve status:", error);
    }
}

displayStatus();
```

This is a simulation, not a real system security assessment.

---

## 14. Key Points to Remember

1. Asynchronous programming allows operations to complete without blocking other JavaScript execution.
    
2. A callback is a function passed to another function.
    
3. A Promise represents the eventual result of an asynchronous operation.
    
4. Promises have pending, fulfilled, and rejected states.
    
5. `then()` handles fulfillment.
    
6. `catch()` handles rejection.
    
7. `finally()` executes after a Promise settles.
    
8. `async` functions always return Promises.
    
9. `await` pauses the surrounding async function until a Promise settles.
    
10. `Promise.all()` waits for all Promises to fulfill.
    
11. `Promise.allSettled()` waits for every Promise to settle.
    
12. `Promise.race()` uses the first settled Promise.
    
13. `Promise.any()` uses the first fulfilled Promise.
    
14. The event loop coordinates asynchronous execution.
    
15. Microtasks are generally processed before the next task.
    
16. `setTimeout()` schedules a callback.
    
17. `setInterval()` schedules repeated callbacks.
    
18. `AbortController` can cancel supported asynchronous operations.
    

## 15. Quick Revision

|Concept|Meaning|
|---|---|
|Synchronous|Executes sequentially|
|Asynchronous|Allows operations to complete later|
|Callback|Function passed as an argument|
|Promise|Represents an eventual result|
|Pending|Promise has not settled|
|Fulfilled|Promise completed successfully|
|Rejected|Promise failed|
|`then()`|Handles fulfillment|
|`catch()`|Handles rejection|
|`finally()`|Runs after settlement|
|`async`|Declares an async function|
|`await`|Waits for a Promise inside an async function|
|Event Loop|Coordinates task execution|
|Microtask|High-priority queued callback|
|`setTimeout()`|Schedules a delayed callback|
|`setInterval()`|Schedules repeated callbacks|
|`Promise.all()`|Waits for all Promises to fulfill|
|`AbortController`|Cancels supported operations|

## Related Notes

- [[Introduction to JavaScript]]
    
- [[JavaScript Functions]]
    
- [[JavaScript Arrays and Objects]]
    
- [[JavaScript DOM]]
    
- [[JavaScript Events]]
    
- [[JavaScript Fetch API]]
    
- [[APIs and HTTP Requests]]
    
- [[Introduction to Secure Coding]]