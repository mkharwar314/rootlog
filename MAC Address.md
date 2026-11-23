## 1. Introduction

MAC stands for **Media Access Control**.

A MAC address is a link-layer address used to identify a network interface on a local network.

It is commonly used for communication within the same local network segment.

Example:

```
00:1A:2B:3C:4D:5E
```

A traditional Ethernet MAC address is 48 bits (6 bytes) long.

## 2. MAC Address Structure

A 48-bit MAC address is usually written as six hexadecimal pairs.

Example:

```
00:1A:2B:3C:4D:5E
```

Each pair represents one byte.

|Part|Meaning|
|---|---|
|00:1A:2B|Organizationally Unique Identifier (OUI) portion|
|3C:4D:5E|Interface-specific portion|

The OUI is associated with an organization that has been assigned an address block.

Note: The structure and interpretation can vary for locally administered addresses and special address types.

## 3. MAC Address vs IP Address

Both MAC and IP addresses are used in networking, but they serve different purposes.

|MAC Address|IP Address|
|---|---|
|Used at the Data Link Layer|Used at the Network Layer|
|Identifies a network interface on a link|Identifies a network interface logically within an IP network|
|Traditionally 48 bits for Ethernet|32 bits for IPv4|
|Usually written in hexadecimal|Written in decimal for IPv4|
|Used for local link delivery|Used for routing between networks|

Example:

```
MAC Address: 00:1A:2B:3C:4D:5E
IP Address:  192.168.1.10
```

## 4. Types of MAC Addresses

### Unicast MAC Address

Identifies a single network interface.

A frame addressed to a unicast MAC address is intended for one interface.

### Multicast MAC Address

Identifies a group of network interfaces.

A frame can be delivered to multiple interfaces that belong to the multicast group.

### Broadcast MAC Address

Used to send an Ethernet frame to all devices on the local broadcast domain.

The standard Ethernet broadcast address is:

```
FF:FF:FF:FF:FF:FF
```

## 5. MAC Address and the OSI Model

MAC addressing operates at **Layer 2 — Data Link Layer** of the OSI model.

The Data Link Layer handles:

- Frame delivery over a local link.
- MAC addressing.
- Media access control.
- Error detection using mechanisms such as the Ethernet Frame Check Sequence.

## 6. How MAC Addresses Work

Consider two computers on the same local network.

```
Computer A
IP: 192.168.1.10
MAC: AA:AA:AA:AA:AA:AA

Computer B
IP: 192.168.1.20
MAC: BB:BB:BB:BB:BB:BB
```

When Computer A sends data to Computer B:

1. Computer A determines that the destination is on its local subnet.
2. It checks its ARP cache for Computer B's MAC address.
3. If necessary, it uses ARP to discover the MAC address.
4. It creates an Ethernet frame addressed to Computer B's MAC address.
5. The network interface sends the frame over the local network.

## 7. MAC Address Spoofing

MAC spoofing is the act of changing or impersonating a network interface's MAC address.

It can be used for legitimate testing and privacy purposes, but attackers may also use it to:

- Impersonate another device.
- Bypass weak MAC-based access controls.
- Evade simple network identification mechanisms.

### Protection Measures

- Do not rely only on MAC address filtering.
- Use strong authentication.
- Monitor network access.
- Use network access control where appropriate.
- Apply switch security features such as port security when suitable.

A MAC address is not a reliable identity or authentication mechanism. It can often be changed or imitated.

## 8. Practical Lab — Windows PowerShell

### Step 1: Display network adapters

```
Get-NetAdapter
```

Find the `MacAddress` column.

### Step 2: Display IP configuration

```
ipconfig /all
```

Look for:

```
Physical Address
```

This is the MAC address reported by Windows.

### Step 3: View ARP information

```
arp -a
```

This displays IPv4-to-MAC address mappings known to your computer.

### Step 4: View detailed adapter information

```
Get-NetAdapter | Format-List Name, InterfaceDescription, MacAddress, Status
```

## 9. Practical Observation

Record the information from your active network adapter.

|Property|Your Result|
|---|---|
|Adapter Name||
|MAC Address||
|IPv4 Address||
|Connection Status||

Do not publish your actual MAC address unnecessarily.

## 10. My Understanding

Write your own explanation:

- What is a MAC address?
- How many bits are in a traditional Ethernet MAC address?
- What is the purpose of an OUI?
- What is the difference between MAC and IP addresses?
- What is MAC spoofing?
- Why is MAC filtering not strong authentication?

## 11. Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[OSI Model]]
- [[Network Devices]]
- [[ARP Protocol]]
- [[Network Security]]
- [[Network Access Control]]

---

**Key Takeaway:** A MAC address is a link-layer address used for frame delivery on a local network, while an IP address supports logical addressing and routing.