> IPv4 is a network-layer addressing system that uses 32-bit addresses to identify interfaces and enable communication across IP networks.

## 1. What Is IPv4?

IPv4 stands for **Internet Protocol Version 4**.

It is one of the most widely used protocols for identifying devices on IP networks.

An IPv4 address consists of 32 bits, divided into four groups called octets.

Example:

```
192.168.1.10
```

Each octet contains 8 bits.

```
192  .  168  .  1  .  10
 8       8       8      8 bits

Total = 32 bits
```

Each octet can have a decimal value between 0 and 255.

## 2. IPv4 Address Structure

An IPv4 address is divided into two logical parts:

1. Network portion
2. Host portion

The subnet mask or prefix length determines which bits belong to the network portion.

Example:

```
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
Prefix:      /24
```

For this example:

- Network address: `192.168.1.0`
- Host address: `192.168.1.10`
- Broadcast address: `192.168.1.255`

The `/24` prefix means the first 24 bits identify the network.

## 3. Binary Representation

Computers process IP addresses in binary.

Each IPv4 octet contains 8 bits.

Example:

```
Decimal: 192.168.1.10

Binary:

192 = 11000000
168 = 10101000
  1 = 00000001
 10 = 00001010
```

Complete binary address:

```
11000000.10101000.00000001.00001010
```

This is the binary representation of `192.168.1.10`.

## 4. IPv4 Address Classes

Historically, IPv4 addresses were divided into five classes.

|Class|First Octet Range|Historical Purpose|
|---|---|---|
|A|1–126|Large networks|
|B|128–191|Medium networks|
|C|192–223|Smaller networks|
|D|224–239|Multicast|
|E|240–255|Experimental/reserved|

Important notes:

- `127.0.0.0/8` is reserved for loopback.
- Class-based addressing is largely obsolete.
- Modern networks use CIDR (Classless Inter-Domain Routing).

**Remember:** Classes are useful historical knowledge, but do not use them as the basis for modern subnet design.

## 5. Network Address, Host Address and Broadcast Address

Consider this network:

```
Network: 192.168.1.0/24
```

|Address|Value|Purpose|
|---|---|---|
|Network address|`192.168.1.0`|Identifies the subnet|
|First usable host|`192.168.1.1`|First conventional host address|
|Last usable host|`192.168.1.254`|Last conventional host address|
|Broadcast address|`192.168.1.255`|IPv4 broadcast to the subnet|

For a conventional `/24` subnet, there are 256 total addresses and 254 traditionally usable host addresses.

Special-purpose prefixes, such as `/31` and `/32`, have different rules.

## 6. Special IPv4 Addresses

|Address or Range|Purpose|
|---|---|
|`127.0.0.1`|Common loopback address|
|`0.0.0.0`|Unspecified address|
|`255.255.255.255`|Limited broadcast|
|`169.254.0.0/16`|IPv4 link-local range|
|`10.0.0.0/8`|Private address range|
|`172.16.0.0/12`|Private address range|
|`192.168.0.0/16`|Private address range|

## 7. IPv4 and Subnet Masks

A subnet mask determines which portion of an IPv4 address represents the network prefix.

Example:

```
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
Prefix:      /24
```

A `/24` prefix means:

- Network bits: 24
- Host bits: 8

You will study subnet masks in detail in [[Subnet Masks]] and [[Subnetting]].

## 8. IPv4 and Cybersecurity

IPv4 knowledge is essential for:

- Network reconnaissance
- Host discovery
- Firewall configuration
- Network traffic analysis
- Incident investigation
- Network segmentation

Common security concepts:

- IP spoofing
- IP scanning
- Packet filtering
- Address conflicts
- Unauthorized network access

Tools:

- Nmap
- Wireshark
- Ping
- Traceroute
- PowerShell networking commands

## 9. Practical Lab — Inspect Your IPv4 Configuration

Open PowerShell.

### Step 1 — Display IP configuration

```
ipconfig
```

### Step 2 — Display detailed information

```
ipconfig /all
```

### Step 3 — Identify your active adapter

Record:

```
IPv4 Address:
Subnet Mask:
Default Gateway:
DHCP Enabled:
```

### Step 4 — Test your loopback address

```
ping 127.0.0.1
```

This tests the local TCP/IP stack without sending traffic to another computer.

### Step 5 — Check your local network address

```
ipconfig
```

Compare your IPv4 address with `127.0.0.1`.

## 10. Key Takeaways

- IPv4 uses 32-bit addresses.
- An IPv4 address contains four octets.
- Each octet has a value from 0 to 255.
- Subnet masks identify network and host portions.
- Network and broadcast addresses have special purposes.
- Modern networks use CIDR rather than traditional address classes.
- IPv4 knowledge is important for network security and troubleshooting.

## 11. My Understanding

Write your own explanation:

- What is IPv4?
- Why does IPv4 use 32 bits?
- What is an octet?
- What is the difference between a network address and a host address?
- What is the purpose of a subnet mask?
- Why is `127.0.0.1` special?

## Related Notes

- [[Introduction to IP Addressing]]
- [[IPv6 Addressing]]
- [[Public and Private IP Addresses]]
- [[Static and Dynamic IP Addresses]]
- [[Subnetting]]
- [[CIDR Notation]]
- [[Subnet Masks]]
- [[Default Gateway]]
- [[MAC Address]]
- [[Nmap]]
- [[Wireshark]]

---