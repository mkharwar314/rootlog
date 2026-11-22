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

## 6. Routing decision example

Imagine a host at `192.168.1.20/24` needs to reach `192.168.1.50`. The destination is in the same `/24` network, so the host sends directly on the local link after resolving the destination MAC address.

If the same host needs to reach `8.8.8.8`, that address is outside the local `/24`. The host sends the Ethernet frame to its default gateway, while the IP packet is addressed to `8.8.8.8`. The router then makes its own routing decision.

## 7. Longest-prefix match

Suppose a routing table contains `10.0.0.0/8` and `10.10.0.0/16`. A packet destined for `10.10.5.4` matches both routes, but `/16` is more specific than `/8`, so it is selected. This is called longest-prefix match.

## 8. Routing versus NAT

Routing selects where a packet should go. NAT changes address and sometimes port information as traffic crosses a translation boundary. They may occur on the same device, but they are separate functions.

## Practical activity

Run `ip route` in Kali or `route print` in Windows. Identify the default route and explain where a packet to an external destination would be sent.

## My understanding

Draw a two-LAN topology connected by a router. Label each subnet, interface address, and default gateway. Trace one packet from a host in the first LAN to a host in the second.
