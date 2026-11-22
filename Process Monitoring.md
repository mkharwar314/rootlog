## 1. What Is Process Monitoring?

Process monitoring is the process of observing running processes and tracking their resource usage and behaviour.

Administrators use process monitoring to understand system performance, identify problems, and detect suspicious activity.

## 2. Why Is Process Monitoring Important?

It helps administrators:

- Monitor CPU usage.
- Monitor memory consumption.
- Identify resource-intensive processes.
- Detect unresponsive applications.
- Investigate suspicious processes.
- Troubleshoot performance problems.
- Understand system activity.

## 3. What Information Can Be Monitored?

|Information|Meaning|
|---|---|
|PID|Process Identifier.|
|PPID|Parent Process Identifier.|
|CPU Usage|CPU resources consumed by a process.|
|Memory Usage|Memory currently used by a process.|
|Process Name|Name of the running process.|
|Process Owner|User associated with the process.|
|Process State|Current execution state.|
|Start Time|When the process started.|

## 4. Process Monitoring in Windows

Windows provides Task Manager, Resource Monitor, and PowerShell for monitoring processes.

### A. Task Manager

1. Press `Ctrl + Shift + Esc`.
2. Open the Processes tab.
3. Observe CPU usage.
4. Observe Memory usage.
5. Identify applications using significant resources.

### B. PowerShell Commands

List running processes:

```
Get-Process
```

Display selected process information:

```
Get-Process |
Select-Object ProcessName, Id, CPU, WorkingSet
```

Sort by CPU time:

```
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 10 ProcessName, Id, CPU
```

Sort by memory usage:

```
Get-Process |
Sort-Object WorkingSet -Descending |
Select-Object -First 10 ProcessName, Id, WorkingSet
```

Find a process by name:

```
Get-Process -Name "notepad"
```

The `CPU` property in `Get-Process` represents accumulated processor time, not instantaneous CPU percentage.

## 5. Process Monitoring in Linux

Linux provides several commands for observing processes.

### A. ps

Display running processes:

```
ps aux
```

Display process IDs and parent process IDs:

```
ps -eo pid,ppid,user,stat,comm
```

### B. top

Display live process information:

```
top
```

Press `q` to exit.

### C. htop

An interactive process-monitoring tool:

```
htop
```

It may need to be installed separately.

### D. free

Display memory usage:

```
free -h
```

### E. uptime

Display system uptime and load averages:

```
uptime
```

## 6. Understanding CPU and Memory Usage

### CPU Usage

CPU usage indicates how much processing capacity a process consumes over a particular period.

High CPU usage may be normal for demanding applications, but unexpected sustained usage can indicate a problem.

### Memory Usage

Memory usage indicates how much RAM a process is using.

A process consuming excessive memory may reduce system performance or contribute to resource exhaustion.

## 7. Parent and Child Processes

Processes can create other processes.

- Parent process: A process that creates another process.
- Child process: A process created by another process.

The relationship can be investigated using PID and PPID.

Example:

```
ps -eo pid,ppid,comm
```

This is useful when investigating unexpected process activity.

## 8. Process Monitoring and Cybersecurity

Process monitoring is an important part of security investigation.

Analysts may look for:

- Unexpected process names.
- Processes running from unusual directories.
- Suspicious parent-child relationships.
- Unusual CPU or memory consumption.
- Unknown processes running under privileged accounts.
- Unexpected network connections.
- Processes that restart after termination.

**Important:** A high CPU process or unfamiliar process name does not automatically indicate malware. Investigate its path, owner, parent process, behaviour, and context.

Related: [[Digital Forensics]], [[Operating System Security]], [[Windows Event Logs]]

## 9. Practical Lab — Monitor Processes

### Lab A: Windows PowerShell

Run:

```
Get-Process
```

Display the top ten processes by memory usage:

```
Get-Process |
Sort-Object WorkingSet -Descending |
Select-Object -First 10 ProcessName, Id, WorkingSet
```

Display process information with parent process IDs:

```
Get-CimInstance Win32_Process |
Select-Object ProcessId, ParentProcessId, Name
```

### Lab B: Kali Linux

Run:

```
ps aux
```

Display process relationships:

```
ps -eo pid,ppid,user,stat,comm
```

Open the live process monitor:

```
top
```

Press `q` to exit.

## 10. Practical Tasks

1. Open Task Manager in Windows.
2. Identify three processes consuming CPU resources.
3. Identify three processes consuming memory.
4. Run `Get-Process` in PowerShell.
5. Run `ps aux` in Kali.
6. Identify the PID and PPID of five processes.
7. Compare process monitoring in Windows and Linux.

Record your observations in your notebook.

## 11. My Understanding

Answer in your own words:

1. What is process monitoring?
2. What is the difference between PID and PPID?
3. What does CPU usage indicate?
4. How can you monitor processes in Windows?
5. How can you monitor processes in Linux?
6. How can process monitoring help detect suspicious activity?

## 12. Related Notes

- [[Process Management]]
- [[Windows Processes]]
- [[Linux Processes]]
- [[Multitasking]]
- [[CPU Scheduling]]
- [[Operating System Security]]
- [[Digital Forensics]]
- [[Windows Event Logs]]

---

**Key Takeaway:** Process monitoring helps administrators understand system activity, troubleshoot performance issues, and investigate potentially suspicious behaviour.