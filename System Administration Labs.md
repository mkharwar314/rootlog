> Learn how to inspect, configure, and maintain an operating system safely.

## 1. Lab Objectives

- Understand basic system administration.
- Inspect system information.
- Monitor system resources.
- Manage services.
- Check system updates.
- Inspect system logs.
- Understand basic maintenance and security practices.

## 2. Windows System Administration

Open PowerShell.

### Lab 1 — Inspect System Information

```
Get-ComputerInfo
```

Display selected information:

```
Get-ComputerInfo | Select-Object WindowsProductName, WindowsVersion, OsArchitecture
```

### Lab 2 — Check Disk Information

```
Get-Volume
```

Check free and used space:

```
Get-PSDrive -PSProvider FileSystem
```

### Lab 3 — Monitor System Resources

```
Get-CimInstance Win32_OperatingSystem |
Select-Object TotalVisibleMemorySize, FreePhysicalMemory
```

Inspect CPU information:

```
Get-CimInstance Win32_Processor |
Select-Object Name, NumberOfCores, NumberOfLogicalProcessors
```

### Lab 4 — Inspect Windows Services

List services:

```
Get-Service
```

Find running services:

```
Get-Service | Where-Object Status -eq "Running"
```

Inspect a particular service:

```
Get-Service -Name Spooler
```

Do not stop or disable unfamiliar services.

### Lab 5 — Inspect Windows Updates

Open Windows Settings:

1. Go to **Windows Update**.
2. Check for available updates.
3. Review update history.
4. Record the latest installed update.

You can also inspect update-related events using Event Viewer.

## 3. Linux System Administration

Open your Kali Linux terminal.

### Lab 6 — Inspect System Information

```
hostnamectl
```

Check kernel information:

```
uname -a
```

Check operating system details:

```
cat /etc/os-release
```

### Lab 7 — Monitor System Resources

Check memory:

```
free -h
```

Check disk usage:

```
df -h
```

Check directory size:

```
du -sh ~
```

### Lab 8 — Inspect Services

List running services:

```
systemctl list-units --type=service --state=running
```

Inspect a service:

```
systemctl status ssh
```

The SSH service may not be installed or running. That is not necessarily an error.

Do not enable or disable services unless you understand their purpose.

### Lab 9 — Inspect System Logs

Display recent system logs:

```
journalctl -n 30
```

Display logs from the current boot:

```
journalctl -b
```

Inspect authentication-related logs where available:

```
sudo journalctl | grep -i "authentication"
```

Log availability and access permissions depend on the system configuration.

## 4. System Update Management

### Windows

- Open Windows Update.
- Check available updates.
- Review update history.
- Understand why security updates matter.

### Linux

Inspect package information:

```
apt list --upgradable
```

Refresh package information:

```
sudo apt update
```

This updates package metadata; it does not install upgrades.

Review available upgrades before installing them:

```
sudo apt upgrade
```

Do not interrupt an active package-management operation.

## 5. Basic System Maintenance

Record the following checks:

|Maintenance task|Windows|Linux|
|---|---|---|
|Check system version|Get-ComputerInfo|cat /etc/os-release|
|Check disk space|Get-Volume|df -h|
|Check memory|Get-CimInstance|free -h|
|Inspect services|Get-Service|systemctl|
|Inspect processes|Get-Process|ps|
|Inspect logs|Event Viewer|journalctl|
|Check updates|Windows Update|apt|

## 6. Security Relevance

System administration is closely connected to cybersecurity.

Important security practices:

- Apply security patches regularly.
- Remove unnecessary software.
- Disable unused services only after evaluating their dependencies.
- Review user accounts and privileges.
- Monitor system logs.
- Maintain backups.
- Investigate unusual resource consumption.
- Keep security tools updated.

## 7. Lab Documentation

|Field|Details|
|---|---|
|Lab Name||
|Operating System||
|Commands Used||
|System Information||
|Observations||
|Problems Encountered||
|Security Relevance||

## 8. Questions to Investigate

1. Why are operating system updates important?
2. What is the purpose of a system service?
3. What is the difference between system monitoring and system auditing?
4. Why should unnecessary services be reviewed?
5. How can system logs help during an incident investigation?
6. What could happen if a system is not maintained?

## Related Notes

- [[System Administration]]
- [[System Configuration]]
- [[Service Management]]
- [[Process Monitoring]]
- [[System Updates]]
- [[Windows Event Logs]]
- [[Linux Services]]
- [[Security Auditing]]
- [[System Hardening]]

---