## 1. Introduction

An IP address identifies a device on an IP network.

There are two common methods of assigning IP addresses:

- **Static IP:** An address configured to remain consistent.
- **Dynamic IP:** An address assigned automatically and potentially changed over time.

These methods describe how an IP address is assigned, not whether it is public or private.

## 2. Static IP Address

A static IP address is an address that is intended to remain unchanged.

It can be configured manually or provided through a DHCP reservation.

### Characteristics

- Remains consistent unless reconfigured.
- Useful for devices that need a predictable address.
- Requires proper IP address management.
- Incorrect configuration can cause IP conflicts.

### Common Uses

- Servers
- Network printers
- Routers and network infrastructure
- Network monitoring systems
- Devices requiring predictable network access

## 3. Dynamic IP Address

A dynamic IP address is assigned automatically by a network service.

In IPv4 networks, this is commonly handled by **DHCP (Dynamic Host Configuration Protocol)**.

The assigned address is usually provided for a limited period called a **DHCP lease**.

### Characteristics

- Automatically assigned.
- Reduces manual configuration.
- Can change when a lease expires or a device reconnects.
- Makes address management easier on large networks.

## 4. DHCP and the DORA Process

DHCP allows devices to obtain network configuration automatically.

The IPv4 DHCP assignment process is commonly called DORA.

1. **Discover:** The client searches for a DHCP server.
2. **Offer:** The DHCP server offers an available IP address.
3. **Request:** The client requests the offered address.
4. **Acknowledge:** The server confirms the assignment.

The client can then use the assigned network configuration.

### DHCP Ports

|Component|UDP Port|
|---|---|
|DHCP Server|67|
|DHCP Client|68|

## 5. DHCP Lease

A DHCP lease is the period during which a client is allowed to use an assigned IP address.

Before the lease expires, the client normally attempts to renew it.

If renewal fails and the lease expires, the address may eventually become available for another device.

## 6. DHCP Reservation

A DHCP reservation associates a particular device, usually identified by its MAC address, with a specific IP address.

This allows the device to receive the same IP address through DHCP without manually configuring it on the device.

A reservation is often useful for printers, servers, and other infrastructure devices.

## 7. Static vs Dynamic IP

|Feature|Static IP|Dynamic IP|
|---|---|---|
|Assignment|Manual or reserved|Automatic|
|Stability|Intended to remain the same|May change|
|Administration|Requires planning|Easier for many devices|
|Common use|Servers and infrastructure|Laptops and mobile devices|
|Configuration|Manual or DHCP reservation|DHCP or other automatic mechanisms|

## 8. Important Distinction

Public/private and static/dynamic are two separate classifications.

An IP address can be:

- Public and static
- Public and dynamic
- Private and static
- Private and dynamic

For example, a laptop may receive a private dynamic IP address from a home router, while a server may use a private static IP address.

## 9. Security Considerations

DHCP introduces some security risks.

### Rogue DHCP Server

An unauthorized DHCP server may provide incorrect network settings, potentially redirecting traffic.

### DHCP Starvation

An attacker may attempt to exhaust the available DHCP address pool by sending many fake requests.

### IP Address Conflicts

Incorrect manual configuration or poor address management can cause multiple devices to use the same IP address.

### Protection Measures

- Use DHCP snooping on supported managed switches.
- Restrict access to network infrastructure.
- Monitor DHCP activity.
- Maintain an organized IP address allocation plan.
- Use reservations for devices requiring predictable addresses.

## 10. Practical Lab — Windows PowerShell

### Objective

Inspect the IP configuration assigned to your Windows computer.

### Step 1: View complete IP configuration

```
ipconfig /all
```

Look for:

- DHCP Enabled
- IPv4 Address
- Subnet Mask
- Default Gateway
- DHCP Server
- Lease Obtained
- Lease Expires

### Step 2: View network configuration

```
Get-NetIPConfiguration
```

### Step 3: View network adapters

```
Get-NetAdapter
```

### Observation

Record the following:

|Property|Your Result|
|---|---|
|IPv4 Address||
|DHCP Enabled||
|DHCP Server||
|Default Gateway||
|Lease Obtained||
|Lease Expires||

Do not change your network configuration during this lab.

## 11. My Understanding

Write your own explanation:

- What is a static IP address?
- What is a dynamic IP address?
- What is DHCP?
- What does DORA stand for?
- What is a DHCP lease?
- What is a DHCP reservation?
- Can a private IP address be static?

## 12. Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[IPv6 Addressing]]
- [[Public and Private IP Addresses]]
- [[Subnetting]]
- [[DHCP Protocol]]
- [[MAC Address]]

---

**Key Takeaway:** Static and dynamic describe how an IP address is assigned. Public and private describe where an IP address can be used.