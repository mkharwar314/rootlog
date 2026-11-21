>Windows Services are programs that run in the background to perform specific operating system or application tasks.

They can operate without a user directly interacting with them.

Examples:

- Windows Update
- Windows Defender Antivirus Service
- Print Spooler
- DHCP Client
- Windows Event Log

## 2. Why Are Services Important?

Windows Services help the operating system:

- Manage network connections.
- Install system updates.
- Provide security protection.
- Manage printing.
- Record system events.
- Support applications and hardware.

## 3. How Services Work

A service is generally managed by the **Service Control Manager (SCM)**.

The SCM is responsible for starting, stopping, and managing Windows services.

Basic workflow:

1. Windows starts.
2. The Service Control Manager initializes.
3. Services configured for startup are started according to their dependencies and configuration.
4. Services perform their assigned tasks.
5. The SCM manages service control requests.

## 4. Types of Service Startup

|Startup Type|Description|
|---|---|
|Automatic|Starts automatically during system startup|
|Automatic (Delayed Start)|Starts automatically after other automatic services|
|Manual|Can be started when required|
|Disabled|Cannot normally be started until its startup configuration is changed|

**Note:** Trigger-start services may start automatically in response to specific system events.

## 5. Service States

|State|Description|
|---|---|
|Running|Service is currently running|
|Stopped|Service is not running|
|Paused|Service is temporarily paused|
|Start Pending|Service is in the process of starting|
|Stop Pending|Service is in the process of stopping|

Not every service supports pausing.

## 6. Service vs Process

A service and a process are not the same thing.

|Service|Process|
|---|---|
|Performs a background task managed through service infrastructure|A running instance of a program|
|Managed by the Service Control Manager|Managed by the operating system|
|Can be configured with a startup type|Has a process ID (PID)|
|May run inside a shared or separate process|Represents executing program code|

A single process can host multiple services.

## 7. Cybersecurity Importance

Services are important in cybersecurity because attackers may abuse them to:

- Maintain persistence.
- Execute malicious programs.
- Operate with excessive privileges.
- Disable security-related services.
- Hide malicious activity among legitimate services.

### Suspicious Service Indicators

Investigators may examine:

- Unusual service names.
- Unexpected executable paths.
- Unknown service publishers.
- Unexpected startup configurations.
- Services running with excessive privileges.

One suspicious indicator alone does not prove malicious activity.

## 8. Practical: Inspect Windows Services Using PowerShell

### Task 1: List All Services

```
Get-Service
```

### Task 2: Display Running Services

```
Get-Service | Where-Object {$_.Status -eq "Running"}
```

### Task 3: Display Stopped Services

```
Get-Service | Where-Object {$_.Status -eq "Stopped"}
```

### Task 4: Inspect a Specific Service

```
Get-Service -Name "Spooler"
```

### Task 5: Display Service Configuration

```
Get-CimInstance Win32_Service |
Select-Object Name, DisplayName, State, StartMode, StartName
```

### Task 6: Inspect Windows Update Service

```
Get-Service -Name "wuauserv"
```

## 9. Important Commands

|Command|Purpose|
|---|---|
|`Get-Service`|Lists Windows services|
|`Start-Service`|Starts a service|
|`Stop-Service`|Stops a service|
|`Restart-Service`|Restarts a service|
|`Set-Service`|Changes service configuration|
|`Get-CimInstance Win32_Service`|Retrieves detailed service information|

**Safety:** For this learning exercise, use inspection commands only. Do not stop, disable, or reconfigure services.

## 10. My Understanding

Answer these questions in your own words:

1. What is a Windows Service?
2. What is the Service Control Manager?
3. What is the difference between Automatic and Manual startup?
4. What is the difference between a service and a process?
5. How can attackers abuse Windows Services?
6. Why should unknown services be investigated carefully?

## 11. Practical Observations

Record your findings:

- Total services displayed:
- Number of running services:
- Number of stopped services:
- One service name:
- Its current status:
- Its startup mode:
- Its service account:

## Related Topics

- [[Windows Architecture]]
- [[Windows Processes]]
- [[Windows Users and Groups]]
- [[Windows Permissions]]
- [[Windows Event Logs]]
- [[Operating System Security]]
- [[Digital Forensics]]

---

**Category:** Windows Operating System

**Status:** Learning