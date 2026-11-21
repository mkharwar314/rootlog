## 1. Introduction

A default gateway is a network device that forwards traffic from a local network to other networks when no more specific route is available.

In most home and small office networks, the default gateway is the router.

Example:

```
Computer IP:     192.168.1.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

Here, `192.168.1.1` is the router's local IP address.

## 2. Why Is a Default Gateway Needed?

Devices on the same local subnet can generally communicate directly.

However, when a device needs to communicate with an IP address outside its local subnet, it sends the traffic to its default gateway.

The gateway then forwards the traffic toward the destination using its routing table.

Without a valid route or gateway, a device may be unable to reach external networks.

## 3. How Does a Default Gateway Work?

Consider this example:

```
Computer A: 192.168.1.10
Router:     192.168.1.1
Server:     8.8.8.8
```

When Computer A communicates with `8.8.8.8`:

1. Computer A checks whether the destination belongs to its local subnet.
2. It determines that `8.8.8.8` is outside its local subnet.
3. It sends the packet to the default gateway.
4. The router checks its routing table.
5. The router forwards the packet toward the destination.

The response traffic returns through the appropriate network route.

## 4. Default Gateway and MAC Address

On an Ethernet network, a device needs the gateway's MAC address to send an Ethernet frame to it.

If the gateway's MAC address is not already known, the device can use ARP to discover it.

Example:

```
Destination IP:       8.8.8.8
Next-Hop IP:          192.168.1.1
Destination MAC:      Router's MAC address
```

Important distinction:

- The IP packet is addressed to the final destination.
- The Ethernet frame is addressed to the next-hop router.

The router removes the incoming Layer 2 frame and forwards the IP packet using a new Layer 2 frame on the next network.

## 5. Default Gateway vs Router

|Default Gateway|Router|
|---|---|
|A next-hop address used by a device|A network device that forwards packets|
|Usually configured as an IP address|Has network interfaces and routing functions|
|Provides a path to other networks|Determines where packets should go|
|Can refer to a router or another Layer 3 device|Performs routing between networks|

A router commonly acts as the default gateway for devices on a local network.

## 6. Default Gateway and Subnet Mask

The subnet mask helps a device determine whether a destination is local or remote.

Example:

```
IP Address:      192.168.1.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

For this configuration:

- `192.168.1.20` is on the same subnet.
- `192.168.2.20` is outside the subnet.
- Traffic for `192.168.2.20` is normally sent through the default gateway, assuming no more specific route exists.

## 7. Default Gateway in Cybersecurity

Default gateways are important in network security because they connect local networks to other networks.

Security considerations include:

### Unauthorized Gateway Changes

An attacker may attempt to change a device's gateway configuration to redirect traffic.

### Rogue Router

An unauthorized router may provide an unintended path for network communication.

### Traffic Monitoring

Network administrators can monitor traffic passing through gateways to identify suspicious activity.

### Firewall Configuration

Routers and gateway devices may enforce firewall rules to control incoming and outgoing traffic.

## 8. Practical Lab — Windows PowerShell

### Step 1: View your network configuration

```
ipconfig
```

Find the `Default Gateway` entry under your active adapter.

### Step 2: View detailed network information

```
ipconfig /all
```

### Step 3: Use PowerShell

```
Get-NetIPConfiguration
```

### Step 4: View your routing table

```
route print -4
```

Look for the default route:

```
Network Destination: 0.0.0.0
Netmask:              0.0.0.0
Gateway:              Your gateway IP
```

The `0.0.0.0/0` route is the IPv4 default route.

## 9. Troubleshooting

If you cannot access external networks, check:

- Is the network adapter connected?
- Does the computer have a valid IP address?
- Is the subnet mask correct?
- Is the default gateway configured?
- Can you reach the gateway?
- Is the router connected to the internet?

You can test gateway connectivity using:

```
ping 192.168.1.1
```

Replace the example address with your actual gateway address.

A failed ping does not always mean the gateway is unavailable because ICMP traffic may be blocked.

## 10. My Understanding

Write your own explanation:

- What is a default gateway?
- Why do devices need a default gateway?
- What happens when a device communicates outside its subnet?
- What is the relationship between a router and a default gateway?
- What is the difference between a destination IP and a next-hop IP?

## 11. Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[Subnetting]]
- [[Subnet Masks]]
- [[MAC Address]]
- [[ARP Protocol]]
- [[Routing Tables]]
- [[NAT]]

---

**Key Takeaway:** A default gateway provides the next hop for traffic that must leave the local network.