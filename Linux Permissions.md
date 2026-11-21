> Understand how Linux controls access to files and directories through ownership and permissions.

## 1. What Are Linux Permissions?

Linux permissions determine who can read, write, or execute a file or directory.

Every file and directory has three permission categories:

|Category|Meaning|
|---|---|
|User (u)|Owner of the file|
|Group (g)|Members of the assigned group|
|Others (o)|Everyone else|

## 2. Types of Permissions

Linux uses three basic permissions:

|Permission|Symbol|Numeric value|Meaning|
|---|---|---|---|
|Read|`r`|4|View file contents|
|Write|`w`|2|Modify file contents|
|Execute|`x`|1|Execute a file or access a directory|

**Important:** For directories, read allows listing entries, write allows creating or removing entries, and execute allows traversing the directory.

## 3. Understanding Permission Notation

Run:

```
ls -l
```

Example output:

```
-rwxr-xr-- 1 student student 1200 Nov 21 10:00 script.sh
```

Breakdown:

```
- | rwx | r-x | r--
   User  Group Others
```

- `-` means regular file.
- `rwx` means the owner can read, write, and execute.
- `r-x` means the group can read and execute.
- `r--` means others can only read.

## 4. Understanding chmod

`chmod` changes file or directory permissions.

### Symbolic Method

```
chmod u+x script.sh
```

Adds execute permission for the owner.

```
chmod g-w file.txt
```

Removes write permission from the group.

```
chmod o-r file.txt
```

Removes read permission from others.

### Numeric Method

Numeric permissions are calculated by adding values:

- Read = 4
- Write = 2
- Execute = 1

Examples:

|Permission|Calculation|Value|
|---|---|---|
|`rwx`|4 + 2 + 1|7|
|`rw-`|4 + 2|6|
|`r-x`|4 + 1|5|
|`r--`|4|4|

Example:

```
chmod 755 script.sh
```

This means:

- Owner: `rwx` (7)
- Group: `r-x` (5)
- Others: `r-x` (5)

Another example:

```
chmod 644 file.txt
```

This means:

- Owner: `rw-` (6)
- Group: `r--` (4)
- Others: `r--` (4)

## 5. Understanding chown

`chown` changes file ownership.

Syntax:

```
chown username file.txt
```

Change both owner and group:

```
chown username:groupname file.txt
```

Changing ownership generally requires administrative privileges.

## 6. Understanding chgrp

`chgrp` changes the group ownership of a file or directory.

Example:

```
chgrp students file.txt
```

This assigns the file to the `students` group.

## 7. Default Permissions and umask

`umask` controls which permission bits are removed from the default permissions when new files and directories are created.

Check your current umask:

```
umask
```

A common value is:

```
0022
```

For typical default creation modes:

- Files start from `666`.
- Directories start from `777`.

The umask removes permission bits from these defaults.

With umask `0022`:

- New files commonly receive `644`.
- New directories commonly receive `755`.

Actual permissions can also depend on the application creating the file.

## 8. Special Permissions

Linux also supports special permission bits.

|Permission|Meaning|
|---|---|
|SUID|Executable runs with the file owner's effective identity|
|SGID|Executable runs with the file group's effective identity; on directories, new entries inherit the directory's group|
|Sticky bit|On directories, restricts deletion or renaming of entries to their owners, the directory owner, or root|

Examples of commands:

```
chmod u+s file
chmod g+s directory
chmod +t directory
```

These permissions should be configured carefully because incorrect use can create security risks.

## 9. Cybersecurity Importance

Incorrect permissions can create serious security problems.

Examples:

1. Sensitive files readable by unauthorized users.
2. Executable scripts writable by untrusted users.
3. Incorrect ownership of system files.
4. Dangerous SUID executables.
5. Shared directories without appropriate restrictions.

### Example: Misconfigured Permissions

Suppose a confidential file has permissions `777`.

Every local user may be able to read, modify, and execute it.

This can expose sensitive information or allow unauthorized modification.

The principle of least privilege applies to file permissions too: grant only the access that is necessary.

## 10. Practical Lab — Inspect Permissions

Use your Kali Linux terminal.

### Task 1 — Display current directory contents

```
ls -l
```

### Task 2 — Create a practice directory

```
mkdir -p ~/ROOTLOG-LAB/permissions
cd ~/ROOTLOG-LAB/permissions
```

### Task 3 — Create a file

```
touch sample.txt
```

### Task 4 — Inspect its permissions

```
ls -l sample.txt
```

### Task 5 — Change permissions

```
chmod 640 sample.txt
```

### Task 6 — Verify the change

```
ls -l sample.txt
```

Expected permission notation:

```
-rw-r-----
```

### Task 7 — Inspect numeric permissions

```
stat -c "%a %n" sample.txt
```

Expected output:

```
640 sample.txt
```

### Task 8 — Check your umask

```
umask
```

Do not modify permissions on system files during this lab.

## 11. Key Takeaways

- Linux permissions control access to files and directories.
- `r` means read, `w` means write, and `x` means execute.
- `chmod` changes permissions.
- `chown` changes ownership.
- `chgrp` changes group ownership.
- `umask` controls default permission restrictions.
- SUID, SGID, and sticky bits provide special permission behavior.
- Misconfigured permissions can create security vulnerabilities.

## 12. My Understanding

Answer in your own words:

1. What are the three Linux permission categories?
2. What is the difference between `chmod` and `chown`?
3. What does permission `755` mean?
4. Why is permission `777` risky for sensitive files?
5. What is the purpose of `umask`?
6. What security risk can an incorrectly configured SUID executable create?

## Related Notes

- [[Linux Users and Groups]]
- [[Linux Processes]]
- [[Linux Services]]
- [[Access Control]]
- [[Privilege Management]]
- [[Operating System Security]]
- [[System Hardening]]

---

**Category:** Linux Operating System

**Status:** Learning