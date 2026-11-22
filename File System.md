> Understand how operating systems organize, store, retrieve, and manage files and directories.

## 1. What Is a File System?

A file system is a method used by an operating system to organize and manage data on a storage device.

It defines how files and directories are:

- Named.
- Stored.
- Organized.
- Retrieved.
- Protected.
- Managed.

Examples include NTFS, FAT32, exFAT, ext4, and XFS.

## 2. What Is a File?

A file is a named collection of data stored on a storage device.

Examples:

- `document.txt`
- `photo.jpg`
- `script.py`
- `report.pdf`

Files can contain text, images, programs, audio, video, or other data.

## 3. What Is a Directory?

A directory is a structure used to organize files and other directories.

Example:

```
Documents/
├── Notes/
│   ├── Linux.md
│   └── Windows.md
├── Reports/
│   └── Security.pdf
└── Projects/
    └── script.py
```

Directories help users organize information logically.

## 4. Common File Systems

|File System|Common Usage|
|---|---|
|NTFS|Windows internal drives|
|FAT32|USB drives and removable storage|
|exFAT|USB drives and external storage|
|ext4|Linux systems|
|XFS|Linux servers and storage systems|
|APFS|Apple devices|

Different file systems provide different features, compatibility, and limitations.

## 5. File System Structure

A file system maintains information about stored data.

Common concepts include:

|Component|Purpose|
|---|---|
|Metadata|Information describing a file|
|File allocation|Tracks storage space assigned to files|
|Directory entries|Connect filenames to file information|
|Permissions|Control access to files|
|Journaling|Records intended filesystem changes for recovery|

The exact implementation depends on the file system.

## 6. File Metadata

Metadata is information about a file rather than its actual contents.

Examples:

- File name.
- File size.
- Owner.
- Permissions.
- Creation or modification timestamps, where supported.
- File type.

Inspect file metadata in Linux:

```
stat sample.txt
```

## 7. Inodes in Linux

In Linux file systems such as ext4, an inode stores metadata about a file.

It commonly contains:

- File type.
- Permissions.
- Owner and group IDs.
- File size.
- Timestamps.
- Pointers or references to data blocks.

The filename is stored in a directory entry, which references the inode.

Inspect an inode number:

```
ls -i sample.txt
```

Inspect detailed inode information:

```
stat sample.txt
```

## 8. File System Mounting

Mounting makes a file system accessible through a directory called a mount point.

Linux commonly uses a single directory hierarchy beginning at `/`.

Example:

```
mount
```

Display disk and mount information:

```
lsblk
```

Display mounted file systems and usage:

```
df -h
```

## 9. Journaling File Systems

A journaling file system records intended changes in a journal before or while applying them to the main file system.

This helps improve consistency and recovery after unexpected shutdowns.

Examples include:

- NTFS.
- ext4.
- XFS.

Journaling does not replace backups and does not guarantee recovery from every form of corruption.

## 10. File Systems and Cybersecurity

File systems are important in cybersecurity and digital forensics.

Security analysts examine:

1. File permissions.
2. File ownership.
3. File modification timestamps.
4. Hidden files.
5. Unusual executable files.
6. Unauthorized file changes.
7. File system artifacts.

### Example: Suspicious File Investigation

Suppose an analyst discovers an unfamiliar executable in a temporary directory.

The analyst may investigate:

- File path.
- File metadata.
- Ownership and permissions.
- Cryptographic hash.
- Related processes.
- Relevant system logs.

An unfamiliar filename alone does not prove malicious activity.

## 11. Practical Lab — File System Inspection

Use your Kali Linux terminal.

### Task 1 — Display disk partitions

```
lsblk
```

### Task 2 — Display mounted file systems

```
df -h
```

### Task 3 — Identify the file system of a mounted device

```
findmnt
```

### Task 4 — Create a practice directory

```
mkdir -p ~/ROOTLOG-LAB/filesystem
cd ~/ROOTLOG-LAB/filesystem
```

### Task 5 — Create a sample file

```
echo "ROOTLOG file system practice" > sample.txt
```

### Task 6 — Inspect file metadata

```
stat sample.txt
```

### Task 7 — Display the inode number

```
ls -i sample.txt
```

### Task 8 — Calculate the file hash

```
sha256sum sample.txt
```

### Task 9 — Display the file contents

```
cat sample.txt
```

Do not format, partition, mount, or modify your system's storage devices during this introductory lab.

## 12. Key Takeaways

- A file system organizes data on storage devices.
- Files contain data; directories organize files.
- NTFS and ext4 are examples of file systems.
- Metadata describes files.
- Inodes store file metadata in many Linux file systems.
- Mounting makes a file system accessible.
- Journaling helps maintain file system consistency.
- File system analysis is important in digital forensics.

## 13. My Understanding

Answer in your own words:

1. What is a file system?
2. What is the difference between a file and a directory?
3. What is file metadata?
4. What is an inode?
5. What is mounting?
6. Why is file system analysis important in digital forensics?

## Related Notes

- [[Linux File System]]
- [[Windows File System]]
- [[Linux Permissions]]
- [[Digital Forensics]]
- [[File System Forensics]]
- [[Operating System Security]]
- [[Device Drivers]]

---