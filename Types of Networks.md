> Understand how computer networks are classified according to their geographical coverage, purpose, and communication technology.

## 1. Introduction

Computer networks can be classified based on:

- Geographical coverage.
- Number of connected devices.
- Network ownership.
- Communication technology.
- Purpose of the network.

The most common network types are PAN, LAN, WLAN, MAN, and WAN.

## 2. PAN — Personal Area Network

A Personal Area Network connects devices around an individual over a short distance.

**Examples:**

- Smartphone connected to Bluetooth earbuds.
- Laptop connected to a wireless mouse.
- Smartphone sharing files with another device.

**Characteristics:**

- Short communication range.
- Usually connects personal devices.
- Can use Bluetooth, USB, or other short-range technologies.

**Cybersecurity relevance:** Unauthorized Bluetooth connections and insecure pairing can expose personal devices to security risks.

## 3. LAN — Local Area Network

A Local Area Network connects devices within a limited geographical area.

**Examples:**

- College computer laboratory.
- Office network.
- Home Ethernet network.

**Characteristics:**

- Covers a limited area.
- Usually managed by one organization or individual.
- Commonly uses Ethernet switches and routers.
- Supports high-speed local communication.

**Cybersecurity relevance:** Poor access control, insecure devices, and misconfigured network services can expose a LAN to unauthorized access.

## 4. WLAN — Wireless Local Area Network

A Wireless Local Area Network is a LAN that uses wireless communication, typically Wi-Fi.

**Examples:**

- Home Wi-Fi.
- College wireless network.
- Office Wi-Fi.

**Characteristics:**

- Allows devices to connect without Ethernet cables.
- Uses wireless access points.
- Commonly follows IEEE 802.11 standards.

**Cybersecurity relevance:**

- Weak Wi-Fi passwords can allow unauthorized access.
- Outdated encryption can expose wireless communication.
- Rogue access points can trick users into connecting to malicious networks.

## 5. MAN — Metropolitan Area Network

A Metropolitan Area Network connects networks across a city or metropolitan region.

**Examples:**

- A university connecting multiple campuses across a city.
- A city's interconnected institutional network.

**Characteristics:**

- Larger coverage than a LAN.
- Smaller geographical scope than a typical WAN.
- May connect multiple LANs.

**Cybersecurity relevance:** Multiple connected locations increase the importance of centralized monitoring, access control, and secure communication links.

## 6. WAN — Wide Area Network

A Wide Area Network connects devices and smaller networks across large geographical areas.

**Examples:**

- A company connecting offices in different countries.
- Networks connecting branches across India.
- The Internet.

**Characteristics:**

- Covers large geographical areas.
- Connects multiple LANs and other networks.
- May use leased lines, fiber-optic links, satellite links, and other technologies.

**Cybersecurity relevance:**

- Secure communication between locations is important.
- VPNs can protect traffic across untrusted networks.
- Firewalls and network monitoring help manage security risks.

## 7. Comparison of Network Types

|Network|Full Form|Coverage|Example|
|---|---|---|---|
|PAN|Personal Area Network|Around an individual|Bluetooth devices|
|LAN|Local Area Network|Home, office, building|College lab|
|WLAN|Wireless Local Area Network|Wireless local coverage|Wi-Fi|
|MAN|Metropolitan Area Network|City or metropolitan region|City-wide network|
|WAN|Wide Area Network|Large geographical area|Internet|

Note: WLAN is a wireless form of LAN, rather than a separate geographical scale.

## 8. Real-World Example

Consider a college with three buildings.

- Computers inside one laboratory communicate through a LAN.
- Students connect through Wi-Fi using a WLAN.
- Different college campuses across the city may be connected through a MAN.
- The college connects to external websites through an Internet service provider and the wider WAN infrastructure.

## 9. Practical Understanding

Think about your own home network.

Identify:

1. Devices connected to your Wi-Fi.
2. Whether devices use Ethernet or wireless connections.
3. The router connecting your devices to the Internet.
4. Whether Bluetooth devices form a PAN.

On Windows, inspect network interfaces:

```
ipconfig /all
```

On Kali Linux:

```
ip link
```

These commands help identify network interfaces, but they do not independently determine the geographical network type.

## 10. What I Learned

Write your own explanations:

- What is PAN?
- What is the difference between LAN and WAN?
- How is WLAN related to LAN?
- Why do organizations use MAN?
- Why is network classification useful in cybersecurity?

## 11. Questions & Doubts

- Can multiple LANs form a WAN?
- Can a home network contain both wired and wireless devices?
- Why is the Internet considered a network of networks?
- What security controls are important for a WAN?

## Related Notes

- [[Introduction to Computer Networking]]
- [[Network Topologies]]
- [[Network Devices]]
- [[Network Architecture]]
- [[OSI Model]]
- [[Network Security]]
- [[Networking]]

---