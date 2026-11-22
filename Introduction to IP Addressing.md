> An IP address is a logical address assigned to a network interface to help identify it and communicate across IP networks.

## 1. What Is an IP Address?

IP stands for **Internet Protocol**.

An IP address is a numerical identifier used by the Internet Protocol to identify a network interface and help deliver packets to their destinations.

Every device communicating over an IP network needs an appropriate IP configuration.

Examples:

```
192.168.1.10
192.168.1.20
8.8.8.8
```

IP addresses are used by computers, servers, smartphones, routers, and other network devices.

**Important:** An IP address identifies a network interface, not necessarily an entire physical device. A device can have multiple network interfaces and multiple IP addresses.

## 2. Why Do We Need IP Addresses?

IP addresses help networks:

- Identify source and destination interfaces.
- Deliver packets between networks.
- Route data to the correct destination.
- Organize devices into networks and subnets.
- Enable communication over the Internet.

Example:

Suppose two computers are connected to the same network.

```
Computer A                 Computer B
192.168.1.10               192.168.1.20
      |                         |
      +--------- Router --------+
```

Computer A can communicate with Computer B using its IP address.

## 3. Types of IP Addresses

There are two main IP versions.

### IPv4

IPv4 stands for Internet Protocol Version 4.

Features:

- Uses 32-bit addresses.
- Written in dotted-decimal notation.
- Contains four octets.
- Each octet ranges from 0 to 255.
- Provides approximately 4.3 billion possible addresses.

Example:

```
192.168.1.10
```

An IPv4 address contains four octets:

```
192 . 168 . 1 . 10
 8      8   8    8 bits

Total = 32 bits
```

### IPv6

IPv6 stands for Internet Protocol Version 6.

Features:

- Uses 128-bit addresses.
- Written using hexadecimal notation.
- Contains eight groups of hexadecimal digits.
- Provides a much larger address space than IPv4.

Example:

```
2001:db8:abcd:0012:0000:0000:0000:0001
```

An IPv6 address can be shortened using rules for removing leading zeros and compressing consecutive zero groups.

## 4. IPv4 vs IPv6

|Feature|IPv4|IPv6|
|---|---|---|
|Address size|32 bits|128 bits|
|Format|Decimal|Hexadecimal|
|Address groups|4 octets|8 groups|
|Separator|Dot (`.`)|Colon (`:`)|
|Example|`192.168.1.10`|`2001:db8::1`|
|Address space|Approximately 4.3 billion|128-bit address space|

## 5. Basic IP Address Structure

An IP address is interpreted using a network prefix and an interface identifier within that network.

For example:

```
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
```

In this example:

- Network portion: `192.168.1`
- Host portion: `10`

This is a simplified explanation for a `/24` network.

The subnet mask determines which bits belong to the network prefix.

You will study this in detail in:

- [[IPv4 Addressing]]
- [[Subnetting]]
- [[Subnet Masks]]
- [[CIDR Notation]]

## 6. IP Address and MAC Address

An IP address and a MAC address serve different purposes.

|Feature|IP Address|MAC Address|
|---|---|---|
|Type|Logical address|Link-layer address|
|OSI layer association|Layer 3|Layer 2|
|Purpose|Network communication and routing|Local link delivery|
|Example|`192.168.1.10`|`00:1A:2B:3C:4D:5E`|

**Remember:**

- IP addresses help route packets between networks.
- MAC addresses are used for delivery across a local network link.

## 7. IP Addressing and Cybersecurity

Understanding IP addressing is essential for cybersecurity.

It helps security professionals:

- Identify communicating hosts.
- Analyze network traffic.
- Investigate suspicious connections.
- Understand network reconnaissance.
- Configure firewalls.
- Monitor network activity.
- Investigate possible IP spoofing.

Tools:

- Wireshark
- Nmap
- Ping
- Traceroute
- IP configuration commands

## 8. Practical Lab — Find Your IP Address

### Step 1 — Open PowerShell

Run:

```
ipconfig
```

### Step 2 — Identify your active adapter

Find the network adapter currently connected to your network.

### Step 3 — Record these values

```
IPv4 Address:
Subnet Mask:
Default Gateway:
```

### Step 4 — Display detailed information

Run:

```
ipconfig /all
```

Find the physical address (MAC address) of the same adapter.

### Step 5 — Answer

- What is your IPv4 address?
- What is your subnet mask?
- What is your default gateway?
- What is your MAC address?

Do not publish your public IP address or other network details unnecessarily.

## 9. Key Takeaways

- IP stands for Internet Protocol.
- IP addresses identify network interfaces for IP communication.
- IPv4 uses 32-bit addresses.
- IPv6 uses 128-bit addresses.
- IP addresses support packet delivery and routing.
- IP addressing is a foundation of network security.

## 10. My Understanding

Write your own explanation:

- What is an IP address?
- Why do networks need IP addresses?
- What is the difference between IPv4 and IPv6?
- What is the difference between an IP address and a MAC address?
- Why is IP addressing important in cybersecurity?

## Related Notes

- [[IPv4 Addressing]]
- [[IPv6 Addressing]]
- [[Public and Private IP Addresses]]
- [[Static and Dynamic IP Addresses]]
- [[Subnetting]]
- [[CIDR Notation]]
- [[Subnet Masks]]
- [[MAC Address]]
- [[Network Encapsulation]]
- [[Wireshark]]
- [[Nmap]]

---