> The TCP/IP Model explains how devices communicate over networks using the protocols that power the Internet.

## 1. What Is the TCP/IP Model?

TCP/IP stands for **Transmission Control Protocol / Internet Protocol**.

It is a networking model that describes how data is transmitted between devices across interconnected networks.

Unlike the OSI Model, which is primarily a conceptual reference model, TCP/IP is closely associated with the actual protocols used for Internet communication.

It is commonly represented using four layers.

## 2. The Four Layers

|Layer|Main Responsibility|Examples|
|---|---|---|
|4. Application|Network services and application communication|HTTP, DNS, SSH, SMTP|
|3. Transport|Process-to-process communication|TCP, UDP|
|2. Internet|Logical addressing and routing|IP, ICMP|
|1. Network Access|Local network delivery and physical transmission|Ethernet, Wi-Fi|

### Layer 4 — Application

**Purpose:** Provides protocols and services used by network applications.

Examples:

- HTTP — Web communication
- HTTPS — Secure web communication
- DNS — Domain name resolution
- SSH — Secure remote access
- SMTP — Sending emails
- DHCP — Automatic IP configuration

This layer combines responsibilities that the OSI Model separates into Application, Presentation, and Session layers.

**Cybersecurity relevance:**

- SQL Injection
- Cross-Site Scripting
- DNS attacks
- HTTP request analysis
- Application security testing

### Layer 3 — Transport

**Purpose:** Provides communication between applications running on different devices.

Main protocols:

**TCP**

- Connection-oriented
- Reliable delivery
- Uses acknowledgements
- Maintains data order

**UDP**

- Connectionless
- Lower protocol overhead
- Does not guarantee delivery or ordering

Important concepts:

- Port numbers
- Segmentation
- Flow control
- Error recovery

**Cybersecurity relevance:**

- Port scanning
- SYN flood attacks
- Firewall rules
- Service enumeration

### Layer 2 — Internet

**Purpose:** Handles logical addressing and packet routing between networks.

Main protocols:

- IPv4
- IPv6
- ICMP

Important concepts:

- IP addresses
- Routing
- Packet forwarding
- Subnetting
- Default gateway

Devices:

- Routers
- Layer 3 switches

**Cybersecurity relevance:**

- IP spoofing
- Network reconnaissance
- Routing attacks
- Packet filtering

### Layer 1 — Network Access

**Purpose:** Handles communication over the local network link and transmission over the physical medium.

Technologies:

- Ethernet
- Wi-Fi

Important concepts:

- MAC addresses
- Frames
- Physical transmission
- Network interfaces

Devices:

- Switches
- Network interface cards
- Wireless access points

**Cybersecurity relevance:**

- ARP spoofing
- MAC spoofing
- Wireless attacks
- Physical network tampering

## 3. Data Units in TCP/IP

|TCP/IP Layer|Common Data Unit|
|---|---|
|Application|Data|
|Transport|TCP Segment / UDP Datagram|
|Internet|Packet|
|Network Access|Frame / Bits|

The exact terminology depends on the protocol and the layer being discussed.

## 4. Encapsulation in TCP/IP

When data travels from an application to the network, each layer adds the information needed for transmission.

```
Application Layer
        |
        v
       Data
        |
        v
Transport Layer
        |
        v
 Segment / Datagram
        |
        v
 Internet Layer
        |
        v
      Packet
        |
        v
 Network Access
        |
        v
      Frame
        |
        v
 Physical Transmission
```

At the receiving device, the process is reversed. This is called decapsulation.

## 5. Example: Accessing a Website

Suppose you open:

`https://example.com`

A simplified communication process:

1. **Application:** The browser uses HTTP to request the webpage.
2. **Transport:** TCP carries the data in a traditional HTTPS-over-TCP connection.
3. **Internet:** IP handles addressing and routing.
4. **Network Access:** Ethernet or Wi-Fi carries frames across the local network.

The receiving device processes the data in reverse order.

**Modern networking note:** HTTP/3 uses QUIC over UDP and incorporates TLS 1.3 security. Not every HTTPS connection uses TCP.

## 6. TCP/IP Model and Cybersecurity

The TCP/IP Model helps security professionals understand real network traffic.

|Layer|Security Examples|
|---|---|
|Application|SQL Injection, XSS, DNS attacks|
|Transport|Port scanning, SYN floods|
|Internet|IP spoofing, routing attacks|
|Network Access|ARP spoofing, wireless attacks|

These are practical associations, not strict boundaries. Many attacks involve multiple layers.

## 7. Practical Commands

Run these commands in Windows PowerShell.

**1. Display IP configuration**

```
ipconfig /all
```

**2. Test connectivity**

```
ping 8.8.8.8
```

**3. Resolve a domain name**

```
nslookup example.com
```

**4. Display the route to a destination**

```
tracert example.com
```

**5. Display active connections**

```
netstat -ano
```

Observe the network information returned by each command.

## 8. Key Takeaways

- TCP/IP is the foundation of Internet communication.
- It is commonly represented using four layers.
- TCP and UDP operate at the Transport layer.
- IP operates at the Internet layer.
- Ethernet and Wi-Fi are common Network Access technologies.
- Encapsulation prepares data for transmission.
- TCP/IP helps us understand real network traffic and troubleshoot communication.

## 9. My Understanding

Write your own explanation:

- What does TCP/IP stand for?
- What are the four TCP/IP layers?
- What is the difference between TCP and UDP?
- What is the role of IP?
- Why is TCP/IP important for cybersecurity?

## Related Notes

- [[OSI Model]]
- [[OSI vs TCP-IP]]
- [[TCP Protocol]]
- [[UDP Protocol]]
- [[IPv4 Addressing]]
- [[Introduction to Network Protocols]]
- [[Network Encapsulation]]
- [[Network Decapsulation]]

---