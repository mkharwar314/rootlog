> Access Control is a security mechanism that determines who can access a resource and what actions they are allowed to perform.

## 1. What Is Access Control?

Access control protects system resources from unauthorized access.

It determines:

- Who can access a resource?
- What resource can they access?
- What actions can they perform?
- Under what conditions is access allowed?

**Example:**

A student can view a file but cannot modify or delete it. An administrator may have permission to perform all three actions.

## 2. Main Components of Access Control

|Component|Meaning|
|---|---|
|Subject|User or process requesting access.|
|Object|Resource being accessed.|
|Permission|Allowed action on a resource.|
|Policy|Rules that determine access.|

Example:

- Subject: Student
- Object: `report.txt`
- Permission: Read
- Policy: Only authorized students can view the report.

## 3. Types of Access Control Models

### 1. Discretionary Access Control (DAC)

The owner of a resource decides who can access it.

Example:

- A file owner grants another user read or write permission.
- Commonly associated with traditional Unix/Linux file permissions.

### 2. Mandatory Access Control (MAC)

Access is determined by centrally enforced security policies and labels.

Users cannot freely change these policies.

Example:

- Military systems use classification levels such as Confidential, Secret, and Top Secret.

### 3. Role-Based Access Control (RBAC)

Permissions are assigned to roles rather than directly to individual users.

Example:

|Role|Permissions|
|---|---|
|Student|View study material|
|Teacher|View and upload material|
|Administrator|Manage users and resources|

### 4. Attribute-Based Access Control (ABAC)

Access decisions are based on attributes of the user, resource, action, and environment.

Example:

A user can access a document only if:

- Their department is Finance.
- The document is classified as Finance.
- They are accessing it from an approved device.

## 4. Access Control in Windows

Windows uses security identifiers (SIDs), security descriptors, and Access Control Lists (ACLs) to manage access.

### Access Control List (ACL)

An ACL contains entries that define which users or groups can access an object.

### Access Control Entry (ACE)

An ACE is an individual entry inside an ACL. It specifies a security principal and its allowed or denied permissions.

### NTFS Permissions

Common NTFS permissions include:

|Permission|Description|
|---|---|
|Full Control|Complete control over a file or folder.|
|Modify|Read, write, and delete.|
|Read & Execute|Read files and execute programs.|
|Read|View file contents.|
|Write|Create or modify files.|

Useful PowerShell command:

```
Get-Acl "C:\Windows"
```

This displays the security information for the specified directory.

## 5. Access Control in Linux

Linux uses ownership and permission bits to control access to files and directories.

Three permission categories:

- User (owner)
- Group
- Others

Three basic permissions:

|Permission|Symbol|Meaning|
|---|---|---|
|Read|r|Read file contents.|
|Write|w|Modify file contents.|
|Execute|x|Execute a file or access a directory.|

Example:

```
-rwxr-xr--
```

Breakdown:

- Owner: `rwx`
- Group: `r-x`
- Others: `r--`

Useful commands:

```
ls -l
```

```
stat filename
```

```
getfacl filename
```

The `getfacl` command displays Access Control Lists when ACL utilities are installed.

## 6. Authentication vs Authorization vs Access Control

|Concept|Purpose|
|---|---|
|Authentication|Verifies identity.|
|Authorization|Determines allowed actions.|
|Access Control|Enforces rules governing resource access.|

Example:

1. A user logs in with a password: Authentication.
2. The system checks whether the user can open a file: Authorization.
3. The file permissions enforce the decision: Access Control.

## 7. Common Access Control Risks

- Excessive permissions.
- Shared user accounts.
- Weak access policies.
- Incorrect file permissions.
- Unnecessary administrator privileges.
- Failure to remove access when users leave an organization.

These problems can lead to unauthorized data access, modification, or deletion.

## 8. Security Best Practices

1. Follow the principle of least privilege.
2. Assign permissions based on job responsibilities.
3. Use groups and roles to manage permissions.
4. Review permissions regularly.
5. Avoid unnecessary administrator access.
6. Remove unused accounts and permissions.
7. Audit access to sensitive resources.

## 9. Practical Lab — Inspect Access Control

Perform these checks without changing permissions.

### Windows PowerShell

```
whoami
Get-Acl "$HOME\Desktop"
icacls "$HOME\Desktop"
```

Observe:

- Current user.
- Folder owner.
- Assigned permissions.
- Access Control Entries.

### Kali Linux

```
whoami
id
ls -l
stat /etc/passwd
getfacl /etc/passwd
```

Observe:

- File ownership.
- User and group permissions.
- Access Control Entries, if present.

Do not modify system file permissions during this lab.

## 10. Key Takeaways

- Access control prevents unauthorized resource access.
- Subjects request access to objects.
- DAC, MAC, RBAC, and ABAC are different access control models.
- Windows uses ACLs and security descriptors.
- Linux uses ownership and permission bits, with optional ACL support.
- Least privilege reduces security risks.

## 11. Questions to Understand

1. What is Access Control?
2. What are subjects and objects?
3. Explain DAC, MAC, RBAC, and ABAC.
4. What is an ACL?
5. What is the difference between authentication and authorization?
6. Why is least privilege important?

## Related Notes

- [[Operating System Security]]
- [[Privilege Management]]
- [[System Hardening]]
- [[Windows Permissions]]
- [[Linux Permissions]]
- [[User Account Management]]
- [[Active Directory]]

---