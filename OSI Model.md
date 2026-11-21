> The OSI (Open Systems Interconnection) Model is a conceptual framework that explains how data travels between devices across a network.

## 1. What Is the OSI Model?

The OSI Model divides network communication into **seven layers**. Each layer has specific responsibilities and works with the layers above and below it.

It helps us understand:

- How data travels across networks.
- How network protocols communicate.
- Where network problems occur.
- How network security controls operate.

**Important:** The OSI Model is a reference model. Real-world networking protocols do not always fit perfectly into its seven layers.

## 2. The Seven Layers

|Layer|Name|Main Function|
|---|---|---|
|7|Application|Provides network services to applications|
|6|Presentation|Handles data representation, encoding, compression and encryption|
|5|Session|Manages communication sessions|
|4|Transport|Provides end-to-end data delivery|
|3|Network|Handles logical addressing and routing|
|2|Data Link|Handles frames and local network delivery|
|1|Physical|Transmits raw bits through physical media|

### Layer 7 — Application

**Purpose:** Provides network services that applications use to communicate.

Examples:

- HTTP — Web communication
- HTTPS — Secure web communication
- DNS — Domain name resolution
- SMTP — Sending email
- SSH — Secure remote access
- FTP — File transfer

**Cybersecurity relevance:**

- SQL Injection
- Cross-Site Scripting (XSS)
- HTTP request analysis
- Application-layer attacks

### Layer 6 — Presentation

**Purpose:** Handles how data is represented and interpreted.

Responsibilities:

- Data encoding and decoding
- Data serialization
- Data compression
- Data encryption and decryption

Examples:

- UTF-8 encoding
- JSON representation
- JPEG compression
- Encryption handled by TLS implementations

**Cybersecurity relevance:**

- Encryption
- Data exposure
- Encoding-related vulnerabilities
- Improper data handling

### Layer 5 — Session

**Purpose:** Manages communication sessions between systems.

Responsibilities:

- Establishing sessions
- Maintaining sessions
- Synchronizing communication
- Terminating sessions

Examples of session-related concepts:

- Authentication sessions
- Session identifiers
- Session management in applications

**Cybersecurity relevance:**

- Session hijacking
- Session fixation
- Weak session management

In modern networking, many session-related functions are implemented within application protocols and libraries rather than as a separate OSI layer.

### Layer 4 — Transport

**Purpose:** Provides communication between processes running on different devices.

Main protocols:

**TCP (Transmission Control Protocol)**

- Connection-oriented
- Reliable data delivery
- Uses acknowledgements and retransmissions
- Maintains data order

**UDP (User Datagram Protocol)**

- Connectionless
- Lower protocol overhead
- Does not guarantee delivery or ordering

Important concepts:

- Port numbers
- Segmentation
- Flow control
- Error recovery
- Multiplexing

Examples:

- TCP port 443 — Commonly used for HTTPS over TCP
- TCP port 22 — SSH
- UDP port 53 — Commonly used for DNS queries

**Cybersecurity relevance:**

- Port scanning
- SYN flood attacks
- Firewall filtering
- Service enumeration

### Layer 3 — Network

**Purpose:** Moves packets between different networks.

Main responsibilities:

- Logical addressing
- Routing
- Packet forwarding
- Path selection

Main protocol:

- IP (IPv4 and IPv6)

Devices:

- Routers
- Layer 3 switches

Important concepts:

- IP addresses
- Routing tables
- Default gateway
- Subnets

**Cybersecurity relevance:**

- IP spoofing
- Routing attacks
- Network reconnaissance
- Packet filtering

### Layer 2 — Data Link

**Purpose:** Transfers data between devices on the same local network link.

Responsibilities:

- Framing
- MAC addressing
- Media access control
- Frame error detection

Technologies:

- Ethernet
- Wi-Fi (IEEE 802.11)

Devices:

- Network switches
- Bridges

Important concepts:

- MAC address
- Ethernet frame
- ARP (used to resolve IPv4 addresses to link-layer addresses on local networks)

**Cybersecurity relevance:**

- ARP spoofing
- MAC spoofing
- VLAN attacks
- MAC flooding

### Layer 1 — Physical

**Purpose:** Transmits raw bits through a physical or wireless medium.

Examples:

- Copper cables
- Fibre-optic cables
- Radio signals
- Connectors
- Electrical and optical signals

Devices:

- Hubs
- Repeaters
- Physical network interfaces

**Cybersecurity relevance:**

- Cable tapping
- Physical device tampering
- Signal interception
- Physical network disruption

## 3. Protocol Data Units (PDUs)

A Protocol Data Unit is the name given to data at a particular layer.

|Layer|PDU|
|---|---|
|Layers 7–5|Data|
|Layer 4|Segment (TCP) / Datagram (UDP)|
|Layer 3|Packet|
|Layer 2|Frame|
|Layer 1|Bits|

Terminology can vary slightly between networking references.

## 4. Addressing at Different Layers

Different layers use different identifiers.

|Layer|Addressing|Example|
|---|---|---|
|Layer 2|MAC address|`00:1A:2B:3C:4D:5E`|
|Layer 3|IP address|`192.168.1.10`|
|Layer 4|Port number|`443`|

**Remember:**

- MAC address identifies a network interface at the local link layer.
- IP address identifies a network interface logically for network communication.
- Port number identifies a communication endpoint or service on a host.

## 5. Encapsulation

Encapsulation happens when data moves down the network layers before transmission.

Each layer adds its own information, such as headers.

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
Network Layer
       |
       v
     Packet
       |
       v
Data Link Layer
       |
       v
     Frame
       |
       v
Physical Layer
       |
       v
      Bits
```

The receiving device performs the reverse process, called **decapsulation**.

You will study these processes separately in:

- [[Network Encapsulation]]
- [[Network Decapsulation]]

## 6. Example: Opening a Website

Suppose you open:

`https://example.com`

A simplified communication process:

1. **Application:** The browser uses HTTP to request a webpage.
2. **Presentation:** Data representation and encryption are handled by relevant software libraries and protocols.
3. **Session:** Communication state is managed through the relevant application and protocol mechanisms.
4. **Transport:** TCP carries the data and provides reliable delivery in the traditional HTTPS-over-TCP model.
5. **Network:** IP addresses help route packets to the destination.
6. **Data Link:** Ethernet or Wi-Fi carries frames across the local network.
7. **Physical:** Signals travel through cables or wireless radio.

The receiving system processes the data in the reverse direction.

**Modern networking note:** HTTP/3 uses QUIC over UDP and incorporates TLS 1.3 security. Therefore, not every HTTPS connection follows the traditional TCP-based example above.

## 7. OSI Model and Cybersecurity

The OSI Model helps security professionals understand where different attacks and controls operate.

|Layer|Example Security Concern|
|---|---|
|Application|SQL Injection, XSS|
|Presentation|Encryption and encoding issues|
|Session|Session hijacking|
|Transport|Port scanning, SYN floods|
|Network|IP spoofing, routing attacks|
|Data Link|ARP spoofing, MAC spoofing|
|Physical|Cable tapping, physical tampering|

These are useful learning associations, not strict boundaries. Some attacks and security controls involve multiple layers.

## 8. Practical Commands

Run these commands on your Windows system.

**1. Display network configuration**

```
ipconfig /all
```

Observe:

- IPv4 address
- Subnet mask
- Default gateway
- Physical address (MAC)

**2. Test network connectivity**

```
ping 8.8.8.8
```

Observe the replies and response times.

**3. Trace the network route**

```
tracert example.com
```

Observe the intermediate network hops.

**4. Display active network connections**

```
netstat -ano
```

Observe:

- Local addresses
- Foreign addresses
- Connection states
- Process IDs

## 9. Key Takeaways

- The OSI Model contains seven layers.
- Each layer has a specific networking responsibility.
- Data is encapsulated before transmission.
- The receiving device decapsulates the data.
- MAC addresses operate at Layer 2.
- IP addresses operate at Layer 3.
- Port numbers operate at Layer 4.
- The OSI Model helps troubleshoot and understand network security.

## 10. My Understanding

Write your own explanation:

- What is the OSI Model?
- Why are network functions divided into layers?
- What is the difference between Layer 2 and Layer 3?
- What happens during encapsulation?
- How does the OSI Model help cybersecurity professionals?

## Related Notes

- [[Introduction to Computer Networking]]
- [[Network Architecture]]
- [[TCP-IP Model]]
- [[OSI vs TCP-IP]]
- [[Network Encapsulation]]
- [[Network Decapsulation]]
- [[Introduction to Network Security]]
- [[Wireshark]]