>A Linux file system is a method of organizing, storing, managing, and accessing files and directories.
   Linux uses a hierarchical directory structure that begins at the root directory `/`.
   Unlike Windows, Linux does not use drive letters such as `C:` or `D:` for its main directory structure.

## 2. Linux Directory Structure

The Linux file system follows the Filesystem Hierarchy Standard (FHS).

Important directories include:

|Directory|Purpose|
|---|---|
|`/`|Root of the entire directory tree|
|`/home`|Stores regular users' home directories|
|`/root`|Home directory of the root user|
|`/bin`|Essential user command binaries|
|`/sbin`|System administration utilities|
|`/etc`|System-wide configuration files|
|`/var`|Variable data such as logs and caches|
|`/tmp`|Temporary files|
|`/usr`|User applications, libraries, and shared data|
|`/boot`|Files needed for booting|
|`/dev`|Device files|
|`/proc`|Virtual filesystem exposing process and kernel information|
|`/sys`|Virtual filesystem exposing device and kernel information|
|`/mnt`|Common temporary mount point|
|`/media`|Common mount point for removable media|

## 3. Understanding the Root Directory

The `/` directory is the starting point of the Linux file system.

Example:

```
/
├── bin
├── boot
├── dev
├── etc
├── home
│   └── student
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── sys
├── tmp
├── usr
└── var
```

The exact directories and layout can vary between distributions.

## 4. Absolute and Relative Paths

### Absolute Path

An absolute path specifies the complete location of a file or directory from `/`.

Example:

```
/home/student/Documents
```

### Relative Path

A relative path specifies a location in relation to the current working directory.

Example:

```
Documents/file.txt
```

Important path symbols:

|Symbol|Meaning|
|---|---|
|`/`|Root directory or path separator|
|`.`|Current directory|
|`..`|Parent directory|
|`~`|Current user's home directory|

## 5. Linux File Types

Linux supports several types of filesystem objects.

|Symbol|File Type|
|---|---|
|`-`|Regular file|
|`d`|Directory|
|`l`|Symbolic link|
|`c`|Character device|
|`b`|Block device|
|`p`|Named pipe|
|`s`|Unix domain socket|

You can identify file types using:

```
ls -l
```

The first character in the permissions column indicates the file type.

## 6. Linux File System Types

Different file systems are designed for different storage requirements.

|File System|Description|
|---|---|
|ext4|Common Linux journaling file system|
|XFS|High-performance journaling file system|
|Btrfs|Supports snapshots and advanced storage features|
|FAT32|Widely compatible filesystem|
|exFAT|Commonly used for removable storage|
|NTFS|Common Windows filesystem, also supported by Linux|

## 7. Important Linux File System Concepts

### Inodes

An inode stores metadata about a filesystem object, such as:

- File permissions.
- Owner and group.
- File size.
- Timestamps.
- Data block references.

The filename is stored in its directory entry, not directly as part of the inode.

### Mounting

Mounting makes a filesystem accessible at a directory called a mount point.

Example:

```
mount
```

### Journaling

A journaling filesystem records certain planned changes in a journal to help maintain filesystem consistency after crashes or unexpected shutdowns.

## 8. Linux File System and Cybersecurity

Understanding the filesystem helps security professionals:

- Locate configuration files.
- Investigate suspicious files.
- Examine system logs.
- Identify unauthorised modifications.
- Analyse user activity.
- Investigate malware persistence.

Important locations for security investigations:

|Location|Investigation Value|
|---|---|
|`/etc`|System configuration|
|`/var/log`|System and application logs|
|`/home`|User files and activity|
|`/tmp`|Temporary files that may contain suspicious artifacts|
|`/root`|Root user's files and configuration|
|`/proc`|Runtime process and kernel information|

A suspicious file location alone does not prove malicious activity.

## 9. Practical: Explore the Linux File System

Open your Kali Linux terminal.

### Task 1: Display Current Directory

```
pwd
```

### Task 2: List Files and Directories

```
ls
```

### Task 3: Display Detailed Information

```
ls -la
```

### Task 4: Explore the Root Directory

```
ls /
```

### Task 5: Explore the /etc Directory

```
ls /etc
```

### Task 6: Identify Filesystem Types

```
df -Th
```

### Task 7: Display Mounted Filesystems

```
findmnt
```

### Task 8: Explore System Logs

```
ls /var/log
```

These commands are for inspection and do not intentionally modify files.

## 10. Important Commands

|Command|Purpose|
|---|---|
|`pwd`|Displays the current directory|
|`ls`|Lists directory contents|
|`ls -la`|Displays hidden and detailed entries|
|`cd`|Changes the current directory|
|`find`|Searches for files and directories|
|`df -h`|Displays filesystem disk usage|
|`df -Th`|Displays filesystem types and usage|
|`findmnt`|Displays mounted filesystems|
|`stat`|Displays file metadata|

## 11. My Understanding

Answer these questions in your own words:

1. What is a Linux file system?
2. What is the purpose of the `/` directory?
3. What is the difference between `/home` and `/root`?
4. What is the difference between absolute and relative paths?
5. What is an inode?
6. What is mounting?
7. Why is `/var/log` important in digital forensics?

## 12. Practical Observations

Record your findings:

- Current working directory:
- Number of entries in `/`:
- One important file inside `/etc`:
- Filesystem type of your main Linux partition:
- Total disk space:
- One observation from `/var/log`:

## Related Topics

- [[Introduction to Linux]]
- [[Linux Architecture]]
- [[Linux Commands]]
- [[Linux Permissions]]
- [[Linux Users and Groups]]
- [[Digital Forensics]]
- [[Practical Labs]]

---

**Category:** Linux Operating System

**Status:** Learning