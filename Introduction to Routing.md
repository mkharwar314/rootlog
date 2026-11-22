# Introduction to Routing

> Understand how routers move packets between different IP networks.

## 1. What is routing?

**Routing** is the process of selecting a path for packets to travel from a source network toward a destination network. A router examines the destination IP address and consults its routing table to choose a next hop or outgoing interface.

Switching generally forwards frames within a local network; routing forwards IP packets between networks.

## 2. How a router forwards a packet

1. A router receives a frame.
2. It removes the Layer 2 framing and examines the destination IP address.
3. It looks for the best matching route.
4. It decrements the IPv4 TTL or IPv6 Hop Limit.
5. It forwards the packet in a new Layer 2 frame, if a route is available.

The Layer 2 source and destination addresses are rewritten for each routed link. The end-to-end IP addresses usually remain the same, except where mechanisms such as NAT modify them.

## 3. Default gateway

A host sends traffic for remote networks to its configured default gateway when no more specific route applies. See [[Default Gateway]].

## 4. Routing concepts

- **Next hop:** the next router toward the destination.
- **Outgoing interface:** interface used to forward the packet.
- **Metric:** value used to compare routes within a routing protocol or routing process.
- **Longest-prefix match:** the most specific matching route is preferred.
- **Default route:** route used when no more specific route matches.

## 5. Safe practical inspection

Windows:

```powershell
route print
Get-NetRoute
```

Linux:

```bash
ip route
ip -6 route
```

Identify the default route, destination prefix, gateway, and interface.

## Key points

- Routers connect IP networks.
- Routing decisions are based on destination prefixes and routing tables.
- Longest-prefix match selects the most specific matching route.

## Related notes
- [[Routing Tables]]
- [[Static and Dynamic Routing]]
- [[Default Gateway]]
- [[Packet Forwarding]]
