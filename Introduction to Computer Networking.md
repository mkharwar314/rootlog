> Learn how computers and other devices communicate and exchange information.

## 1. What Is Computer Networking?

A computer network is a collection of two or more connected devices that communicate and share resources.

These devices may include:

- Computers
- Smartphones
- Servers
- Routers
- Switches
- Printers
- IoT devices

**Example:** When your laptop connects to Wi-Fi and opens a website, it communicates with other devices and servers through a network.

## 2. Why Do We Need Computer Networks?

Computer networks allow devices to:

1. Share files and information.
2. Access the internet.
3. Communicate through email and messaging.
4. Share hardware such as printers.
5. Access centralized servers.
6. Exchange data between applications.

## 3. How Does a Network Work?

Consider opening a website from your computer.

A simplified communication process:

1. You enter a website address in your browser.
2. Your device uses DNS to find the server's IP address.
3. Your device establishes communication with the server.
4. Data travels through the network.
5. The server processes the request.
6. The server sends a response.
7. Your browser displays the website.

This communication involves several technologies, including IP, DNS, TCP or UDP, and HTTP or HTTPS.

We will study these individually in later notes.

## 4. Basic Components of a Network

|Component|Function|
|---|---|
|Client|Requests a service or resource.|
|Server|Provides services or resources.|
|Router|Connects different networks and forwards packets.|
|Switch|Connects devices within a local network.|
|Network Interface Card (NIC)|Allows a device to connect to a network.|
|Access Point|Provides wireless network connectivity.|
|Transmission Medium|Carries data between devices.|

## 5. Types of Computer Networks

### PAN — Personal Area Network

A small network around an individual.

Example: A smartphone connected to wireless earbuds using Bluetooth.

### LAN — Local Area Network

A network covering a limited geographical area.

Example: Computers connected within a college computer laboratory.

### WLAN — Wireless Local Area Network

A LAN that uses wireless communication, usually Wi-Fi.

Example: Your home Wi-Fi network.

### MAN — Metropolitan Area Network

A network covering a city or large metropolitan area.

### WAN — Wide Area Network

A network covering large geographical areas, potentially across countries or continents.

Example: The Internet.

## 6. Client-Server Communication

In the client-server model:

- The client requests a service.
- The server receives and processes the request.
- The server sends a response.

Example:

A browser is a client, and a website's hosting server provides the requested web content.

Related note: [[Client-Server Model]]

## 7. Peer-to-Peer Communication

In a peer-to-peer (P2P) network, devices can communicate and share resources directly without relying on a dedicated central server for every interaction.

Example: Two computers sharing files directly over a local network.

Related note: [[Peer-to-Peer Model]]

## 8. Network Communication Fundamentals

### Data

Information exchanged between devices.

Examples:

- Text
- Images
- Videos
- Documents
- Application requests

### Packets

Data is commonly divided into smaller units called packets before transmission across packet-switched networks.

Each packet contains information needed to deliver and process the data.

### Protocols

Protocols are agreed rules that define how devices communicate.

Examples:

|Protocol|Purpose|
|---|---|
|HTTP|Transfers web content.|
|HTTPS|Secure web communication.|
|TCP|Reliable, connection-oriented transport.|
|UDP|Connectionless transport.|
|IP|Provides addressing and packet forwarding.|
|DNS|Resolves domain names to IP addresses.|

## 9. Network Security Connection

Networking knowledge is essential for cybersecurity.

Security professionals use networking concepts to:

- Identify connected devices.
- Analyze network traffic.
- Detect suspicious communication.
- Discover exposed services.
- Investigate unauthorized access.
- Understand network-based attacks.
- Configure firewalls and security controls.

Tools such as Wireshark and Nmap help security professionals observe and analyze networks.

Only scan or test networks when you have authorization.

## 10. Practical Observation

On your Windows computer, open PowerShell.

Check your IP configuration:

```
ipconfig
```

Display detailed information:

```
ipconfig /all
```

Test connectivity:

```
ping 127.0.0.1
```

On Kali Linux, run:

```
ip addr
```

Display the routing table:

```
ip route
```

Test connectivity to your local network stack:

```
ping -c 4 127.0.0.1
```

Record the results.

## 11. What I Learned

Write your own explanation:

- What is a computer network?
- Why do devices communicate?
- What is the difference between LAN and WAN?
- What is the role of a router?
- What is the difference between a client and a server?
- Why is networking important in cybersecurity?

## 12. Questions & Doubts

- How does data travel across the Internet?
- How does a router know where to forward packets?
- What happens when two devices communicate?
- How are IP addresses assigned?

## Related Notes

- [[Types of Networks]]
- [[Network Topologies]]
- [[Network Devices]]
- [[Network Architecture]]
- [[Client-Server Model]]
- [[Peer-to-Peer Model]]
- [[OSI Model]]
- [[TCP-IP Model]]
- [[02 - Operating Systems]]

---