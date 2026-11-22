## 1. Introduction

ARP stands for **Address Resolution Protocol**.

It is used in IPv4 local networks to discover the MAC address associated with a known IPv4 address.

In simple terms:

- IP address identifies the destination logically.
- MAC address is used to deliver an Ethernet frame on the local network.
- ARP helps discover the MAC address needed for local delivery.

Example:

```
IP Address:  192.168.1.20
MAC Address: BB:BB:BB:BB:BB:BB
```

ARP helps a device discover that mapping.

## 2. Why Is ARP Needed?

Devices communicate using IP addresses, but Ethernet frames are delivered using MAC addresses.

Before sending an Ethernet frame to another device on the same local network, a computer may need to discover the destination's MAC address.

ARP provides this address-resolution mechanism.

## 3. How ARP Works

Consider two devices on the same local network:

```
Computer A
IP: 192.168.1.10
MAC: AA:AA:AA:AA:AA:AA

Computer B
IP: 192.168.1.20
MAC: BB:BB:BB:BB:BB:BB
```

Computer A wants to communicate with Computer B.

### Step 1: Check ARP Cache

Computer A checks whether it already knows the MAC address associated with `192.168.1.20`.

### Step 2: ARP Request

If the mapping is unknown, Computer A broadcasts an ARP request:

```
Who has 192.168.1.20?
Tell 192.168.1.10
```

The request is sent to the Ethernet broadcast MAC address:

```
FF:FF:FF:FF:FF:FF
```

### Step 3: ARP Reply

Computer B recognizes its IP address and responds with its MAC address:

```
192.168.1.20 is at BB:BB:BB:BB:BB:BB
```

### Step 4: Update ARP Cache

Computer A stores the mapping temporarily in its ARP cache.

### Step 5: Send Data

Computer A can now send an Ethernet frame addressed to Computer B's MAC address.

## 4. ARP Request vs ARP Reply

|ARP Request|ARP Reply|
|---|---|
|Usually broadcast|Usually unicast|
|Asks for a MAC address|Provides the MAC address|
|Sent by the device needing the mapping|Sent by the device owning the requested IP|

## 5. ARP Cache

An ARP cache stores recently learned IP-to-MAC address mappings.

This prevents devices from broadcasting an ARP request every time they communicate with a known local device.

Example:

```
192.168.1.1    AA-BB-CC-DD-EE-FF
192.168.1.20   11-22-33-44-55-66
```

ARP entries can be dynamic or static.

- **Dynamic entries:** Learned automatically through ARP.
- **Static entries:** Configured manually and retained according to the operating system's behavior.

## 6. ARP and the OSI Model

ARP operates between the Internet Layer and Link Layer functions in the TCP/IP model.

In the traditional OSI model, it is commonly associated with the boundary between:

- Layer 2 — Data Link
- Layer 3 — Network

ARP is not itself an IP packet. In Ethernet, it is carried directly inside an Ethernet frame.

## 7. ARP and Default Gateway

ARP is also used when a device needs to send traffic outside its local subnet.

Example:

```
Computer IP:     192.168.1.10
Default Gateway: 192.168.1.1
Remote Server:   8.8.8.8
```

The computer does not use ARP to discover the MAC address of `8.8.8.8`.

Instead:

1. It determines that `8.8.8.8` is outside its local subnet.
2. It identifies `192.168.1.1` as the next hop.
3. It uses ARP to discover the gateway's MAC address if necessary.
4. It sends the Ethernet frame to the gateway.

The IP packet still has `8.8.8.8` as its destination.

## 8. ARP Security Risks

ARP does not provide authentication for IP-to-MAC mappings.

This creates opportunities for attacks.

### ARP Spoofing

An attacker sends forged ARP messages to associate their MAC address with another device's IP address.

### ARP Poisoning

An attacker corrupts devices' ARP caches with false mappings.

### Man-in-the-Middle Attack

If successful, an attacker may position their device between two communicating systems and potentially intercept or modify traffic.

### Protection Measures

- Use Dynamic ARP Inspection on supported managed switches.
- Apply DHCP snooping where appropriate as a foundation for inspection.
- Use network segmentation.
- Monitor unusual ARP activity.
- Use encryption such as HTTPS and SSH to protect application traffic.

## 9. ARP vs DNS

These protocols perform different functions.

|ARP|DNS|
|---|---|
|Resolves IPv4 addresses to MAC addresses|Resolves domain names to IP addresses|
|Used on local IPv4 networks|Used across IP networks|
|Works with local link delivery|Helps applications locate network services|
|Example: IP to MAC|Example: example.com to IP|

## 10. Practical Lab — Windows PowerShell

### Step 1: View the ARP cache

```
arp -a
```

Observe the Internet Address and Physical Address columns.

### Step 2: View ARP information using PowerShell

```
Get-NetNeighbor -AddressFamily IPv4
```

### Step 3: View your default gateway

```
Get-NetIPConfiguration
```

### Step 4: Generate local network traffic

Ping your actual default gateway:

```
ping YOUR_GATEWAY_IP
```

Replace `YOUR_GATEWAY_IP` with the gateway address shown by your computer.

Then inspect the ARP cache again:

```
arp -a
```

You may see the gateway's IP-to-MAC mapping.

Note: A cached entry may already exist, and a failed ping does not necessarily mean ARP failed because ICMP may be blocked.

## 11. Practical Observation

Record your observations:

|Property|Your Result|
|---|---|
|Default Gateway IP||
|Gateway MAC Address||
|ARP Entry Type||
|Other Local Devices Found||

Do not publish your actual network details unnecessarily.

## 12. My Understanding

Write your own explanation:

- What is ARP?
- Why is ARP required in IPv4 Ethernet networks?
- What is an ARP request?
- What is an ARP reply?
- What is an ARP cache?
- What is ARP spoofing?
- How does ARP help a computer reach its default gateway?

## 13. Related Notes

- [[Introduction to IP Addressing]]
- [[IPv4 Addressing]]
- [[MAC Address]]
- [[Default Gateway]]
- [[Subnet Masks]]
- [[Network Devices]]
- [[Network Security]]
- [[Wireshark]]

---

**Key Takeaway:** ARP discovers the MAC address associated with a local IPv4 next hop, allowing Ethernet frames to reach the correct device.