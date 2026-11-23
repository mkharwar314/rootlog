> Understand how computers communicate and share resources directly with one another without depending on a dedicated central server for every interaction.

## 1. What Is the Peer-to-Peer Model?

Peer-to-Peer (P2P) is a network architecture in which connected devices, called peers, can share resources and communicate directly.

A peer can act as both:

- A client when requesting resources.
- A server when providing resources.

Unlike a traditional client-server architecture, P2P systems do not necessarily depend on one central server to provide every service.

## 2. How P2P Communication Works

Consider two computers sharing files.

```
       COMPUTER A
       (Peer A)
           |
           | File Request
           |
           v
       COMPUTER B
       (Peer B)
           |
           | File Response
           |
           v
       COMPUTER A
```

In this example:

1. Computer A requests a file.
2. Computer B provides the file.
3. Data is transferred directly between the peers.

## 3. Characteristics of P2P Networks

- Peers can communicate directly.
- Each peer may provide and request resources.
- Resources can be distributed across multiple devices.
- Some P2P systems operate without a central server.
- Availability may depend on which peers are online.

Not every P2P system is completely decentralized. Some use central servers for discovery, coordination, or indexing.

## 4. Types of P2P Networks

### Pure P2P

A pure P2P network does not rely on a central server for its core peer communication or coordination.

Peers communicate and organize themselves in a distributed manner.

### Hybrid P2P

A hybrid P2P network combines peer-to-peer communication with centralized services.

A central server may help peers discover one another, while the actual data transfer happens directly between peers.

### Structured P2P

Peers follow an organized structure, often using a Distributed Hash Table (DHT), to locate resources efficiently.

### Unstructured P2P

Peers connect without following a strict global organization.

Resource discovery may use searches or queries across connected peers.

## 5. Examples of P2P Systems

|Example|Purpose|
|---|---|
|BitTorrent|Distributed file sharing|
|IPFS|Distributed content addressing and storage|
|Some blockchain networks|Distributed transaction and ledger communication|
|Direct local file sharing|Sharing files between computers|

A system may combine P2P and centralized components.

## 6. Advantages of P2P Networks

- Reduced dependence on dedicated central servers.
- Resources can be distributed among peers.
- Can scale by adding participating peers.
- Direct communication can reduce some infrastructure costs.
- No single central server is necessarily responsible for all data transfers.

## 7. Disadvantages of P2P Networks

- Security management can be difficult.
- Peers may disconnect unexpectedly.
- Resource availability can change.
- Malicious or untrusted peers may distribute harmful files.
- Centralized administration is limited in pure P2P designs.
- Data integrity and authenticity need careful verification.

## 8. Client-Server vs Peer-to-Peer

|Feature|Client-Server|Peer-to-Peer|
|---|---|---|
|Main architecture|Service provider and clients|Participating peers|
|Dedicated server|Commonly used|Not always required|
|Resource management|Usually centralized|Often distributed|
|Administration|Centralized|More distributed|
|Availability|Depends on server infrastructure|Depends on peer availability|
|Example|Website hosting|BitTorrent|

## 9. P2P and Cybersecurity

P2P networks introduce several security considerations.

### Common Risks

- Malicious file distribution.
- Malware disguised as legitimate files.
- Unauthorized file sharing.
- Exposure of private information.
- Untrusted peers.
- Insecure communication.

### Security Practices

- Download files only from trusted sources.
- Verify file hashes or digital signatures when available.
- Use updated security software.
- Avoid sharing sensitive files publicly.
- Restrict shared directories.
- Understand the permissions granted to sharing applications.

## 10. Practical Understanding

### Lab 1 — Identify Your Local Network

On Windows:

```
ipconfig
```

On Kali Linux:

```
ip addr
```

Identify the IP address of each device you own.

### Lab 2 — Test Local Connectivity

From one device, test connectivity to another device on your own network:

```
ping -c 4 <TARGET_IP>
```

Replace `<TARGET_IP>` with the other device's actual IP address.

On Windows, use:

```
ping <TARGET_IP>
```

A failed ping does not necessarily mean the device is offline; a firewall may block ICMP.

### Lab 3 — Understand Direct File Sharing

Research how BitTorrent distributes file pieces among multiple peers.

Record:

- What is a peer?
- What is a seed?
- What is a leecher?
- Why can multiple peers contribute to one download?

## 11. What I Learned

Write your own explanations:

- What is a peer-to-peer network?
- How can one device act as both a client and a server?
- What is the difference between pure and hybrid P2P?
- Why is P2P useful for distributed file sharing?
- What security risks exist in P2P systems?

## 12. Questions & Doubts

- How do peers discover one another?
- What is a Distributed Hash Table?
- How does BitTorrent divide files into pieces?
- Why can a P2P network continue operating without one central server?
- How can malicious files spread through P2P networks?

## Related Notes

- [[Introduction to Computer Networking]]
- [[Network Architecture]]
- [[Client-Server Model]]
- [[Network Topologies]]
- [[Network Devices]]
- [[Network Security]]
- [[Networking]]

---