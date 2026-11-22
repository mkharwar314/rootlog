## 1. Introduction

A subnet mask is a 32-bit value used in IPv4 networking to distinguish the network portion of an IP address from the host portion.

It helps devices determine whether another IP address belongs to the same local subnet or whether traffic should be sent through a router.

Example:

```
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
CIDR:        /24
```

In this example:

- Network portion: `192.168.1`
- Host portion: `10`
- Network address: `192.168.1.0`

## 2. Why Are Subnet Masks Important?

Subnet masks are used to:

- Identify network boundaries.
- Determine whether devices belong to the same subnet.
- Divide networks into smaller subnets.
- Support routing decisions.
- Manage IP address allocation.

Without a correct subnet mask, a device may incorrectly determine where to send network traffic.

## 3. Understanding Binary Representation

An IPv4 address contains 32 bits, divided into four octets.

A subnet mask also contains 32 bits.

In a subnet mask:

- `1` represents a network bit.
- `0` represents a host bit.

Example:

```
Subnet Mask: 255.255.255.0

Binary:
11111111.11111111.11111111.00000000
```

There are 24 network bits and 8 host bits.

Therefore, its CIDR notation is `/24`.

## 4. Common Subnet Masks

|CIDR|Subnet Mask|Total Addresses|Conventional Usable Hosts|
|---|---|---|---|
|/8|255.0.0.0|16,777,216|16,777,214|
|/16|255.255.0.0|65,536|65,534|
|/24|255.255.255.0|256|254|
|/25|255.255.255.128|128|126|
|/26|255.255.255.192|64|62|
|/27|255.255.255.224|32|30|
|/28|255.255.255.240|16|14|
|/29|255.255.255.248|8|6|
|/30|255.255.255.252|4|2|

The conventional usable-host calculation excludes the network and broadcast addresses. Special cases such as `/31` point-to-point networks and `/32` host routes are exceptions.

## 5. How Does a Subnet Mask Work?

A device uses a logical AND operation between its IP address and subnet mask to calculate the network address.

Example:

```
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
```

Binary representation of the last octet:

```
IP Address:  00001010
Subnet Mask: 00000000
---------------------
Result:      00000000
```

The resulting network address is:

```
192.168.1.0
```

This process helps identify the network to which an IP address belongs.

## 6. Example: /24 Subnet Mask

Given:

```
IP Address:  192.168.1.50
Subnet Mask: 255.255.255.0
```

Network details:

|Property|Value|
|---|---|
|Network Address|192.168.1.0|
|First Usable Host|192.168.1.1|
|Last Usable Host|192.168.1.254|
|Broadcast Address|192.168.1.255|
|Total Addresses|256|
|Usable Hosts|254|

## 7. Example: /26 Subnet Mask

Given:

```
IP Address:  192.168.1.70
Subnet Mask: 255.255.255.192
CIDR:        /26
```

A `/26` subnet contains 64 total addresses.

The subnet ranges within `192.168.1.0/24` are:

|Subnet|Address Range|Broadcast|
|---|---|---|
|1|192.168.1.0–63|192.168.1.63|
|2|192.168.1.64–127|192.168.1.127|
|3|192.168.1.128–191|192.168.1.191|
|4|192.168.1.192–255|192.168.1.255|

The IP address `192.168.1.70` belongs to the second subnet.

Its network address is `192.168.1.64`.

Its usable host range is `192.168.1.65–192.168.1.126`.

## 8. Subnet Mask vs CIDR

|Subnet Mask|CIDR|
|---|---|
|Written in dotted-decimal format|Written as a prefix length|
|Example: 255.255.255.0|Example: /24|
|Contains 32 bits|Represents the number of network bits|
|Used in IPv4 configuration|Used in routing and network notation|

Both represent the same network boundary information.

## 9. Security Importance

Subnet masks play an important role in network security and administration.

They help administrators:

- Separate internal networks.
- Organize departments into different subnets.
- Configure firewall rules.
- Control routing boundaries.
- Troubleshoot incorrect network configurations.

An incorrect subnet mask can cause connectivity problems or unintended network communication.

Remember: A subnet mask does not itself provide security. Network segmentation must be combined with access controls and firewall policies.

## 10. Practical Lab — Windows PowerShell

### Step 1: Display network configuration

```
ipconfig /all
```

### Step 2: Identify your active adapter

```
Get-NetIPConfiguration
```

### Step 3: Display interface IP configuration

```
Get-NetIPAddress -AddressFamily IPv4
```

Find your active adapter and record:

|Property|Your Result|
|---|---|
|IPv4 Address||
|Prefix Length||
|Subnet Mask||
|Default Gateway||

Note: PowerShell commonly displays the prefix length, while `ipconfig` displays the subnet mask.

## 11. Practice Questions

1. What is a subnet mask?
2. What does `/24` represent?
3. What is the subnet mask for `/26`?
4. How many total addresses are in a `/27` subnet?
5. What is the network address of `192.168.1.70/26`?
6. What is the difference between a subnet mask and a CIDR prefix?

## 12. My Understanding

Write your own explanation:

- How does a subnet mask work?
- What do binary `1` and `0` represent?
- How is a network address calculated?
- Why do devices need subnet masks?
- How do subnet masks support network segmentation?

## 13. Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[Subnetting]]
- [[CIDR Notation]]
- [[Default Gateway]]
- [[Network Segmentation]]
- [[Routing Tables]]

---

**Key Takeaway:** A subnet mask identifies the network and host portions of an IPv4 address, helping devices communicate within and between networks.