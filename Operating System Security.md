> Operating System Security is the practice of protecting an operating system, its resources, and its users from unauthorized access, attacks, and misuse.

## 1. What Is Operating System Security?

Operating System Security involves protecting:

- User accounts and credentials.
- Files and directories.
- Running processes.
- System services.
- Memory and system resources.
- Network connections.
- System configurations.

Its primary goal is to maintain the **Confidentiality, Integrity, and Availability (CIA) Triad**.

## 2. CIA Triad

|Principle|Meaning|Example|
|---|---|---|
|Confidentiality|Prevent unauthorized access to information.|Protecting files with permissions.|
|Integrity|Prevent unauthorized modification of data.|Using file integrity monitoring.|
|Availability|Ensure systems remain accessible.|Protecting against denial-of-service attacks.|

## 3. Core Security Mechanisms

### Authentication

Authentication verifies the identity of a user or system.

Examples:

- Passwords.
- PINs.
- Biometrics.
- Multi-Factor Authentication (MFA).

### Authorization

Authorization determines what an authenticated user is allowed to access or perform.

Example:

- A standard user can read a file.
- An administrator can modify system settings.

### Accounting and Auditing

Accounting and auditing record user activities and system events.

Examples:

- Login records.
- Failed authentication attempts.
- Permission changes.
- Administrative activities.

## 4. Important OS Security Controls

|Security Control|Purpose|
|---|---|
|Access Control|Restricts access to resources.|
|User Permissions|Controls what users can do.|
|Privilege Management|Limits administrative privileges.|
|Process Isolation|Separates running processes.|
|Memory Protection|Prevents unauthorized memory access.|
|Firewall|Controls network traffic.|
|Antivirus|Detects and helps remove malicious software.|
|Security Updates|Fixes known vulnerabilities.|
|Secure Boot|Helps prevent unauthorized boot components.|

## 5. Common Operating System Threats

### Malware

Malicious software designed to damage systems, steal information, or perform unauthorized activities.

Examples:

- [[Virus]]
- [[Worm]]
- [[Trojan]]
- [[Ransomware]]
- [[Spyware]]

### Privilege Escalation

An attacker gains permissions beyond those originally assigned.

Two common types:

- **Vertical:** A standard user gains administrator or root privileges.
- **Horizontal:** A user accesses another user's resources at the same privilege level.

### Credential Theft

Attackers obtain passwords, authentication tokens, or other credentials.

### Unpatched Vulnerabilities

Outdated software may contain known security weaknesses that attackers can exploit.

### Insecure Services

Unnecessary or incorrectly configured services can expose additional attack surfaces.

### Misconfiguration

Weak passwords, excessive permissions, and insecure settings can make a system vulnerable.

## 6. Windows Operating System Security

Windows provides several built-in security mechanisms:

- Windows Defender Antivirus.
- Windows Defender Firewall.
- User Account Control (UAC).
- NTFS permissions.
- Windows Security.
- BitLocker drive encryption.
- Windows Event Logs.
- Windows Update.

Useful PowerShell commands:

**Check Windows Defender status**

```
Get-MpComputerStatus
```

**Check firewall profiles**

```
Get-NetFirewallProfile
```

**Check logged-in user**

```
whoami
```

**Check current privileges**

```
whoami /priv
```

## 7. Linux Operating System Security

Linux provides security mechanisms such as:

- User and group management.
- File permissions.
- sudo privilege management.
- Firewall tools.
- Security updates.
- Process isolation.
- System logging.

Useful commands:

**Check current user**

```
whoami
```

**Check user identity and groups**

```
id
```

**Check file permissions**

```
ls -l
```

**Check listening network services**

```
sudo ss -tulpen
```

**Check running services**

```
systemctl --type=service --state=running
```

**Check firewall status (if UFW is installed)**

```
sudo ufw status
```

## 8. Basic Security Principles

### Principle of Least Privilege

Give users and processes only the permissions they need to perform their tasks.

### Defense in Depth

Use multiple layers of security instead of depending on one security mechanism.

### Secure by Default

Configure systems with secure settings from the beginning.

### Regular Updates

Install security patches to reduce exposure to known vulnerabilities.

### Reduce Attack Surface

Disable unnecessary services, remove unused software, and restrict exposed interfaces.

## 9. Practical Lab — Inspect Operating System Security

Perform these checks without changing system settings.

### Windows PowerShell

1. Open PowerShell.
2. Run:

```powershell
whoami
Get-MpComputerStatus
Get-NetFirewallProfile
whoami /priv
```

3. Observe:  
- Current username.
- Antivirus status.
- Firewall status.
- Assigned user privileges.

### Kali Linux

1. Open the terminal.
2. Run:

```bash
whoami
id
ls -l
sudo ss -tulpen
systemctl --type=service --state=running
```

3. Observe:
- Current user.
- Group memberships.
- File permissions.
- Listening network ports.
- Running services.    

Some commands may require administrative privileges or may not be available on every installation.

## 10. Key Takeaways

- Operating System Security protects system resources and information.
- The CIA Triad defines three major security objectives.
- Authentication verifies identity.
- Authorization controls access.
- Auditing records system activities.
- Windows and Linux use different tools but share many security principles.
- Least privilege and defense in depth are important security practices.

## 11. Questions to Understand

1. What is Operating System Security?
2. Explain the CIA Triad.
3. What is the difference between authentication and authorization?
4. What is privilege escalation?
5. Why are security updates important?
6. What is the principle of least privilege?

## Related Notes

- [[Access Control]]
- [[Privilege Management]]
- [[System Hardening]]
- [[Patch Management]]
- [[Security Auditing]]
- [[Windows Permissions]]
- [[Linux Permissions]]
- [[User Account Management]]
- [[Service Management]]
- [[System Updates]]
- [[Digital Forensics]]

---