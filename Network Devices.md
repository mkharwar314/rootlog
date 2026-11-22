> Understand the hardware devices that connect networks, forward data, and enable communication between computers.

## 1. What Are Network Devices?

Network devices are hardware components used to connect computers and other devices so they can communicate and exchange data.

They perform different functions, such as:

- Connecting devices.
- Forwarding data.
- Managing network traffic.
- Connecting different networks.
- Providing wireless connectivity.
- Protecting network communication.

## 2. Network Interface Card (NIC)

A Network Interface Card (NIC) allows a computer or device to connect to a network.

Types:

- Ethernet NIC — Wired network connection.
- Wireless NIC — Wi-Fi connection.

**Functions:**

- Provides network connectivity.
- Uses a MAC address for link-layer identification.
- Sends and receives network frames.

**Example:** Your laptop's Wi-Fi adapter is a wireless NIC.

**Cybersecurity relevance:** Network interfaces are important when inspecting connected devices and analyzing network traffic.

## 3. Hub

A hub connects multiple devices within a LAN.

When a hub receives data on one port, it repeats the signal to its other ports.

**Characteristics:**

- Operates at OSI Layer 1 (Physical Layer).
- Does not intelligently filter traffic based on MAC addresses.
- Creates one shared collision domain in traditional Ethernet networks.

**Disadvantages:**

- Sends traffic to all other ports.
- Creates unnecessary traffic.
- Less efficient than a switch.

Hubs are largely obsolete in modern Ethernet networks.

## 4. Switch

A switch connects devices within a LAN and forwards Ethernet frames based on MAC addresses.

**Functions:**

- Learns MAC addresses.
- Maintains a MAC address table.
- Forwards frames toward the appropriate destination port.
- Reduces unnecessary traffic compared with a hub.

**Example:** Computers in a college laboratory connected through an Ethernet switch.

**OSI Layer:** A traditional Ethernet switch primarily operates at Layer 2 (Data Link Layer).

Some multilayer switches can also perform Layer 3 routing.

**Cybersecurity relevance:**

- VLANs can separate network segments.
- Port security can restrict device connections.
- Monitoring switch traffic can help investigate suspicious activity.

## 5. Router

A router connects different IP networks and forwards packets between them.

**Functions:**

- Examines destination IP addresses.
- Uses a routing table to select a next hop or outgoing interface.
- Connects local networks to external networks.
- Can provide NAT and basic firewall features.

**Example:** Your home router connects your home LAN to your Internet Service Provider.

**OSI Layer:** Layer 3 (Network Layer).

**Cybersecurity relevance:**

- Controls communication between networks.
- Can enforce traffic-filtering rules.
- Helps isolate network segments.

## 6. Modem

A modem provides communication between a local network and an Internet Service Provider's access infrastructure.

The term comes from _modulator-demodulator_.

Its exact operation depends on the access technology.

Examples:

- Cable modem.
- DSL modem.
- Cellular modem.

A modem and a router perform different functions, although many home devices combine both.

## 7. Wireless Access Point (AP)

A wireless access point allows wireless devices to connect to a wired network using Wi-Fi.

**Functions:**

- Provides wireless connectivity.
- Connects wireless clients to the LAN.
- Manages wireless communication.

**Example:** A college Wi-Fi access point.

**Cybersecurity relevance:**

- Uses wireless authentication and encryption.
- Should use strong security configurations.
- Rogue access points can create security risks.

## 8. Repeater

A repeater regenerates or retransmits signals to extend communication distance.

**Functions:**

- Extends network coverage.
- Helps overcome signal attenuation.
- Does not normally make forwarding decisions based on IP addresses.

A Wi-Fi range extender is a common consumer example, although its implementation may include additional networking functions.

## 9. Bridge

A bridge connects network segments and forwards frames based on MAC addresses.

**Functions:**

- Connects LAN segments.
- Learns MAC addresses.
- Filters frames between segments.

A traditional bridge operates at Layer 2.

Modern switches perform similar functions and are more commonly used.

## 10. Gateway

A gateway connects networks or systems that may use different communication methods or protocols.

In everyday IP networking, the **default gateway** is usually the router or Layer 3 device that forwards traffic from a local network to other networks.

Example:

When your laptop sends traffic to an external Internet address, it generally forwards the packet to its default gateway.

A gateway can also translate between different protocols or application systems.

## 11. Firewall

A firewall monitors and controls network traffic according to configured security rules.

Types include:

- Hardware firewall.
- Software firewall.
- Network firewall.
- Host-based firewall.

**Functions:**

- Allows permitted traffic.
- Blocks prohibited traffic.
- Applies security policies.
- Helps protect systems from unauthorized network access.

**Cybersecurity relevance:** Firewalls are important security controls for protecting hosts and networks.

## 12. Network Device Comparison

|Device|Main Function|Typical OSI Layer|
|---|---|---|
|NIC|Connects a device to a network|Layer 1 and 2|
|Hub|Repeats signals|Layer 1|
|Switch|Forwards frames using MAC addresses|Layer 2|
|Router|Forwards packets between networks|Layer 3|
|Modem|Connects through ISP access technology|Depends on technology|
|Access Point|Provides Wi-Fi connectivity|Primarily Layer 2|
|Repeater|Regenerates signals|Layer 1|
|Bridge|Connects LAN segments|Layer 2|
|Gateway|Connects or translates between systems|Depends on function|
|Firewall|Controls traffic using security rules|Depends on implementation|

## 13. Practical Observation

On Windows, inspect your network configuration:

```
ipconfig /all
```

Look for:

- Network adapter name.
- Physical Address (MAC address).
- IPv4 Address.
- Default Gateway.

On Kali Linux:

```
ip link
```

Display IP addresses:

```
ip addr
```

Display the routing table:

```
ip route
```

Find your default gateway.

You can also inspect your home router's connected-device list through its administration interface, if you have permission.

## 14. What I Learned

Write your own explanations:

- What is the difference between a hub and a switch?
- Why does a router use IP addresses?
- What is the purpose of a NIC?
- How is an access point different from a router?
- What is a default gateway?
- Why is a firewall important?

## 15. Questions & Doubts

- How does a switch learn MAC addresses?
- How does a router select a route?
- Can a router and modem exist in one device?
- What is the difference between a bridge and a switch?
- How does a firewall inspect network traffic?

## Related Notes

- [[Introduction to Computer Networking]]
- [[Types of Networks]]
- [[Network Topologies]]
- [[Network Architecture]]
- [[OSI Model]]
- [[MAC Address]]
- [[ARP Protocol]]
- [[Routing]]
- [[Switching]]
- [[Firewalls]]
- [[Network Security]]

---