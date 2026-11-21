> A collection of practical exercises for learning Windows administration, system inspection, security, and troubleshooting using PowerShell.

## 1. Lab Environment

**Requirements:**

- Windows 10 or Windows 11.
- Windows PowerShell or PowerShell 7.
- A standard Windows user account.
- Administrator access only when required.

**Important:** Start with normal user privileges. Use an elevated PowerShell session only when a task specifically requires it.

## 2. Lab 01 — Basic PowerShell Navigation

### Objective

Understand how to navigate directories and inspect files.

### Commands

```
Get-Location
```

Displays the current directory.

```
Get-ChildItem
```

Lists files and directories.

```
Set-Location Desktop
```

Changes the current directory.

```
New-Item -ItemType Directory -Name PS_Lab
```

Creates a directory.

```
Get-ChildItem -Force
```

Displays hidden items as well.

### Tasks

1. Display your current directory.
2. List its contents.
3. Create a directory named `PS_Lab`.
4. Enter that directory.
5. Verify your location.

## 3. Lab 02 — File Management

### Objective

Create, inspect, copy, move, and delete files.

### Commands

```
New-Item -ItemType File -Name notes.txt
```

Creates a file.

```
Set-Content notes.txt "Learning PowerShell"
```

Writes text into the file, replacing existing content.

```
Get-Content notes.txt
```

Reads file contents.

```
Add-Content notes.txt "Practicing file management"
```

Appends text.

```
Copy-Item notes.txt notes-copy.txt
```

Copies the file.

```
Rename-Item notes-copy.txt backup.txt
```

Renames the copy.

```
Remove-Item backup.txt
```

Deletes the copy.

### Tasks

1. Create a text file.
2. Write two lines into it.
3. Display its contents.
4. Copy and rename it.
5. Delete only the copy.

## 4. Lab 03 — System Information

### Objective

Collect basic information about Windows.

### Commands

```
hostname
```

Displays the computer name.

```
Get-ComputerInfo
```

Displays detailed system information.

```
Get-CimInstance Win32_OperatingSystem
```

Displays operating system information.

```
Get-CimInstance Win32_Processor
```

Displays processor information.

```
Get-CimInstance Win32_LogicalDisk
```

Displays logical disk information.

### Tasks

Record:

- Computer name.
- Windows version.
- Processor name.
- Total RAM.
- Available disk space.

## 5. Lab 04 — User and Group Inspection

### Objective

Understand local Windows accounts and groups.

### Commands

```
whoami
```

Displays the current username.

```
whoami /groups
```

Displays group memberships.

```
Get-LocalUser
```

Lists local user accounts.

```
Get-LocalGroup
```

Lists local groups.

```
Get-LocalGroupMember -Group "Administrators"
```

Lists members of the local Administrators group.

### Tasks

1. Identify your current user.
2. List local accounts.
3. Identify the Administrators group.
4. Inspect its members.

## 6. Lab 05 — Process Management

### Objective

Inspect running processes and their resource usage.

### Commands

```
Get-Process
```

Lists running processes.

```
Get-Process | Sort-Object CPU -Descending
```

Sorts processes by reported CPU time.

```
Get-Process | Sort-Object WorkingSet -Descending
```

Sorts processes by memory usage.

```
Get-Process -Name explorer
```

Displays the Explorer process, if running.

```
Get-Process | Measure-Object
```

Counts the returned process objects.

### Tasks

1. List running processes.
2. Identify the process with the highest reported CPU time.
3. Identify a process using significant memory.
4. Record three process names and their IDs.

## 7. Lab 06 — Service Management

### Objective

Inspect Windows services.

### Commands

```
Get-Service
```

Lists services.

```
Get-Service | Where-Object {$_.Status -eq "Running"}
```

Lists running services.

```
Get-Service | Where-Object {$_.Status -eq "Stopped"}
```

Lists stopped services.

```
Get-Service -Name Spooler
```

Inspects the Print Spooler service.

### Tasks

1. Find three running services.
2. Find two stopped services.
3. Record their service names and status.
4. Research the purpose of one service.

Do not stop or disable services during this exercise.

## 8. Lab 07 — Network Inspection

### Objective

Inspect basic network configuration.

### Commands

```
ipconfig
```

Displays IP configuration.

```
ipconfig /all
```

Displays detailed network configuration.

```
Get-NetIPConfiguration
```

Displays network interface configuration.

```
Get-NetTCPConnection
```

Displays TCP connections.

```
Get-NetIPAddress
```

Displays configured IP addresses.

### Tasks

1. Identify your IPv4 address.
2. Identify your default gateway.
3. Identify your DNS servers.
4. Inspect established TCP connections.

## 9. Lab 08 — Security Inspection

### Objective

Inspect basic Windows security settings.

### Commands

```
Get-NetFirewallProfile
```

Displays firewall profile settings.

```
Get-MpComputerStatus
```

Displays Microsoft Defender status, if available.

```
whoami /priv
```

Displays assigned privileges.

```
Get-HotFix
```

Lists installed hotfixes.

### Tasks

1. Inspect firewall profiles.
2. Check antivirus status.
3. Review assigned privileges.
4. Identify recently installed hotfixes.

## 10. Lab 09 — Event Log Investigation

### Objective

Read Windows event logs.

### Commands

```
Get-WinEvent -ListLog *
```

Lists available event logs.

```
Get-WinEvent -LogName System -MaxEvents 10
```

Displays recent System events.

```
Get-WinEvent -LogName Application -MaxEvents 10
```

Displays recent Application events.

```
Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4625
} -MaxEvents 10
```

Searches for failed logon events.

### Tasks

1. Display recent System events.
2. Display recent Application events.
3. Search for failed logon events.
4. Record one event ID and explain its meaning.

Some Security log queries require administrator permissions.

## 11. Lab 10 — PowerShell Scripting

### Objective

Create and execute a basic PowerShell script.

Create a file named `system-info.ps1`.

Add:

```
Write-Host "SYSTEM INFORMATION"

Write-Host "Computer Name:"
hostname

Write-Host "Current User:"
whoami

Write-Host "Operating System:"
(Get-CimInstance Win32_OperatingSystem).Caption

Write-Host "Current Date:"
Get-Date
```

Save the file.

Run it from its directory:

```
.\system-info.ps1
```

If script execution is blocked, inspect the current execution policy with:

```
Get-ExecutionPolicy -List
```

Do not weaken system-wide execution policies just to run this beginner exercise.

### Tasks

1. Create the script.
    
2. Execute it.
    
3. Understand each command.
    
4. Add a command that displays your computer's IP configuration.
    

## 12. Lab Documentation Template

Record every practical exercise using this format:

### Lab Name

**Objective:**

What am I trying to learn?

**Commands Used:**

List the commands executed.

**Observations:**

What output did I receive?

**Analysis:**

What does the output mean?

**Result:**

What did I successfully verify?

**Questions:**

What do I still need to understand?

## 13. Learning Principles

- Understand commands before executing them.
    
- Prefer read-only inspection before making changes.
    
- Use administrator privileges only when necessary.
    
- Never run unknown scripts without reviewing them.
    
- Record important commands and observations.
    
- Repeat exercises until you can explain the results.
    

## Related Notes

- [[02 - Operating Systems]]
    
- [[Windows Architecture]]
    
- [[Windows Commands]]
    
- [[Windows Users and Groups]]
    
- [[Windows Permissions]]
    
- [[Windows Services]]
    
- [[Windows Processes]]
    
- [[Windows Event Logs]]
    
- [[System Administration]]
    
- [[Operating System Security]]
    
- [[07 - Practical Labs]]