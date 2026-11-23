> Understand how web clients and servers exchange resources and how TLS protects web traffic.

## 1. HTTP

**HTTP (Hypertext Transfer Protocol)** is an application-layer protocol used for communication between clients (such as browsers) and web servers. It follows a request-response model.

A typical exchange:
1. A client sends an HTTP request.
2. The server processes it.
3. The server returns an HTTP response.

HTTP is **stateless**: each request is independent at the protocol level. Applications can maintain state using cookies, session identifiers, or tokens.

## 2. HTTP request structure

A request commonly contains:
- **Method** — the intended operation.
- **Request target** — path and optional query string.
- **Headers** — metadata such as host, accepted formats, and authentication.
- **Body** — optional data, often used with POST, PUT, or PATCH.

Common methods:

| Method | Typical purpose |
|---|---|
| GET | Retrieve a resource |
| POST | Submit data or request an action |
| PUT | Create or replace a resource at a known URI |
| PATCH | Partially update a resource |
| DELETE | Delete a resource |
| HEAD | Retrieve headers without the response body |
| OPTIONS | Ask which communication options are supported |

## 3. HTTP response structure

A response contains a status line, headers, and an optional body.

Status-code classes:

| Class | Meaning | Examples |
|---|---|---|
| 1xx | Informational | 100 Continue |
| 2xx | Success | 200 OK, 201 Created, 204 No Content |
| 3xx | Redirection | 301 Moved Permanently, 302 Found, 304 Not Modified |
| 4xx | Client-side error | 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found |
| 5xx | Server-side error | 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable |

## 4. Headers, cookies, and sessions

Headers carry metadata. Examples include `Host`, `Content-Type`, `Authorization`, and `Cache-Control`.

A cookie is data stored by a browser and sent with matching requests. Websites commonly use cookies to identify a session. The server can use a session identifier to look up state stored server-side.

Useful cookie attributes:
- `Secure` — send the cookie only over secure connections.
- `HttpOnly` — prevent ordinary JavaScript access to the cookie.
- `SameSite` — restrict when the browser sends the cookie in cross-site contexts.

These attributes reduce risk but do not replace secure application design.

## 5. HTTPS and TLS

**HTTPS** is HTTP carried over **TLS (Transport Layer Security)**. TLS provides:
- **Confidentiality** — encrypts traffic against passive observation.
- **Integrity** — helps detect modification in transit.
- **Authentication** — normally authenticates the server using a certificate.

A browser validates the certificate chain, hostname, validity period, and trust status. A certificate warning should not be ignored.

HTTPS does not prove that a website is honest, malware-free, or safe to use. It protects the connection, not the intentions of the site.

## 6. Ports and HTTP versions

- HTTP commonly uses TCP port **80**.
- HTTPS commonly uses TCP port **443**.
- HTTP/3 uses QUIC over UDP, commonly UDP port **443**.

## 7. HTTP vs HTTPS

| HTTP | HTTPS |
|---|---|
| No TLS protection by itself | Uses TLS |
| Traffic can be read or modified in transit | Traffic is encrypted and integrity-protected |
| Common default port: TCP 80 | Common default port: TCP 443 |
| Does not authenticate the server through TLS certificates | Normally authenticates the server with a certificate |

## 8. Security considerations

Risks include cleartext credentials over HTTP, session theft, cross-site scripting (XSS), cross-site request forgery (CSRF), and insecure cookie handling. Defences include HTTPS everywhere, HSTS, secure cookie attributes, output encoding, CSRF protections, and strong session management.

## 9. Safe practical lab

On Windows PowerShell, inspect response headers:

```powershell
Invoke-WebRequest -Uri https://example.com -Method Head
```

Or use curl:

```powershell
curl.exe -I https://example.com
```

Observe the status code and headers. Do not enter credentials into a test page.

## Key points

- HTTP uses a request-response model and is stateless.
- HTTPS is HTTP protected by TLS.
- A successful HTTPS connection does not guarantee that the website itself is trustworthy.
- Default ports are TCP 80 and TCP 443; HTTP/3 commonly uses UDP 443.

## Related notes
- [[Introduction to Network Protocols]]
- [[TCP Protocol]]
- [[DNS Protocol]]
- [[Common Network Ports]]
- [[Network Security Best Practices]]

## 10. Follow one web request

When you enter `https://example.com/` in a browser, several separate operations occur. The browser resolves the hostname through DNS, establishes a transport connection, negotiates TLS, and then sends an HTTP request. The server responds with a status code, headers, and possibly HTML. The browser may then request CSS, JavaScript, images, and other resources.

This separation matters during troubleshooting. A DNS failure happens before the HTTP request. A TLS certificate error occurs during connection security setup. A `404` response means the server was reached and returned an HTTP-level result, but the requested resource was not found.

## 11. HTTP versions

HTTP/1.1 commonly uses persistent TCP connections. HTTP/2 adds multiplexing and header compression over a connection. HTTP/3 uses QUIC, which runs over UDP and incorporates transport security based on TLS 1.3. The HTTP version does not change the basic request/response concepts, but it changes transport behaviour and performance characteristics.

## 12. Common mistakes

- Treating `401 Unauthorized` and `403 Forbidden` as identical. A 401 generally indicates missing or invalid authentication; a 403 indicates the server refuses the request.
- Assuming every `POST` request is unsafe or every `GET` request is harmless. Method semantics matter, but application design determines actual impact.
- Assuming the padlock means a business is legitimate. It indicates a protected connection to the authenticated domain, not trustworthiness of the content.

## Practical activity — inspect a response

Run `curl.exe -I https://example.com` and record the status line, server response headers, and any redirect information. Compare this with opening the same URL in a browser's Developer Tools → Network panel. Explain which steps happen before the first HTTP response.

## My understanding

Write a short explanation of the difference between DNS resolution, TLS negotiation, and the HTTP request. Include why HTTPS protects traffic but cannot guarantee that a website is safe.
