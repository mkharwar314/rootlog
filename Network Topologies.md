> Understand how devices and connections are arranged within a computer network.

## 1. What Is Network Topology?

Network topology describes the physical or logical arrangement of devices and communication links in a network.

It explains how devices are connected and how data moves between them.

There are two main categories:

- **Physical topology:** The actual physical arrangement of cables, devices, and connections.
- **Logical topology:** How data flows between devices, regardless of their physical arrangement.


## 2. Bus Topology

In bus topology, all devices connect to one shared communication cable called the backbone.

**Structure:**

```
PC1      PC2      PC3      PC4
 |        |        |        |
================================
          Backbone
```

**Advantages:**

- Simple structure.
- Requires less cable than some other topologies.
- Relatively inexpensive for small networks.

**Disadvantages:**

- Backbone failure can disrupt the entire network.
- Performance can decrease as traffic increases.
- Troubleshooting can be difficult.

## 3. Star Topology

In star topology, every device connects to a central device, usually a switch or access point.

**Structure:**

```
          PC1
           |
PC2 ---- Switch ---- PC3
           |
          PC4
```

**Advantages:**

- Easy to manage.
- Failure of one connected cable usually affects only that device.
- Easy to add or remove devices.
- Fault isolation is relatively simple.

**Disadvantages:**

- Central device failure can disrupt the connected network.
- Requires more cable than bus topology.

**Real-world example:** Most modern wired Ethernet LANs use a physical star or extended-star arrangement.

## 4. Ring Topology

In ring topology, devices connect in a circular arrangement.

**Structure:**

```
PC1 ------ PC2
 |          |
 |          |
PC4 ------ PC3
```

**Advantages:**

- Can provide predictable access to the communication medium in some implementations.
- Certain ring technologies support controlled data transmission.

**Disadvantages:**

- A link or device failure can disrupt a basic ring.
- Changes and troubleshooting can be difficult.

Some ring technologies use dual rings or protection mechanisms to improve reliability.

## 5. Mesh Topology

In mesh topology, devices have multiple interconnections.

Two common forms:

- **Full mesh:** Every device connects directly to every other device.
- **Partial mesh:** Only selected devices have multiple direct connections.

**Full mesh example:**

```
       A -------- B
       |\        /|
       | \      / |
       |  \    /  |
       |   \  /   |
       |    \/    |
       |    /\    |
       |   /  \   |
       |  /    \  |
       | /      \ |
       |/        \|
       C -------- D
```

**Advantages:**

- Multiple communication paths.
- High redundancy.
- Can improve fault tolerance.

**Disadvantages:**

- Expensive to implement.
- Requires more connections.
- More complex to manage.

## 6. Tree Topology

Tree topology organizes devices in a hierarchical structure.

**Structure:**

```
             Core Switch
             /         \
       Switch A       Switch B
        /   \          /   \
      PC1   PC2      PC3   PC4
```

**Advantages:**

- Suitable for larger networks.
- Supports hierarchical management.
- Easy to expand by adding branches.

**Disadvantages:**

- Failure of an important upper-level device can affect multiple branches.
- Requires careful planning and configuration.

## 7. Hybrid Topology

Hybrid topology combines two or more different topology types.

Example:

An organization may use star topology inside each office while connecting multiple offices through a partially meshed WAN.

**Advantages:**

- Flexible design.
- Can support different organizational requirements.
- Scalable.

**Disadvantages:**

- More complex to design.
- Can be expensive.
- Requires careful management.

## 8. Topology Comparison

|Topology|Main Structure|Major Advantage|Major Disadvantage|
|---|---|---|---|
|Bus|Shared backbone|Simple design|Backbone failure|
|Star|Central device|Easy management|Central device dependency|
|Ring|Circular connection|Predictable access in some designs|Link failure risk|
|Mesh|Multiple paths|Redundancy|High cost|
|Tree|Hierarchical|Scalable|Upper-level dependency|
|Hybrid|Combined structures|Flexible|Complex design|

## 9. Network Topology and Cybersecurity

Topology affects network security because it determines how devices communicate and where security controls can be placed.

Examples:

- Network segmentation can isolate sensitive systems.
- Redundant paths can improve availability.
- Poorly designed networks can allow unauthorized lateral movement.
- Central switches and routers are important monitoring and control points.
- Firewalls can separate networks with different security requirements.

## 10. Practical Understanding

Observe your home network.

1. Identify your Wi-Fi router.
2. List devices connected to it.
3. Check whether any devices use Ethernet cables.
4. Draw a simple network diagram.
5. Identify which device acts as the central connection point.

Remember: A typical home network may have a star-like logical structure, but its actual physical and logical topology can differ.

## 11. What I Learned

Write your own explanations:

- What is network topology?
- What is the difference between physical and logical topology?
- Why is star topology common in Ethernet LANs?
- What makes mesh topology fault-tolerant?
- Why do large organizations use hybrid topology?

## 12. Questions & Doubts

- What happens if a central switch fails?
- How does network redundancy improve availability?
- Can a network use multiple topology types?
- How does topology influence network segmentation?

## Related Notes

- [[Introduction to Computer Networking]]
- [[Types of Networks]]
- [[Network Devices]]
- [[Network Architecture]]
- [[Switching]]
- [[Routing]]
- [[Network Segmentation]]
- [[Network Security]]

---