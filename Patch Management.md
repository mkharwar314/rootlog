> System Hardening is the process of reducing security vulnerabilities by configuring an operating system and its components securely.

## 1. What Is System Hardening?

System hardening involves strengthening a computer against cyberattacks by removing unnecessary features, restricting access, and applying secure configurations.

The main objective is to reduce the system's **attack surface**.

### What Is an Attack Surface?

An attack surface is the collection of points through which an attacker could potentially interact with or attack a system.

Examples:

- Open network ports.
- Running services.
- User accounts.
- Installed applications.
- Exposed management interfaces.
- Unpatched software.

A larger attack surface can create more opportunities for attackers.

## 2. Why Is System Hardening Important?

System hardening helps to:

- Reduce unauthorized access.
- Prevent exploitation of known vulnerabilities.
- Protect sensitive information.
- Reduce malware infection risks.
- Limit the impact of security incidents.
- Improve system reliability.

## 3. Important System Hardening Techniques

### 1. Remove Unnecessary Software

Uninstall applications that are not required.

Why?

Unused software may contain vulnerabilities and increase the attack surface.

### 2. Disable Unnecessary Services

Services run in the background and provide system functionality.

Unnecessary services should be disabled when they are not required.

Example:

A computer that does not provide file-sharing services may not need an exposed file-sharing service.

### 3. Apply Security Updates

Keep the operating system and applications updated.

Updates often include:

- Security patches.
- Bug fixes.
- Stability improvements.

### 4. Secure User Accounts

- Use strong passwords.
- Disable unused accounts.
- Avoid shared administrator accounts.
- Apply least privilege.
- Review account permissions.

### 5. Configure Firewall Rules

A firewall controls incoming and outgoing network traffic according to defined rules.

Only required network communication should be allowed.

### 6. Secure File Permissions

Restrict access to sensitive files and directories.

Users should receive only the permissions required for their work.

### 7. Enable Security Protection

Use available security mechanisms such as:

- Antivirus or endpoint protection.
- Disk encryption.
- Secure Boot.
- Host-based firewalls.
- Security auditing.

## 4. Windows System Hardening

Important Windows security features include:

|Feature|Purpose|
|---|---|
|Windows Defender|Detects and helps remove malware.|
|Windows Firewall|Controls network traffic.|
|BitLocker|Encrypts supported storage volumes.|
|UAC|Helps control administrative elevation.|
|Windows Update|Delivers security updates and fixes.|
|NTFS Permissions|Controls file and folder access.|
|Secure Boot|Helps prevent unauthorized boot components.|

Useful PowerShell commands:

**Check firewall profiles**

```
Get-NetFirewallProfile
```

**Check antivirus status**

```
Get-MpComputerStatus
```

**List running services**

```
Get-Service | Where-Object {$_.Status -eq "Running"}
```

**List installed programs through registry uninstall entries**

```
Get-ItemProperty `
"HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\*" |
Select-Object DisplayName, DisplayVersion
```

This command may not show every installed application, including some per-user or 32-bit entries.

## 5. Linux System Hardening

Important Linux security practices include:

- Restrict root access.
- Use sudo appropriately.
- Configure file permissions.
- Disable unnecessary services.
- Apply package updates.
- Configure a firewall.
- Monitor system logs.
- Secure remote access.

Useful Kali Linux commands:

**Check operating system information**

```
cat /etc/os-release
```

**List running services**

```
systemctl --type=service --state=running
```

**Check listening network ports**

```
sudo ss -tulpen
```

**Check firewall status**

```
sudo ufw status
```

**Check available package updates**

```
sudo apt update
apt list --upgradable
```

`apt update` refreshes package information; it does not install upgrades.

## 6. Security Baseline

A security baseline is a documented set of minimum security configurations that systems are expected to follow.

Example baseline:

|Area|Recommended Configuration|
|---|---|
|Accounts|Disable unused accounts.|
|Passwords|Use strong authentication.|
|Permissions|Apply least privilege.|
|Firewall|Enable appropriate firewall rules.|
|Services|Remove unnecessary exposure.|
|Updates|Apply security patches.|
|Antivirus|Keep protection active.|
|Logging|Enable relevant security logs.|

Organizations often use security benchmarks such as CIS Benchmarks to establish secure configurations.

## 7. Common System Hardening Mistakes

- Disabling services without understanding their purpose.
- Applying firewall rules without checking required connectivity.
- Giving users unnecessary administrator privileges.
- Ignoring application updates.
- Disabling antivirus to improve performance.
- Applying random security commands from the internet.
- Changing configurations without recording the original settings.

**Important:** Hardening should be planned and tested. An incorrect configuration can break system functionality.

## 8. Practical Lab — Inspect System Configuration

This lab is observational. Do not disable services or modify firewall rules.

### Windows PowerShell

```
Get-NetFirewallProfile
Get-MpComputerStatus
Get-Service | Where-Object {$_.Status -eq "Running"}
whoami /groups
```

Record:

- Firewall status.
- Antivirus status.
- Number of running services.
- Your account's group memberships.

### Kali Linux

```
sudo ss -tulpen
systemctl --type=service --state=running
sudo ufw status
id
```

Record:

- Listening ports.
- Running services.
- Firewall status.
- Current user and groups.

## 9. Key Takeaways

- System hardening reduces security weaknesses.
- Attack surface represents possible entry points into a system.
- Unnecessary services and software increase exposure.
- Secure permissions and account management are essential.
- Firewalls and security updates help protect systems.
- Hardening must preserve required system functionality.

## 10. Questions to Understand

1. What is System Hardening?
2. What is an attack surface?
3. Why should unnecessary services be disabled?
4. What is a security baseline?
5. How does a firewall help protect an operating system?
6. Why should system configuration changes be tested?

## Related Notes

- [[Operating System Security]]
- [[Access Control]]
- [[Privilege Management]]
- [[Patch Management]]
- [[Security Auditing]]
- [[Windows Services]]
- [[Linux Services]]
- [[System Configuration]]
- [[System Updates]]
- [[Practical Labs]]

---