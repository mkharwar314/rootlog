## 1. Introduction

UDP stands for **User Datagram Protocol**.

It is a transport-layer protocol used to send data between applications over an IP network.

Unlike TCP, UDP does not establish a connection before sending data and does not guarantee delivery or ordering.

UDP is useful for applications where low latency and reduced protocol overhead are important.

## 2. Characteristics of UDP

Important characteristics include:

- Connectionless communication.
- No connection handshake.
- No built-in delivery guarantee.
- No built-in retransmission.
- No built-in ordering guarantee.
- Low protocol overhead.
- Supports broadcast and multicast communication where the underlying network supports them.

UDP sends data in independent units called **datagrams**.

## 3. How UDP Works

Consider a client sending a DNS query to a DNS server.

1. The client creates a UDP datagram.
2. It specifies the source and destination ports.
3. The datagram is passed to IP for delivery.
4. The destination application receives the datagram if it arrives and is accepted by the system.

UDP does not wait for an acknowledgement or automatically retransmit a lost datagram.

If reliability is required, the application must implement suitable mechanisms itself.

## 4. UDP Communication Diagram

```
Client                         Server
  |                               |
  | -------- UDP Datagram ------> |
  |                               |
  |       Application processes   |
  |             data              |
  |                               |
```

There is no TCP-style three-way handshake.

## 5. UDP Header

The UDP header is only 8 bytes long.

It contains four fields:

|Field|Purpose|
|---|---|
|Source Port|Identifies the sending application endpoint|
|Destination Port|Identifies the receiving application endpoint|
|Length|Specifies the length of the UDP header and data|
|Checksum|Helps detect transmission errors|

UDP has a smaller header than TCP, which contributes to its low overhead.

## 6. UDP vs TCP

|TCP|UDP|
|---|---|
|Connection-oriented|Connectionless|
|Reliable byte stream|Datagram-based|
|Ordered delivery|No built-in ordering|
|Retransmission mechanisms|No built-in retransmission|
|Connection establishment|No connection handshake|
|Minimum header: 20 bytes|Header: 8 bytes|
|Flow and congestion control|No built-in transport-level flow or congestion control|

Neither protocol is universally better. The application determines which is appropriate.

## 7. Common UDP Services

|Service|Common UDP Port|
|---|---|
|DNS|53|
|DHCP Server|67|
|DHCP Client|68|
|TFTP|69|
|NTP|123|
|SNMP|161|
|Syslog|514|

Some services can use both TCP and UDP depending on the application and situation.

For example, DNS commonly uses UDP for ordinary queries but can also use TCP.

## 8. Real-World Uses of UDP

UDP is commonly used in applications such as:

### DNS

DNS commonly uses UDP for standard queries because of its low overhead.

### Voice and Video Communication

Real-time communication applications may use UDP because waiting for retransmissions can increase latency.

### Online Gaming

Games may use UDP for time-sensitive updates where receiving the latest information is more important than retransmitting every older update.

### Streaming and Real-Time Applications

UDP can support real-time media delivery, often with additional protocols and application-level mechanisms.

### QUIC and HTTP/3

QUIC operates over UDP and provides features such as reliable streams, encryption, and congestion control.

HTTP/3 uses QUIC rather than TCP.

## 9. UDP in Cybersecurity

UDP knowledge is important when analyzing network traffic.

Security professionals use UDP analysis to:

- Identify exposed UDP services.
- Investigate suspicious DNS traffic.
- Detect unusual UDP traffic patterns.
- Analyze network scans.
- Investigate potential UDP flooding attacks.

### UDP Flood

A UDP flood is a denial-of-service attack that sends large volumes of UDP packets toward a target.

It may consume network bandwidth or system resources.

### Protection Measures

- Apply firewall rules.
- Monitor unusual traffic volumes.
- Restrict unnecessary UDP services.
- Use rate limiting where appropriate.
- Monitor exposed network services.

## 10. Practical Lab — Windows PowerShell

### Step 1: View UDP endpoints

```
Get-NetUDPEndpoint
```

### Step 2: Display UDP endpoint details

```
Get-NetUDPEndpoint |
Select-Object LocalAddress, LocalPort, OwningProcess
```

### Step 3: Identify the process

```
Get-Process -Id YOUR_PID
```

Replace `YOUR_PID` with an actual process ID.

### Step 4: View network statistics

```
netstat -s -p udp
```

This displays UDP-related network statistics.

## 11. Practical Observation

Record two UDP endpoints from your system.

|Property|Endpoint 1|Endpoint 2|
|---|---|---|
|Local Address|||
|Local Port|||
|Process ID|||
|Process Name|||

Not every UDP endpoint represents a publicly reachable service. Interpret addresses and network exposure carefully.

## 12. My Understanding

Write your own explanation:

- What is UDP?
- Why is UDP called connectionless?
- What is a UDP datagram?
- How large is the UDP header?
- What is the difference between TCP and UDP?
- Why do real-time applications often use UDP?
- Does UDP always mean faster application performance?

## 13. Related Notes

- [[Introduction to Network Protocols]]
- [[TCP Protocol]]
- [[TCP-IP Model]]
- [[OSI Model]]
- [[DNS Protocol]]
- [[DHCP Protocol]]
- [[Common Network Ports]]
- [[Wireshark]]
- [[Network Analysis and Tools]]

---

**Key Takeaway:** UDP provides connectionless datagram communication with low overhead, but applications must handle reliability when they need it.