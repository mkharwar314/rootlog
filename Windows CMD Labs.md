> A collection of practical exercises for learning Windows Command Prompt (CMD), system administration, networking, and troubleshooting.

## 1. Lab Environment

**Requirements:**

- Windows 10 or Windows 11.
- Command Prompt (CMD).
- A standard Windows user account.

Open CMD:

```
cmd
```

Check the CMD version:

```
ver
```

## 2. Lab 01 — Basic CMD Navigation

### Objective

Understand how to navigate directories.

### Commands

```
cd
```

Displays the current directory.

```
dir
```

Lists files and directories.

```
cd Desktop
```

Enters the Desktop directory.

```
cd ..
```

Moves one directory level up.

```
mkdir CMD_Lab
```

Creates a directory.

```
cd CMD_Lab
```

Enters the new directory.

### Tasks

1. Display your current directory.
2. List its contents.
3. Create a directory named `CMD_Lab`.
4. Enter that directory.
5. Verify your location.

## 3. Lab 02 — File Management

### Objective

Create, read, copy, rename, and delete files.

### Commands

```
echo Learning CMD > notes.txt
```

Creates a file and writes text into it.

```
type notes.txt
```

Displays file contents.

```
echo Practicing file management >> notes.txt
```

Appends text to the file.

```
copy notes.txt backup.txt
```

Copies the file.

```
ren backup.txt old-notes.txt
```

Renames the copy.

```
del old-notes.txt
```

Deletes the copy.

### Tasks

1. Create a text file.
2. Add two lines.
3. Display its contents.
4. Create a backup copy.
5. Rename and delete only the copy.

## 4. Lab 03 — System Information

### Objective

Collect basic information about Windows.

### Commands

```
hostname
```

Displays the computer name.

```
systeminfo
```

Displays detailed system information.

```
ver
```

Displays the Windows version information.

```
whoami
```

Displays the current user.

```
echo %USERNAME%
```

Displays the current username.

```
echo %COMPUTERNAME%
```

Displays the computer name.

### Tasks

Record:

- Computer name.
- Windows version.
- Current username.
- System architecture.
- Total physical memory.

## 5. Lab 04 — User and Group Inspection

### Objective

Inspect local Windows users and groups.

### Commands

```
whoami
```

Displays the current account.

```
net user
```

Lists local user accounts.

```
net user username
```

Displays information about a specific user.

Replace `username` with an actual account name.

```
net localgroup
```

Lists local groups.

```
net localgroup Administrators
```

Displays members of the local Administrators group.

### Tasks

1. List local accounts.
2. Inspect your account.
3. List local groups.
4. Identify members of the Administrators group.

## 6. Lab 05 — Process Management

### Objective

Inspect running processes.

### Commands

```
tasklist
```

Lists running processes.

```
tasklist /svc
```

Displays processes and their associated services.

```
tasklist /FI "IMAGENAME eq explorer.exe"
```

Filters processes by image name.

```
tasklist /FI "STATUS eq RUNNING"
```

Filters running processes.

```
tasklist /?
```

Displays command help.

### Tasks

1. Display running processes.
2. Find `explorer.exe`.
3. Record three process names and their PIDs.
4. Identify one process that you do not recognize and research its purpose.

## 7. Lab 06 — Service Management

### Objective

Inspect Windows services.

### Commands

```
sc query
```

Displays service information.

```
sc query state= all
```

Displays services in all states.

```
sc query Spooler
```

Inspects the Print Spooler service.

```
sc qc Spooler
```

Displays the service configuration.

### Tasks

1. Inspect the Print Spooler service.
2. Identify its current state.
3. Record its service name.
4. Research its purpose.

Do not stop or disable services during this exercise.

## 8. Lab 07 — Network Inspection

### Objective

Inspect network configuration and connectivity.

### Commands

```
ipconfig
```

Displays basic IP configuration.

```
ipconfig /all
```

Displays detailed network configuration.

```
ping 127.0.0.1
```

Tests the local TCP/IP stack using the loopback address.

```
ping google.com
```

Tests connectivity to a domain, subject to DNS and network availability.

```
tracert google.com
```

Displays the route taken by packets toward a destination.

```
nslookup google.com
```

Queries DNS information.

```
netstat -ano
```

Displays network connections and listening ports with associated PIDs.

### Tasks

1. Identify your IPv4 address.
2. Identify your default gateway.
3. Test loopback connectivity.
4. Perform a DNS lookup.
5. Inspect active network connections.

## 9. Lab 08 — File and Directory Permissions

### Objective

Inspect Windows file permissions.

### Commands

```
icacls .
```

Displays permissions for the current directory.

```
icacls notes.txt
```

Displays permissions for a specific file.

```
attrib notes.txt
```

Displays file attributes.

```
dir /a
```

Lists files, including hidden and system files.

### Tasks

1. Inspect permissions on a test file.
2. Identify its owner and permission entries where available.
3. Check its attributes.
4. Explain the difference between file attributes and access permissions.

Do not change permissions during this exercise.

## 10. Lab 09 — Event Log Inspection

### Objective

Open and inspect Windows Event Viewer.

### Commands

```
eventvwr.msc
```

Opens Event Viewer.

```
wevtutil el
```

Lists available event logs.

```
wevtutil qe System /c:10 /rd:true /f:text
```

Displays the ten most recent System log events.

```
wevtutil qe Application /c:10 /rd:true /f:text
```

Displays the ten most recent Application log events.

### Tasks

1. Open Event Viewer.
2. Inspect the System log.
3. Inspect the Application log.
4. Record one event ID and explain its meaning.

## 11. Lab 10 — Basic Troubleshooting

### Objective

Use CMD commands to diagnose common system and network issues.

### Commands

**Check network configuration**

```
ipconfig /all
```

**Test local connectivity**

```
ping 127.0.0.1
```

**Check DNS resolution**

```
nslookup google.com
```

**Inspect network routes**

```
route print
```

**Inspect active connections**

```
netstat -ano
```

**Check disk health status reported by Windows**

```
chkdsk C:
```

This checks the file system. It does not automatically repair errors.

### Tasks

1. Inspect your IP configuration.
2. Test loopback connectivity.
3. Check DNS resolution.
4. Display the routing table.
5. Record your observations.

## 12. Useful CMD Shortcuts

|Command|Purpose|
|---|---|
|`cls`|Clears the screen.|
|`exit`|Closes CMD.|
|`help`|Lists available commands.|
|`command /?`|Displays help for a command.|
|`history`|Not a standard CMD history command; use F7 to view command history in a typical interactive CMD session.|
|`doskey /history`|Displays command history.|
|`echo %PATH%`|Displays the PATH environment variable.|

## 13. Lab Documentation Template

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

## 14. Learning Principles

- Understand commands before executing them.
- Use test files for file-management exercises.
- Avoid modifying system configurations without understanding the impact.
- Do not execute unknown commands from the internet.
- Record command outputs and observations.
- Compare CMD commands with their PowerShell equivalents.

## Related Notes

- [[02 - Operating Systems]]
- [[Windows PowerShell Labs]]
- [[Windows Command Prompt (CMD)]]
- [[Windows Users and Groups]]
- [[Windows Permissions]]
- [[Windows Services]]
- [[Windows Processes]]
- [[Windows Event Logs]]
- [[System Administration]]
- [[Operating System Security]]
- [[07 - Practical Labs]]

---