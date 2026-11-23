> The kernel is the core component of an operating system that manages hardware resources and provides essential services to system processes.

## 1. What is a Kernel?

The kernel is the central part of an operating system.

It acts as a bridge between software and hardware and manages resources such as:

- CPU
- RAM
- Storage
- Input and output devices
- System processes

The kernel operates with high privileges to perform these tasks.

## 2. Why is the Kernel Important?

Without a kernel, an operating system cannot manage hardware and provide essential system services.

Its responsibilities include:

- Managing processes.
- Allocating memory.
- Handling hardware devices.
- Managing system calls.
- Enforcing process isolation.
- Controlling access to system resources.

## 3. How Does a Kernel Work?

Consider opening a text editor.

1. You request the application to open.
2. The application requests operating-system services.
3. The kernel manages the required CPU and memory resources.
4. The application executes.
5. The kernel coordinates hardware access when required.

## 4. Kernel Mode and User Mode

Modern operating systems separate execution into different privilege levels.

### Kernel Mode

- Has privileged access to system resources.
- Executes core operating-system code.
- Can perform privileged hardware operations.

### User Mode

- Used by ordinary applications.
- Has restricted access to hardware and memory.
- Requests privileged services through system calls.

|Kernel Mode|User Mode|
|---|---|
|Privileged execution|Restricted execution|
|Runs kernel code|Runs ordinary applications|
|Direct access to privileged resources|Access through OS services|
|A kernel fault can affect the whole system|Application faults are generally isolated|

## 5. Types of Kernel Architecture

### 5.1 Monolithic Kernel

Most core operating-system services run in kernel space.

**Example:** Linux.

### 5.2 Microkernel

Only essential services run in kernel space. Other services operate outside it.

**Example:** MINIX 3.

### 5.3 Hybrid Kernel

Combines design ideas from monolithic and microkernel architectures.

**Example:** Windows NT architecture and Apple's XNU kernel.

## 6. Kernel and Cybersecurity

The kernel is a critical security boundary.

Cybersecurity professionals study it to understand:

- Privilege escalation.
- Kernel vulnerabilities.
- Rootkits.
- Driver security.
- Process isolation.
- Operating-system security.

**Example:** A kernel-level vulnerability may allow an attacker to gain highly privileged access to a system.

## 7. Practical Observation — Windows

Open PowerShell and execute:

**Display Windows system information:**

```
systeminfo
```

**Display operating-system details:**

```
Get-CimInstance Win32_OperatingSystem |
Select-Object Caption, Version, BuildNumber, OSArchitecture
```

**Display running processes:**

```
Get-Process
```

These commands help you inspect the operating system. They do not directly expose the kernel's internal implementation.

## 8. My Understanding

Answer in your own words:

1. What is a kernel?
2. Why does an OS need a kernel?
3. What is the difference between kernel mode and user mode?
4. What is a monolithic kernel?
5. Why are kernel vulnerabilities dangerous?

## 9. Knowledge Check

1. What is the core component of an operating system?
2. Which mode has privileged access?
3. Which kernel architecture does Linux primarily use?
4. What is a rootkit?
5. What is the purpose of process isolation?

## Related Notes

- [[02 - Operating Systems]]
- [[Introduction to Operating Systems]]
- [[Functions of an Operating System]]
- [[Types of Operating Systems]]
- [[Shell]]
- [[System Calls]]
- [[Process Management]]
- [[Memory Management]]
- [[Operating System Security]]

---

**Category:** Operating System Fundamentals

**Status:** Learning