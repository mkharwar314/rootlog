> Operating systems can be classified according to how they manage resources, execute tasks, and support users.

## 1. Introduction

Different operating systems are designed for different purposes.

Some support one user, while others manage multiple users, processes, or computers simultaneously.

## 2. Types of Operating Systems

### 2.1 Batch Operating System

A Batch OS executes groups of similar jobs in batches without requiring continuous user interaction.

**Characteristics:**

- Jobs are collected and grouped.
- Jobs execute automatically.
- Users do not interact with each job during execution.

**Example:** Early IBM mainframe batch-processing systems.

### 2.2 Time-Sharing Operating System

A Time-Sharing OS allows multiple users or processes to share CPU time.

The CPU switches rapidly between tasks, giving each a time slice.

**Characteristics:**

- Supports multiple users.
- Provides interactive computing.
- Shares CPU time between processes.

**Example:** UNIX.

### 2.3 Multiprogramming Operating System

A Multiprogramming OS keeps multiple programs in memory so the CPU can execute another program when one is waiting for an operation, such as I/O.

**Purpose:** Improve CPU utilization.

### 2.4 Multitasking Operating System

A Multitasking OS allows multiple applications or tasks to make progress during the same period.

**Example:** Running a browser, music player, and text editor on Windows.

### 2.5 Multiprocessing Operating System

A Multiprocessing OS uses two or more processing units or CPU cores to execute tasks in parallel.

**Example:** Linux running workloads across multiple CPU cores.

### 2.6 Multiuser Operating System

A Multiuser OS allows multiple users to access the same computer system and its resources.

**Example:** A Linux server supporting multiple user accounts and remote sessions.

### 2.7 Real-Time Operating System (RTOS)

An RTOS is designed to respond to events within specified timing constraints.

**Types:**

- **Hard Real-Time:** Missing a deadline is considered a system failure.
- **Soft Real-Time:** Missing a deadline reduces system performance but may be acceptable.

**Examples:** FreeRTOS and QNX.

### 2.8 Distributed Operating System

A Distributed OS manages multiple interconnected computers and coordinates their resources as a system.

**Purpose:** Coordinate computing resources across multiple machines.

## 3. Comparison Table

|Type|Main Purpose|
|---|---|
|Batch OS|Executes jobs in batches|
|Time-Sharing OS|Shares CPU time among users or processes|
|Multiprogramming OS|Keeps CPU busy with multiple programs|
|Multitasking OS|Supports multiple tasks|
|Multiprocessing OS|Uses multiple processors or cores|
|Multiuser OS|Supports multiple users|
|Real-Time OS|Meets timing constraints|
|Distributed OS|Coordinates multiple computers|

## 4. Operating Systems in the Real World

|Operating System|Common Context|
|---|---|
|Windows|Personal computers|
|Linux|Servers and desktops|
|Android|Mobile devices|
|QNX|Automotive and embedded systems|
|FreeRTOS|Embedded and IoT devices|

**Important:** These classifications describe different operating-system capabilities. A modern OS can belong to several categories at once.

For example, Linux supports multitasking, multiprocessing, and multiple users.

## 5. My Understanding

Answer in your own words:

1. What is a Batch Operating System?
2. How does a Time-Sharing OS work?
3. What is the difference between multitasking and multiprocessing?
4. What makes an RTOS different from a general-purpose OS?
5. Why do servers commonly support multiple users?

## 6. Knowledge Check

1. Which OS executes jobs in batches?
2. Which OS is designed for strict timing requirements?
3. What is the main purpose of multiprocessing?
4. Can Linux support multiple users?
5. What is the difference between multiprogramming and multitasking?

## Related Notes

- [[02 - Operating Systems]]
- [[Introduction to Operating Systems]]
- [[Functions of an Operating System]]
- [[Kernel]]
- [[Linux OS]]
- [[Windows OS]]
- [[Embedded Systems]]

---

**Category:** Operating System Fundamentals

**Status:** Learning