> A file system is a method used by an operating system to organize, store, retrieve, and manage data on storage devices.

## 1. What is a File System?

A file system defines how files and directories are organized and stored on a storage device.

Windows supports several file systems, including:

- NTFS
- FAT32
- exFAT
- ReFS

## 2. Types of Windows File Systems

### 2.1 NTFS (New Technology File System)

NTFS is the primary file system used by modern Windows installations.

**Features:**

- File and folder permissions (ACLs).
- File compression.
- Encryption support through EFS.
- Disk quotas.
- Journaling.
- Support for large files and volumes.

**Example:** A typical Windows system drive uses NTFS.

### 2.2 FAT32

FAT32 is an older file system commonly found on removable storage devices.

**Features:**

- Broad compatibility.
- Simple file-system structure.
- Maximum individual file size of approximately 4 GB minus 1 byte.

**Example:** Older USB drives and memory cards.

### 2.3 exFAT

exFAT is designed primarily for flash storage devices.

**Features:**

- Supports files larger than 4 GB.
- Suitable for USB drives and SD cards.
- Compatible with many operating systems.

### 2.4 ReFS (Resilient File System)

ReFS is a Microsoft file system designed for resilience and data integrity in supported Windows environments.

**Features:**

- Data integrity mechanisms.
- Resilience against certain forms of corruption.
- Designed for large storage environments.

## 3. Windows Directory Structure

Windows organizes files into directories.

Important directories include:

|Directory|Purpose|
|---|---|
|`C:\Windows`|Windows operating-system files|
|`C:\Program Files`|Installed applications|
|`C:\Users`|User profiles|
|`C:\ProgramData`|Shared application data|
|`C:\Windows\System32`|Important system files and utilities|
|`C:\Temp`|May contain temporary files if configured|

**Important:** `System32` contains critical Windows components. Do not modify or delete files there without understanding their purpose.

## 4. File Permissions and Security

NTFS supports Access Control Lists (ACLs).

Permissions determine what users and groups can do with files and directories.

Common permissions include:

- Full Control
- Modify
- Read and Execute
- Read
- Write

**Example:** A standard user may be allowed to read a file but not modify it.

Related: [[Windows Permissions]]

## 5. Important NTFS Concepts

### Master File Table (MFT)

The MFT is a central NTFS metadata structure containing records describing files and directories on an NTFS volume.

### File Metadata

Metadata describes information about a file.

Examples:

- File name
- File size
- File timestamps
- File attributes
- Security information

### Journaling

NTFS uses a transaction log to help maintain file-system consistency after certain unexpected interruptions.

## 6. Windows File System and Cybersecurity

Understanding the file system helps security professionals:

- Investigate suspicious files.
- Examine file permissions.
- Identify unauthorized modifications.
- Analyze malware persistence locations.
- Recover digital evidence.
- Investigate file activity.

**Example:** An investigator may examine suspicious executables in user profile directories.

## 7. Practical Lab — PowerShell

### 7.1 Display Available Drives

```
Get-PSDrive -PSProvider FileSystem
```

### 7.2 Check Disk File Systems

```
Get-Volume |
Select-Object DriveLetter, FileSystem, FileSystemLabel
```

### 7.3 List Files and Directories

```
Get-ChildItem C:\
```

### 7.4 Display File Information

```
Get-Item "$env:WINDIR\explorer.exe" |
Select-Object Name, Length, CreationTime, LastWriteTime
```

### 7.5 View File Permissions

```
Get-Acl "$env:WINDIR\explorer.exe" |
Format-List
```

## 8. My Understanding

Answer in your own words:

1. What is a file system?
2. Why is NTFS commonly used in Windows?
3. What is the difference between FAT32 and exFAT?
4. What is the purpose of the MFT?
5. Why are file permissions important for cybersecurity?

## 9. Knowledge Check

1. Which file system is commonly used by Windows?
2. What is the maximum individual file size supported by FAT32?
3. What does NTFS stand for?
4. What is an ACL?
5. Which PowerShell command displays available volumes?

## Related Notes

- [[Operating Systems]]
- [[Introduction to Windows]]
- [[Windows Architecture]]
- [[Windows Registry]]
- [[Windows Permissions]]
- [[Windows Users and Groups]]
- [[Windows Event Logs]]
- [[Digital Forensics]]

---

**Category:** Windows Operating System

**Status:** Learning