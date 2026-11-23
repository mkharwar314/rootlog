> Understand how operating systems create, monitor, and manage running processes.

## 1. Lab Objectives

- Identify running processes.
- Understand Process IDs (PID).
- Monitor CPU and memory usage.
- Inspect process details.
- Understand parent and child processes.
- Safely stop a test process.
- Learn why process monitoring matters in cybersecurity.

## 2. Important Concepts

|Concept|Meaning|
|---|---|
|Process|A running instance of a program.|
|PID|Unique process identifier.|
|PPID|Parent Process ID.|
|CPU Usage|Amount of processor capacity used.|
|Memory Usage|Amount of RAM used by a process.|
|Foreground Process|Process interacting with the terminal.|
|Background Process|Process running without direct terminal interaction.|
|Process Termination|Ending a running process.|

## 3. Windows Process Management

Open PowerShell.

### Lab 1 — List Running Processes

```
Get-Process
```

Display selected information:

```
Get-Process | Select-Object Name, Id, CPU
```

**Observe:**

- Process name.
- Process ID.
- CPU usage.

### Lab 2 — Find a Specific Process

```
Get-Process -Name explorer
```

Try:

```
Get-Process -Name notepad
```

If Notepad is not running, open it first.

### Lab 3 — Inspect Process Details

```
Get-Process notepad | Format-List *
```

Observe the process information, including its ID and resource usage.

### Lab 4 — Monitor Processes

```
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10
```

This displays processes with the highest accumulated CPU time.

To inspect memory usage:

```
Get-Process | Sort-Object WorkingSet64 -Descending | Select-Object -First 10 Name, Id, WorkingSet64
```

`WorkingSet64` represents the physical memory currently used by a process.

## 4. Windows Process Control

### Lab 5 — Start a Test Process

Open Notepad using PowerShell:

```
Start-Process notepad
```

Find its process ID:

```
Get-Process notepad
```

### Lab 6 — Stop the Test Process

After identifying the correct Notepad process:

```
Stop-Process -Name notepad
```

Verify:

```
Get-Process notepad
```

If no Notepad process is running, PowerShell will report that it cannot find one.

**Safety:** Only stop your own test process. Never terminate unfamiliar system or security processes.

## 5. Linux Process Management

Open your Kali Linux terminal.

### Lab 7 — List Running Processes

```
ps
```

Display processes with more details:

```
ps aux
```

Understand the columns:

|Column|Meaning|
|---|---|
|USER|Process owner|
|PID|Process ID|
|%CPU|CPU usage|
|%MEM|Memory usage|
|COMMAND|Executed command|

### Lab 8 — Find a Process

```
pgrep -a bash
```

Search for a particular process:

```
ps aux | grep firefox
```

The `grep` command may also appear in its own search results.

### Lab 9 — Inspect Process Relationships

```
ps -ef
```

Display processes in a tree:

```
pstree -p
```

If `pstree` is unavailable, install the `psmisc` package using your distribution's package manager.

Observe the relationship between parent and child processes.

## 6. Linux Resource Monitoring

### Lab 10 — Monitor Processes

```
top
```

Press `q` to exit.

If installed, use:

```
htop
```

`htop` provides an interactive process-monitoring interface.

### Lab 11 — Check a Process by PID

```
sleep 300 &
```

This starts a harmless test process in the background.

Display its PID:

```
echo $!
```

Inspect it:

```
ps -p PID -f
```

Replace `PID` with the actual number returned by the previous command.

## 7. Linux Process Control

### Lab 12 — Terminate the Test Process

Use the actual PID from Lab 11:

```
kill PID
```

Verify that it has stopped:

```
ps -p PID
```

If no process is displayed, it has exited.

Use `kill -9` only as a last resort. It forcibly terminates a process without allowing normal cleanup.

Never use it on unfamiliar system processes.

## 8. Process Management and Cybersecurity

Process monitoring is useful for identifying:

- Unexpected programs.
- Suspicious background activity.
- Unusual CPU or memory consumption.
- Unauthorized software.
- Processes launched by unexpected parent processes.
- Potentially malicious scripts or binaries.

However, a high CPU usage value or an unfamiliar process name does not automatically mean malware. Investigate the executable path, parent process, user account, command line, and related system events.

## 9. Lab Documentation

|Field|Details|
|---|---|
|Lab Name||
|Operating System||
|Process Name||
|PID||
|Parent PID||
|CPU Usage||
|Memory Usage||
|Commands Used||
|Observations||
|Security Relevance||

## 10. Questions to Investigate

1. What is the difference between a program and a process?
2. Why does every process have a PID?
3. What is a parent process?
4. What happens when a process is terminated?
5. How can process monitoring help identify suspicious activity?
6. Why is forcefully terminating a process potentially risky?

## Related Notes

- [[Process Management]]
- [[Windows Processes]]
- [[Linux Processes]]
- [[Memory Management]]
- [[CPU Scheduling]]
- [[Operating System Security]]
- [[Security Auditing]]
- [[Windows Event Logs]]

---