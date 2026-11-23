>Linux commands are instructions entered into a shell to perform operations on the operating system.

They allow users to:

- Navigate directories.
- Manage files and folders.
- Inspect system information.
- Manage processes.
- Monitor network activity.
- Manage users and permissions.

## 2. Basic Command Structure

A Linux command generally follows this structure:

```
command [options] [arguments]
```

Example:

```
ls -la /home
```

Explanation:

- `ls` = Command
- `-la` = Options
- `/home` = Argument

Not every command requires options or arguments.

## 3. Directory Navigation Commands

|Command|Purpose|
|---|---|
|`pwd`|Displays current directory|
|`ls`|Lists directory contents|
|`ls -la`|Lists all entries with details|
|`cd`|Changes directory|
|`cd ..`|Moves to parent directory|
|`cd ~`|Moves to home directory|
|`tree`|Displays directory structure, if installed|

Examples:

```
pwd
ls -la
cd /home
cd ..
cd ~
```

## 4. File and Directory Management

|Command|Purpose|
|---|---|
|`touch`|Creates an empty file or updates timestamps|
|`mkdir`|Creates a directory|
|`cp`|Copies files or directories|
|`mv`|Moves or renames files|
|`rm`|Removes files|
|`rmdir`|Removes an empty directory|
|`cat`|Displays file contents|
|`less`|Views file contents page by page|

Examples:

```
touch notes.txt
mkdir LinuxLab
cp notes.txt backup.txt
mv backup.txt old-notes.txt
cat notes.txt
```

**Warning:** `rm` can permanently remove files. Check paths carefully before using it.

## 5. File Search Commands

|Command|Purpose|
|---|---|
|`find`|Searches for files and directories|
|`locate`|Searches an indexed file database, if available|
|`which`|Finds a command's executable path|
|`whereis`|Locates binary, source, and manual files|

Examples:

```
find /home -name "notes.txt"
which python3
whereis nmap
```

## 6. Text Processing Commands

|Command|Purpose|
|---|---|
|`head`|Displays the beginning of a file|
|`tail`|Displays the end of a file|
|`grep`|Searches text using patterns|
|`sort`|Sorts lines|
|`wc`|Counts lines, words, and bytes|
|`cut`|Extracts selected fields|
|`uniq`|Removes adjacent duplicate lines|

Examples:

```
head -n 5 notes.txt
tail -n 5 notes.txt
grep "Linux" notes.txt
wc -l notes.txt
```

## 7. System Information Commands

|Command|Purpose|
|---|---|
|`uname -a`|Displays kernel and system information|
|`hostname`|Displays the hostname|
|`whoami`|Displays current username|
|`id`|Displays user and group IDs|
|`lscpu`|Displays CPU information|
|`free -h`|Displays memory usage|
|`df -h`|Displays filesystem disk usage|
|`uptime`|Displays system uptime and load averages|

## 8. Process Management Commands

|Command|Purpose|
|---|---|
|`ps`|Displays process information|
|`top`|Monitors running processes|
|`htop`|Interactive process monitor, if installed|
|`pgrep`|Finds processes by name or pattern|
|`kill`|Sends a signal to a process|
|`killall`|Sends a signal to processes by name|

Examples:

```
ps aux
top
pgrep bash
```

Use process termination commands carefully. Do not terminate unfamiliar system processes.

## 9. Networking Commands

|Command|Purpose|
|---|---|
|`ip addr`|Displays network interfaces and addresses|
|`ip route`|Displays routing information|
|`ping`|Tests network reachability|
|`ss -tuln`|Displays listening TCP and UDP sockets|
|`curl`|Transfers data using URLs|
|`dig`|Performs DNS queries|
|`traceroute`|Traces a network path, if installed|

Examples:

```
ip addr
ip route
ping -c 4 127.0.0.1
ss -tuln
```

## 10. Help and Documentation Commands

|Command|Purpose|
|---|---|
|`man`|Opens a command manual|
|`--help`|Displays command help|
|`whatis`|Gives a short command description|
|`apropos`|Searches manual descriptions|

Examples:

```
man ls
ls --help
whatis pwd
```

## 11. Command Chaining and Redirection

Linux allows commands to be combined and their input or output redirected.

### Pipe (`|`)

Passes one command's output to another command.

```
ps aux | grep firefox
```

### Output Redirection (`>`)

Writes output to a file, replacing existing content.

```
echo "Learning Linux" > notes.txt
```

### Append Redirection (`>>`)

Adds output to the end of a file.

```
echo "Learning commands" >> notes.txt
```

### Command Separator (`;`)

Runs commands sequentially.

```
pwd; whoami
```

## 12. Linux Commands and Cybersecurity

Linux commands are widely used for:

- Network reconnaissance.
- System administration.
- Log analysis.
- Process investigation.
- File analysis.
- Permission auditing.
- Security testing.

Understanding what a command does is more important than memorising it.

## 13. Practical Lab: Linux Command Practice

Perform these tasks in your Kali terminal.

### Task 1: Identify Your User

```
whoami
id
```

### Task 2: Explore Your Home Directory

```
cd ~
pwd
ls -la
```

### Task 3: Create a Practice Directory

```
mkdir -p ~/ROOTLOG-LAB
cd ~/ROOTLOG-LAB
```

### Task 4: Create a File

```
touch practice.txt
```

### Task 5: Write Information into the File

```
echo "I am learning Linux commands." > practice.txt
```

### Task 6: Read the File

```
cat practice.txt
```

### Task 7: Copy the File

```
cp practice.txt backup.txt
```

### Task 8: Rename the Backup

```
mv backup.txt linux-backup.txt
```

### Task 9: List Your Files

```
ls -l
```

### Task 10: Search for Your Practice File

```
find ~/ROOTLOG-LAB -name "practice.txt"
```

Keep this practice directory for future Linux exercises.

## 14. My Understanding

Answer these questions in your own words:

1. What is a Linux command?
2. What is the difference between `pwd` and `ls`?
3. What is the difference between `cp` and `mv`?
4. What does `grep` do?
5. What is the purpose of a pipe?
6. What is the difference between `>` and `>>`?
7. Why should commands such as `rm` be used carefully?

## 15. Practical Observations

Record your findings:

- Current username:
- Current working directory:
- Files created:
- Difference between `cp` and `mv`:
- One command I found useful:
- One command I need to practise:

## Related Topics

- [[Introduction to Linux]]
- [[Linux Architecture]]
- [[Linux File System]]
- [[Linux Users and Groups]]
- [[Linux Permissions]]
- [[Linux Processes]]
- [[Practical Labs]]

---

**Category:** Linux Operating System

**Status:** Learning