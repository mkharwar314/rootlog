>Windows permissions define what actions a user or group can perform on a resource, such as a file, folder, or system object.

They help protect data from unauthorised access, modification, and deletion.

## 2. Types of Basic Permissions

Windows commonly provides these file and folder permissions:

|Permission|Description|
|---|---|
|Full Control|Allows all permitted actions, including changing permissions|
|Modify|Allows reading, writing, modifying, and deleting|
|Read & Execute|Allows viewing and running files|
|List Folder Contents|Allows viewing folder contents|
|Read|Allows viewing file or folder information|
|Write|Allows creating files and modifying data|

The exact effective access depends on the resource, permission entries, and security context.

## 3. NTFS Permissions

NTFS permissions control access to files and folders stored on NTFS volumes.

They are implemented through **Access Control Lists (ACLs)**.

Two important concepts:

- **DACL (Discretionary Access Control List):** Determines which users or groups are allowed or denied access.
- **SACL (System Access Control List):** Defines which access events can be audited.

## 4. Allow and Deny Permissions

### Allow

Grants a user or group specified access.

### Deny

Explicitly blocks specified access.

Deny entries generally take precedence over conflicting allow entries, although effective access also depends on the complete security context and applicable rules.

## 5. Permission Inheritance

Permission inheritance allows child files and folders to receive permissions from their parent folder.

Example:

A folder may grant the Users group read access. Files inside that folder can inherit the same permission.

Inheritance can be disabled or overridden through explicit permission entries.

## 6. NTFS Permissions vs Share Permissions

|NTFS Permissions|Share Permissions|
|---|---|
|Apply to files and folders on NTFS volumes|Apply when accessing resources through a network share|
|Work for local and network access|Apply to network access through the share|
|Managed through file and folder security settings|Managed through sharing settings|
|Combine with share permissions for network access|Combine with NTFS permissions for network access|

For network access, the effective permissions are generally the most restrictive combination of the applicable share and NTFS permissions.

## 7. Cybersecurity Importance

Permissions are important because they help prevent:

- Unauthorised file access.
- Accidental deletion of important data.
- Unauthorised system modifications.
- Privilege abuse.
- Exposure of confidential information.

### Principle of Least Privilege

The principle of least privilege means giving users and applications only the permissions they need to perform their tasks.

Example:

A normal user who only needs to read a report should not automatically receive permission to modify or delete it.

## 8. Practical: Inspect Permissions Using PowerShell

### Task 1: Check Current User

```
whoami
```

### Task 2: Inspect a Folder's Permissions

```
Get-Acl "$env:USERPROFILE\Documents"
```

### Task 3: Inspect Windows Folder Permissions

```
Get-Acl "$env:WINDIR"
```

### Task 4: Display Access Control Entries

```
(Get-Acl "$env:USERPROFILE\Documents").Access
```

### Task 5: Inspect File Permissions

```
Get-Acl "$env:WINDIR\explorer.exe"
```

## 9. Important Terms

|Term|Meaning|
|---|---|
|ACL|Access Control List|
|DACL|Defines allowed and denied access|
|SACL|Defines access auditing rules|
|Inheritance|Passing permissions from parent to child|
|Least Privilege|Granting only necessary permissions|
|Effective Access|Access a security principal can actually exercise|

## 10. My Understanding

Answer these questions in your own words:

1. What are Windows permissions?
2. What is the difference between Read and Modify?
3. What is an ACL?
4. What is the difference between DACL and SACL?
5. What is permission inheritance?
6. Explain the principle of least privilege.

## 11. Practical Observations

Record your findings:

- Folder inspected:
- Current user:
- One permission entry:
- Which group or user has access?
- What type of access is granted?
- One security observation:

## Related Topics

- [[Windows Users and Groups]]
- [[Windows File System]]
- [[Windows Registry]]
- [[Windows Services]]
- [[Windows Event Logs]]
- [[Operating System Security]]
- [[Access Control]]
- [[Digital Forensics]]

---

**Category:** Windows Operating System

**Status:** Learning