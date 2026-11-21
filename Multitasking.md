>Multitasking is an operating system capability that allows multiple tasks to make progress during the same period.

A task may be a process or a thread.

For example, while using a computer, you might:

- Play music.
- Browse the internet.
- Download a file.
- Run a terminal.
- Edit a document.

The operating system manages CPU time so these activities can make progress without requiring the user to run each one manually.

## 2. Task, Process, and Thread

These terms are related but not identical.

|Term|Meaning|
|---|---|
|Task|A general unit of work performed by a system.|
|Process|A running program with its own virtual address space and resources.|
|Thread|A unit of execution within a process.|

A process can contain multiple threads.

**Example:**

A web browser may run as multiple processes, and each process may contain several threads handling different activities.

Related: [[Process Management]]

## 3. Concurrency vs Parallelism

These concepts are important in operating systems.

### Concurrency

Concurrency means multiple tasks make progress during overlapping periods.

On a single CPU core, the operating system can rapidly switch between tasks, giving the appearance that they run simultaneously.

### Parallelism

Parallelism means multiple tasks actually execute at the same time using different CPU cores or processing units.

|Concurrency|Parallelism|
|---|---|
|Tasks make progress over overlapping periods.|Tasks execute simultaneously.|
|Possible on a single CPU core.|Requires multiple execution units.|
|Often uses task switching.|Uses multiple cores or processors.|

## 4. Types of Multitasking

### A. Preemptive Multitasking

The operating system decides how long a task can use the CPU.

The scheduler can interrupt a running task and give CPU time to another task.

Modern Windows and Linux systems use preemptive multitasking.

### B. Cooperative Multitasking

A running task voluntarily gives up CPU control so another task can execute.

If a task does not cooperate, it may prevent other tasks from receiving CPU time.

## 5. Time Sharing

Time sharing divides CPU execution time into small intervals.

These intervals are commonly called **time slices** or **time quanta**.

Example:

1. Process A receives CPU time.
2. Its time slice expires.
3. The scheduler selects Process B.
4. Process B receives CPU time.
5. The cycle continues.

This allows multiple processes to share CPU resources.

## 6. CPU Scheduler

The CPU scheduler selects which eligible process or thread should execute next.

Its responsibilities include:

- Selecting tasks for CPU execution.
- Managing CPU time allocation.
- Supporting system responsiveness.
- Applying scheduling priorities

Related: [[CPU Scheduling]]

## 7. Context Switching

A context switch occurs when the CPU stops executing one task and switches to another.

The operating system saves the current task's execution state and restores the state of the next task.

The saved state may include:

- CPU registers.
- Program counter.
- Stack pointer.
- Other execution-related information.

**Important:** Context switching has overhead. The CPU spends time switching tasks instead of executing application instructions.

## 8. Single-Core vs Multicore Multitasking

### Single-Core CPU

A single-core CPU executes one instruction stream at a time. The operating system switches between tasks to support concurrency.

### Multicore CPU

A multicore CPU contains multiple processing cores.

Different tasks or threads can execute in parallel on separate cores, while the operating system also manages concurrency.

Useful commands:

Linux:

```
nproc
lscpu
```

Windows PowerShell:

```
Get-CimInstance Win32_Processor |
Select-Object Name, NumberOfCores, NumberOfLogicalProcessors
```

## 9. Advantages of Multitasking

- Better CPU utilization.
- Improved user experience.
- Multiple applications can run together.
- Efficient sharing of system resources.
- Better system responsiveness.

## 10. Limitations of Multitasking

- Context switching creates overhead.
- Too many active tasks can reduce performance.
- Processes compete for CPU and memory.
- Poorly managed tasks can cause resource exhaustion.
- Synchronization problems can occur when threads share data.

## 11. Multitasking and Cybersecurity

Multitasking is relevant to cybersecurity because several processes and services operate simultaneously.

Security considerations include:

- **Process isolation:** Helps prevent one process from directly interfering with another.
- **Resource exhaustion:** Excessive processes or threads can consume CPU and memory.
- **Denial of Service (DoS):** An attacker may attempt to exhaust system resources.
- **Suspicious processes:** Unexpected processes may indicate malware or unauthorized activity.
- **Race conditions:** Concurrent operations can produce unexpected results when shared resources are accessed without proper synchronization.

Related: [[Operating System Security]], [[Windows Processes]], [[Linux Processes]]

## 12. Practical Lab — Observe Running Tasks

### Lab A: Kali Linux

List running processes:

```
ps -e -o pid,ppid,stat,comm
```

Open the interactive process monitor:

```
top
```

Press `q` to exit.

Check available CPU processing units:

```
nproc
```

View CPU information:

```
lscpu
```

### Lab B: Windows PowerShell

Display running processes:

```
Get-Process
```

Display selected information:

```
Get-Process |
Select-Object -First 10 ProcessName, Id, CPU
```

Observe CPU and memory usage:

```
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 10 ProcessName, Id, CPU, WorkingSet
```

## 13. Practical Tasks

1. Open at least three applications on Windows.
2. Run `Get-Process` in PowerShell.
3. Identify their process names and process IDs.
4. Open `top` in Kali Linux.
5. Identify at least five running processes.
6. Compare the number of CPU cores and logical processors.

Record your observations in your notebook.

## 14. My Understanding

Write your answers in your own words:

1. What is multitasking?
2. What is the difference between a process and a thread?
3. What is the difference between concurrency and parallelism?
4. What is a context switch?
5. Why does context switching create overhead?
6. How can excessive processes affect system security?

## 15. Related Notes

- [[Process Management]]
- [[Windows Processes]]
- [[Linux Processes]]
- [[CPU Scheduling]]
- [[Virtual Memory]]
- [[Operating System Security]]

---

**Key Takeaway:** Multitasking allows an operating system to manage multiple tasks efficiently through scheduling, time sharing, and context switching.