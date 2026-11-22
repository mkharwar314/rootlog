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

## 6. Unknown unicast and broadcast handling

If a switch does not know the destination MAC address, it normally floods the frame out eligible ports in the same VLAN, except the port on which it arrived. Broadcast frames are also flooded within the VLAN. This is one reason VLAN boundaries matter: they limit the scope of Layer 2 broadcasts.

## 7. MAC address table behaviour

A switch learns from the source MAC address of incoming frames. Entries can age out after a period of inactivity. If a device moves to another port, the switch can relearn the address from the new source traffic.

## 8. Security implications

MAC flooding attempts to overwhelm a switch's MAC table. Port security can limit the number of learned MAC addresses on an access port. 802.1X can require device or user authentication before normal network access is granted.

## Practical activity

On a managed lab switch, inspect the MAC address table and identify which port has learned a test device. If you do not have a managed switch, draw the learning process for two hosts communicating through a switch.

## My understanding

Explain what a switch does when it knows the destination MAC address and what it does when the destination is unknown.
