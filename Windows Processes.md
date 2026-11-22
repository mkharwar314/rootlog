>A **process** is an instance of a program that is currently executing.

When you open an application, Windows creates a process to execute its instructions.

Examples:

- Notepad
- Google Chrome
- Windows Explorer
- PowerShell
- Task Manager

A process uses system resources such as CPU time, memory, and sometimes disk and network resources.

## 2. Program vs Process

|Program|Process|
|---|---|
|A stored set of instructions|A running instance of a program|
|Exists as a file on storage|Exists while executing|
|Does not necessarily use CPU or RAM for execution|Uses memory and other resources|
|Example: `notepad.exe` on disk|A running Notepad instance|

One program can have multiple processes.

## 3. Process Identification

Windows assigns each process a unique **Process ID (PID)** while it exists.

A PID helps the operating system and administrators identify and manage a process.

Example:

|Process Name|PID|
|---|---|
|notepad.exe|4200|
|explorer.exe|1850|
|powershell.exe|5120|

These are illustrative values, not actual process IDs.

## 4. Process States

A process may move through different execution states.

|State|Description|
|---|---|
|New|Process is being created|
|Ready|Waiting for CPU time|
|Running|Currently executing|
|Waiting/Blocked|Waiting for an event or resource|
|Terminated|Execution has ended|

Windows internally uses more detailed scheduling states.

## 5. Parent and Child Processes

A process can create another process.

- **Parent process:** Creates another process.
- **Child process:** Created by a parent process.

Example:

A PowerShell process may launch Notepad.

```
powershell.exe
      |
      └── notepad.exe
```

Process relationships are useful during security investigations because suspicious programs may launch other processes.

## 6. Process Resources

Processes use several system resources:

- CPU: Executes instructions.
- RAM: Stores active program data.
- Disk: Reads and writes files.
- Network: Communicates with other systems.
- Handles: References operating system resources.

## 7. Process vs Service

|Process|Service|
|---|---|
|Running instance of a program|Background component managed through Windows service infrastructure|
|Identified by a PID|Identified by a service name|
|Can run interactively or in the background|Usually performs background tasks|
|May be launched by a user or another process|Managed by the Service Control Manager|

A Windows service runs inside a process. Multiple services may share one process.

## 8. Cybersecurity Importance

Processes are important in cybersecurity because attackers may use them to:

- Execute malicious programs.
- Launch additional payloads.
- Run scripts.
- Inject code into other processes.
- Perform suspicious network activity.
- Hide malicious execution among legitimate processes.

### Suspicious Process Indicators

Investigators may examine:

- Unusual process names.
- Unexpected executable paths.
- Unknown publishers.
- Unusual parent-child relationships.
- Unexpected command-line arguments.
- Unusual CPU or memory usage.
- Unexpected network connections.

A process name alone is not enough to determine whether it is malicious.

## 9. Practical: Inspect Processes Using PowerShell

### Task 1: List Running Processes

```
Get-Process
```

### Task 2: Find Notepad

```
Get-Process -Name "notepad" -ErrorAction SilentlyContinue
```

### Task 3: Display Process IDs

```
Get-Process | Select-Object ProcessName, Id
```

### Task 4: Display CPU and Memory Information

```
Get-Process |
Select-Object ProcessName, Id, CPU, WorkingSet64
```

`WorkingSet64` represents the process's current physical memory working set in bytes.

### Task 5: Display Process Executable Paths

```
Get-CimInstance Win32_Process |
Select-Object ProcessId, ParentProcessId, Name, ExecutablePath
```

Some executable paths may be unavailable because of permissions or process restrictions.

### Task 6: Open Task Manager

Press:

```
Ctrl + Shift + Esc
```

Explore:

- Processes
- Performance
- Details
- Startup apps

## 10. Important Commands

|Command|Purpose|
|---|---|
|`Get-Process`|Lists processes|
|`Get-Process -Name`|Finds a process by name|
|`Stop-Process`|Terminates a process|
|`Start-Process`|Starts a program or process|
|`Get-CimInstance Win32_Process`|Retrieves detailed process information|

**Safety:** Use inspection commands only during this exercise. Do not terminate unfamiliar processes.

## 11. My Understanding

Answer these questions in your own words:

1. What is a process?
2. What is the difference between a program and a process?
3. What is a PID?
4. What is a parent-child process relationship?
5. How can attackers abuse processes?
6. Why should investigators examine executable paths and command-line arguments?

## 12. Practical Observations

Record your findings:

- Total processes displayed:
- One process name:
- Its PID:
- Its memory usage:
- Its executable path:
- One observation from Task Manager:

## Related Topics

- [[Windows Architecture]]
- [[Windows Services]]
- [[Process Management]]
- [[Memory Management]]
- [[Windows Event Logs]]
- [[Digital Forensics]]
- [[Operating System Security]]

---

**Category:** Windows Operating System

**Status:** Learning