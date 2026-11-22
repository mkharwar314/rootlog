> Windows architecture describes how different operating-system components interact to manage hardware, applications, memory, and system resources.

## 1. Introduction

Windows uses a layered architecture that separates application execution from privileged operating-system operations.

Its architecture is broadly divided into two execution modes:

1. User Mode
2. Kernel Mode

This separation improves system stability and security.

## 2. User Mode

User Mode is where ordinary applications and many operating-system services execute.

Examples:

- Web browsers
- Text editors
- PowerShell
- Windows services

**Characteristics:**

- Applications operate with restricted privileges.
- Processes generally have separate virtual address spaces.
- Applications request privileged services through operating-system interfaces.
- An ordinary application crash usually does not crash the entire OS.

## 3. Kernel Mode

Kernel Mode is the privileged execution environment of Windows.

It contains core operating-system components that manage hardware and system resources.

Major components include:

- Windows Executive
- Windows Kernel
- Device Drivers
- Hardware Abstraction Layer (HAL)

**Characteristics:**

- Executes privileged operating-system code.
- Manages critical system resources.
- Provides low-level hardware interaction.
- A serious kernel-mode fault can cause a system crash.

## 4. Major Components of Windows Architecture

### 4.1 Windows Executive

The Windows Executive provides major operating-system services.

Important components include:

- Object Manager
- Memory Manager
- Process and Thread Manager
- I/O Manager
- Security Reference Monitor
- Cache Manager

### 4.2 Windows Kernel

The Windows Kernel handles low-level operating-system operations.

Responsibilities include:

- Thread scheduling
- Interrupt and exception handling
- Synchronization
- Low-level processor management

### 4.3 Device Drivers

Device drivers allow Windows to communicate with hardware devices.

Examples:

- Graphics drivers
- Network drivers
- Storage drivers
- Audio drivers

### 4.4 Hardware Abstraction Layer (HAL)

The HAL provides an abstraction between the Windows kernel and platform-specific hardware details.

It helps Windows operate across different hardware configurations.

## 5. Windows Architecture Diagram

```
+--------------------------------+
|         Applications           |
+--------------------------------+
                |
                v
+--------------------------------+
|           USER MODE            |
|                                |
| Applications                   |
| Windows Services               |
| User-Mode System Libraries     |
+--------------------------------+
                |
       System Call Interface
                |
                v
+--------------------------------+
|          KERNEL MODE           |
|                                |
| Windows Executive              |
| Windows Kernel                 |
| Device Drivers                 |
| Hardware Abstraction Layer     |
+--------------------------------+
                |
                v
+--------------------------------+
|            Hardware            |
+--------------------------------+
```

**Important:** This is a simplified conceptual diagram. Actual Windows architecture contains additional components and interfaces.

## 6. User Mode vs Kernel Mode

|User Mode|Kernel Mode|
|---|---|
|Restricted privileges|Privileged execution|
|Runs ordinary applications|Runs core kernel components and drivers|
|Separate process address spaces|Access to kernel address space|
|Application faults are generally isolated|Serious faults can affect the whole system|

## 7. Windows Architecture and Cybersecurity

Understanding Windows architecture helps security professionals investigate:

- Kernel-level malware
- Rootkits
- Privilege escalation
- Vulnerable device drivers
- Process isolation
- Unauthorized system access

**Example:** A malicious kernel-mode driver can potentially gain highly privileged access to the operating system.

## 8. Practical Lab — Explore Windows Processes

Open PowerShell.

**List running processes:**

```
Get-Process
```

**View process names and IDs:**

```
Get-Process | Select-Object Name, Id
```

**View Windows services:**

```
Get-Service
```

**Check system information:**

```
Get-ComputerInfo | Select-Object WindowsProductName, WindowsVersion, OsArchitecture
```

These commands help inspect Windows components. They do not directly expose the internal kernel architecture.

## 9. My Understanding

Answer in your own words:

1. What are User Mode and Kernel Mode?
2. Why does Windows separate these execution modes?
3. What is the role of the Windows Executive?
4. What is the purpose of device drivers?
5. Why are kernel-mode vulnerabilities dangerous?

## 10. Knowledge Check

1. In which mode do ordinary applications generally execute?
2. Which component manages memory?
3. What does HAL stand for?
4. What is the role of the I/O Manager?
5. Can a faulty kernel-mode driver crash Windows?

## Related Notes

- [[02 - Operating Systems]]
- [[Introduction to Windows]]
- [[Kernel]]
- [[System Calls]]
- [[Windows File System]]
- [[Windows Registry]]
- [[Windows Processes]]
- [[Windows Services]]
- [[Operating System Security]]

---

**Category:** Windows Operating System

**Status:** Learning