> Understand how an operating system creates, schedules, executes, and terminates processes.

## 1. What Is Process Management?

Process management is an operating system function responsible for controlling and managing running processes.

The operating system manages:

- Process creation.
- Process execution.
- Process scheduling.
- Process synchronization.
- Process communication.
- Process termination.

Both Windows and Linux use process management to coordinate running programs.

## 2. What Is a Process?

A process is a program in execution.

A process contains:

- Program instructions.
- Process state.
- Memory allocation.
- CPU register information.
- Process identifiers.
- Open files and other resources.

Example:

When you open a web browser, the operating system creates one or more processes to execute it.

## 3. Process Control Block (PCB)

A Process Control Block (PCB) is a kernel data structure containing information the operating system needs to manage a process.

Typical information includes:

|Component|Purpose|
|---|---|
|PID|Identifies the process|
|Process state|Shows its current state|
|Program counter|Tracks the next instruction|
|CPU registers|Stores execution context|
|Scheduling information|Helps determine CPU allocation|
|Memory information|Describes process memory|
|I/O information|Tracks input/output resources|

The PCB allows the operating system to track and manage processes.

## 4. Process States

A process changes states during execution.

Common simplified process states:

|State|Meaning|
|---|---|
|New|Process is being created|
|Ready|Waiting for CPU allocation|
|Running|Currently executing on a CPU|
|Waiting|Waiting for an event or resource|
|Terminated|Execution has finished|

### Process State Diagram

```
        New
         |
         v
       Ready <----------+
         |              |
         v              |
      Running -----> Waiting
         |              |
         v              |
     Terminated         |
                        |
             Event completed
                        |
                        +----> Ready
```

A process can move between states depending on CPU scheduling and events.

## 5. Process Scheduling

Process scheduling determines which ready process receives CPU time.

The operating system uses a scheduler to manage CPU allocation.

Common scheduling algorithms:

|Algorithm|Description|
|---|---|
|FCFS|First Come, First Served|
|SJF|Shortest Job First|
|Priority Scheduling|Executes according to priority|
|Round Robin|Gives processes fixed time slices|
|Multilevel Queue|Organizes processes into separate queues|

## 6. Context Switching

A context switch occurs when the CPU stops executing one process or thread and switches to another.

The operating system saves the current execution context and restores the next one.

This may involve:

- CPU registers.
- Program counter.
- Scheduling state.
- Memory-management context.

Context switching enables multitasking but introduces overhead.

## 7. Multitasking

Multitasking allows an operating system to manage multiple tasks during overlapping periods.

Two important concepts:

**Preemptive multitasking:** The operating system can interrupt a running task and allocate CPU time to another task.

**Cooperative multitasking:** Tasks voluntarily yield control so other tasks can execute.

Modern Windows and Linux systems primarily use preemptive multitasking.

## 8. Process Synchronization

Process synchronization coordinates processes or threads that share resources.

Without proper synchronization, concurrent operations can produce incorrect results.

Example:

Two processes attempt to update the same bank account balance simultaneously.

If their operations are not coordinated, the final balance may be incorrect.

Important concepts:

- Critical section.
- Mutex.
- Semaphore.
- Race condition.
- Deadlock.

These concepts will be explored further in operating-system studies.

## 9. Inter-Process Communication (IPC)

Inter-Process Communication allows processes to exchange information and coordinate activities.

Common IPC mechanisms:

|Mechanism|Purpose|
|---|---|
|Pipes|Transfer data between processes|
|Message queues|Exchange structured messages|
|Shared memory|Share memory regions|
|Sockets|Communicate between processes, locally or across networks|
|Signals|Notify processes about events|

IPC is important for both application development and system security.

## 10. Process Management in Cybersecurity

Process management helps security analysts investigate system activity.

Analysts examine:

1. Unknown processes.
2. Suspicious parent-child relationships.
3. Unexpected execution privileges.
4. Unusual CPU and memory usage.
5. Processes communicating over networks.
6. Unauthorized background execution.

### Example: Suspicious Process

Suppose a process is running under an unexpected user account.

An analyst may investigate:

- Process name.
- PID and PPID.
- Executable path.
- Process owner.
- Network connections.
- Related system logs.

A suspicious process name alone does not prove malicious activity.

## 11. Practical Lab — Process Inspection

Use your Kali Linux terminal.

### Task 1 — Display running processes

```
ps aux
```

### Task 2 — Display process hierarchy

```
pstree -p
```

If `pstree` is unavailable, record that result rather than installing it.

### Task 3 — Inspect PID 1

```
ps -p 1 -o pid,ppid,state,comm,args
```

### Task 4 — Inspect your shell process

```
ps -p $$ -o pid,ppid,state,comm,args
```

### Task 5 — Monitor CPU and memory usage

```
top
```

Press `q` to exit.

### Task 6 — Create a temporary process

```
sleep 120 &
```

### Task 7 — Find the process

```
pgrep -a sleep
```

### Task 8 — Inspect the process

Replace `PID` with the process ID returned above:

```
ps -p PID -o pid,ppid,state,user,comm,args
```

### Task 9 — Terminate your test process

```
kill -TERM PID
```

Replace `PID` with the actual process ID.

## 12. Key Takeaways

- Process management controls running processes.
- PCB stores process-management information.
- Processes move through different states.
- Scheduling allocates CPU time.
- Context switching changes the executing process.
- Synchronization coordinates shared resources.
- IPC allows processes to communicate.
- Process analysis is useful in cybersecurity investigations.

## 13. My Understanding

Answer in your own words:

1. What is process management?
2. What is a Process Control Block?
3. What is the difference between ready and running states?
4. What is context switching?
5. What is a race condition?
6. Why is process inspection important in cybersecurity?

## Related Notes

- [[Linux Processes]]
- [[Memory Management]]
- [[CPU Scheduling]]
- [[Operating System Security]]
- [[Digital Forensics]]
- [[Windows Processes]]

---