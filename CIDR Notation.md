## 1. Introduction

CIDR stands for **Classless Inter-Domain Routing**.

It is a method of representing IP network addresses using a prefix length.

CIDR notation helps identify how many bits of an IP address belong to the network portion.

Example:

```
192.168.1.0/24
```

Here:

- `192.168.1.0` is the network address.
- `/24` indicates that the first 24 bits represent the network portion.
- The remaining 8 bits represent the host portion.

## 2. Why CIDR Was Introduced

Earlier IPv4 networks commonly used class-based addressing:

- Class A
- Class B
- Class C

Class-based allocation could waste IP addresses because organizations often received address blocks that were larger than required.

CIDR introduced flexible network prefixes.

Benefits include:

- More efficient IP address allocation.
- Flexible subnet sizes.
- Better use of IPv4 address space.
- Route aggregation, which reduces routing table entries.

## 3. Understanding CIDR Prefix Length

An IPv4 address contains 32 bits.

The number after `/` tells us how many bits belong to the network prefix.

Examples:

|CIDR|Network Bits|Host Bits|
|---|---|---|
|/8|8|24|
|/16|16|16|
|/24|24|8|
|/25|25|7|
|/26|26|6|
|/27|27|5|
|/28|28|4|
|/30|30|2|

Formula:

```
Host Bits = 32 - Prefix Length
```

For example:

```
/24

Host Bits = 32 - 24
          = 8
```

## 4. CIDR and Subnet Masks

A CIDR prefix can be converted into a subnet mask.

Examples:

|CIDR|Subnet Mask|
|---|---|
|/8|255.0.0.0|
|/16|255.255.0.0|
|/24|255.255.255.0|
|/25|255.255.255.128|
|/26|255.255.255.192|
|/27|255.255.255.224|
|/28|255.255.255.240|
|/29|255.255.255.248|
|/30|255.255.255.252|

## 5. Calculating Total IP Addresses

For ordinary IPv4 prefixes, the total number of addresses is:

[  
2^{(32-\text{prefix length})}  
]

Example:

```
192.168.1.0/24
```

Calculation:

[  
2^{(32-24)} = 2^8 = 256  
]

Therefore, a `/24` network contains 256 total addresses.

For a conventional IPv4 subnet, the usable host count is usually:

[  
2^h - 2  
]

Where `h` is the number of host bits.

For `/24`:

[  
2^8 - 2 = 254  
]

The subtraction accounts for the network and broadcast addresses.

Note: Special cases such as `/31` point-to-point networks and `/32` host routes do not follow this ordinary usable-host calculation.

## 6. Example: Understanding /26

Consider:

```
192.168.1.0/26
```

Step 1: Calculate host bits.

```
32 - 26 = 6
```

Step 2: Calculate total addresses.

[  
2^6 = 64  
]

Step 3: Calculate conventional usable hosts.

[  
64 - 2 = 62  
]

The subnet details are:

|Property|Value|
|---|---|
|Network Address|192.168.1.0|
|First Usable Host|192.168.1.1|
|Last Usable Host|192.168.1.62|
|Broadcast Address|192.168.1.63|
|Total Addresses|64|
|Usable Hosts|62|

## 7. CIDR Block Example

Consider the network:

```
192.168.1.0/24
```

It can be divided into four equal `/26` subnets:

|Subnet|Network Address|Usable Host Range|Broadcast|
|---|---|---|---|
|1|192.168.1.0/26|.1 – .62|.63|
|2|192.168.1.64/26|.65 – .126|.127|
|3|192.168.1.128/26|.129 – .190|.191|
|4|192.168.1.192/26|.193 – .254|.255|

Each subnet contains 64 total addresses and 62 conventional usable host addresses.

## 8. CIDR in Networking and Cybersecurity

CIDR is used in:

- Router configuration.
- Firewall rules.
- Network scanning.
- Network segmentation.
- Routing tables.
- Cloud network configuration.
- IP address management.

For example, an authorized network scan may target:

```
192.168.1.0/24
```

This represents the entire IPv4 address block containing 256 addresses.

Only scan networks and systems you own or have permission to test.

## 9. Practical Lab — Windows

### Step 1: View your IP configuration

```
ipconfig
```

Find your IPv4 address and subnet mask.

### Step 2: View detailed network information

```
ipconfig /all
```

### Step 3: Calculate the prefix length

For example:

```
Subnet Mask: 255.255.255.0
CIDR Prefix: /24
```

Record your own network details:

|Property|Your Result|
|---|---|
|IPv4 Address||
|Subnet Mask||
|CIDR Prefix||
|Default Gateway||

## 10. Practice Questions

Calculate the following:

1. How many host bits are in `/24`?
2. How many total addresses are in `/26`?
3. How many conventional usable hosts are in `/27`?
4. What subnet mask represents `/25`?
5. What CIDR prefix represents `255.255.255.0`?

## 11. My Understanding

Write your own explanation:

- What does CIDR stand for?
- Why was CIDR introduced?
- What does `/24` mean?
- How do you calculate host bits?
- How does CIDR help subnetting?
- What is the difference between CIDR and a subnet mask?

## 12. Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[Subnetting]]
- [[Subnet Masks]]
- [[Public and Private IP Addresses]]
- [[Routing Tables]]
- [[Network Segmentation]]

---

**Key Takeaway:** CIDR represents an IP network using a prefix length, allowing flexible allocation and division of IP address space.