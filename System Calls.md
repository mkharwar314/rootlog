> System calls provide a controlled interface through which user-space programs request services from the operating-system kernel.

## 1. What is a System Call?

A system call is a mechanism that allows an application to request a service from the operating-system kernel.

Applications generally cannot directly perform privileged operations. They use system calls to request the required services.

**Example:** When a program needs to read a file, it can request the operating system to perform the file operation.

## 2. Why Are System Calls Needed?

System calls are necessary because they:

- Allow applications to access OS services.
- Provide controlled access to hardware resources.
- Support file operations.
- Support process management.
- Enable communication between user programs and the kernel.
- Help enforce security boundaries.

## 3. How Does a System Call Work?

Consider an application opening a file.

1. The application requests a file operation.
2. It invokes the appropriate system-call interface.
3. The processor transfers control to the kernel through a controlled mechanism.
4. The kernel checks the request and performs the operation if permitted.
5. The result is returned to the application.

### Basic Architecture

```
+---------------------------+
|       Application         |
+---------------------------+
             |
             v
+---------------------------+
|      System Call API      |
+---------------------------+
             |
             v
+---------------------------+
|          Kernel           |
+---------------------------+
             |
             v
+---------------------------+
|          Hardware         |
+---------------------------+
```

## 4. Types of System Calls

### 4.1 Process Control

Used to create, execute, and terminate processes.

Examples:

- `fork()`
- `execve()`
- `exit()`

### 4.2 File Management

Used to perform file operations.

Examples:

- `open()`
- `read()`
- `write()`
- `close()`

### 4.3 Device Management

Used to interact with hardware devices.

Examples:

- `ioctl()`
- Device-specific operations

### 4.4 Information Maintenance

Used to obtain or update system information.

Examples:

- `getpid()`
- `uname()`

### 4.5 Communication

Used to exchange information between processes.

Examples:

- `pipe()`
- `socket()`
- `send()`
- `recv()`

## 5. System Call vs API

These concepts are related but not identical.

|System Call|API|
|---|---|
|Interface to kernel services|Interface for software components|
|Requests OS-level services|Provides functions for developers|
|Often involves a privilege transition|May or may not invoke a system call|
|Example: Linux `read()` system call|Example: Windows API|

**Important:** An API can internally use one or more system calls, but not every API call is a system call.

## 6. System Calls and Cybersecurity

System calls are important for security analysis because they help professionals understand how programs interact with the operating system.

They are useful for:

- Malware behavior analysis.
- Process monitoring.
- System activity investigation.
- Security auditing.
- Understanding privilege boundaries.
- Detecting suspicious program behavior.

**Example:** A security analyst may monitor unusual file access or process creation activity to investigate suspicious software.

## 7. Practical Observation

On Windows, open PowerShell.

**View running processes:**

```
Get-Process
```

**View process details:**

```
Get-CimInstance Win32_Process |
Select-Object Name, ProcessId, ParentProcessId
```

On Linux, you can inspect system-call activity using `strace`:

```
strace -c ls
```

This displays a summary of system calls made by the `ls` command. The Windows commands above show process information; they do not directly display system calls.

## 8. My Understanding

Answer in your own words:

1. What is a system call?
2. Why can't ordinary applications directly perform all privileged operations?
3. How does a system call connect an application to the kernel?
4. What is the difference between an API and a system call?
5. Why are system calls useful in malware analysis?

## 9. Knowledge Check

1. What is the purpose of a system call?
2. Which component handles system calls?
3. Which system call is commonly used to read a file in Linux?
4. What is `fork()` used for?
5. Does every API call invoke a system call?

## Related Notes

- [[02 - Operating Systems]]
- [[Introduction to Operating Systems]]
- [[Functions of an Operating System]]
- [[Kernel]]
- [[Shell]]
- [[Process Management]]
- [[File System]]
- [[Operating System Security]]
- [[Digital Forensics]]

---

**Category:** Operating System Fundamentals

**Status:** Learning