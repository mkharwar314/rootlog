## 1. Introduction

A network protocol is a set of rules that defines how devices communicate and exchange data over a network.

Protocols establish how information is:

- Formatted
- Transmitted
- Received
- Addressed
- Interpreted
- Protected

Without protocols, devices from different manufacturers and operating systems would struggle to communicate reliably.

## 2. Why Are Network Protocols Important?

Network protocols make communication possible between different devices and systems.

Their importance includes:

1. **Standardization:** Define common communication rules.
2. **Reliability:** Support accurate data delivery.
3. **Security:** Provide mechanisms for encryption and authentication.
4. **Interoperability:** Allow different systems to communicate.
5. **Network Management:** Support monitoring and troubleshooting.

## 3. How Network Protocols Work

Consider opening a website in a browser.

Several protocols may work together:

1. DNS resolves the domain name to an IP address.
2. TCP establishes a connection when the application uses TCP.
3. TLS provides encryption for HTTPS.
4. HTTP handles the request and response.
5. IP provides logical addressing and routing.
6. Ethernet or Wi-Fi carries frames across the local network.

These protocols work together in layers.

Note: Modern HTTP/3 uses QUIC over UDP rather than TCP.

## 4. Types of Network Protocols

### A. Communication Protocols

Used to exchange information between devices.

Examples:

- TCP
- UDP
- HTTP
- HTTPS

### B. Addressing and Network Protocols

Used for addressing, routing, and network communication.

Examples:

- IP
- ARP
- ICMP

### C. Network Service Protocols

Provide services such as name resolution and automatic network configuration.

Examples:

- DNS
- DHCP
- NTP

### D. File Transfer and Remote Access Protocols

Used to transfer files and access remote systems.

Examples:

- FTP
- SFTP
- SSH

### E. Email Protocols

Used for sending and retrieving email.

Examples:

- SM
- IMAP
- POP3

## 5. Common Network Protocols

|Protocol|Purpose|
|---|---|
|TCP|Reliable, connection-oriented transport|
|UDP|Connectionless transport|
|IP|Logical addressing and routing|
|HTTP|Web communication|
|HTTPS|HTTP protected by TLS|
|DNS|Domain name resolution|
|DHCP|Automatic IP configuration|
|FTP|File transfer|
|SFTP|Secure file transfer over SSH|
|SSH|Secure remote access|
|SMTP|Sending email|
|IMAP|Accessing and synchronizing email|
|ICMP|Network diagnostics and error reporting|
|ARP|IPv4-to-MAC address resolution on local links|
|NTP|Time synchronization|

## 6. What Is a Port Number?

A port number identifies a communication endpoint associated with an application or service.

Transport protocols such as TCP and UDP use port numbers.

Examples:

|Port|Common Service|
|---|---|
|20/21|FTP|
|22|SSH|
|25|SMTP|
|53|DNS|
|67/68|DHCP|
|80|HTTP|
|110|POP3|
|123|NTP|
|143|IMAP|
|443|HTTPS|
|445|SMB|
|3389|RDP|

A port number alone does not prove which application is running. Services can use non-standard ports.

## 7. TCP vs UDP

TCP and UDP are transport-layer protocols.

|TCP|UDP|
|---|---|
|Connection-oriented|Connectionless|
|Provides reliable, ordered delivery|Does not guarantee delivery or ordering|
|Uses acknowledgements and retransmissions|No built-in retransmission mechanism|
|Has more transport overhead|Usually has lower transport overhead|
|Commonly used by HTTPS over HTTP/1.1 and HTTP/2|Used by DNS, DHCP, and real-time applications|

The appropriate protocol depends on the application's requirements.

## 8. Network Protocols and Cybersecurity

Understanding protocols is essential in cybersecurity.

Security professionals use protocol knowledge to:

- Identify exposed network services.
- Analyze network traffic.
- Investigate suspicious connections.
- Configure firewalls.
- Detect insecure communication.
- Perform authorized network assessments.

For example, an exposed service running on TCP port 22 may indicate SSH access.

However, a port number alone cannot establish whether a service is vulnerable.

## 9. Practical Lab — Windows PowerShell

### Step 1: View network connections

```
netstat -ano
```

Observe:

- Local Address
- Foreign Address
- State
- PID

### Step 2: View listening TCP ports

```
Get-NetTCPConnection -State Listen
```

### Step 3: View listening UDP endpoints

```
Get-NetUDPEndpoint
```

### Step 4: Identify a process by PID

```
Get-Process -Id YOUR_PID
```

Replace `YOUR_PID` with an actual PID from your output.

## 10. My Understanding

Write your own explanation:

- What is a network protocol?
- Why are protocols necessary?
- What is a port number?
- What is the difference between TCP and UDP?
- How do multiple protocols work together when opening a website?
- Why is protocol knowledge important in cybersecurity?

## 11. Related Notes

- [[OSI Model]]
- [[TCP-IP Model]]
- [[TCP Protocol]]
- [[UDP Protocol]]
- [[HTTP and HTTPS]]
- [[DNS Protocol]]
- [[DHCP Protocol]]
- [[Common Network Ports]]
- [[Network Analysis and Tools]]

---

**Key Takeaway:** Network protocols define the rules that allow devices and applications to communicate reliably and securely.