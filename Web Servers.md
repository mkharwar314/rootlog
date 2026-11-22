# Web Servers

> Understand how web-server software receives HTTP requests and serves web content.

## 1. What is a web server?

A web server can refer to the software that handles HTTP requests or the computer/system running that software. It may serve static files, route requests to application code, or act as a reverse proxy.

Examples of web-server software include Apache HTTP Server, Nginx, and Microsoft IIS.

## 2. Request handling

A simplified request path:
1. DNS resolves the hostname.
2. The client establishes a connection.
3. TLS is negotiated for HTTPS.
4. The server receives the HTTP request.
5. The server serves a static resource or passes the request to application logic.
6. The server returns an HTTP response.

## 3. Reverse proxy

A reverse proxy accepts client requests and forwards them to one or more backend servers. It can provide TLS termination, load balancing, caching, and centralized access controls.

## 4. Security risks

Common risks include outdated software, exposed administrative interfaces, directory listing, insecure TLS configuration, weak permissions, path traversal, request smuggling, and application vulnerabilities.

## 5. Hardening practices

- Keep server and runtime software updated.
- Remove unused modules and default content.
- Use least-privilege service accounts.
- Restrict administrative interfaces.
- Configure TLS securely.
- Set appropriate security headers.
- Log and monitor requests.
- Back up configuration and content.

## 6. Safe inspection

For a site you are permitted to inspect:

```bash
curl -I https://example.com
```

Review response headers and server behaviour without attempting exploitation.

## Key points

- Web servers process HTTP requests and return responses.
- Reverse proxies sit in front of backend services.
- Server hardening includes patching, least privilege, TLS, and monitoring.

## Related notes
- [[HTTP and HTTPS]]
- [[Proxy Servers]]
- [[Network Security Best Practices]]
