>Linux architecture describes how different components of a Linux operating system work together to manage hardware, execute applications, and provide system services.

The Linux operating system can be understood through several layers:

```
+--------------------------------+
|         Applications           |
+--------------------------------+
|      Shell and Utilities       |
+--------------------------------+
|       System Libraries         |
+--------------------------------+
|          Linux Kernel          |
+--------------------------------+
|           Hardware             |
+--------------------------------+
```

## 2. Main Components of Linux Architecture

### 2.1 Hardware

Hardware refers to the physical components of a computer.

Examples:

- CPU
- RAM
- Storage devices
- Network adapters
- Keyboard and mouse

The kernel manages access to these resources.

### 2.2 Kernel

The kernel is the core component of Linux.

Its responsibilities include:

- Process management.
- Memory management.
- Device management.
- File system management.
- Network management.
- Security enforcement.

Linux uses a monolithic kernel design with support for dynamically loadable kernel modules.

### 2.3 System Libraries

System libraries provide reusable functions that applications can use to interact with operating system services.

For example, the GNU C Library (glibc) provides interfaces commonly used by Linux applications.

### 2.4 Shell

A shell is a command interpreter that allows users to interact with the operating system.

Common Linux shells:

|Shell|Description|
|---|---|
|Bash|Bourne Again Shell|
|Zsh|Z Shell|
|Fish|Friendly Interactive Shell|
|Sh|Traditional Unix shell interface|

Example:

```
pwd
```

The shell interprets the command and invokes the appropriate functionality.

### 2.5 System Utilities

System utilities are programs used to manage and inspect the operating system.

Examples:

- `ls` – List directory contents.
- `cp` – Copy files.
- `mv` – Move or rename files.
- `ps` – Display process information.
- `ip` – Inspect network interfaces and routes.

### 2.6 Applications

Applications are programs that perform tasks for users.

Examples:

- Firefox
- Wireshark
- Nmap
- Burp Suite
- Text editors

## 3. User Mode and Kernel Mode

Linux separates execution into privilege levels.

### User Mode

Applications normally execute in user mode.

They have restricted access to hardware and protected kernel memory.

### Kernel Mode

The kernel executes with elevated privileges.

It can manage hardware, memory, processes, and other protected resources.

|User Mode|Kernel Mode|
|---|---|
|Restricted privileges|Elevated privileges|
|Runs normal applications|Runs kernel code|
|Cannot directly access protected kernel memory|Can access protected kernel memory|
|Requests services through system calls|Handles system calls|

## 4. How a Linux Command Works

Consider the command:

```
ls
```

Basic execution flow:

1. The user enters `ls` in the terminal.
2. The shell locates the executable.
3. The shell starts the program.
4. The program requests required operating system services.
5. The kernel performs the necessary operations.
6. The output is displayed in the terminal.

## 5. System Calls in Linux

A system call is a controlled interface through which a user-space program requests a service from the kernel.

Examples include:

|System Call|Purpose|
|---|---|
|`openat()`|Opens or accesses a file|
|`read()`|Reads data|
|`write()`|Writes data|
|`fork()`|Creates a child process|
|`execve()`|Executes a program|
|`socket()`|Creates a communication endpoint|

## 6. Linux Architecture and Cybersecurity

Understanding Linux architecture helps security professionals:

- Understand process execution.
- Investigate suspicious applications.
- Analyse system calls.
- Understand privilege boundaries.
- Investigate kernel-level threats.
- Troubleshoot security problems.

### Kernel-Level Threats

Malicious kernel modules or kernel vulnerabilities may allow attackers to gain highly privileged access.

A rootkit may attempt to hide malicious activity by manipulating operating system behaviour.

## 7. Practical: Inspect Linux Architecture

Open your Kali Linux terminal.

### Task 1: Identify Kernel Information

```
uname -a
```

### Task 2: Identify CPU Architecture

```
uname -m
```

### Task 3: Display CPU Information

```
lscpu
```

### Task 4: Display Memory Information

```
free -h
```

### Task 5: Display Kernel Modules

```
lsmod
```

### Task 6: Display System Information

```
hostnamectl
```

These commands inspect your system without intentionally modifying its configuration.

## 8. Important Commands

|Command|Purpose|
|---|---|
|`uname -a`|Displays kernel and system information|
|`lscpu`|Displays CPU information|
|`free -h`|Displays memory usage|
|`lsmod`|Lists loaded kernel modules|
|`hostnamectl`|Displays system identity information|
|`ps`|Displays running processes|

## 9. My Understanding

Answer these questions in your own words:

1. What is Linux architecture?
2. What is the role of the Linux kernel?
3. What is the purpose of system libraries?
4. What is the difference between user mode and kernel mode?
5. What is a system call?
6. How does a command such as `ls` interact with the kernel?
7. Why is kernel security important?

## 10. Practical Observations

Record your findings:

- Kernel version:
- CPU architecture:
- CPU model:
- Total RAM:
- Number of loaded kernel modules:
- One interesting observation:

## Related Topics

- [[Introduction to Linux]]
- [[Kernel]]
- [[Shell]]
- [[Linux File System]]
- [[Linux Processes]]
- [[System Calls]]
- [[Operating System Security]]

---

**Category:** Linux Operating System

**Status:** Learning