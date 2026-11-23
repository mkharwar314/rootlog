## 1. Introduction

Subnetting is the process of dividing a large IP network into smaller logical networks called **subnets**.

It helps network administrators organize devices, manage IP addresses, and control network traffic.

For example, an organization may divide its network into separate subnets for:

- Employees
- Servers
- Guest Wi-Fi
- Management systems

## 2. Why Is Subnetting Important?

Subnetting provides several benefits:

1. **Efficient IP Address Usage:** Helps allocate IP addresses according to network requirements.
2. **Network Organization:** Divides large networks into smaller sections.
3. **Security:** Helps isolate different groups of devices.
4. **Traffic Management:** Reduces unnecessary broadcast traffic within each subnet.
5. **Network Administration:** Makes troubleshooting and management easier.

## 3. Basic Subnetting Concepts

Before understanding subnetting, learn these terms:

|Term|Meaning|
|---|---|
|IP Address|Identifies a device on an IP network|
|Network Address|Identifies a particular network or subnet|
|Host Address|Identifies a device within a subnet|
|Broadcast Address|IPv4 address used to reach all hosts in a subnet|
|Subnet Mask|Separates the network portion from the host portion|
|CIDR|Represents the network prefix length|

## 4. Network Portion and Host Portion

An IPv4 address contains 32 bits.

These bits are divided into:

- Network portion
- Host portion

The subnet mask determines which bits belong to each portion.

Example:

```
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
CIDR: /24
```

In this example:

```
Network Portion: 192.168.1
Host Portion:    10
```

The network is `192.168.1.0/24`.

## 5. What Happens During Subnetting?

Subnetting borrows bits from the host portion to create additional network bits.

As more bits are borrowed:

- The number of subnets increases.
- The number of available host addresses per subnet decreases.

This is the fundamental principle of IPv4 subnetting.

## 6. Basic Subnetting Example

Consider this network:

```
192.168.1.0/24
```

Its subnet mask is:

```
255.255.255.0
```

A `/24` network contains 256 total IPv4 addresses.

These include:

- 1 network address
- 254 traditionally usable host addresses
- 1 broadcast address

The usable host range is:

```
192.168.1.1 - 192.168.1.254
```

The broadcast address is:

```
192.168.1.255
```

## 7. Dividing a Network into Smaller Subnets

Suppose we divide:

```
192.168.1.0/24
```

into two equal subnets.

We borrow one host bit, changing the prefix from `/24` to `/25`.

The resulting networks are:

|Subnet|Network Address|Usable Host Range|Broadcast|
|---|---|---|---|
|1|192.168.1.0/25|192.168.1.1–126|192.168.1.127|
|2|192.168.1.128/25|192.168.1.129–254|192.168.1.255|

Each subnet contains:

- 128 total addresses
- 126 traditionally usable host addresses

## 8. Important Subnetting Formulas

For ordinary IPv4 subnets, excluding special cases:

### Total Addresses

[  
2^h  
]

Where `h` is the number of host bits.

### Usable Host Addresses

[  
2^h - 2  
]

The two excluded addresses are traditionally the network and broadcast addresses.

### Number of Subnets

If `s` bits are borrowed from the original host portion:

[  
2^s  
]

Modern subnetting supports subnet zero; do not automatically subtract two from the number of subnets.

## 9. Subnetting and Cybersecurity

Subnetting is important in network security.

It can help organizations:

- Separate internal departments.
- Isolate servers from user devices.
- Create guest networks.
- Restrict communication between network segments.
- Reduce the impact of some network incidents.

However, subnetting alone does not provide security. Firewalls, access-control rules, and proper network configuration are also necessary.

## 10. Practical Understanding

Imagine a college network with 200 computers.

Instead of placing every device in one large network, the administrator can create separate subnets for:

- Computer laboratories
- Faculty offices
- Administration
- Guest network

This improves organization and makes it easier to apply different security policies.

## 11. My Understanding

Write your own explanation:

- What is subnetting?
- Why do we divide networks into subnets?
- What is a network address?
- What is a broadcast address?
- What happens when we borrow host bits?
- How does subnetting help network security?

## 12. Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[CIDR Notation]]
- [[Subnet Masks]]
- [[Default Gateway]]
- [[Network Segmentation]]
- [[Network Architecture]]

---

**Key Takeaway:** Subnetting divides a large IP network into smaller networks by borrowing bits from the host portion of an IP address.