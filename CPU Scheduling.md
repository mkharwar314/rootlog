## 1. What Is CPU Scheduling?

CPU scheduling is the process by which an operating system selects which ready process or thread gets CPU time next.

A computer may have many processes waiting to execute, but CPU resources are limited.

The operating system uses a **CPU scheduler** to decide which task should run.

## 2. Why Is CPU Scheduling Important?

CPU scheduling helps the operating system:

- Use CPU resources efficiently.
- Improve system responsiveness.
- Reduce waiting time.
- Share CPU time among processes.
- Manage multiple running applications.

## 3. Process States and Scheduling

A process commonly moves through these states:

|State|Meaning|
|---|---|
|New|The process is being created.|
|Ready|The process is waiting for CPU time.|
|Running|The process is currently executing.|
|Waiting/Blocked|The process is waiting for an event or resource.|
|Terminated|The process has finished execution.|

### Basic Process Flow

```
       New
        |
        v
      Ready <----------+
        |              |
        v              |
     Running           |
      /   \             |
     v     v            |
 Waiting  Terminated    |
     |                  |
     +------------------+
```

A process usually returns from waiting to the ready state when the event or resource it needs becomes available.

## 4. Types of CPU Scheduling

### A. Preemptive Scheduling

The operating system can interrupt a running process and assign CPU time to another process.

Example: A higher-priority task may be scheduled before a lower-priority task finishes.

### B. Non-Preemptive Scheduling

Once a process receives the CPU, it continues executing until it finishes or voluntarily gives up the CPU, such as by waiting for an event.

## 5. Common CPU Scheduling Algorithms

### 1. First Come, First Served (FCFS)

Processes are executed in the order they arrive.

**Advantage:** Simple to understand and implement.

**Disadvantage:** A long process can make shorter processes wait.

### 2. Shortest Job First (SJF)

The process with the shortest expected CPU burst is selected first.

**Advantage:** Can reduce average waiting time.

**Disadvantage:** The operating system may not know the exact future CPU burst length.

### 3. Priority Scheduling

Each process is assigned a priority. The scheduler selects a process based on its priority.

**Advantage:** Important tasks can receive CPU time sooner.

**Disadvantage:** Low-priority processes may suffer starvation.

### 4. Round Robin (RR)

Each process receives a fixed time slice in turn.

After its time slice expires, the process may be moved to the back of the ready queue if it still needs CPU time.

**Advantage:** Provides fair CPU sharing and responsiveness.

**Disadvantage:** Very small time slices can create excessive context-switching overhead.

## 6. Important Scheduling Terms

|Term|Meaning|
|---|---|
|Arrival Time|When a process enters the ready queue.|
|Burst Time|CPU execution time needed for a CPU burst.|
|Waiting Time|Time spent waiting in the ready queue.|
|Turnaround Time|Total time from arrival to completion.|
|Response Time|Time from arrival until the process first gets CPU time.|
|Time Quantum|Maximum time slice given in Round Robin scheduling.|
|Starvation|A process waits indefinitely because other processes keep getting selected.|

## 7. CPU Scheduling and Context Switching

When the scheduler selects another process, the operating system may perform a context switch.

It saves the current execution state and restores the state of the selected process.

Context switching allows multiple tasks to share CPU resources, but it also introduces overhead.

Related: [[Multitasking]], [[Process Management]]

## 8. CPU Scheduling in Windows and Linux

### Windows

Windows uses priority-based, preemptive scheduling.

The scheduler selects eligible threads based on factors including priority and scheduling conditions.

### Linux

Linux uses scheduling classes and policies.

For ordinary tasks, Linux commonly uses the Completely Fair Scheduler (CFS) on many traditional kernel configurations. Newer Linux kernels also use the EEVDF scheduling approach for fair scheduling.

The exact scheduling behaviour depends on the kernel version, scheduling class, and task policy.

## 9. Scheduling and Cybersecurity

CPU scheduling is relevant to security and system reliability.

Important considerations:

- **Resource exhaustion:** Too many CPU-intensive tasks can reduce system availability.
- **Denial of Service:** Attackers may attempt to consume CPU resources.
- **Priority abuse:** Incorrect or excessive priority settings can affect system responsiveness.
- **Starvation:** A task may receive insufficient CPU time.
- **Real-time requirements:** Some security and industrial systems require predictable response times.

## 10. Practical Lab — Observe CPU Activity

### Lab A: Kali Linux

Display running processes:

```
ps -eo pid,ni,pri,stat,comm
```

Open the interactive process monitor:

```
top
```

Press `q` to exit.

Display CPU information:

```
lscpu
```

### Lab B: Windows PowerShell

Display processes and their priorities:

```
Get-Process |
Select-Object -First 10 ProcessName, Id, PriorityClass
```

Display processes sorted by CPU time:

```
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 10 ProcessName, Id, CPU
```

These commands inspect process information. They do not change scheduling priorities.

## 11. Practical Tasks

1. Run `top` in Kali Linux.
2. Identify three processes using CPU resources.
3. Run `Get-Process` in PowerShell.
4. Compare the CPU usage information shown by both systems.
5. Explain why Round Robin scheduling is useful for interactive systems.
6. Explain what starvation means.

## 12. My Understanding

Answer in your own words:

1. What is CPU scheduling?
2. What is the difference between preemptive and non-preemptive scheduling?
3. Explain FCFS and Round Robin.
4. What is a time quantum?
5. What is starvation?
6. Why is CPU scheduling important for system performance and security?

## 13. Related Notes

- [[Process Management]]
- [[Multitasking]]
- [[Memory Management]]
- [[Virtual Memory]]
- [[Windows Processes]]
- [[Linux Processes]]
- [[Operating System Security]]

---

**Key Takeaway:** CPU scheduling determines which ready process or thread receives CPU time, helping the operating system balance performance, responsiveness, and resource sharing.