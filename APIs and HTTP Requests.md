> Understand how applications communicate through APIs, how HTTP requests work, and how to interact with web services programmatically.

## 1. Introduction

An API (Application Programming Interface) is a defined interface that allows different software applications to communicate and exchange information.

For example:

- A weather application retrieves weather information from a server.
    
- A banking application communicates with banking services.
    
- A security tool retrieves threat intelligence from an API.
    
- A website sends login details to a backend server.
    

APIs define how applications request and exchange data.

## 2. What Is an API?

An API provides a set of rules, endpoints, and operations that applications can use to interact with another system.

Consider a weather application.

The application needs weather information but does not need to maintain its own global weather database.

Instead, it sends a request to a weather service API.

The API processes the request and returns the available information.

### Basic API Communication

```
Client Application
       |
       | HTTP Request
       v
    API Server
       |
       | Process Request
       v
    Database
       |
       | Return Data
       v
    API Server
       |
       | HTTP Response
       v
Client Application
```

## 3. Types of APIs

### 3.1 REST API

REST stands for Representational State Transfer.

REST is an architectural style commonly used to build web APIs.

REST APIs commonly use HTTP methods and resource-based URLs.

Example:

```
GET /users/101
```

This requests information about a user with ID 101.

### 3.2 SOAP API

SOAP stands for Simple Object Access Protocol.

It is a messaging protocol commonly associated with XML-based messages.

It defines a structured approach to exchanging information between applications.

### 3.3 GraphQL API

GraphQL is a query language and runtime for APIs.

It allows clients to request specific fields of data.

Example:

```
{
  user(id: 101) {
    name
    email
  }
}
```

### 3.4 WebSocket API

WebSocket enables persistent, two-way communication between a client and server over a connection.

It is useful for:

- Live notifications.
    
- Chat applications.
    
- Real-time dashboards.
    
- Live monitoring systems.
    

## 4. What Is HTTP?

HTTP stands for Hypertext Transfer Protocol.

It is an application-layer protocol used for communication between clients and servers.

HTTP follows a request-response model.

A client sends an HTTP request, and the server returns an HTTP response.

Common HTTP methods include:

|Method|Purpose|
|---|---|
|GET|Retrieve information|
|POST|Submit data or request processing|
|PUT|Replace a resource|
|PATCH|Partially update a resource|
|DELETE|Delete a resource|
|HEAD|Retrieve response headers without the response body|
|OPTIONS|Discover supported communication options|

The actual effect of a method depends on how the server implements its API.

## 5. HTTP Request Structure

An HTTP request commonly contains:

1. Request method.
    
2. Request URL or target.
    
3. HTTP headers.
    
4. Optional request body.
    

Example:

```
POST /api/users HTTP/1.1
Host: example.com
Content-Type: application/json
Accept: application/json

{
  "username": "student",
  "role": "analyst"
}
```

Explanation:

- `POST` is the HTTP method.
    
- `/api/users` is the request target.
    
- `Host` identifies the target host.
    
- `Content-Type` describes the request body format.
    
- `Accept` indicates the response format the client can accept.
    
- The JSON object is the request body.
    

## 6. HTTP Response Structure

An HTTP response commonly contains:

1. HTTP version.
    
2. Status code.
    
3. Status message.
    
4. Response headers.
    
5. Optional response body.
    

Example:

```
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": 101,
  "username": "student",
  "status": "created"
}
```

The status code `201` indicates that the request successfully created a resource.

## 7. HTTP Status Codes

HTTP status codes communicate the result of a request.

|Code Range|Category|Meaning|
|---|---|---|
|1xx|Informational|Request processing continues|
|2xx|Success|Request succeeded|
|3xx|Redirection|Further action or redirection|
|4xx|Client Error|Problem with the request|
|5xx|Server Error|Server failed to fulfill the request|

### Common Status Codes

|Status Code|Meaning|
|---|---|
|200|OK|
|201|Created|
|204|No Content|
|301|Moved Permanently|
|302|Found|
|304|Not Modified|
|400|Bad Request|
|401|Unauthorized|
|403|Forbidden|
|404|Not Found|
|405|Method Not Allowed|
|429|Too Many Requests|
|500|Internal Server Error|
|502|Bad Gateway|
|503|Service Unavailable|
|504|Gateway Timeout|

**Important:** HTTP `401 Unauthorized` generally means valid authentication credentials are missing or invalid. `403 Forbidden` means the server understood the request but refuses to authorize it.

## 8. HTTP Headers

HTTP headers carry additional information about requests and responses.

Common request and response headers:

|Header|Purpose|
|---|---|
|Host|Identifies the target host|
|Content-Type|Describes the body media type|
|Accept|Lists acceptable response media types|
|Authorization|Carries authentication credentials|
|User-Agent|Identifies the client software|
|Cookie|Sends stored cookies|
|Set-Cookie|Instructs the browser to store cookies|
|Cache-Control|Defines caching behavior|
|Origin|Identifies the request origin in relevant contexts|

Headers are important for API communication, authentication, caching, and security.

## 9. API Endpoints

An endpoint is a specific URL through which an API exposes a resource or operation.

Example base URL:

```
https://api.example.com
```

Example endpoints:

```
GET    /users
GET    /users/101
POST   /users
PATCH  /users/101
DELETE /users/101
```

These endpoints represent common operations on user resources.

A real API may use different endpoint names and permissions.

## 10. API Authentication

APIs often require authentication to verify the identity of a client or user.

Common approaches include:

### 10.1 API Keys

An API key is a credential used to identify or authorize an application.

Example header:

```
X-API-Key: YOUR_API_KEY
```

API keys should be stored securely and should not be exposed in public source code.

### 10.2 Bearer Tokens

Bearer tokens are credentials sent with requests, commonly in the Authorization header.

Example:

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Anyone who obtains a valid bearer token may be able to use it within its permissions and lifetime.

### 10.3 OAuth 2.0

OAuth 2.0 is an authorization framework that allows applications to obtain limited access to protected resources.

It commonly uses access tokens and defined authorization flows.

### 10.4 Basic Authentication

Basic Authentication sends a Base64-encoded username and password in the Authorization header.

Base64 is encoding, not encryption.

Basic Authentication should only be used over properly secured HTTPS connections.

## 11. Making HTTP Requests in Python

Python can send HTTP requests using third-party libraries such as `requests`.

Install it:

```
python -m pip install requests
```

Import the library:

```
import requests
```

### 11.1 GET Request

A GET request retrieves information.

```
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"

response = requests.get(url, timeout=10)

print(response.status_code)
print(response.text)
```

### 11.2 Convert JSON Response

```
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"

response = requests.get(url, timeout=10)

if response.ok:
    data = response.json()
    print(data)
```

The `.json()` method parses a JSON response into Python data structures.

### 11.3 POST Request

A POST request can submit information to a server.

```
import requests

url = "https://jsonplaceholder.typicode.com/posts"

data = {
    "title": "Cybersecurity",
    "body": "Learning API requests",
    "userId": 1
}

response = requests.post(url, json=data, timeout=10)

print(response.status_code)
print(response.text)
```

This example uses a public demonstration API. Its responses may be simulated rather than permanently stored.

### 11.4 Custom Headers

```
import requests

url = "https://api.example.com/users"

headers = {
    "Accept": "application/json"
}

response = requests.get(
    url,
    headers=headers,
    timeout=10
)

print(response.status_code)
```

### 11.5 Handling Errors

Network requests can fail because of timeouts, connection errors, unsuccessful HTTP responses, or invalid JSON.

```
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"

try:
    response = requests.get(url, timeout=10)
    response.raise_for_status()

    data = response.json()

    print(data)

except requests.exceptions.Timeout:
    print("Request timed out")

except requests.exceptions.HTTPError as error:
    print("HTTP error:", error)

except requests.exceptions.RequestException as error:
    print("Request failed:", error)

except ValueError:
    print("Response did not contain valid JSON")
```

## 12. Making HTTP Requests in JavaScript

JavaScript provides the Fetch API for making HTTP requests.

### 12.1 GET Request

```
async function getUser() {
    const response = await fetch(
        "https://jsonplaceholder.typicode.com/users/1"
    );

    if (!response.ok) {
        throw new Error(`HTTP error: ${response.status}`);
    }

    const data = await response.json();

    console.log(data);
}

getUser().catch(console.error);
```

### 12.2 POST Request

```
async function createPost() {
    const response = await fetch(
        "https://jsonplaceholder.typicode.com/posts",
        {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                title: "Cybersecurity",
                body: "Learning API communication",
                userId: 1
            })
        }
    );

    if (!response.ok) {
        throw new Error(`HTTP error: ${response.status}`);
    }

    const data = await response.json();

    console.log(data);
}

createPost().catch(console.error);
```

## 13. API Security

APIs can expose sensitive application functionality and data.

Common API security risks include:

### 13.1 Broken Object Level Authorization

An attacker changes an object identifier to access another user's information.

Example:

```
/api/users/101
/api/users/102
```

The server must verify whether the requesting user is authorized to access each object.

### 13.2 Broken Authentication

Weak authentication or poorly managed tokens may allow unauthorized access.

### 13.3 Excessive Data Exposure

An API may return more information than the client actually needs.

Responses should contain only appropriate fields.

### 13.4 Injection

Untrusted input may be used unsafely in database queries, commands, or other interpreters.

Use parameterized queries and appropriate input handling.

### 13.5 Unrestricted Resource Consumption

Attackers may send excessive requests or unusually large payloads.

Defenses can include:

- Rate limiting.
    
- Request-size limits.
    
- Timeouts.
    
- Resource quotas.
    
- Monitoring.
    

### 13.6 Security Misconfiguration

Incorrect CORS policies, exposed debug information, unnecessary endpoints, or weak TLS settings can increase risk.

## 14. API Security Best Practices

- Use HTTPS.
    
- Authenticate clients appropriately.
    
- Enforce authorization on every protected operation.
    
- Validate incoming data.
    
- Avoid exposing sensitive information.
    
- Apply rate limits.
    
- Set request-size limits.
    
- Use secure token storage and handling.
    
- Keep dependencies updated.
    
- Log relevant security events.
    
- Avoid placing credentials in URLs.
    
- Use least-privilege access.
    

## 15. Practical Lab

**Objective:** Understand HTTP requests and API responses using Python.

Create a file named:

```
api_lab.py
```

### Lab A — Send a GET Request

```
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"

response = requests.get(url, timeout=10)

print("Status:", response.status_code)
print("Response:", response.text)
```

Observe:

- HTTP status code.
    
- Response body.
    
- Returned JSON fields.
    

### Lab B — Extract Specific Fields

```
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"

response = requests.get(url, timeout=10)
response.raise_for_status()

data = response.json()

print("User ID:", data["userId"])
print("Title:", data["title"])
```

### Lab C — Send a POST Request

```
import requests

url = "https://jsonplaceholder.typicode.com/posts"

payload = {
    "title": "Network Security",
    "body": "Understanding API requests",
    "userId": 1
}

response = requests.post(
    url,
    json=payload,
    timeout=10
)

print("Status:", response.status_code)
print("Response:", response.text)
```

### Lab D — Inspect Response Headers

```
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"

response = requests.get(url, timeout=10)

print("Status:", response.status_code)

for header, value in response.headers.items():
    print(header, ":", value)
```

### Lab E — Use a Custom Header

```
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"

headers = {
    "Accept": "application/json",
    "User-Agent": "ROOTLOG-Lab/1.0"
}

response = requests.get(
    url,
    headers=headers,
    timeout=10
)

print(response.status_code)
print(response.text)
```

Only send requests to services you are authorized to test. The examples above use a public demonstration API.

## 16. Key Takeaways

- APIs allow software applications to communicate.
    
- REST, SOAP, GraphQL, and WebSocket are different API technologies or approaches.
    
- HTTP uses a request-response communication model.
    
- HTTP methods define common request operations.
    
- Status codes communicate request results.
    
- Headers carry additional request and response information.
    
- API authentication verifies identity or credentials.
    
- Python's `requests` library supports HTTP communication.
    
- JavaScript provides the Fetch API.
    
- API security requires authentication, authorization, validation, and resource controls.
    

## 17. Related Topics

- [[Introduction to Python]]
    
- [[Python Modules]]
    
- [[Python Exception Handling]]
    
- [[JavaScript Fetch API]]
    
- [[JavaScript Asynchronous Programming]]
    
- [[JSON]]
    
- [[HTTP and HTTPS]]
    
- [[SQL Injection]]
    
- [[Input Validation]]
    
- [[Authentication and Authorization]]
    
- [[Secure Error Handling]]
    
- [[Network Security]]