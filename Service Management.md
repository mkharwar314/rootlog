## 1. What Is Service Management?

Service management is the process of controlling and maintaining background services that provide functionality to an operating system or applications.

A service can run without requiring a user to interact with it directly.

Examples:

- Windows Update
    
- Windows Defender services
    
- SSH service
    
- Web server services
    
- Database services
    

## 2. What Is a Service?

A service is a background program that performs a specific function.

Examples:

|Service|Purpose|
|---|---|
|Windows Update|Manages Windows updates.|
|Print Spooler|Manages printing tasks.|
|SSH|Provides secure remote login.|
|Apache|Provides web server functionality.|
|Cron|Runs scheduled tasks on Linux.|

## 3. Services in Windows

Windows uses the **Service Control Manager (SCM)** to manage services.

Services can be configured to start:

- Automatically.
- Automatically with delayed start.
- Manually.
- Disabled.

### Open Windows Services

1. Press `Win + R`.
2. Type `services.msc`.
3. Press Enter.
4. Inspect the available services.

### Important PowerShell Commands

List services:

```
Get-Service
```

Find a specific service:

```
Get-Service -Name "Spooler"
```

Display running services:

```
Get-Service | Where-Object Status -eq "Running"
```

Display stopped services:

```
Get-Service | Where-Object Status -eq "Stopped"
```

Inspect detailed service configuration:

```
Get-CimInstance Win32_Service |
Select-Object Name, DisplayName, State, StartMode
```

## 4. Services in Linux

Linux commonly uses `systemd` as its service and system manager.

The `systemctl` command is used to inspect and manage systemd services.

### Important Commands

Check systemd status:

```
systemctl status
```

List running services:

```
systemctl list-units --type=service --state=running
```

List all service units:

```
systemctl list-unit-files --type=service
```

Check a specific service:

```
systemctl status ssh
```

The SSH service may not be installed or enabled on every system.

## 5. Service States

Common service states include:

|State|Meaning|
|---|---|
|Running / Active|Service is currently running.|
|Stopped / Inactive|Service is not currently running.|
|Failed|Service encountered an error.|
|Enabled|Configured to start automatically when applicable.|
|Disabled|Prevented from starting automatically.|

**Important:** Enabled does not necessarily mean running. A service can be enabled but currently inactive.

## 6. Service Management Commands

### Windows

Start a service:

```
Start-Service -Name "Spooler"
```

Stop a service:

```
Stop-Service -Name "Spooler"
```

Restart a service:

```
Restart-Service -Name "Spooler"
```

These commands change system state and may require administrator privileges. Do not run them during the introductory inspection lab.

### Linux

Start a service:

```
sudo systemctl start ssh
```

Stop a service:

```
sudo systemctl stop ssh
```

Restart a service:

```
sudo systemctl restart ssh
```

Enable a service at boot:

```
sudo systemctl enable ssh
```

Disable automatic startup:

```
sudo systemctl disable ssh
```

These commands modify service configuration or state. Use them only when you understand the effect and have authorization.

## 7. Service Management and Cybersecurity

Services are important attack surfaces because they may expose network ports, process requests, or operate with elevated privileges.

Security risks include:

- Unnecessary services increasing the attack surface.
- Vulnerable services being exploited.
- Weak service permissions.
- Exposed remote-access services.
- Services running with excessive privileges.
- Unauthorized or malicious services maintaining persistence.

### Security Best Practices

- Disable services that are genuinely unnecessary.
- Keep services updated.
- Restrict network access.
- Use least-privilege service accounts.
- Monitor unexpected service changes.
- Review service logs.
- Secure remote-access services.

**Important:** Do not disable a service simply because you do not recognize its name. It may be required by the operating system or another application.

## 8. Practical Lab — Inspect Services

### Lab A: Windows PowerShell

List services:

```
Get-Service
```

Find running services:

```
Get-Service |
Where-Object Status -eq "Running"
```

Inspect service configuration:

```
Get-CimInstance Win32_Service |
Select-Object Name, State, StartMode, StartName
```

Record five services and their current states.

### Lab B: Kali Linux

Check the system manager:

```
systemctl status
```

List running services:

```
systemctl list-units --type=service --state=running
```

Inspect service unit files:

```
systemctl list-unit-files --type=service
```

Check SSH if available:

```
systemctl status ssh
```

If SSH is not installed, record that observation rather than installing it.

## 9. Practical Tasks

1. Open `services.msc` in Windows.
2. Identify five running services.
3. Inspect their startup configuration.
4. Run `Get-Service` in PowerShell.
5. Run `systemctl` commands in Kali.
6. Identify one service that provides network functionality.
7. Explain why unnecessary services can increase security risks.

Do not stop, start, enable, or disable services during this lab.

## 10. My Understanding

Answer in your own words:

1. What is a service?
2. What is the Windows Service Control Manager?
3. What is `systemd`?
4. What is the difference between enabled and running?
5. Why can unnecessary services create security risks?
6. Why should services follow the principle of least privilege?

## 11. Related Notes

- [[Windows Services]]
- [[Linux Services]]
- [[User Account Management]]
- [[Permission Management]]
- [[Privilege Management]]
- [[System Hardening]]
- [[Operating System Security]]

---

**Key Takeaway:** Service management controls background services that support an operating system. Proper configuration and monitoring help reduce the system's attack surface.