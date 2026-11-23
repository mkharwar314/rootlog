> Network security is the practice of protecting network infrastructure, connected devices, communication channels, and transmitted data from unauthorized access, misuse, modification, and disruption.

## 1. Introduction to Network Security

Network security focuses on protecting how computers and devices communicate with each other.

A network may contain:

- Computers and laptops
    
- Servers
    
- Routers and switches
    
- Wireless access points
    
- Firewalls
    
- Internet-connected devices
    
- Applications and network services
    

Every connected device and communication channel can introduce security risks.

### Main Goals

1. **Confidentiality:** Prevent unauthorized individuals from accessing network information.
    
2. **Integrity:** Prevent unauthorized modification of transmitted or stored data.
    
3. **Availability:** Ensure network services remain accessible to authorized users.
    

These goals are part of the [[CIA Triad]].

## 2. Common Network Security Threats

### 2.1 Unauthorized Access

Occurs when someone accesses a network, device, or service without permission.

Examples:

- Accessing a router using stolen credentials.
    
- Connecting an unauthorized device to an internal network.
    
- Using weak passwords to gain access.
    

### 2.2 Packet Sniffing

Packet sniffing involves capturing and examining network traffic.

It can be legitimate when used by administrators for troubleshooting and security monitoring.

It becomes a security threat when attackers capture sensitive information without authorization.

### 2.3 IP and MAC Spoofing

- **IP spoofing:** Modifying packet source IP information to make traffic appear to originate from another address.
    
- **MAC spoofing:** Changing a device's MAC address to impersonate another device.
    

Spoofing can support other attacks, but changing an address alone does not automatically grant access.

### 2.4 Man-in-the-Middle (MITM)

An attacker positions themselves between two communicating parties and attempts to intercept or modify their communication.

Possible consequences:

- Credential theft
    
- Data interception
    
- Communication manipulation
    

Encryption and proper certificate validation help reduce this risk.

### 2.5 Denial of Service (DoS)

A DoS attack attempts to make a service unavailable by overwhelming or exhausting its resources.

A Distributed Denial of Service (DDoS) attack uses multiple sources to generate the traffic.

### 2.6 Malware Propagation

Malware can spread through networks by exploiting vulnerable systems, shared resources, or compromised credentials.

Examples include worms and ransomware.

### 2.7 Rogue Devices

A rogue device is an unauthorized device connected to an organization's network.

It may create an entry point for attackers or expose sensitive information.

### 2.8 Network Misconfiguration

Incorrect network settings can expose systems to unnecessary risks.

Examples:

- Open ports that are not required.
    
- Weak wireless security.
    
- Incorrect firewall rules.
    
- Unprotected administrative interfaces.
    

## 3. Network Security Architecture

Network security architecture describes how security controls are arranged to protect a network.

A strong architecture uses multiple layers of protection.

### Defense in Depth

Defense in Depth means applying multiple independent security controls rather than relying on one security mechanism.

Example:

1. Firewall controls incoming and outgoing traffic.
    
2. Network segmentation separates sensitive systems.
    
3. Authentication verifies user identity.
    
4. Encryption protects communication.
    
5. IDS/IPS monitors suspicious activity.
    
6. Logging supports investigation and incident response.
    

If one control fails, other controls may still reduce the impact.

## 4. Network Security Controls

### 4.1 Firewalls

A firewall monitors and controls network traffic according to predefined security rules.

It can allow or block traffic based on factors such as:

- Source IP address
    
- Destination IP address
    
- Port number
    
- Protocol
    
- Connection state
    
- Application information (depending on firewall type)
    

Common firewall types:

|Type|Description|
|---|---|
|Packet-filtering firewall|Filters packets using network and transport-layer information.|
|Stateful firewall|Tracks connection states and makes decisions using connection context.|
|Proxy firewall|Acts as an intermediary between clients and servers.|
|Next-generation firewall|May include application awareness, intrusion prevention, and advanced inspection.|

**Web Application Firewall (WAF):** Protects web applications by inspecting HTTP and HTTPS requests for suspicious application-layer traffic. It does not replace a network firewall.

Related note: [[Firewalls]]

### 4.2 Intrusion Detection System (IDS)

An IDS monitors network or system activity to identify suspicious behavior.

Its primary role is detection and alerting.

### 4.3 Intrusion Prevention System (IPS)

An IPS detects suspicious activity and can automatically take action to block or prevent it.

|IDS|IPS|
|---|---|
|Detects suspicious activity|Detects and can block suspicious activity|
|Generates alerts|Can take preventive action|
|Often deployed for monitoring|Often deployed inline|
|Does not normally block traffic|Can block malicious traffic|

Both systems may generate false positives, so alerts require investigation.

Related note: [[IDS and IPS]]

### 4.4 Virtual Private Network (VPN)

A VPN creates an encrypted communication tunnel between endpoints across an untrusted network.

Common uses:

- Secure remote access.
    
- Connecting separate office networks.
    
- Protecting traffic on untrusted networks.
    

A VPN does not make a compromised device safe or guarantee anonymity.

Related note: [[VPN]]

### 4.5 Network Access Control (NAC)

NAC controls which users and devices can connect to a network.

It may evaluate:

- User identity
    
- Device identity
    
- Security configuration
    
- Device compliance
    
- Authentication status
    

Related note: [[Network Access Control]]

### 4.6 Encryption

Encryption converts readable information (plaintext) into an unreadable form (ciphertext) using cryptographic methods.

It helps protect data from unauthorized disclosure.

Examples:

- TLS for secure network communication.
    
- IPsec for securing IP communications.
    
- WPA2/WPA3 for wireless network protection.
    

Encryption does not prevent every type of attack. Endpoint security, authentication, and correct configuration are also necessary.

## 5. Network Segmentation

Network segmentation divides a larger network into smaller logical or physical sections.

Benefits:

- Limits unauthorized access.
    
- Reduces the spread of malware.
    
- Protects sensitive systems.
    
- Makes monitoring and access control easier.
    

### VLAN

A Virtual Local Area Network (VLAN) logically separates devices within a switched network.

Different VLANs can represent different departments or security zones.

### DMZ

A Demilitarized Zone (DMZ) is a separate network segment used to host services that must be accessible from less-trusted networks, such as the internet.

Examples:

- Public web servers
    
- Public-facing mail gateways
    
- DNS servers intended for external access
    

The DMZ helps prevent direct exposure of the internal network.

Related notes:

- [[VLAN]]
    
- [[Network Segmentation]]
    

## 6. Wireless Network Security

Wireless networks transmit data through radio signals, so their security configuration is important.

### Wireless Security Standards

|Standard|Security|
|---|---|
|WEP|Outdated and insecure|
|WPA|Older standard; no longer recommended|
|WPA2|Strong security when correctly configured|
|WPA3|Newer standard with improved security protections|

### Wireless Security Best Practices

- Prefer WPA3 or WPA2-AES.
    
- Use a strong Wi-Fi password.
    
- Change default router administrator credentials.
    
- Update router firmware.
    
- Disable WPS if it is not needed.
    
- Use a guest network for visitors.
    
- Avoid unnecessary remote administration.
    
- Monitor connected devices.
    

Related note: [[Wireless Network Security]]

## 7. Secure Network Protocols

Network protocols define how devices communicate.

Some protocols provide encryption and authentication, while older protocols may transmit information without adequate protection.

|Protocol|Purpose|Security|
|---|---|---|
|HTTPS|Secure web communication|Uses TLS|
|SSH|Secure remote administration|Encrypted|
|SFTP|Secure file transfer over SSH|Encrypted|
|TLS|Protects communication between applications|Cryptographic security|
|SNMPv3|Network device monitoring and management|Supports authentication and encryption|
|HTTP|Web communication|No built-in transport encryption|
|FTP|File transfer|No built-in encryption|
|Telnet|Remote terminal access|No built-in encryption|
|SNMPv1/v2c|Network monitoring and management|Community strings do not provide modern encryption|

Prefer secure alternatives to legacy protocols when possible.

Related notes:

- [[HTTP and HTTPS]]
    
- [[SSH Protocol]]
    
- [[FTP and SFTP]]
    

## 8. Network Monitoring

Network monitoring involves observing network activity to identify problems, performance issues, and suspicious behavior.

### Important Monitoring Activities

- Monitoring bandwidth usage.
    
- Observing active connections.
    
- Reviewing firewall logs.
    
- Detecting unusual traffic patterns.
    
- Identifying unexpected devices.
    
- Monitoring failed authentication attempts.
    
- Investigating suspicious communication.
    

### Common Monitoring Tools

|Tool|Purpose|
|---|---|
|Wireshark|Captures and analyzes network packets|
|Nmap|Discovers hosts and services on authorized networks|
|tcpdump|Captures network traffic from the command line|
|Netstat|Displays network connections and statistics|
|ss|Displays socket and connection information|
|IDS/IPS|Detects or prevents suspicious network activity|

Related notes:

- [[Wireshark]]
    
- [[Nmap]]
    
- [[Network Monitoring]]
    

## 9. Network Security Best Practices

### For Individuals

1. Use strong and unique passwords.
    
2. Enable multi-factor authentication where available.
    
3. Keep operating systems and applications updated.
    
4. Secure home Wi-Fi with WPA2 or WPA3.
    
5. Avoid connecting to unknown networks unnecessarily.
    
6. Use HTTPS websites.
    
7. Disable unused network services.
    
8. Review connected devices.
    

### For Organizations

1. Implement network segmentation.
    
2. Deploy and maintain firewalls.
    
3. Use IDS/IPS where appropriate.
    
4. Apply least-privilege access.
    
5. Monitor network activity.
    
6. Maintain secure configurations.
    
7. Patch network devices regularly.
    
8. Maintain backups and incident response procedures.
    
9. Perform authorized security assessments.
    
10. Document network architecture and changes.
    

## 10. Network Security Incident Response

When a network security incident occurs, organizations need a structured response.

A common incident response process includes:

1. **Preparation:** Establish policies, tools, and response procedures.
    
2. **Identification:** Detect and verify suspicious activity.
    
3. **Containment:** Limit the spread and impact.
    
4. **Eradication:** Remove the threat and its cause.
    
5. **Recovery:** Restore normal operations safely.
    
6. **Lessons Learned:** Review the incident and improve defenses.
    

For example, if a compromised device is spreading malware, administrators may isolate it from the network while investigating the incident.

## 11. Relationship with Other Cybersecurity Domains

Network security is one part of the broader cybersecurity field.

|Domain|Main Focus|
|---|---|
|Network Security|Protecting network infrastructure and communication|
|Application Security|Protecting software and applications|
|Cloud Security|Protecting cloud infrastructure and services|
|Information Security|Protecting information in all forms|
|Endpoint Security|Protecting individual devices|

These domains overlap and work together.

Related notes:

- [[Cybersecurity Domains]]
    
- [[Application Security]]
    
- [[Cloud Security]]
    
- [[Information Security]]
    
- [[Security Principles]]
    

## 12. Practical Lab — Inspect Your Network Configuration

**Objective:** Understand your own device's network configuration and firewall status.

Perform these checks on your own Windows computer.

### Step 1: View Network Configuration

Open PowerShell and run:

```
Get-NetIPConfiguration
```

Observe:

- Network interface
    
- IPv4 address
    
- Default gateway
    
- DNS server
    

### Step 2: Check Network Profile

```
Get-NetConnectionProfile
```

Observe whether your network is classified as:

- Public
    
- Private
    
- DomainAuthenticated
    

Do not change the profile unless you understand the security implications.

### Step 3: Inspect Firewall Profiles

```
Get-NetFirewallProfile
```

Observe:

- Name
    
- Enabled status
    
- Default inbound action
    
- Default outbound action
    

### Step 4: Check Listening Ports

```
Get-NetTCPConnection -State Listen
```

This displays TCP connections in the listening state.

A listening port is not automatically a vulnerability. Identify the associated application and determine whether the service is necessary.

### Step 5: Record Your Observations

Document:

- Your IPv4 address
    
- Your default gateway
    
- Your network profile
    
- Whether Windows Firewall is enabled
    
- The number of listening TCP connections
    
- Any unfamiliar service that you want to investigate
    

**Safety:** Perform network analysis only on devices and networks you own or have explicit permission to assess. Never scan external systems without authorization.

## 13. Key Terms

|Term|Meaning|
|---|---|
|Firewall|Controls network traffic using security rules|
|IDS|Detects suspicious activity|
|IPS|Detects and can prevent suspicious activity|
|VPN|Creates an encrypted communication tunnel|
|MITM|Interception between communicating parties|
|DoS|Attack intended to make a service unavailable|
|DDoS|DoS attack using multiple sources|
|VLAN|Logical separation within a switched network|
|DMZ|Separate network zone for public-facing services|
|NAC|Controls network access for users and devices|
|Packet Sniffing|Capturing and examining network traffic|
|Segmentation|Dividing a network into smaller sections|

## 14. Summary

Network security protects network infrastructure, devices, communication, and transmitted information.

Its major components include:

- Firewalls
    
- IDS and IPS
    
- VPNs
    
- Network segmentation
    
- Wireless security
    
- Encryption
    
- Access control
    
- Network monitoring
    

Effective network security requires multiple layers of protection, regular monitoring, secure configurations, and continuous maintenance.

## 15. My Understanding

Write your own explanation:

- What is network security?
    
- Why is defense in depth important?
    
- What is the difference between IDS and IPS?
    
- Why is network segmentation useful?
    
- How does a VPN protect communication?
    
- Why should legacy protocols such as Telnet and FTP be avoided?
    

## 16. Questions & Doubts

Record questions you encounter while studying or performing the practical lab.