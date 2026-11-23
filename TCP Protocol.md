## 1. Introduction

TCP stands for **Transmission Control Protocol**.

It is a transport-layer protocol used to provide reliable, ordered communication between applications running on different devices.

TCP ensures that data is delivered in sequence and retransmits lost data when necessary.

It is commonly used by applications that require reliable data transmission.

## 2. Characteristics of TCP

Important characteristics include:

- Connection-oriented communication.
- Reliable data delivery.
- Ordered data transmission.
- Error detection.
- Retransmission of lost data.
- Flow control.
- Congestion control.

TCP uses acknowledgements and sequence numbers to manage data delivery.

## 3. How TCP Works

TCP communication generally involves three stages:

1. Connection establishment.
2. Data transmission.
3. Connection termination.

Before normal data exchange begins, TCP establishes a connection using a process called the **Three-Way Handshake**.

## 4. TCP Three-Way Handshake

The TCP three-way handshake establishes a connection between a client and a server.

It uses three messages:

### Step 1: SYN

The client sends a SYN segment to request a connection.

```
Client → Server: SYN
```

### Step 2: SYN-ACK

The server acknowledges the request and sends its own SYN.

```
Server → Client: SYN-ACK
```

### Step 3: ACK

The client acknowledges the server's response.

```
Client → Server: ACK
```

The connection is now established.

### Handshake Diagram

```
Client                         Server
  |                               |
  | -------- SYN ---------------> |
  |                               |
  | <------ SYN-ACK ------------- |
  |                               |
  | -------- ACK ---------------> |
  |                               |
  |       Connection Established  |
```

## 5. TCP Data Transmission

After establishing a connection, TCP transmits application data using TCP segments.

TCP uses:

- Sequence numbers to track data order.
- Acknowledgements to confirm received data.
- Retransmissions to recover from detected loss.
- Checksums to detect corruption.

TCP provides a reliable byte stream. It does not preserve application message boundaries.

## 6. TCP Connection Termination

TCP normally terminates a connection through a process involving FIN and ACK segments.

A simplified example:

```
Client                         Server
  |                               |
  | -------- FIN ---------------> |
  | <-------- ACK --------------- |
  | <-------- FIN --------------- |
  | -------- ACK ---------------> |
  |                               |
  |       Connection Closed       |
```

This is commonly called the four-segment TCP termination process.

The exact sequence can vary depending on which side closes first and how the connection is handled.

## 7. Important TCP Flags

TCP uses control flags to manage connections.

|Flag|Meaning|
|---|---|
|SYN|Synchronizes sequence numbers and initiates a connection|
|ACK|Acknowledges received data or control information|
|FIN|Indicates that a side wants to close its sending direction|
|RST|Resets a connection|
|PSH|Requests prompt delivery of buffered data to the receiving application|
|URG|Indicates urgent data is present|

## 8. TCP Header

A TCP header contains information required for communication.

Important fields include:

- Source Port
- Destination Port
- Sequence Number
- Acknowledgement Number
- Header Length
- Control Flags
- Window Size
- Checksum
- Urgent Pointer
- Options

The minimum TCP header size is 20 bytes without options.

## 9. TCP vs UDP

|TCP|UDP|
|---|---|
|Connection-oriented|Connectionless|
|Reliable delivery|No delivery guarantee|
|Ordered byte stream|Datagram-based|
|Acknowledgements and retransmissions|No built-in acknowledgement or retransmission|
|Flow and congestion control|No built-in transport-level flow or congestion control|
|More overhead|Lower overhead|

TCP is commonly used when reliable, ordered delivery is important.

## 10. Common TCP Services

Examples of applications and services that commonly use TCP include:

|Service|Common TCP Port|
|---|---|
|HTTP|80|
|HTTPS over HTTP/1.1 or HTTP/2|443|
|SSH|22|
|FTP Control|21|
|SMTP|25|
|SMB|445|
|RDP|3389|

Port numbers are conventions, not guarantees. Services can be configured to use other ports.

Note: HTTP/3 uses QUIC over UDP, not TCP.

## 11. TCP in Cybersecurity

TCP knowledge is important for network analysis and security testing.

Security professionals use TCP to:

- Identify open TCP ports.
- Analyze connection establishment.
- Investigate suspicious connections.
- Understand SYN scans.
- Detect unusual connection patterns.
- Troubleshoot network communication.

### TCP SYN Scan

A SYN scan is a common Nmap scanning technique.

Example, against a system you own or are authorized to test:

```
nmap -sS 192.168.1.10
```

It sends TCP SYN probes to identify port states without completing a normal TCP connection in the usual open-port case.

## 12. Practical Lab — Windows PowerShell

### Step 1: View TCP connections

```
Get-NetTCPConnection
```

### Step 2: View established connections

```
Get-NetTCPConnection -State Established
```

### Step 3: View listening TCP ports

```
Get-NetTCPConnection -State Listen
```

### Step 4: Identify a process using a TCP port

```
Get-NetTCPConnection -State Listen |
Select-Object LocalAddress, LocalPort, OwningProcess
```

Use the process ID to identify the application:

```
Get-Process -Id YOUR_PID
```

Replace `YOUR_PID` with the actual process ID.

## 13. My Understanding

Write your own explanation:

- What is TCP?
- Why is TCP called connection-oriented?
- What happens during the three-way handshake?
- What is the purpose of SYN, ACK, and FIN?
- How does TCP recover from data loss?
- What is the difference between TCP and UDP?
- Why is TCP important in cybersecurity?

## 14. Related Notes

- [[Introduction to Network Protocols]]
- [[TCP-IP Model]]
- [[OSI Model]]
- [[UDP Protocol]]
- [[Common Network Ports]]
- [[Nmap]]
- [[Wireshark]]
- [[Network Analysis and Tools]]

---

**Key Takeaway:** TCP provides reliable, ordered, connection-oriented data transmission using acknowledgements, sequence numbers, and retransmissions.