> Understand how Linux creates, manages, monitors, and terminates running programs.

## 1. What Is a Process?

A process is an instance of a program that is currently executing.

Examples:

- A running web browser.
- A terminal session.
- An SSH server.
- A Python script.

A program is a set of instructions stored on disk. A process is that program in execution.

## 2. Important Process Identifiers

Linux uses identifiers to track processes.

|Term|Meaning|
|---|---|
|PID|Process Identifier|
|PPID|Parent Process Identifier|
|UID|User Identifier associated with the process|
|GID|Group Identifier associated with the process|

Every process has a PID.

Find your current shell's PID:

```
echo $$
```

## 3. Parent and Child Processes

Processes can create other processes.

- Parent process: Creates another process.
- Child process: Created by a parent process.

A child process usually inherits certain attributes from its parent, although some attributes can change.

View process relationships:

```
ps -ef
```

Look at the PID and PPID columns.

## 4. Process States

Linux processes can exist in different states.

|State|Meaning|
|---|---|
|R|Running or runnable|
|S|Interruptible sleep|
|D|Uninterruptible sleep, commonly waiting for I/O|
|T|Stopped or traced|
|Z|Zombie process|

A zombie process has finished execution, but its parent has not yet collected its exit status.

## 5. Important Process Commands

|Command|Purpose|
|---|---|
|`ps`|Displays process information|
|`top`|Monitors processes in real time|
|`htop`|Interactive process monitor, if installed|
|`pgrep`|Finds processes by name or other criteria|
|`pidof`|Finds PIDs associated with a program|
|`kill`|Sends a signal to a process|
|`pkill`|Sends a signal to matching processes|
|`nice`|Starts a process with a scheduling priority adjustment|
|`renice`|Changes the priority adjustment of a running process|
|`jobs`|Lists jobs in the current shell|
|`bg`|Resumes a stopped job in the background|
|`fg`|Brings a job to the foreground|

## 6. Understanding ps

`ps` displays information about running processes.

Show processes associated with your terminal:

```
ps
```

Show processes from all users:

```
ps aux
```

Show processes in full-format listing:

```
ps -ef
```

Important columns include:

- PID: Process identifier.
- USER: Process owner.
- %CPU: CPU usage.
- %MEM: Memory usage.
- COMMAND: Command associated with the process.

## 7. Understanding top

`top` provides real-time process monitoring.

Run:

```
top
```

It displays information such as:

- CPU utilization.
- Memory utilization.
- Running processes.
- Process IDs.
- Process owners.

Press `q` to exit.

## 8. Understanding Process Signals

Linux uses signals to communicate with processes.

|Signal|Number|Purpose|
|---|---|---|
|SIGHUP|1|Hangup|
|SIGINT|2|Interrupt|
|SIGKILL|9|Force termination|
|SIGTERM|15|Request termination|
|SIGSTOP|19|Stop a process|

The exact numeric signal values can vary across architectures.

### SIGTERM vs SIGKILL

**SIGTERM (15):**

- Requests that a process terminate.
- Allows the process to perform cleanup.
- Is generally the preferred first attempt.

**SIGKILL (9):**

- Forces the kernel to terminate a process.
- Cannot be caught or ignored by the process.
- Should be used only when necessary.

Example syntax:

```
kill -TERM PID
```

Replace `PID` with the actual process ID.

## 9. Foreground and Background Processes

A foreground process runs while the terminal waits for it to finish.

A background process runs without keeping the terminal occupied.

Example:

```
sleep 60
```

Press `Ctrl + Z` to suspend it.

Resume it in the background:

```
bg
```

Bring it back to the foreground:

```
fg
```

You can also start a command in the background:

```
sleep 60 &
```

## 10. Process Priority

Linux uses scheduling priorities to manage CPU time.

The `nice` value generally ranges from `-20` to `19`.

|Nice value|Relative priority|
|---|---|
|-20|Highest scheduling priority|
|0|Default|
|19|Lowest scheduling priority|

Examples:

```
nice -n 10 sleep 60
```

Inspect process priority:

```
ps -o pid,ni,comm -p PID
```

Replace `PID` with the actual process ID.

Changing a process's nice value may require additional privileges.

## 11. Cybersecurity Importance

Process monitoring is important in security investigations.

Security analysts examine processes to identify:

1. Unknown or suspicious programs.
2. Unexpected processes running with elevated privileges.
3. Unusual CPU or memory consumption.
4. Suspicious parent-child process relationships.
5. Unauthorized background programs.
6. Potential malware execution.

### Example: Suspicious Process Investigation

Suppose a Linux server shows an unknown process consuming excessive CPU.

An analyst may:

1. Identify the process using `top`.
2. Record its PID.
3. Inspect it using `ps`.
4. Identify its owner and parent process.
5. Investigate the executable and its origin.
6. Decide whether containment is necessary.

High CPU usage alone does not prove malware.

## 12. Practical Lab — Process Management

Run these commands in Kali Linux.

### Task 1 — Display your current shell PID

```
echo $$
```

### Task 2 — Display your processes

```
ps
```

### Task 3 — Display all processes

```
ps aux
```

### Task 4 — Monitor processes

```
top
```

Press `q` to exit.

### Task 5 — Start a background process

```
sleep 300 &
```

### Task 6 — Find the sleep process

```
pgrep -a sleep
```

### Task 7 — Inspect its details

```
ps -ef | grep '[s]leep'
```

### Task 8 — Terminate your test process

```
pkill -TERM -x sleep
```

This terminates processes named exactly `sleep` that your account is permitted to signal. If you have other sleep processes running, inspect them first rather than using this command.

### Task 9 — Verify termination

```
pgrep -a sleep
```

No output means no matching process was found.

## 13. Key Takeaways

- A process is a running instance of a program.
- Every process has a PID.
- Processes can create parent-child relationships.
- Linux processes have different execution states.
- `ps` displays process information.
- `top` monitors processes in real time.
- Signals are used to communicate with processes.
- Process monitoring helps identify suspicious activity.

## 14. My Understanding

Answer in your own words:

1. What is the difference between a program and a process?
2. What are PID and PPID?
3. What is a zombie process?
4. What is the difference between SIGTERM and SIGKILL?
5. Why do cybersecurity analysts monitor running processes?
6. Why should high CPU usage not automatically be treated as evidence of malware?

## Related Notes

- [[Linux Users and Groups]]
- [[Linux Permissions]]
- [[Linux Services]]
- [[Process Management]]
- [[Operating System Security]]
- [[Digital Forensics]]

---

**Category:** Linux Operating System

**Status:** Learning