> Cybersecurity consists of multiple specialized domains that work together to protect systems, networks, applications, devices, and information from digital threats.

## 1. Introduction

Cybersecurity is a broad field. Protecting an organization requires more than securing computers or installing antivirus software.

Different domains focus on different parts of the technology environment.

For example:

- Network Security protects communication and network infrastructure.
    
- Application Security protects software and applications.
    
- Cloud Security protects cloud environments.
    
- Digital Forensics investigates digital evidence.
    
- Incident Response handles security incidents.
    

These domains overlap and depend on each other.

## 2. Major Cybersecurity Domains

### 2.1 Network Security

Network Security protects network infrastructure, connected devices, and communication channels.

Main responsibilities:

- Securing routers and switches.
    
- Configuring firewalls.
    
- Monitoring network traffic.
    
- Detecting suspicious connections.
    
- Implementing network segmentation.
    
- Protecting wireless networks.
    

Common technologies:

- Firewalls
    
- IDS/IPS
    
- VPNs
    
- Wireshark
    
- Nmap
    

Related note: [[Network Security]]

### 2.2 Application Security

Application Security focuses on protecting software applications throughout their development and operational lifecycle.

Main responsibilities:

- Identifying software vulnerabilities.
    
- Securing authentication and authorization.
    
- Preventing injection attacks.
    
- Testing application security.
    
- Reviewing source code.
    
- Applying secure coding practices.
    

Common vulnerabilities:

- SQL Injection
    
- Cross-Site Scripting (XSS)
    
- Broken Access Control
    
- Security Misconfiguration
    
- Insecure File Uploads
    

Related note: [[Application Security]]

### 2.3 Information Security

Information Security protects information from unauthorized access, modification, disclosure, and destruction.

It covers both digital and physical information.

Main responsibilities:

- Protecting confidential information.
    
- Managing access permissions.
    
- Applying encryption.
    
- Maintaining data backups.
    
- Establishing information security policies.
    
- Preventing data leakage.
    

Related note: [[Information Security]]

### 2.4 Cloud Security

Cloud Security protects cloud-based infrastructure, applications, services, and data.

Main responsibilities:

- Securing cloud accounts.
    
- Managing identity and access.
    
- Protecting cloud storage.
    
- Monitoring cloud activity.
    
- Configuring cloud network controls.
    
- Managing cloud security policies.
    

Examples of cloud platforms:

- Amazon Web Services (AWS)
    
- Microsoft Azure
    
- Google Cloud Platform (GCP)
    

Related note: [[Cloud Security]]

### 2.5 Endpoint Security

Endpoint Security protects devices that connect to a network.

Examples:

- Desktop computers
    
- Laptops
    
- Servers
    
- Smartphones
    
- Tablets
    

Main responsibilities:

- Detecting malware.
    
- Managing device security.
    
- Applying operating system updates.
    
- Monitoring endpoint activity.
    
- Enforcing security policies.
    
- Controlling removable devices.
    

Common technologies:

- Antivirus
    
- Endpoint Detection and Response (EDR)
    
- Host-based firewalls
    
- Device encryption
    

### 2.6 Identity and Access Management (IAM)

IAM ensures that the correct users and systems receive appropriate access to resources.

Main responsibilities:

- Managing user accounts.
    
- Enforcing authentication.
    
- Assigning permissions.
    
- Applying least privilege.
    
- Managing privileged accounts.
    
- Reviewing access regularly.
    

Important concepts:

- Authentication: Verifying identity.
    
- Authorization: Determining permitted actions.
    
- Multi-Factor Authentication (MFA): Using multiple authentication factors.
    
- Role-Based Access Control (RBAC): Assigning permissions according to roles.
    

### 2.7 Security Operations (SecOps)

Security Operations focuses on continuously monitoring systems and responding to security threats.

A Security Operations Center (SOC) is a team or function responsible for monitoring and coordinating security operations.

Main responsibilities:

- Monitoring security alerts.
    
- Investigating suspicious activity.
    
- Analyzing logs.
    
- Detecting potential attacks.
    
- Coordinating incident response.
    
- Reporting security events.
    

Common technologies:

- SIEM
    
- EDR
    
- IDS/IPS
    
- Threat intelligence platforms
    

### 2.8 Incident Response

Incident Response is the structured process of identifying, containing, investigating, and recovering from security incidents.

Examples:

- Ransomware infection.
    
- Unauthorized account access.
    
- Data breach.
    
- Malware outbreak.
    
- Compromised server.
    

Common stages:

1. Preparation
    
2. Identification
    
3. Containment
    
4. Eradication
    
5. Recovery
    
6. Lessons Learned
    

### 2.9 Digital Forensics

Digital Forensics involves collecting, preserving, examining, and presenting digital evidence.

Evidence may come from:

- Computers
    
- Mobile devices
    
- Storage media
    
- Network traffic
    
- System logs
    
- Cloud environments
    

Main responsibilities:

- Preserving evidence integrity.
    
- Creating forensic images.
    
- Examining files and metadata.
    
- Analyzing system activity.
    
- Maintaining chain of custody.
    
- Preparing forensic reports.
    

Related note: [[Digital Forensics]]

### 2.10 Malware Analysis

Malware Analysis examines malicious software to understand its behavior, functionality, and impact.

Main responsibilities:

- Identifying malware characteristics.
    
- Examining suspicious files.
    
- Understanding malware behavior.
    
- Extracting indicators of compromise.
    
- Supporting incident investigations.
    

Common approaches:

- Static Analysis
    
- Dynamic Analysis
    
- Behavioral Analysis
    

Related note: [[Malware]]

### 2.11 Governance, Risk, and Compliance (GRC)

GRC focuses on managing cybersecurity risks and ensuring that an organization follows appropriate policies, standards, and regulations.

Main responsibilities:

- Identifying security risks.
    
- Developing security policies.
    
- Conducting risk assessments.
    
- Managing compliance requirements.
    
- Performing security audits.
    
- Tracking remediation activities.
    

### 2.12 Penetration Testing

Penetration Testing is an authorized security assessment in which testers evaluate systems for exploitable vulnerabilities.

Typical activities:

- Defining scope and permission.
    
- Information gathering.
    
- Vulnerability identification.
    
- Controlled exploitation.
    
- Impact assessment.
    
- Reporting findings.
    

The goal is to identify weaknesses so they can be fixed before malicious attackers exploit them.

### 2.13 Threat Intelligence

Threat Intelligence involves collecting, analyzing, and interpreting information about cyber threats.

It helps organizations understand:

- Threat actors.
    
- Attack techniques.
    
- Malware campaigns.
    
- Indicators of compromise.
    
- Emerging vulnerabilities.
    
- Potential attack targets.
    

## 3. Comparison of Cybersecurity Domains

|Domain|Primary Focus|
|---|---|
|Network Security|Networks and communication|
|Application Security|Software and applications|
|Information Security|Information and data|
|Cloud Security|Cloud infrastructure and services|
|Endpoint Security|Computers and connected devices|
|IAM|Identity and access permissions|
|Security Operations|Monitoring and detection|
|Incident Response|Handling security incidents|
|Digital Forensics|Digital evidence investigation|
|Malware Analysis|Understanding malicious software|
|GRC|Risk, policies, and compliance|
|Penetration Testing|Authorized security testing|
|Threat Intelligence|Understanding cyber threats|

## 4. How These Domains Work Together

Consider a company experiencing a ransomware attack.

Different cybersecurity domains contribute to the investigation and recovery:

1. **Endpoint Security:** Detects suspicious activity on an employee's computer.
    
2. **Security Operations:** Investigates alerts and identifies affected systems.
    
3. **Network Security:** Helps isolate compromised devices.
    
4. **Incident Response:** Coordinates containment and recovery.
    
5. **Digital Forensics:** Examines evidence to understand what happened.
    
6. **Threat Intelligence:** Helps identify related indicators and attack techniques.
    
7. **GRC:** Reviews the incident's policy, risk, and compliance implications.
    

This demonstrates why cybersecurity requires cooperation between different specialties.

## 5. Cybersecurity Roles and Career Paths

|Role|Main Responsibilities|
|---|---|
|Security Analyst|Monitors and investigates security events|
|SOC Analyst|Monitors alerts and handles initial investigations|
|Penetration Tester|Performs authorized security assessments|
|Security Engineer|Designs and implements security controls|
|Network Security Engineer|Secures network infrastructure|
|Digital Forensics Analyst|Examines digital evidence|
|Incident Responder|Handles security incidents|
|Malware Analyst|Analyzes malicious software|
|Cloud Security Engineer|Secures cloud infrastructure|
|GRC Analyst|Manages security risks and compliance|
|Security Architect|Designs security architecture|

A cybersecurity professional may specialize in one domain while maintaining knowledge of several others.

## 6. Practical Learning Exercise

**Objective:** Understand how different cybersecurity domains contribute to a single security incident.

### Scenario

An employee receives a suspicious email containing a malicious attachment. After opening it, the employee's computer begins communicating with an unfamiliar external server.

Identify which cybersecurity domains would help investigate the incident.

Use this table:

|Investigation Activity|Relevant Domain|
|---|---|
|Investigating the suspicious email||
|Detecting unusual network communication||
|Identifying malicious software||
|Isolating the affected computer||
|Examining system evidence||
|Coordinating recovery||

Write your answers in your notebook and explain why each domain is relevant.

## 7. Key Terms

|Term|Meaning|
|---|---|
|IAM|Identity and Access Management|
|SOC|Security Operations Center|
|SIEM|Security Information and Event Management|
|EDR|Endpoint Detection and Response|
|GRC|Governance, Risk, and Compliance|
|MFA|Multi-Factor Authentication|
|RBAC|Role-Based Access Control|
|IOC|Indicator of Compromise|
|IR|Incident Response|
|VAPT|Vulnerability Assessment and Penetration Testing|

## 8. Summary

Cybersecurity is made up of several interconnected domains.

Each domain addresses a different security requirement, from protecting networks and applications to investigating incidents and managing organizational risk.

Understanding these domains helps cybersecurity students identify career paths and understand how security teams work together.

## 9. My Understanding

Write your own explanation:

- Why is cybersecurity divided into different domains?
    
- What is the difference between Network Security and Information Security?
    
- How are SOC and Incident Response related?
    
- What does a Digital Forensics Analyst do?
    
- What is the purpose of Penetration Testing?
    
- Which cybersecurity domains interest you most, and why?
    

## 10. Questions & Doubts

Record unfamiliar terms, technologies, and career roles that you want to investigate further.