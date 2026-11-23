> Understand how an operating system allocates, manages, protects, and releases computer memory.

## 1. What Is Memory Management?

Memory management is an operating system function responsible for managing main memory (RAM).

It helps:

- Allocate memory to processes.
- Track memory usage.
- Release unused memory.
- Protect one process's memory from another.
- Manage virtual memory.

## 2. What Is RAM?

RAM stands for Random Access Memory.

It is the computer's primary working memory.

Characteristics:

- Stores data currently being used by programs.
- Provides fast access to active data.
- Is generally volatile.
- Loses its contents when power is removed.

Example:

When you open a browser, its running processes use RAM to store instructions and data needed during execution.

## 3. Memory Allocation

Memory allocation is the process of assigning memory to programs and processes.

Two common approaches are:

**Static allocation:** Memory requirements are determined before execution or at compile time, depending on the programming language and allocation mechanism.

**Dynamic allocation:** Memory is requested and released during program execution.

Dynamic allocation allows programs to use memory as needed.

## 4. Virtual Memory

Virtual memory is a memory-management technique that gives each process its own virtual address space.

The operating system and hardware translate virtual addresses into physical memory addresses.

Benefits:

- Process isolation.
- Memory protection.
- Flexible memory allocation.
- Ability to run programs whose total virtual memory usage exceeds available physical RAM.

Virtual memory does not mean that RAM has become unlimited.

## 5. Paging

Paging divides virtual memory into fixed-size blocks called pages.

Physical memory is divided into corresponding blocks called frames.

The operating system maps virtual pages to physical frames.

|Term|Meaning|
|---|---|
|Page|Fixed-size block of virtual memory|
|Frame|Fixed-size block of physical memory|
|Page table|Stores virtual-to-physical mappings|
|Page fault|Occurs when a requested page is not currently mapped as required|

Paging helps manage memory efficiently and supports process isolation.

## 6. Page Fault

A page fault occurs when a process accesses a virtual memory page that cannot currently be resolved through its existing memory mapping.

The operating system handles the fault.

Possible reasons include:

- The page is not currently in physical RAM.
- The mapping needs to be established.
- The access violates memory protection.

A page fault is not automatically an error or sign of malware.

## 7. Swapping

Swapping is the process of moving memory contents between RAM and secondary storage.

Linux commonly uses swap space.

Swap can be provided through a dedicated partition or a swap file.

Check swap usage:

```
free -h
```

View swap devices and files:

```
swapon --show
```

Swap is slower than RAM because it uses storage devices.

## 8. Memory Protection

Memory protection prevents processes from accessing memory regions they are not authorized to access.

It helps:

- Isolate processes.
- Protect sensitive data.
- Prevent unauthorized memory modification.
- Improve system stability.

Modern operating systems use hardware support and memory-management mechanisms to enforce these protections.

## 9. Memory Management in Linux

Linux provides tools to inspect memory usage.

### free

```
free -h
```

Displays RAM and swap usage.

### top

```
top
```

Displays memory and CPU information alongside running processes.

### /proc/meminfo

```
cat /proc/meminfo
```

Provides detailed memory statistics from the Linux kernel.

### vmstat

```
vmstat
```

Displays information about processes, memory, paging, and system activity.

## 10. Memory Management in Cybersecurity

Memory management is important for system security.

Security concepts include:

1. Process memory isolation.
2. Memory corruption.
3. Buffer overflow vulnerabilities.
4. Use-after-free vulnerabilities.
5. Sensitive data exposure.
6. Memory forensics.

### Example: Buffer Overflow

A buffer is a memory region used to hold data.

A buffer overflow occurs when a program writes beyond the allocated buffer boundaries.

Depending on the vulnerability and environment, this may cause:

- Application crashes.
- Memory corruption.
- Unauthorized code execution.

Modern systems use protections such as ASLR, DEP/NX, and stack canaries to reduce certain memory exploitation risks.

## 11. Practical Lab — Memory Inspection

Use your Kali Linux terminal.

### Task 1 — Display RAM usage

```
free -h
```

### Task 2 — Display detailed memory information

```
cat /proc/meminfo
```

### Task 3 — Monitor memory usage

```
top
```

Press `q` to exit.

### Task 4 — Display virtual memory statistics

```
vmstat
```

### Task 5 — Check swap usage

```
swapon --show
```

If no swap is configured, record that result.

### Task 6 — Inspect memory usage of a process

```
ps aux --sort=-%mem | head
```

This displays processes using the most memory.

## 12. Key Takeaways

- RAM stores data used by active programs.
- Memory management allocates and releases memory.
- Virtual memory provides each process with a virtual address space.
- Paging maps virtual pages to physical frames.
- Page faults are part of normal memory management.
- Swap provides additional backing storage for memory.
- Memory protection helps isolate processes.
- Memory vulnerabilities can affect system security.

## 13. My Understanding

Answer in your own words:

1. What is memory management?
2. What is the difference between RAM and virtual memory?
3. What is paging?
4. What is a page fault?
5. Why is memory protection important?
6. How can a buffer overflow become a security vulnerability?

## Related Notes

- [[Process Management]
- [[Virtual Memory]]
- [[Operating System Security]]
- [[Linux Processes]]
- [[Digital Forensics]]
- [[System Hardening]]

---