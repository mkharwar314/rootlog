> Cybersecurity tools help security professionals discover, monitor, analyze, test, and protect computer systems, networks, and applications.

## 1. Introduction

Cybersecurity tools are software applications, command-line utilities, and hardware devices used to perform security-related tasks.

They help professionals:

- Discover devices and services on a network.
    
- Analyze network traffic.
    
- Identify security vulnerabilities.
    
- Test web application security.
    
- Monitor system activity.
    
- Investigate security incidents.
    
- Analyze suspicious files.
    
- Audit password security.
    
- Detect unauthorized activities.
    

**Important:** A tool does not automatically make someone a security professional. Understanding what the tool does, interpreting its results, and validating its findings are equally important.

## 2. Categories of Cybersecurity Tools

### 2.1 Network Scanning and Discovery Tools

These tools identify devices, open ports, running services, and network information.

**Examples:**

|Tool|Purpose|
|---|---|
|Nmap|Network discovery and port scanning|
|Angry IP Scanner|Discover devices and IP addresses|
|Netcat|Network connections and troubleshooting|
|arp-scan|Discover devices on a local network|

**Nmap example:**

```
nmap -sV 192.168.1.10
```

This attempts to identify services and their versions on the specified host.

Only scan systems you own or have explicit permission to test.

Related: [[Nmap]], [[Network Security]]

### 2.2 Network Traffic Analysis Tools

These tools capture and inspect network packets to understand communication between devices.

**Examples:**

- **Wireshark:** Graphical packet analysis tool.
    
- **tcpdump:** Command-line packet capture utility.
    
- **TShark:** Command-line version of Wireshark's analysis engine.
    

Uses:

- Troubleshooting network problems.
    
- Investigating suspicious communication.
    
- Understanding network protocols.
    
- Identifying unusual traffic patterns.
    

**tcpdump example:**

```
sudo tcpdump -i any
```

This displays packets observed on available interfaces.

Packet captures may contain sensitive information. Capture only traffic you are authorized to inspect.

Related: [[Wireshark]], [[Packet Analysis]]

### 2.3 Web Application Security Tools

These tools help assess the security of websites and web applications.

**Examples:**

|Tool|Purpose|
|---|---|
|Burp Suite|Intercept and analyze HTTP requests and responses|
|OWASP ZAP|Web application security testing|
|Postman|Test APIs and inspect HTTP communication|
|Browser Developer Tools|Inspect requests, responses, scripts, and browser behavior|

Common testing areas:

- SQL Injection
    
- Cross-Site Scripting (XSS)
    
- Authentication weaknesses
    
- Access control problems
    
- Insecure file uploads
    
- Session management issues
    

**Example workflow:**

1. Open an authorized test application.
    
2. Configure Burp Suite or ZAP.
    
3. Intercept an HTTP request.
    
4. Inspect request parameters and headers.
    
5. Modify a test request within the approved scope.
    
6. Observe and document the response.
    

These tools assist testing; they do not prove that an application is secure.

Related: [[Application Security]]

### 2.4 Vulnerability Assessment Tools

Vulnerability scanners examine systems for known security weaknesses.

**Examples:**

- Nessus
    
- OpenVAS / Greenbone Vulnerability Management
    
- Qualys VMDR
    

They may identify:

- Outdated software.
    
- Missing security patches.
    
- Insecure configurations.
    
- Known vulnerabilities.
    
- Exposed services.
    

**Important distinction:**

A vulnerability scanner identifies potential weaknesses. A penetration test involves controlled attempts to validate whether weaknesses can actually be exploited and what their impact is.

Scanner results can contain:

- False positives: A reported vulnerability that is not actually present.
    
- False negatives: A vulnerability that the scanner fails to identify.
    

Always validate important findings.

### 2.5 Endpoint Security Tools

Endpoint security tools protect individual devices such as laptops, desktops, and servers.

Examples:

- Microsoft Defender Antivirus
    
- Windows Defender Firewall
    
- Microsoft Defender for Endpoint
    
- CrowdStrike Falcon
    

Common functions:

- Malware detection.
    
- Suspicious process monitoring.
    
- File scanning.
    
- Threat prevention.
    
- Endpoint investigation.
    
- Security alerts.
    

An endpoint is a device connected to a network, such as a computer, laptop, or server.

### 2.6 Digital Forensics Tools

Digital forensics tools help collect, preserve, examine, and analyze digital evidence.

Examples:

|Tool|Purpose|
|---|---|
|Autopsy|Digital forensic investigation|
|FTK Imager|Acquire and examine forensic images|
|Volatility|Analyze memory dumps|
|Eric Zimmerman's tools|Windows forensic artifact analysis|
|ExifTool|Examine file metadata|

Common investigation activities:

- Examining files and folders.
    
- Recovering deleted data.
    
- Analyzing browser history.
    
- Examining timestamps and metadata.
    
- Investigating Windows event logs.
    
- Analyzing memory artifacts.
    

Forensic work requires evidence integrity, proper documentation, and repeatable procedures.

Related: [[06 - Digital Forensics]]

### 2.7 Password Auditing Tools

These tools help assess password strength and audit password security.

Examples:

- John the Ripper
    
- Hashcat
    

Uses:

- Testing password strength.
    
- Auditing password hashes.
    
- Identifying weak passwords.
    
- Evaluating password policies.
    

**Important:** Password auditing must only be performed using authorized accounts, systems, or test data. Never attempt to obtain another person's credentials.

### 2.8 Security Monitoring and SIEM Tools

SIEM stands for **Security Information and Event Management**.

SIEM platforms collect and analyze security events from different systems.

Examples:

- Splunk Enterprise Security
    
- Elastic Security
    
- Microsoft Sentinel
    
- IBM QRadar
    

They help security teams:

- Collect logs from multiple devices.
    
- Correlate security events.
    
- Detect suspicious activities.
    
- Generate alerts.
    
- Investigate incidents.
    
- Monitor security operations.
    

**Example:**

A SIEM might correlate several failed login attempts followed by a successful login from an unusual location. This combination may indicate suspicious account activity and deserves investigation.

A SIEM does not automatically understand every attack. Detection depends on the quality of logs, rules, analytics, and investigation.

Related: [[Cybersecurity Labs]], [[Network Security]]

### 2.9 Malware Analysis Tools

Malware analysis tools help researchers examine suspicious software and understand its behavior.

Examples:

|Tool|Purpose|
|---|---|
|Ghidra|Reverse engineering|
|YARA|Identify files using pattern-based rules|
|PE-bear|Inspect Windows executable files|
|Detect It Easy (DIE)|Identify file types and executable packers|
|Process Monitor|Monitor Windows process and file activity|

Two common approaches:

**Static analysis**

Examining a file without executing it.

Examples:

- Inspecting file metadata.
    
- Calculating file hashes.
    
- Examining strings.
    
- Inspecting executable structure.
    

**Dynamic analysis**

Observing a program while it runs in a controlled environment.

Examples:

- Monitoring process creation.
    
- Observing file changes.
    
- Monitoring network connections.
    
- Recording system behavior.
    

Never execute unknown malware on your normal computer. Use an appropriately isolated analysis environment.

Related: [[Malware]]

### 2.10 Operating System and Administration Tools

Operating systems provide built-in tools that are useful for security investigations and troubleshooting.

**Windows tools:**

|Tool|Purpose|
|---|---|
|Task Manager|View running processes and resource usage|
|Event Viewer|Examine Windows event logs|
|PowerShell|Automate administration and investigations|
|Windows Defender|Scan for malware|
|Windows Firewall|Control network traffic|
|Sysmon|Record detailed system activity|

**Linux tools:**

|Command|Purpose|
|---|---|
|`ps`|Display running processes|
|`top`|Monitor system processes|
|`ss`|Display socket information|
|`ip`|Examine network configuration|
|`journalctl`|Examine system logs|
|`sha256sum`|Calculate file hashes|
|`find`|Search for files and directories|

These built-in tools are often sufficient for initial system investigation.

Related: [[02 - Operating Systems]]

## 3. Important Security Tool Comparisons

### 3.1 IDS vs IPS vs SIEM

|Technology|Main Function|
|---|---|
|IDS|Detects suspicious network or system activity|
|IPS|Detects and can actively block suspicious activity|
|SIEM|Collects, correlates, and analyzes security events|

**Remember:**

- IDS = Detect
    
- IPS = Detect and prevent
    
- SIEM = Collect and analyze
    

### 3.2 Static vs Dynamic Analysis

|Static Analysis|Dynamic Analysis|
|---|---|
|Examines a file without executing it|Examines behavior during execution|
|Can inspect strings and metadata|Can monitor processes and network activity|
|Does not require running the sample|Requires a controlled execution environment|

Both approaches can provide useful evidence. Combining them often gives a better understanding of suspicious software.

### 3.3 Vulnerability Scanner vs Penetration Testing

|Vulnerability Scanner|Penetration Testing|
|---|---|
|Automatically checks for known weaknesses|Tests security through controlled assessment|
|Often examines many systems quickly|Investigates selected targets in greater depth|
|May produce false positives|Requires validation and analysis|
|Identifies potential vulnerabilities|Evaluates exploitability and impact|

## 4. How to Select the Right Security Tool

Before choosing a tool, ask:

1. **Objective:** What exactly am I trying to investigate?
    
2. **Authorization:** Do I have permission to perform this activity?
    
3. **Scope:** Which systems and resources are included?
    
4. **Environment:** Is the tool compatible with my operating system?
    
5. **Evidence:** What data will the tool collect?
    
6. **Accuracy:** Could the results contain false positives or false negatives?
    
7. **Documentation:** Can I reproduce and explain the results?
    

**Example:**

If the objective is to investigate suspicious network traffic, Wireshark is more appropriate than a password auditing tool.

Tool selection should be based on the investigation objective, not popularity.

## 5. Safe Installation and Usage Practices

Follow these practices when working with cybersecurity tools:

- Download software from official websites or trusted repositories.
    
- Verify checksums or digital signatures when available.
    
- Read the documentation before executing commands.
    
- Understand the permissions required by a tool.
    
- Use virtual machines for isolated experiments where appropriate.
    
- Create VM snapshots before risky experiments.
    
- Avoid running unknown scripts as administrator or root.
    
- Do not scan or test systems without authorization.
    
- Keep tools updated.
    
- Record commands, results, timestamps, and observations.
    

## 6. Practical Lab — Exploring Built-in Security Tools

**Objective:** Learn how to inspect your own computer using built-in commands.

Perform these activities on your Windows computer.

### Task 1: Check network configuration

Open Command Prompt:

```
ipconfig /all
```

Observe:

- IPv4 address.
    
- Subnet mask.
    
- Default gateway.
    
- DNS servers.
    
- Network adapter information.
    

### Task 2: Examine active network connections

```
netstat -ano
```

Observe:

- Local addresses.
    
- Foreign addresses.
    
- Connection states.
    
- Process IDs (PIDs).
    

To identify a process using a PID:

```
tasklist /FI "PID eq 1234"
```

Replace `1234` with an actual PID from your results.

### Task 3: Check Windows Firewall

```
netsh advfirewall show allprofiles
```

Observe whether the Domain, Private, and Public firewall profiles are enabled.

### Task 4: Calculate a file hash

Create a small text file named `sample.txt`.

Run:

```
certutil -hashfile sample.txt SHA256
```

Record the SHA-256 hash.

A cryptographic hash helps identify whether file contents have changed. It does not prove that a file is safe.

### Task 5: Explore Windows Event Viewer

1. Press `Win + R`.
    
2. Enter `eventvwr.msc`.
    
3. Open **Windows Logs**.
    
4. Select **System** or **Security**.
    
5. Examine a few available events.
    
6. Record the event ID, timestamp, and description.
    

Do not delete or modify event logs during this exercise.

## 7. Practical Observation Template

Record your findings:

|Activity|Tool or Command|Observation|
|---|---|---|
|Network configuration|`ipconfig /all`||
|Active connections|`netstat -ano`||
|Firewall status|`netsh advfirewall`||
|File hash|`certutil`||
|Event investigation|Event Viewer||

## 8. Common Mistakes

1. Assuming that a tool can identify every vulnerability.
    
2. Trusting scanner results without validation.
    
3. Running commands without understanding their effects.
    
4. Using tools against systems without permission.
    
5. Ignoring false positives and false negatives.
    
6. Confusing vulnerability scanning with penetration testing.
    
7. Executing suspicious files on a normal computer.
    
8. Treating a successful scan as proof that a system is secure.
    

## 9. Key Takeaways

- Cybersecurity tools support security assessment, monitoring, testing, and investigation.
    
- Different tools are designed for different objectives.
    
- Nmap is used for network discovery and scanning.
    
- Wireshark is used for packet analysis.
    
- Burp Suite and OWASP ZAP support web application testing.
    
- Nessus and OpenVAS support vulnerability assessment.
    
- Autopsy and Volatility support digital forensics.
    
- John the Ripper and Hashcat support authorized password auditing.
    
- SIEM platforms collect and analyze security events.
    
- Tool output must be interpreted and validated by a human analyst.
    
- Authorization and evidence integrity are essential.
    

## 10. Related Notes

- [[01 - Cybersecurity]]
    
- [[Network Security]]
    
- [[Application Security]]
    
- [[Cybersecurity Labs]]
    
- [[Malware]]
    
- [[06 - Digital Forensics]]
    
- [[07 - Practical Labs]]
    
- [[Resources]]
    

## 11. My Understanding

Write your own explanation:

- What are cybersecurity tools?
    
- Why are different tools needed for different tasks?
    
- What is the difference between IDS, IPS, and SIEM?
    
- What is the difference between static and dynamic analysis?
    
- Why should security tool results be validated?
    

## 12. Questions & Doubts

- How does Nmap discover open ports?
    
- How does Wireshark capture packets?
    
- How does a SIEM correlate security events?
    
- How do analysts validate vulnerability scanner findings?
    
- How are forensic tools used during incident investigations?