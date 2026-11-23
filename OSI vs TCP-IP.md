> The OSI and TCP/IP models explain network communication using layers, but they differ in structure, purpose, and practical implementation.

## 1. Introduction

Both models help us understand how data travels between devices over a network.

**OSI Model**

- Developed by the International Organization for Standardization (ISO).
- Contains seven layers.
- Primarily serves as a conceptual reference model.
- Helps understand network functions and troubleshoot problems.

**TCP/IP Model**

- Developed through research supported by the US Department of Defense.
- Commonly represented using four layers.
- Closely associated with real-world Internet protocols.
- Explains how Internet communication works.

## 2. Layer Comparison

|OSI Model|TCP/IP Model|
|---|---|
|7. Application|4. Application|
|6. Presentation|4. Application|
|5. Session|4. Application|
|4. Transport|3. Transport|
|3. Network|2. Internet|
|2. Data Link|1. Network Access|
|1. Physical|1. Network Access|

**Important:** The mapping is approximate. The TCP/IP Network Access layer covers functions associated with both the OSI Data Link and Physical layers.

## 3. Main Differences

|Feature|OSI Model|TCP/IP Model|
|---|---|---|
|Number of layers|7|4 commonly represented|
|Developer|ISO|DARPA research community|
|Main purpose|Reference framework|Practical networking architecture|
|Layer separation|More detailed|More broadly grouped|
|Protocol dependency|Protocol-independent reference model|Built around Internet protocols|
|Usage|Learning, design, troubleshooting|Real-world Internet communication|

## 4. Understanding Layer Mapping

### OSI Layers 7, 6 and 5 → TCP/IP Application

The OSI model separates:

- Application services
- Data representation
- Session management

TCP/IP groups these responsibilities into its Application layer.

Examples:

- HTTP
- DNS
- SMTP
- SSH

### OSI Layer 4 → TCP/IP Transport

Both models describe process-to-process communication.

Main protocols:

- TCP
- UDP

Important concepts:

- Port numbers
- Segmentation
- Reliable delivery
- Flow control

### OSI Layer 3 → TCP/IP Internet

Both models handle logical addressing and routing.

Main protocols:

- IPv4
- IPv6
- ICMP

### OSI Layers 2 and 1 → TCP/IP Network Access

Both models account for local network communication and physical transmission.

Examples:

- Ethernet
- Wi-Fi
- MAC addressing
- Frames
- Physical signals

## 5. Diagram: Layer Mapping

```
          OSI MODEL                 TCP/IP MODEL

     7. Application
             |
     8. Presentation  -------->   4. Application
             |
     9. Session
             |
     10. Transport    -------->   3. Transport
             |
     11. Network      -------->   2. Internet
             |
     12. Data Link
             |              \
     13. Physical      -------->   1. Network Access
```

## 6. Practical Example

Suppose you open a website using HTTPS.

The communication can be understood through both models.

**Using the OSI Model:**

1. Application — HTTP request.
2. Presentation — Data representation and encryption functions.
3. Session — Session-related communication management.
4. Transport — TCP carries data in a traditional HTTPS-over-TCP connection.
5. Network — IP routing.
6. Data Link — Ethernet or Wi-Fi framing.
7. Physical — Signals travel through the transmission medium.

**Using the TCP/IP Model:**

1. Application — HTTP and related application protocols.
2. Transport — TCP.
3. Internet — IP.
4. Network Access — Ethernet or Wi-Fi.

Modern HTTP/3 uses QUIC over UDP rather than the traditional TCP-based transport arrangement.

## 7. Importance in Cybersecurity

Both models are useful when analyzing network security.

|Security Activity|Useful Model Concepts|
|---|---|
|Web application testing|Application|
|Port scanning|Transport|
|IP reconnaissance|Internet / Network|
|Packet analysis|Multiple layers|
|ARP spoofing analysis|Data Link / Network Access|
|Network troubleshooting|Both models|

Security professionals should understand both models because network attacks and defenses can involve multiple layers.

## 8. Key Takeaways

- OSI has seven layers.
- TCP/IP is commonly represented with four layers.
- OSI is a detailed reference model.
- TCP/IP describes the architecture behind Internet communication.
- OSI Application, Presentation and Session map approximately to TCP/IP Application.
- OSI Transport maps to TCP/IP Transport.
- OSI Network maps to TCP/IP Internet.
- OSI Data Link and Physical map approximately to TCP/IP Network Access.

## 9. My Understanding

Write your own explanation:

- What is the main difference between OSI and TCP/IP?
- Why does OSI have seven layers while TCP/IP has four?
- Which TCP/IP layer corresponds to the OSI Network layer?
- Why is TCP/IP important in real-world networking?
- Which model would you use to explain network communication, and why?

## Related Notes

- [[OSI Model]]
- [[TCP-IP Model]]
- [[Network Encapsulation]]
- [[Network Decapsulation]]
- [[Introduction to Network Protocols]]
- [[Introduction to Network Security]]

---