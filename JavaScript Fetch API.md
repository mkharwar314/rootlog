> Learn how JavaScript communicates with web servers and APIs using the Fetch API.

## 1. Introduction to Fetch API

The **Fetch API** is a built-in JavaScript interface used to make HTTP requests and receive responses from servers.

It allows web applications to:

- Retrieve data from APIs.
    
- Send information to servers.
    
- Submit forms.
    
- Update or delete server-side data.
    
- Communicate with backend applications.
    

For example, a weather application can use Fetch to retrieve current weather data from a weather API.

### Basic Syntax

```
fetch(url, options);
```

- `url`: The API endpoint.
    
- `options`: Optional request configuration, such as HTTP method and headers.
    

Fetch returns a **Promise** that resolves to a `Response` object.

## 2. Making a GET Request

A GET request retrieves information from a server.

```
fetch("https://jsonplaceholder.typicode.com/users/1")
    .then(response => response.json())
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error("Error:", error);
    });
```

### Explanation

1. `fetch()` sends the HTTP request.
    
2. The first `.then()` receives the response.
    
3. `response.json()` reads and parses the JSON response.
    
4. The next `.then()` receives the parsed data.
    
5. `.catch()` handles network-level or other rejected Promise errors.
    

## 3. Understanding the Response Object

Fetch resolves with a `Response` object containing information about the server's response.

Important properties:

|Property|Description|
|---|---|
|`status`|HTTP status code|
|`ok`|True when status is between 200 and 299|
|`statusText`|Status description|
|`headers`|Response headers|
|`url`|Final response URL|

Example:

```
fetch("https://jsonplaceholder.typicode.com/users/1")
    .then(response => {
        console.log(response.status);
        console.log(response.ok);
        console.log(response.headers);
    });
```

**Important:** Fetch does not automatically reject a Promise for HTTP errors such as 404 or 500. You must check `response.ok` or `response.status`.

## 4. Reading Response Data

The Response object provides methods to read the response body.

|Method|Purpose|
|---|---|
|`json()`|Parses JSON data|
|`text()`|Reads text|
|`blob()`|Reads binary data as a Blob|
|`arrayBuffer()`|Reads binary data as an ArrayBuffer|
|`formData()`|Reads form data|

Example:

```
fetch("https://jsonplaceholder.typicode.com/users/1")
    .then(response => response.json())
    .then(data => console.log(data));
```

These methods return Promises. The response body is generally consumable only once, so don't try to parse the same response body multiple times.

## 5. Using Async and Await with Fetch

`async` and `await` provide a cleaner way to work with Fetch.

```
async function getUser() {
    try {
        const response = await fetch(
            "https://jsonplaceholder.typicode.com/users/1"
        );

        if (!response.ok) {
            throw new Error(`HTTP error: ${response.status}`);
        }

        const data = await response.json();

        console.log(data);
    } catch (error) {
        console.error("Request failed:", error);
    }
}

getUser();
```

### Advantages

- Easier to read.
    
- Cleaner error handling.
    
- Less nested Promise chaining.
    
- Suitable for larger applications.
    

## 6. Fetch Request Options

The second argument of `fetch()` is an options object.

```
fetch(url, {
    method: "GET",
    headers: {},
    body: null
});
```

Important options:

|Option|Purpose|
|---|---|
|`method`|HTTP method|
|`headers`|Request headers|
|`body`|Data sent to the server|
|`mode`|Request mode, including CORS behavior|
|`credentials`|Controls sending credentials|
|`cache`|Controls HTTP cache behavior|
|`redirect`|Controls redirect handling|
|`signal`|Connects an AbortSignal to the request|

GET and HEAD requests generally should not contain a request body.

## 7. Sending a POST Request

POST is commonly used to submit data or create a resource.

```
async function createUser() {
    const user = {
        name: "Mohit",
        email: "mohit@example.com"
    };

    try {
        const response = await fetch(
            "https://jsonplaceholder.typicode.com/users",
            {
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify(user)
            }
        );

        if (!response.ok) {
            throw new Error(`HTTP error: ${response.status}`);
        }

        const result = await response.json();

        console.log(result);
    } catch (error) {
        console.error(error);
    }
}

createUser();
```

### Important Concepts

- `Content-Type` tells the server what format the request body uses.
    
- `JSON.stringify()` converts a JavaScript object into JSON text.
    
- The server processes the submitted data.
    

JSONPlaceholder is a testing API. It simulates data creation rather than permanently storing your submitted record.

## 8. PUT, PATCH and DELETE Requests

These methods are commonly used to modify or remove resources.

### PUT Request

PUT generally replaces the representation of a resource.

```
fetch("https://jsonplaceholder.typicode.com/users/1", {
    method: "PUT",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        id: 1,
        name: "Updated User",
        email: "updated@example.com"
    })
});
```

### PATCH Request

PATCH generally updates selected fields.

```
fetch("https://jsonplaceholder.typicode.com/users/1", {
    method: "PATCH",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        name: "New Name"
    })
});
```

### DELETE Request

DELETE requests the removal of a resource.

```
fetch("https://jsonplaceholder.typicode.com/users/1", {
    method: "DELETE"
});
```

### Comparison

|Method|Purpose|
|---|---|
|GET|Retrieve data|
|POST|Submit or create data|
|PUT|Replace a resource|
|PATCH|Partially update a resource|
|DELETE|Delete a resource|

The exact behavior depends on how the server implements its API.

## 9. Request Headers

HTTP headers carry additional information about a request or response.

Example:

```
fetch("https://example.com/api/data", {
    method: "GET",
    headers: {
        "Accept": "application/json",
        "Authorization": "Bearer YOUR_TOKEN"
    }
});
```

Common headers:

|Header|Purpose|
|---|---|
|`Content-Type`|Describes the request body format|
|`Accept`|Indicates acceptable response formats|
|`Authorization`|Provides authentication credentials|
|`User-Agent`|Identifies the requesting client|

Never put real API secrets or privileged credentials directly in public frontend JavaScript.

## 10. Request, Response and Headers Objects

The Fetch API includes three important interfaces.

### Request

Represents an HTTP request.

```
const request = new Request(
    "https://jsonplaceholder.typicode.com/users/1",
    {
        method: "GET"
    }
);

fetch(request);
```

### Response

Represents the server's response.

```
fetch("https://jsonplaceholder.typicode.com/users/1")
    .then(response => {
        console.log(response.status);
    });
```

### Headers

Used to work with HTTP headers.

```
const headers = new Headers();

headers.append("Accept", "application/json");

console.log(headers.get("Accept"));
```

## 11. Error Handling

There are two important categories of errors.

### HTTP Errors

The server responds with an HTTP error status, such as:

- 400 — Bad Request
    
- 401 — Unauthorized
    
- 403 — Forbidden
    
- 404 — Not Found
    
- 500 — Internal Server Error
    

Fetch still normally resolves with a Response object for these statuses.

### Network Errors

The request may fail because of:

- Network disconnection.
    
- DNS resolution failure.
    
- Connection problems.
    
- Browser-enforced CORS restrictions.
    

These can cause the Fetch Promise to reject.

### Reliable Error Handling

```
async function fetchData(url) {
    try {
        const response = await fetch(url);

        if (!response.ok) {
            throw new Error(`HTTP ${response.status}`);
        }

        return await response.json();

    } catch (error) {
        console.error("Fetch failed:", error.message);
        throw error;
    }
}

fetchData("https://jsonplaceholder.typicode.com/users/1")
    .then(data => console.log(data))
    .catch(error => console.error("Could not load data."));
```

## 12. CORS (Cross-Origin Resource Sharing)

CORS is a browser security mechanism that controls whether a webpage can access resources from another origin.

An origin consists of:

- Scheme (HTTP or HTTPS).
    
- Hostname.
    
- Port.
    

For example:

```
https://example.com
https://api.example.com
```

These are different origins because their hostnames differ.

### How CORS Works

1. A webpage sends a cross-origin request.
    
2. The browser checks the server's CORS response headers.
    
3. The server indicates which origins are allowed.
    
4. The browser permits or blocks access to the response according to the CORS rules.
    

Example server response header:

```
Access-Control-Allow-Origin: https://example.com
```

Some requests require a preflight request using the HTTP OPTIONS method before the actual request.

### Important Security Points

- CORS is not an authentication system.
    
- CORS does not replace server-side access control.
    
- `mode: "no-cors"` is not a general solution to CORS errors. It produces an opaque response that JavaScript cannot read normally.
    
- The server must be configured to allow the requesting origin.
    

## 13. AbortController

AbortController allows JavaScript to cancel a Fetch request.

```
const controller = new AbortController();

async function getData() {
    try {
        const response = await fetch(
            "https://jsonplaceholder.typicode.com/users",
            {
                signal: controller.signal
            }
        );

        const data = await response.json();

        console.log(data);

    } catch (error) {
        if (error.name === "AbortError") {
            console.log("Request cancelled.");
        } else {
            console.error(error);
        }
    }
}

getData();

// Cancel the request:
controller.abort();
```

### Common Uses

- Canceling outdated search requests.
    
- Stopping requests when a user leaves a page.
    
- Implementing request timeouts.
    
- Preventing unnecessary network activity.
    

## 14. Fetch API Security

Fetch is frequently used in applications that handle sensitive information. Poor implementation can introduce security problems.

### 1. Use HTTPS

Use HTTPS endpoints to protect data in transit.

### 2. Validate API Responses

Never assume that API data is correct or trustworthy.

Validate expected fields and data types before using them.

### 3. Avoid Hardcoding Secrets

Do not store private API keys, database passwords or privileged credentials in frontend JavaScript.

Frontend code is visible to users.

### 4. Prevent Cross-Site Scripting (XSS)

Avoid inserting untrusted API data using `innerHTML`.

Unsafe:

```
element.innerHTML = data.name;
```

Safer:

```
element.textContent = data.name;
```

### 5. Protect Authentication Credentials

Use appropriate authentication mechanisms and avoid sending credentials unnecessarily.

For cookie-based authentication:

- Use `Secure` cookies over HTTPS.
    
- Use `HttpOnly` to prevent JavaScript access to cookies.
    
- Configure `SameSite` appropriately.
    
- Protect state-changing operations against CSRF.
    

### 6. Understand CORS

Do not treat CORS as a replacement for authentication or authorization. The backend must independently verify permissions.

## 15. Practical Applications

The Fetch API is used in:

- Login and registration systems.
    
- Weather applications.
    
- Search interfaces.
    
- Dashboards.
    
- E-commerce applications.
    
- Security monitoring tools.
    
- Web applications communicating with REST APIs.
    

### Example: Display API Data

```
<!DOCTYPE html>
<html>
<head>
    <title>Fetch API Demo</title>
</head>
<body>

    <h2>User Information</h2>

    <button id="loadUser">Load User</button>

    <p id="result"></p>

    <script>
        document.getElementById("loadUser").addEventListener("click", async () => {
            const result = document.getElementById("result");

            try {
                const response = await fetch(
                    "https://jsonplaceholder.typicode.com/users/1"
                );

                if (!response.ok) {
                    throw new Error(`HTTP ${response.status}`);
                }

                const user = await response.json();

                result.textContent =
                    `Name: ${user.name}, Email: ${user.email}`;

            } catch (error) {
                result.textContent = "Unable to load user information.";
                console.error(error);
            }
        });
    </script>

</body>
</html>
```

## 16. Practical Labs

### Lab 1: GET Request

Retrieve user information from:

```
https://jsonplaceholder.typicode.com/users/1
```

Tasks:

1. Make a GET request.
    
2. Display the response in the console.
    
3. Identify the user's name and email.
    

### Lab 2: POST Request

Send a JSON object containing a name and email.

Tasks:

1. Create a JavaScript object.
    
2. Convert it using `JSON.stringify()`.
    
3. Send it using POST.
    
4. Display the response.
    

### Lab 3: HTTP Error Handling

Request a nonexistent resource:

```
https://jsonplaceholder.typicode.com/users/9999
```

Tasks:

1. Inspect the HTTP status.
    
2. Check `response.ok`.
    
3. Handle unsuccessful responses.
    

### Lab 4: Cancel a Request

Tasks:

1. Create an AbortController.
    
2. Pass its signal to Fetch.
    
3. Cancel the request.
    
4. Handle the AbortError.
    

### Lab 5: Mini API Dashboard

Build a small webpage that:

1. Retrieves user information.
    
2. Displays the name and email.
    
3. Shows a loading message.
    
4. Handles HTTP and network errors.
    
5. Uses `textContent` to display API data safely.
    

## 17. Key Takeaways

- Fetch API is used for HTTP communication.
    
- Fetch returns a Promise.
    
- The Response object contains status and response information.
    
- `response.json()` parses JSON data asynchronously.
    
- HTTP errors must be checked using `response.ok` or `response.status`.
    
- Async/await simplifies asynchronous code.
    
- CORS controls browser access to cross-origin responses.
    
- AbortController cancels requests.
    
- API responses must be treated as untrusted input.
    
- Frontend code must never contain private secrets.
    

## 18. Related Topics

- [[Introduction to JavaScript]]
    
- [[JavaScript Functions]]
    
- [[JavaScript Asynchronous Programming]]
    
- [[JavaScript Events]]
    
- [[APIs and HTTP Requests]]
    
- [[HTTP and HTTPS]]
    
- [[Authentication and Authorization]]
    
- [[Cross-Site Scripting Prevention]]
    
- [[SQL Injection Prevention]]
    

## 19. My Understanding

Write your own explanation:

- What is the Fetch API?
    
- What is a Promise?
    
- What is the difference between GET and POST?
    
- Why should we check `response.ok`?
    
- What is CORS?
    
- How does AbortController work?
    
- Why should API data be treated as untrusted input?
    

## 20. Questions & Doubts

Record questions that need further research.