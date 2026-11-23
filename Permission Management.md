## 1. What Is Permission Management?

Permission management is the process of controlling what users and processes are allowed to do with system resources.

These resources include:

- Files and folders.
- Applications.
- System settings.
- Devices.
- Network resources.

Permissions help prevent unauthorized access and modification.

## 2. Why Is Permission Management Important?

It helps administrators:

- Protect sensitive files.
- Restrict unauthorized changes.
- Control access to resources.
- Separate user privileges.
- Reduce security risks.
- Enforce the principle of least privilege.

## 3. Types of Permissions

Common permissions include:

|Permission|Meaning|
|---|---|
|Read|View or access information.|
|Write|Modify information.|
|Execute|Run a program or execute a file.|
|Modify|Read, write, and delete in many Windows access-control contexts.|
|Full Control|Includes extensive permissions, such as changing permissions and ownership.|

The exact meaning depends on the operating system and resource.

## 4. Windows Permissions

Windows uses Access Control Lists (ACLs) to control access to resources.

An ACL contains Access Control Entries (ACEs) that specify which users or groups are allowed or denied particular actions.

### Common Windows Permissions

- Read
- Write
- Read & Execute
- Modify
- Full Control

### Inspect Permissions Using PowerShell

Check file permissions:

```
Get-Acl "C:\Users"
```

Display access rules:

```
(Get-Acl "C:\Users").Access
```

Check a specific file:

```
Get-Acl "C:\Windows\System32\drivers\etc\hosts"
```

### Windows Security Interface

1. Right-click a file or folder.
2. Select Properties.
3. Open the Security tab.
4. Select a user or group.
5. Inspect the assigned permissions.

Do not change system permissions during this introductory lab.

## 5. Linux Permissions

Linux uses a permission model based on three classes:

- Owner
- Group
- Others

Each class can have three basic permissions:

|Permission|Symbol|Meaning|
|---|---|---|
|Read|`r`|Read file contents or list directory entries.|
|Write|`w`|Modify a file or directory entries.|
|Execute|`x`|Execute a file or traverse a directory.|

### Example

Run:

```
ls -l
```

Example output:

```
-rwxr-xr-- 1 user group 1024 Nov 21 example.sh
```

Permission breakdown:

```
- rwx r-x r--
  |   |   |
  |   |   +--- Others
  |   +------- Group
  +----------- Owner
```

In this example:

- Owner: Read, write, execute.
- Group: Read, execute.
- Others: Read only.

## 6. Understanding Linux Permission Numbers

Linux permissions can also be represented numerically.

|Permission|Value|
|---|---|
|Read (`r`)|4|
|Write (`w`)|2|
|Execute (`x`)|1|

Values are added together.

Examples:

|Number|Permissions|
|---|---|
|7|Read + Write + Execute|
|6|Read + Write|
|5|Read + Execute|
|4|Read only|
|0|No permissions|

### Example: 755

```
755 = rwx r-x r-x
```

- Owner: 7 = Read, Write, Execute.
- Group: 5 = Read, Execute.
- Others: 5 = Read, Execute.

### Example: 644

```
644 = rw- r-- r--
```

- Owner: Read and Write.
- Group: Read only.
- Others: Read only.

## 7. Important Linux Permission Commands

Display file permissions:

```
ls -l
```

Display permissions of a specific file:

```
stat example.txt
```

Change file permissions:

```
chmod 644 example.txt
```

Change file ownership:

```
chown user:group example.txt
```

**Warning:** `chmod` and `chown` modify permissions and ownership. Do not run them on system files or directories during this introductory lab.

## 8. Special Linux Permissions

Linux also supports special permission bits.

### SUID

Set User ID allows an executable to run with the effective user ID of its owner.

### SGID

Set Group ID can cause an executable to run with the effective group ID of its group owner. On directories, it can cause newly created entries to inherit the directory's group.

### Sticky Bit

On directories, the sticky bit restricts deletion or renaming of entries to their owners, the directory owner, or privileged users.

Example:

```
drwxrwxrwt
```

The final `t` indicates the sticky bit.

## 9. Windows vs Linux Permissions

|Windows|Linux|
|---|---|
|Uses ACLs and access-control entries.|Uses owner, group, and others permissions, with additional mechanisms available.|
|Permissions include Modify and Full Control.|Basic permissions are read, write, and execute.|
|Managed through Security properties and tools such as `icacls`.|Managed through tools such as `chmod` and `chown`.|
|Supports detailed per-user and group access rules.|Supports ACLs for more detailed access control too.|

## 10. Permission Management and Cybersecurity

Incorrect permissions can create security vulnerabilities.

Examples:

- World-writable files may allow unauthorized modification.
- Excessive privileges can enable privilege escalation.
- Sensitive files may be readable by unauthorized users.
- Incorrect directory permissions may expose important data.
- Misconfigured service permissions may allow attackers to interfere with services.

Follow the principle of least privilege: give each user or process only the permissions required for its work.

Related: [[Privilege Management]], [[Access Control]], [[Operating System Security]]

## 11. Practical Lab — Inspect Permissions

### Lab A: Kali Linux

Create a practice directory and file:

```
mkdir -p ~/permission-lab
cd ~/permission-lab
touch example.txt
```

Inspect permissions:

```
ls -l example.txt
```

Inspect detailed metadata:

```
stat example.txt
```

Change permissions on this practice file:

```
chmod 640 example.txt
```

Verify:

```
ls -l example.txt
```

Expected permissions:

```
-rw-r-----
```

### Lab B: Windows PowerShell

Inspect permissions:

```
Get-Acl "$env:USERPROFILE\Desktop"
```

Display access rules:

```
(Get-Acl "$env:USERPROFILE\Desktop").Access
```

Compare the Windows permission information with the Linux output.

## 12. Practical Tasks

1. Run `ls -l` in Kali Linux.
2. Identify the owner, group, and permissions of a file.
3. Create a practice file.
4. Change its permissions to `640`.
5. Verify the result.
6. Inspect a folder's permissions in Windows PowerShell.
7. Explain the difference between Windows ACLs and basic Linux permissions.

## 13. My Understanding

Answer in your own words:

1. What is permission management?
2. What are the three Linux permission classes?
3. What do read, write, and execute mean?
4. What does `755` represent?
5. What is an Access Control List?
6. How can incorrect permissions create security vulnerabilities?

## 14. Related Notes

- [[User Account Management]]
- [[Windows Permissions]]
- [[Linux Permissions]]
- [[Privilege Management]]
- [[Access Control]]
- [[Operating System Security]]
- [[Windows Users and Groups]]
- [[Linux Users and Groups]]

---

**Key Takeaway:** Permission management controls access to system resources. Correct permissions help protect data and prevent unauthorized actions.