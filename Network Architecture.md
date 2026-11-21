> Understand how network components, protocols, services, and communication systems are organized to create a functioning network.

## 1. What Is Network Architecture?

Network architecture is the overall design and structure of a computer network.

It defines:

- How devices are connected.
- How data is transmitted.
- How network services operate.
- How communication is managed.
- How security and access control are implemented.

A network architecture provides a framework for building, operating, and maintaining networks.

## 2. Main Components of Network Architecture

|Component|Purpose|
|---|---|
|Clients|Request network services.|
|Servers|Provide network services.|
|Network devices|Connect devices and forward traffic.|
|Protocols|Define communication rules.|
|Transmission media|Carry network signals.|
|Network services|Provide functions such as DNS and DHCP.|
|Security controls|Protect network communication and resources.|

## 3. Client-Server Architecture

Client-server architecture uses dedicated servers to provide services to clients.

**Example:**

When you open a website:

1. Your browser acts as the client.
    
2. It sends a request to a web server.
    
3. The server processes the request.
    
4. The server sends a response.
    
5. Your browser displays the content.
    

**Advantages:**

- Centralized management.
    
- Easier data administration.
    
- Centralized access control.
    
- Suitable for large applications.
    

**Disadvantages:**

- Server failure can interrupt services.
    
- Requires server maintenance.
    
- Infrastructure can be expensive.
    

Related note: [[Client-Server Model]]

## 4. Peer-to-Peer Architecture

Peer-to-peer architecture allows devices to communicate and share resources directly.

Each participating device can act as both a client and a server.

**Example:** Two computers sharing files directly.

**Advantages:**

- No dedicated central server is required for every interaction.
    
- Can be inexpensive for small environments.
    
- Resources can be shared directly.
    

**Disadvantages:**

- Centralized management is limited.
    
- Security administration can be difficult.
    
- Availability depends on participating peers.
    

Related note: [[Peer-to-Peer Model]]

## 5. Centralized Architecture

In centralized architecture, important services and resources are managed through a central system.

**Example:** An organization using a central authentication server to manage employee access.

**Advantages:**

- Centralized administration.
    
- Consistent security policies.
    
- Easier monitoring.
    

**Disadvantages:**

- Central systems can become bottlenecks.
    
- A central failure can affect multiple users.
    
- Requires appropriate redundancy and backups.
    

## 6. Distributed Architecture

In distributed architecture, services and processing are spread across multiple interconnected systems.

**Examples:**

- Distributed databases.
    
- Cloud computing platforms.
    
- Content delivery networks.
    

**Advantages:**

- Can improve scalability.
    
- Can improve availability.
    
- Distributes workload.
    

**Disadvantages:**

- More complex management.
    
- Requires coordination between systems.
    
- Security must be maintained across multiple components.
    

## 7. Network Architecture Models

### Two-Tier Architecture

A two-tier architecture separates an application into two main parts:

1. Client or presentation layer.
    
2. Server or data-processing layer.
    

Example: A desktop application communicating directly with a database server.

### Three-Tier Architecture

A three-tier architecture separates an application into:

1. Presentation layer — User interface.
    
2. Application layer — Business logic.
    
3. Data layer — Database and storage.
    

Example:

A web browser communicates with an application server, which communicates with a database server.

**Advantages:**

- Better separation of responsibilities.
    
- Easier maintenance.
    
- Improved scalability.
    
- More flexible security controls.
    

## 8. Network Segmentation

Network segmentation divides a larger network into smaller logical or physical sections.

**Example:**

A college network may separate:

- Student network.
    
- Faculty network.
    
- Administration network.
    
- Server network.
    
- Guest Wi-Fi network.
    

**Benefits:**

- Limits unauthorized access.
    
- Reduces unnecessary traffic.
    
- Helps contain security incidents.
    
- Allows different security policies for different groups.
    

Related note: [[Network Segmentation]]

## 9. Network Architecture and Cybersecurity

Network architecture directly influences an organization's security.

Important design principles:

- Least privilege.
    
- Network segmentation.
    
- Defense in depth.
    
- Secure communication.
    
- Centralized monitoring.
    
- Redundancy and fault tolerance.
    
- Strong authentication and access control.
    

A poorly designed architecture can expose sensitive systems and make unauthorized lateral movement easier.

## 10. Practical Understanding

Consider a small office network.

Draw a diagram containing:

- Employee computers.
    
- Network switch.
    
- Router.
    
- Firewall.
    
- Application server.
    
- Database server.
    
- Internet connection.
    

Identify:

1. Which devices are clients?
    
2. Which devices provide services?
    
3. Where should the firewall be placed?
    
4. Which systems should be isolated?
    
5. How would you prevent guest devices from accessing internal servers?
    

## 11. What I Learned

Write your own explanations:

- What is network architecture?
    
- What is the difference between centralized and distributed architecture?
    
- How does client-server architecture work?
    
- What is a three-tier architecture?
    
- Why is network segmentation important?
    

## 12. Questions & Doubts

- Why do organizations use distributed systems?
    
- What happens if a central server fails?
    
- How does network architecture affect security?
    
- Why should guest networks be separated from internal networks?
    

## Related Notes

- [[Introduction to Computer Networking]]
    
- [[Types of Networks]]
    
- [[Network Topologies]]
    
- [[Network Devices]]
    
- [[Client-Server Model]]
    
- [[Peer-to-Peer Model]]
    
- [[Network Segmentation]]
    
- [[Network Security]]
    
- [[OSI Model]]