> Public and private IP addresses are used to identify network interfaces in different addressing scopes.

## 1. What Is a Public IP Address?

A public IP address is an IP address that is globally reachable through the Internet, subject to routing, firewall rules, and network configuration.

It is commonly assigned to:

- Internet-facing routers
- Web servers
- Public cloud services
- Other Internet-accessible systems

Example:

```
8.8.8.8
```

This is a public IPv4 address used by Google's public DNS service.

### Characteristics

- Globally unique within the public Internet addressing system.
- Routable across the Internet.
- Commonly assigned by an Internet Service Provider (ISP).
- Can be used to communicate with Internet-facing services.

## 2. What Is a Private IP Address?

A private IP address is used for communication within private networks.

Private IPv4 addresses are not directly routed across the public Internet.

They are commonly used in:

- Home networks
- Office networks
- College networks
- Internal servers
- Virtual machines

Example:

```
192.168.1.10
```

### Characteristics

- Used inside private networks.
- Can be reused in different independent networks.
- Usually accesses the Internet through a router using NAT.
- Not directly reachable from the public Internet through ordinary public routing.

## 3. Private IPv4 Address Ranges

The three private IPv4 ranges are defined by RFC 1918.

|Class|Private Range|CIDR|
|---|---|---|
|A|`10.0.0.0 – 10.255.255.255`|`10.0.0.0/8`|
|B|`172.16.0.0 – 172.31.255.255`|`172.16.0.0/12`|
|C|`192.168.0.0 – 192.168.255.255`|`192.168.0.0/16`|

**Remember:** Not every address beginning with `172` is private. Only `172.16.0.0` through `172.31.255.255` belong to the private range.

## 4. Public vs Private IP Addresses

|Feature|Public IP|Private IP|
|---|---|---|
|Scope|Public Internet|Private network|
|Global routing|Yes|No|
|Assignment|ISP or provider|Router or network administrator|
|Reuse|Must be globally unique in public routing|Can be reused across separate networks|
|Example|`8.8.8.8`|`192.168.1.10`|
|Common use|Public-facing services|Internal devices|

## 5. How Public and Private IP Addresses Work Together

Consider a home network.

```
       Internet
           |
           |
    Public IP Address
      203.0.113.10
           |
         Router
       (NAT enabled)
           |
    -----------------
    |               |
 Computer         Phone
192.168.1.10    192.168.1.20
```

The computer and phone use private IP addresses.

The router uses its public-facing IP address to communicate with the Internet.

When an internal device sends traffic to the Internet, the router commonly uses Network Address Translation (NAT) to translate the private source address and track the connection.

**Note:** `203.0.113.10` is an example address reserved for documentation, not a real public address to use on the Internet.

## 6. What Is NAT?

NAT stands for **Network Address Translation**.

It modifies IP address information as packets pass through a router or other network device.

A common form is Port Address Translation (PAT), which allows multiple private devices to share one public IPv4 address using different transport-layer ports.

Example:

```
Computer A: 192.168.1.10
Computer B: 192.168.1.20
                  |
                  v
             NAT Router
                  |
                  v
          Shared Public IP
```

You will study NAT in detail in [[NAT]].

## 7. Public and Private IP Addresses in Cybersecurity

Understanding IP address scope is important for:

- Network reconnaissance
- Firewall configuration
- Access control
- Network segmentation
- Incident investigation
- Identifying Internet-facing systems

### Security Considerations

**Public IP security:**

- Exposed services may be discovered through scanning.
- Misconfigured firewalls can expose internal services.
- Public-facing servers require regular patching and monitoring.

**Private IP security:**

- Internal devices can still be compromised.
- Attackers may move laterally between internal systems.
- Weak network segmentation can increase risk.

**Important:** A private IP address does not automatically make a device secure.

## 8. Practical Lab — Identify Your IP Addresses

### Step 1 — Find your private IP address

Open PowerShell:

```
ipconfig
```

Identify the IPv4 address of your active adapter.

### Step 2 — Find your public IP address

You can use a reputable IP-checking website, such as:

[https://api.ipify.org](https://api.ipify.org)

Alternatively, use PowerShell:

```
(Invoke-RestMethod -Uri "https://api.ipify.org").Trim()
```

This sends a request to an external service to identify the public IP address it sees.

### Step 3 — Compare both addresses

Record:

```
Private IPv4 Address:
Public IPv4 Address:
```

### Step 4 — Answer these questions

1. Why are the two addresses different?
2. Which device commonly performs NAT?
3. Can two separate home networks use the same private IP address?

**Note:** Your public IP may be shared with other customers through carrier-grade NAT (CGNAT). Therefore, the address shown by an IP-checking service is not necessarily assigned directly to your router.

## 9. Key Takeaways

- Public IP addresses are globally routable.
- Private IPv4 addresses are used inside private networks.
- RFC 1918 defines three private IPv4 ranges.
- NAT commonly allows private devices to access the Internet.
- Multiple private networks can reuse the same address ranges.
- Private addressing does not guarantee security.

## 10. My Understanding

Write your own explanation:

- What is a public IP address?
- What is a private IP address?
- What are the three private IPv4 ranges?
- What is NAT?
- Why can two homes use the same private IP address?
- Does using a private IP address make a network secure?

## Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[IPv6 Addressing]]
- [[Static and Dynamic IP Addresses]]
- [[Subnetting]]
- [[CIDR Notation]]
- [[Subnet Masks]]
- [[Default Gateway]]
- [[NAT]]
- [[Firewalls]]
- [[Network Security]]

---