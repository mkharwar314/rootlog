> Network decapsulation is the process of removing and processing protocol-related information from received data as it moves up the network layers.

## 1. What Is Decapsulation?

When a device receives network data, it must process the information added by the sender.

Each networking layer examines its corresponding protocol information and passes the remaining payload to the next layer.

This process is called **decapsulation**.

Encapsulation prepares data for transmission.

Decapsulation processes received data.

## 2. Decapsulation Process

```
        BITS
          |
          v
  Physical Reception
          |
          v
   NETWORK FRAME
          |
          v
 Network Access Layer
          |
          v
      IP PACKET
          |
          v
    Internet Layer
          |
          v
 TCP SEGMENT / UDP DATAGRAM
          |
          v
   Transport Layer
          |
          v
        DATA
          |
          v
   Application Layer
          |
          v
 Application Processes Data
```

The receiving device processes the data from the lower networking layers toward the upper layers.

## 3. What Happens at Each Layer?

### Layer 1 — Physical

The network interface receives signals through the physical or wireless medium.

These signals are interpreted as bits.

### Layer 2 — Network Access

The receiving network interface processes the link-layer frame.

For Ethernet, it can examine:

- Destination MAC address
- Source MAC address
- EtherType
- Frame Check Sequence (FCS)

The frame's payload is passed to the appropriate network-layer protocol.

### Layer 3 — Internet

The Internet layer processes the IP packet.

It examines information such as:

- Source IP address
- Destination IP address
- Protocol field
- Time To Live (TTL)

The protocol field identifies the next protocol, such as TCP, UDP, or ICMP.

### Layer 4 — Transport

The Transport layer processes the TCP segment or UDP datagram.

For TCP, it handles:

- Source port
- Destination port
- Sequence numbers
- Acknowledgments
- Data ordering and reliability

For UDP, it handles:

- Source port
- Destination port
- Length
- Checksum

The data is delivered to the appropriate application endpoint.

### Layer 5 — Application

The application receives and processes the data according to the relevant application protocol.

Examples:

- A browser processes HTTP responses.
- A DNS resolver processes DNS responses.
- An email client processes email-related data.

## 4. Example: Receiving a Website Response

Suppose your browser requests:

`https://example.com`

The web server sends a response to your device.

A simplified HTTPS-over-TCP reception process:

1. **Physical:** Your network interface receives transmitted signals.
2. **Network Access:** The link-layer frame is processed.
3. **Internet:** The IP packet is examined and processed.
4. **Transport:** TCP processes the segment and delivers the data to the appropriate connection.
5. **Application:** The browser processes the HTTP response.

The browser can then display the webpage.

**Important:** In modern HTTP/3 communication, QUIC over UDP handles transport-related functions instead of traditional TCP.

## 5. Encapsulation vs Decapsulation

|Feature|Encapsulation|Decapsulation|
|---|---|---|
|Direction|Upper layers to lower layers|Lower layers to upper layers|
|Purpose|Prepare data for transmission|Process received data|
|Headers|Added by protocols|Examined and processed|
|Sender/receiver|Usually performed by sender|Usually performed by receiver|
|Result|Data becomes ready for transmission|Data reaches the intended application|

## 6. Why Is Decapsulation Important?

Decapsulation allows receiving devices to:

- Identify the destination application.
- Process network protocol information.
- Validate received frames and packets.
- Deliver data to the correct protocol.
- Reconstruct the information needed by applications.

## 7. Decapsulation and Cybersecurity

Understanding decapsulation helps security professionals analyze incoming network traffic.

It is useful for:

- Inspecting packet headers.
- Identifying suspicious source addresses.
- Investigating unusual ports.
- Analyzing malformed packets.
- Understanding network-layer attacks.
- Troubleshooting communication failures.

Examples:

- Packet sniffing
- IP spoofing analysis
- TCP connection analysis
- Malformed packet investigation

## 8. Practical Lab — Inspect Received Packets

**Objective:** Observe how received network traffic is represented in Wireshark.

### Step 1 — Open Wireshark

Open Wireshark and select your active network interface.

Start capturing.

### Step 2 — Generate network traffic

Open PowerShell and run:

```
ping 8.8.8.8
```

### Step 3 — Stop the capture

Return to Wireshark and stop capturing.

### Step 4 — Select a received packet

Find an ICMP Echo Reply packet, if one was received.

Expand its protocol sections.

You should see information such as:

- Ethernet II
- Internet Protocol Version 4
- Internet Control Message Protocol

### Step 5 — Observe the protocol information

Identify:

- Source MAC address
- Destination MAC address
- Source IP address
- Destination IP address
- ICMP message type

### Step 6 — Record your findings

Write down what information each protocol section provides.

**Note:** Wireshark displays decoded protocol information. It does not show the exact internal processing steps performed by the network interface and operating system.

## 9. Key Takeaways

- Decapsulation processes received network data.
- It occurs from lower layers toward upper layers.
- Each layer examines its corresponding protocol information.
- The Transport layer helps deliver data to the appropriate application endpoint.
- The Application layer processes the received application data.
- Decapsulation is the reverse counterpart of encapsulation.

## 10. My Understanding

Write your own explanation:

- What is network decapsulation?
- How is it different from encapsulation?
- What happens at the Internet layer?
- How does the Transport layer identify the intended application endpoint?
- Why is decapsulation important in packet analysis?

## Related Notes

- [[OSI Model]]
- [[TCP-IP Model]]
- [[OSI vs TCP-IP]]
- [[Network Encapsulation]]
- [[TCP Protocol]]
- [[UDP Protocol]]
- [[Wireshark]]
- [[Packet Analysis]]

---