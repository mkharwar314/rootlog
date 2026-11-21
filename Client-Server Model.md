> Understand how clients request services and how servers process and provide those services over a network.

## 1. What Is the Client-Server Model?

The client-server model is a network communication architecture in which one device or application (the client) requests a service, and another device or application (the server) provides it.

**Example:**

When you open a website:

- Your web browser acts as the client.
- The website's web server provides the requested content.
- The client and server communicate using network protocols.

## 2. Main Components

### Client

A client is a device or application that requests a service.

Examples:

- Web browser.
- Email application.
- Mobile application.
- Desktop application.

### Server

A server is a system or application that provides services or resources to clients.

Examples:

- Web server.
- Database server.
- File server.
- Email server.
- Authentication server.

### Network

The network provides the communication path between clients and servers.

It may use:

- Ethernet.
- Wi-Fi.
- The Internet.
- Private organizational networks.

## 3. How Client-Server Communication Works

Consider opening a website.

```
       CLIENT                         SERVER
   +-------------+               +-------------+
   | Web Browser |               | Web Server  |
   +-------------+               +-------------+
          |                              |
          |------ Request -------------->|
          |                              |
          |                     Process Request
          |                              |
          |<----- Response --------------|
          |                              |
   Display Webpage                       |
```

### Communication steps

1. The user enters a website address.
2. The browser obtains the server's IP address through DNS if needed.
3. The client establishes the required network communication.
4. The browser sends an HTTP or HTTPS request.
5. The server processes the request.
6. The server returns a response.
7. The browser displays the received content.

This is a simplified example. Real applications may involve proxies, load balancers, CDNs, application servers, and databases.

## 4. Types of Servers

|Server Type|Function|
|---|---|
|Web Server|Delivers web content and handles HTTP requests.|
|File Server|Stores and shares files.|
|Database Server|Stores and manages database information.|
|Mail Server|Handles email delivery and storage.|
|DNS Server|Resolves domain names.|
|DHCP Server|Assigns IP configuration to clients.|
|Authentication Server|Verifies user identities.|
|Proxy Server|Acts as an intermediary for network requests.|

## 5. Advantages of Client-Server Architecture

- Centralized data management.
- Easier administration.
- Centralized authentication and authorization.
- Resources can be shared between multiple clients.
- Security policies can be managed centrally.
- Suitable for large organizations.

## 6. Disadvantages

- Server failure can interrupt services.
- Requires maintenance and administration.
- Infrastructure can be expensive.
- A server can become a performance bottleneck.
- Centralized servers can become attractive attack targets.

Organizations use backups, redundancy, monitoring, and load balancing to reduce these risks.

## 7. Client-Server Model vs Peer-to-Peer Model

|Feature|Client-Server|Peer-to-Peer|
|---|---|---|
|Architecture|Centralized service providers|Distributed participation|
|Server|Dedicated server commonly used|No dedicated server required for every interaction|
|Management|Centralized|More distributed|
|Security|Policies can be centrally managed|Security management can be more difficult|
|Scalability|Can scale with suitable infrastructure|Depends on peer participation and design|
|Example|Website hosting|Direct file sharing|

## 8. Common Communication Protocols

Client-server applications use protocols to communicate.

|Protocol|Purpose|
|---|---|
|HTTP|Transfers web resources.|
|HTTPS|Secure HTTP communication using TLS.|
|DNS|Resolves domain names.|
|SSH|Secure remote administration.|
|FTP|File transfer.|
|SFTP|Secure file transfer over SSH.|
|SMTP|Sends email.|
|TCP|Reliable, connection-oriented transport.|
|UDP|Connectionless transport.|

Related notes:

- [[Network Protocols]]
- [[TCP Protocol]]
- [[UDP Protocol]]
- [[HTTP and HTTPS]]

## 9. Client-Server Security

Client-server systems face several security risks.

### Common risks

- Unauthorized access.
- Weak authentication.
- SQL injection.
- Cross-site scripting.
- Denial-of-service attacks.
- Insecure communication.
- Server misconfiguration.

### Security controls

- Strong authentication.
- Access control.
- HTTPS and TLS.
- Input validation.
- Secure server configuration.
- Regular patching.
- Network firewalls.
- Logging and monitoring.

## 10. Practical Observation

### Lab 1 — Identify Your Client

Your browser or application acts as a client when requesting a network service.

### Lab 2 — Inspect Network Connections on Windows

Open PowerShell:

```
Get-NetTCPConnection
```

Display connection details:

```
Get-NetTCPConnection |
Select-Object LocalAddress, LocalPort, RemoteAddress, RemotePort, State
```

### Lab 3 — Inspect Network Connections on Linux

```
ss -tunap
```

This displays TCP and UDP sockets, including process information where permissions allow.

### Lab 4 — Test a Web Server

```
curl -I https://example.com
```

Observe the HTTP response headers returned by the server.

This demonstrates a client sending a request and receiving a server response.

## 11. What I Learned

Write your own explanations:

- What is a client?
- What is a server?
- How does a browser communicate with a web server?
- What is the difference between a request and a response?
- Why is centralized authentication useful?
- What security risks affect client-server systems?

## 12. Questions & Doubts

- Can one computer act as both client and server?
- Can a server communicate with another server?
- What happens when a server becomes unavailable?
- How does HTTPS protect client-server communication?
- Why do websites use load balancers?

## Related Notes

- [[Introduction to Computer Networking]]
- [[Network Architecture]]
- [[Peer-to-Peer Model]]
- [[Network Protocols]]
- [[HTTP and HTTPS]]
- [[DNS Protocol]]
- [[TCP Protocol]]
- [[Network Security]]
- [[03 - Networking]]

---