# Introduction to Switching

> Understand how Ethernet switches connect devices inside a local area network.

## 1. What is a network switch?

A network switch connects devices in a LAN and forwards Ethernet frames based on destination MAC addresses. A typical Layer 2 switch learns which MAC addresses are reachable through each port.

## 2. MAC address learning

A switch:
1. Receives a frame on a port.
2. Learns the source MAC address and associates it with the incoming port and VLAN.
3. Looks up the destination MAC address.
4. Forwards the frame to the known port, floods unknown unicast traffic within the VLAN, or handles broadcast traffic according to Ethernet rules.

Switches maintain a MAC address table, also called a forwarding database.

## 3. Collision domains and broadcast domains

Each full-duplex switch port is its own collision domain. A VLAN typically defines a separate Layer 2 broadcast domain. Routers or Layer 3 switches are used to route traffic between VLANs.

## 4. Switch vs router

| Switch | Router |
|---|---|
| Commonly forwards using MAC addresses | Forwards using IP routes |
| Connects devices within LAN/VLANs | Connects different IP networks |
| Layer 2 in a basic Ethernet design | Layer 3 |

Modern switches may also provide Layer 3 routing.

## 5. Security considerations

Risks include MAC flooding, rogue devices, VLAN misconfiguration, and unauthorized access to switch management. Defences include port security, 802.1X, unused-port shutdown, secure management, VLAN design, and firmware updates.

## Key points

- A Layer 2 switch forwards frames using MAC addresses.
- Switches learn source MAC addresses.
- VLANs separate Layer 2 broadcast domains.

## Related notes
- [[Network Devices]]
- [[VLAN]]
- [[MAC Address]]
- [[Network Segmentation]]
