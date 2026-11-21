## 1. What Is Virtual Memory?

Virtual memory is a memory management technique that allows an operating system to give each process its own virtual address space.

It allows programs to use memory without needing every part of the program to remain in physical RAM at all times.

The operating system and CPU work together to translate virtual addresses into physical memory addresses.

**Important:** Virtual memory is not the same as additional physical RAM.

## 2. Why Is Virtual Memory Needed?

Virtual memory provides several advantages:

- Each process gets its own virtual address space.
- Processes are isolated from one another.
- Programs can use more memory than the currently available physical RAM.
- Memory can be managed more efficiently.
- The operating system can control access to memory.

## 3. Virtual Memory vs Physical Memory

|Virtual Memory|Physical Memory|
|---|---|
|Address space presented to a process.|Actual RAM installed in the computer.|
|Uses virtual addresses.|Uses physical addresses.|
|Managed through address translation.|Stores data and instructions currently in RAM.|
|Provides process isolation.|Provides hardware memory storage.|

## 4. How Does Virtual Memory Work?

Consider a program accessing a memory address.

1. The program generates a virtual address.
2. The CPU's Memory Management Unit (MMU) translates the address.
3. Page tables help map virtual addresses to physical memory.
4. The required data is accessed from physical RAM.
5. If the required page is not currently in RAM, a page fault may occur.

### Basic Architecture

```
        Application
             |
             v
      Virtual Address
             |
             v
     Memory Management
       Unit (MMU)
             |
             v
         Page Tables
             |
             v
      Physical Address
             |
             v
         Physical RAM
```

## 5. Paging

Paging is a memory management technique that divides:

- Virtual memory into fixed-size blocks called pages.
- Physical memory into fixed-size blocks called frames.

A page can be mapped to a physical frame.

This allows memory to be allocated without requiring a process to occupy one continuous physical memory region.

## 6. Page Tables

A page table stores mapping information between virtual pages and physical frames.

The operating system manages page tables, while the CPU's MMU uses them during address translation.

A page table entry may contain:

- Physical frame information.
- Present or valid status.
- Read/write permissions.
- User or supervisor access permissions.

## 7. Page Fault

A page fault occurs when a process accesses a virtual memory page that cannot currently be accessed through its present memory mapping.

For example, the page may not currently be resident in physical RAM.

The operating system handles the fault. Depending on the situation, it may:

1. Validate the memory access.
2. Locate the required page.
3. Load the page into RAM if necessary.
4. Update the relevant page-table information.
5. Resume execution.

**Important:** Not every page fault is an error. Page faults are a normal part of virtual memory operation.

An invalid or unauthorized memory access may instead cause the operating system to terminate the process or report an access violation.

## 8. Swapping and Page Files

When physical RAM is under pressure, an operating system may move some memory contents out of RAM.

Examples:

- Linux commonly uses a swap partition or swap file.
- Windows uses a page file (`pagefile.sys`).

This can help the system manage memory pressure, but accessing data from storage is generally much slower than accessing RAM.

**Remember:** A page file or swap space does not provide the same performance as physical RAM.

## 9. Memory Protection

Virtual memory also provides memory protection.

For example:

- One process normally cannot directly access another process's private memory.
- Memory pages can have read, write, and execute permissions.
- The operating system can restrict access to sensitive memory regions.

These protections help reduce the impact of software bugs and certain attacks.

## 10. Virtual Memory and Cybersecurity

Virtual memory is important in cybersecurity because memory management affects system security.

Important concepts:

- **Memory isolation:** Helps prevent unauthorized access between processes.
- **Memory corruption:** Bugs can cause unintended changes to memory.
- **Buffer overflow:** Writing beyond an allocated memory boundary can corrupt adjacent memory.
- **ASLR:** Address Space Layout Randomization makes memory locations less predictable.
- **DEP/NX:** Helps prevent execution of code from memory regions marked non-executable.

Related: [[Operating System Security]], [[Windows Processes]], [[Linux Processes]]

## 11. Practical Lab — Inspect Memory

### Lab A: Windows PowerShell

Check total physical memory:

```
Get-CimInstance Win32_ComputerSystem |
Select-Object TotalPhysicalMemory
```

Check memory usage:

```
Get-CimInstance Win32_OperatingSystem |
Select-Object TotalVisibleMemorySize, FreePhysicalMemory
```

Check page file information:

```
Get-CimInstance Win32_PageFileUsage
```

### Lab B: Kali Linux

Check RAM usage:

```
free -h
```

View detailed memory information:

```
cat /proc/meminfo
```

Check swap information:

```
swapon --show
```

These commands are for inspection only. They do not modify memory configuration.

## 12. Practical Tasks

1. Run `free -h` in Kali Linux.
2. Identify total RAM and available memory.
3. Run `swapon --show`.
4. Check page file information in Windows PowerShell.
5. Compare how Windows and Linux report memory usage.
6. Write down why virtual memory is not equivalent to physical RAM.

## 13. My Understanding

Answer in your own words:

1. What is virtual memory?
2. What is the difference between virtual and physical memory?
3. What is paging?
4. What is a page table?
5. What is a page fault?
6. How does virtual memory improve process isolation?

## 14. Related Notes

- [[Memory Management]]
- [[Process Management]]
- [[Multitasking]]
- [[CPU Scheduling]]
- [[Operating System Security]]
- [[Windows Processes]]
- [[Linux Processes]]

---

**Key Takeaway:** Virtual memory gives processes separate virtual address spaces and allows the operating system to manage memory efficiently while providing isolation and protection.