## 1. What Is System Configuration?

System configuration is the process of setting up and managing an operating system's settings, hardware, software, and services.

It determines how a computer behaves and how its resources are managed.

Examples:

- Network settings.
- User account settings.
- Startup applications.
- Display settings.
- Security settings.
- Environment variables.
- System services.

## 2. Why Is System Configuration Important?

System configuration helps administrators:

- Customize system behaviour.
- Manage hardware and software.
- Configure network connectivity.
- Control system resources.
- Improve security.
- Troubleshoot system problems.
- Maintain consistent system settings.

## 3. Windows System Configuration

Windows provides several tools to manage system settings.

### A. Settings

Open Windows Settings using:

```
Win + I
```

You can configure:

- Network and Internet.
- Accounts.
- System.
- Privacy and Security.
- Windows Update.
- Applications.

### B. System Configuration Utility

Open the Run dialog:

```
Win + R
```

Enter:

```
msconfig
```

The System Configuration utility provides options related to:

- General startup.
- Boot configuration.
- Services.
- Startup-related troubleshooting.

Be careful when changing boot or service settings.

### C. Environment Variables

Environment variables store configuration values used by applications and the operating system.

Display environment variables:

```
Get-ChildItem Env:
```

Display the PATH variable:

```
$env:Path
```

### D. Windows System Information

Open System Information:

```
msinfo32
```

Or inspect basic system details:

```
Get-ComputerInfo |
Select-Object WindowsProductName, WindowsVersion, OsArchitecture
```

## 4. Linux System Configuration

Linux stores many system configuration files in the `/etc` directory.

Examples:

|File or Directory|Purpose|
|---|---|
|`/etc/hostname`|System hostname.|
|`/etc/hosts`|Local hostname-to-address mappings.|
|`/etc/fstab`|Filesystem mount configuration.|
|`/etc/passwd`|User account information.|
|`/etc/group`|Group information.|
|`/etc/ssh/`|SSH server and client configuration files, depending on installed packages.|
|`/etc/systemd/`|Systemd configuration files and overrides.|

### A. Display Hostname

```
hostname
```

### B. Display Operating System Information

```
cat /etc/os-release
```

### C. Display Network Configuration

```
ip addr
```

### D. Display Environment Variables

```
printenv
```

### E. Display the PATH Variable

```
echo "$PATH"
```

## 5. Configuration Files

Configuration files contain settings that control how applications and operating system components behave.

For example, a network configuration file may define network interfaces or connection parameters.

Configuration formats include:

- Plain text.
- INI.
- YAML.
- JSON.
- XML.

Always understand the purpose of a configuration file before modifying it.

## 6. System Configuration and Cybersecurity

Incorrect system configurations can create security weaknesses.

Examples:

- Unnecessary network services.
- Weak authentication settings.
- Excessive user privileges.
- Insecure file permissions.
- Exposed remote-access services.
- Incorrect firewall rules.
- Unsafe environment variables or application settings.

### Security Best Practices

- Use secure configuration defaults.
- Restrict administrative access.
- Review important configuration files.
- Disable genuinely unnecessary services.
- Maintain configuration backups.
- Apply security updates.
- Document configuration changes.

## 7. Practical Lab — Inspect System Configuration

### Lab A: Windows PowerShell

Inspect system information:

```
Get-ComputerInfo |
Select-Object WindowsProductName, WindowsVersion, OsArchitecture
```

Display environment variables:

```
Get-ChildItem Env:
```

Display PATH:

```
$env:Path
```

Display hostname:

```
hostname
```

### Lab B: Kali Linux

Display hostname:

```
hostname
```

Inspect operating system information:

```
cat /etc/os-release
```

Inspect network interfaces:

```
ip addr
```

Display environment variables:

```
printenv
```

Inspect configuration directory:

```
ls -la /etc
```

These commands inspect system configuration without modifying it.

## 8. Practical Tasks

1. Find your Windows hostname.
2. Identify your Windows architecture.
3. Display Windows environment variables.
4. Find your Kali Linux hostname.
5. Identify your Kali Linux version.
6. Inspect the `/etc` directory.
7. Explain why configuration changes should be documented.

Record your observations in your notebook.

## 9. My Understanding

Answer in your own words:

1. What is system configuration?
2. What is the purpose of the `/etc` directory in Linux?
3. What are environment variables?
4. What is the purpose of `msconfig`?
5. How can incorrect configuration create security vulnerabilities?
6. Why should administrators back up important configuration files?

## 10. Related Notes

- [[System Updates]]
- [[Service Management]]
- [[Permission Management]]
- [[User Account Management]]
- [[System Hardening]]
- [[Operating System Security]]
- [[Linux File System]]
- [[Windows File System]]

---

**Key Takeaway:** System configuration controls how an operating system behaves. Secure configuration is essential for reliability, administration, and cybersecurity.