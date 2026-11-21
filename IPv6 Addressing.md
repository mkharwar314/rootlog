> IPv6 (Internet Protocol Version 6) is a 128-bit addressing system designed to provide a much larger IP address space and support modern Internet communication.

## 1. What Is IPv6?

IPv6 stands for **Internet Protocol Version 6**.

It was developed to address limitations of IPv4, especially the shortage of publicly available IPv4 addresses.

IPv6 uses 128-bit addresses instead of IPv4's 32-bit addresses.

Example:

```
2001:0db8:0000:0000:0000:ff00:0042:8329
```

IPv6 provides approximately:

[  
2^{128}  
]

possible addresses.

This is an extremely large address space.

## 2. IPv6 Address Structure

An IPv6 address contains:

- 128 bits.
- Eight groups called hextets.
- Each hextet contains 16 bits.
- Each hextet is written using hexadecimal digits.
- Groups are separated by colons (`:`).

Example:

```
2001:0db8:0000:0000:0000:ff00:0042:8329
```

Structure:

```
2001 : 0db8 : 0000 : 0000 : 0000 : ff00 : 0042 : 8329
 16      16     16     16     16     16     16     16 bits

Total = 128 bits
```

Hexadecimal uses 16 symbols:

```
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

## 3. IPv6 Address Shortening

IPv6 addresses can be shortened using two rules.

### Rule 1 — Remove Leading Zeros

Leading zeros in each hextet can be removed.

Example:

```
Original:
2001:0db8:0000:0000:0000:ff00:0042:8329

Shortened:
2001:db8:0:0:0:ff00:42:8329
```

### Rule 2 — Replace Consecutive Zero Groups

One consecutive sequence of zero hextets can be replaced with `::`.

Example:

```
Original:
2001:0db8:0000:0000:0000:ff00:0042:8329

Shortened:
2001:db8::ff00:42:8329
```

**Important:** `::` can be used only once in an IPv6 address because using it multiple times would make the number of omitted groups ambiguous.

## 4. Types of IPv6 Addresses

IPv6 has several important address types.

### 1. Unicast

Identifies a single network interface.

A packet sent to a unicast address is intended for that interface.

Examples:

- Global unicast
- Link-local unicast
- Unique local addresses

### 2. Multicast

Identifies a group of network interfaces.

A packet sent to a multicast address is delivered to members of that group.

IPv6 multicast addresses begin with:

```
ff00::/8
```

### 3. Anycast

An anycast address can be assigned to multiple interfaces.

A packet sent to an anycast address is delivered to one suitable member of that group, typically according to routing distance or policy.

**Important:** IPv6 does not use broadcast addresses. Multicast provides many functions that broadcast serves in IPv4.

## 5. Important IPv6 Address Ranges

|Address or Prefix|Purpose|
|---|---|
|`::1/128`|Loopback address|
|`::/128`|Unspecified address|
|`fe80::/10`|Link-local unicast|
|`fc00::/7`|Unique local address space|
|`2000::/3`|Global unicast address space|
|`ff00::/8`|Multicast|

Example:

```
::1
```

This is the IPv6 loopback address, equivalent in purpose to IPv4 `127.0.0.1`.

## 6. IPv4 vs IPv6

|Feature|IPv4|IPv6|
|---|---|---|
|Address size|32 bits|128 bits|
|Format|Decimal|Hexadecimal|
|Groups|4 octets|8 hextets|
|Separator|Dot|Colon|
|Example|`192.168.1.10`|`2001:db8::1`|
|Broadcast|Supported|Not supported|
|Address configuration|Manual or DHCP|Manual, SLAAC, DHCPv6|
|Header|Variable length|Fixed 40-byte base header|

## 7. IPv6 Header

The IPv6 base header is 40 bytes long.

Important fields include:

- Version
- Traffic Class
- Flow Label
- Payload Length
- Next Header
- Hop Limit
- Source Address
- Destination Address

The **Hop Limit** is similar in purpose to IPv4's Time To Live (TTL): it limits how many router hops a packet can pass through.

Unlike IPv4, IPv6 routers do not fragment packets in transit. Fragmentation, when needed, is handled by the source using an IPv6 Fragment extension header.

## 8. IPv6 and Cybersecurity

IPv6 is important in modern network security.

Security professionals should understand:

- IPv6 addressing and routing.
- IPv6 firewall configuration.
- Neighbor Discovery Protocol (NDP).
- Router Advertisement security.
- IPv6 network reconnaissance.
- Dual-stack network environments.

Potential security concerns include:

- Rogue Router Advertisements.
- NDP spoofing.
- IPv6 misconfiguration.
- Unauthorized IPv6 traffic.
- Firewall rules that protect IPv4 but overlook IPv6.

**Important:** Disabling or ignoring IPv6 without understanding the network can create connectivity and security problems.

## 9. Practical Lab — Find Your IPv6 Address

Open Windows PowerShell.

### Step 1 — Display network configuration

```
ipconfig /all
```

### Step 2 — Find IPv6 addresses

Look for entries such as:

```
IPv6 Address
Temporary IPv6 Address
Link-local IPv6 Address
```

Your system may display multiple IPv6 addresses.

### Step 3 — Test the IPv6 loopback address

```
ping ::1
```

### Step 4 — Display IPv6 configuration

```
netsh interface ipv6 show address
```

### Step 5 — Record your observations

```
IPv6 Address:
Link-local IPv6 Address:
Loopback Address:
```

Do not share your full network configuration publicly.

## 10. Key Takeaways

- IPv6 uses 128-bit addresses.
- An IPv6 address contains eight 16-bit hextets.
- Hexadecimal notation is used.
- Leading zeros can be removed.
- `::` compresses one consecutive sequence of zero groups.
- IPv6 supports unicast, multicast, and anycast.
- IPv6 does not use broadcast.
- IPv6 security is important in modern networks.

## 11. My Understanding

Write your own explanation:

- What is IPv6?
- Why was IPv6 developed?
- What is a hextet?
- How can an IPv6 address be shortened?
- What is the difference between unicast, multicast, and anycast?
- Why is IPv6 security important?

## Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[Public and Private IP Addresses]]
- [[Static and Dynamic IP Addresses]]
- [[Subnetting]]
- [[CIDR Notation]]
- [[Subnet Masks]]
- [[Default Gateway]]
- [[Network Security]]
- [[Wireshark]]

---