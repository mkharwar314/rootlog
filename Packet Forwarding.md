# Packet Forwarding

> Follow what happens to a packet as it moves through a network.

## 1. Frame vs packet

At the network layer, IP packets carry source and destination IP addresses. On an Ethernet link, a packet is encapsulated inside a frame containing source and destination MAC addresses.

The IP packet is carried across links; the Layer 2 frame is rebuilt for each link.

## 2. Local vs remote destination

A host uses its subnet information to decide whether a destination is on the local network:
- **Local destination:** the host resolves the destination's link-layer address and sends directly.
- **Remote destination:** the host sends the frame to its default gateway.

For IPv4, ARP commonly resolves IPv4-to-MAC mappings. IPv6 uses Neighbor Discovery.

## 3. Router forwarding

A router examines the destination IP, selects a route, updates the TTL/Hop Limit, and forwards the packet in a new frame. If no usable route exists, it may drop the packet and send an ICMP error.

## 4. Encapsulation path

Application data is encapsulated by transport protocols such as TCP or UDP, then by IP, then by the link-layer protocol. At the receiver, the layers are processed in reverse order.

See [[Network Encapsulation]] and [[Network Decapsulation]].

## 5. Troubleshooting packet flow

Ask:
1. Is the source IP and subnet configuration correct?
2. Is the destination local or remote?
3. Is ARP/Neighbor Discovery working?
4. Is the default gateway reachable?
5. Does a route exist?
6. Are firewalls or ACLs dropping traffic?
7. Is the destination service listening?

## Key points

- IP addresses identify network-layer endpoints.
- MAC addresses deliver frames on a local link.
- Routers forward packets; switches forward frames in a Layer 2 network.

## Related notes
- [[Introduction to Routing]]
- [[Introduction to Switching]]
- [[ARP Protocol]]
- [[Default Gateway]]
