> Privilege Management is the process of controlling and managing the permissions and privileges assigned to users, applications, and system processes.

## 1. What Are Privileges?

A privilege is a permission that allows a user or process to perform a particular operation on a system.

Examples:

- Installing software.
- Creating user accounts.
- Modifying system configurations.
- Managing system services.
- Accessing protected files.
- Shutting down a computer.

Not every user should have permission to perform these operations.

## 2. Standard User vs Administrator

Operating systems commonly separate standard users from administrative users.

|Standard User|Administrator|
|---|---|
|Performs everyday tasks.|Manages system-wide settings.|
|Has limited permissions.|Has elevated privileges.|
|Cannot normally modify protected system files.|Can modify protected system resources.|
|Lower impact if compromised.|Compromise can affect the entire system.|

In Linux, the administrator account is commonly called `root`.

In Windows, administrative privileges are generally associated with membership in the Administrators group.

## 3. Privilege Escalation

Privilege escalation occurs when a user or process obtains privileges beyond those originally authorized.

### Vertical Privilege Escalation

A user gains a higher level of privilege.

Example:

A standard user obtains administrator or root access.

### Horizontal Privilege Escalation

A user accesses another user's resources without authorization while remaining at a similar privilege level.

Example:

A normal user accesses another employee's private files.

## 4. Privilege Management in Windows

Windows uses security tokens, user accounts, groups, and User Account Control (UAC) to manage privileges.

### User Account Control (UAC)

UAC helps prevent unauthorized system-level changes by requesting approval or administrator credentials when elevated actions are required.

### Windows Groups

Important groups include:

- Administrators
- Users
- Remote Desktop Users
- Backup Operators

Group membership can grant significant permissions.

Useful PowerShell commands:

**Check current user**

```
whoami
```

**Check group membership**

```
whoami /groups
```

**Check assigned privileges**

```
whoami /priv
```

**List local users**

```
Get-LocalUser
```

**List local groups**

```
Get-LocalGroup
```

## 5. Privilege Management in Linux

Linux uses users, groups, file permissions, and privilege elevation tools.

### Root User

The root user has extensive administrative privileges.

Its user ID (UID) is normally `0`.

### sudo

`sudo` allows authorized users to execute commands with elevated privileges according to the system's configuration.

Example:

```
sudo apt update
```

This runs the package update command with elevated privileges.

### su

`su` is used to switch to another user account.

Example:

```
su username
```

Useful commands:

**Check user identity**

```
id
```

**Check sudo permissions**

```
sudo -l
```

**Check root UID**

```
id root
```

**Check current username**

```
whoami
```

## 6. Principle of Least Privilege

The Principle of Least Privilege (PoLP) states:

> Every user, application, and process should receive only the minimum permissions necessary to perform its required tasks.

Example:

A student who only needs to read a document should not receive administrator access to the computer.

Benefits:

- Reduces unauthorized access.
- Limits damage caused by compromised accounts.
- Reduces accidental system changes.
- Makes security monitoring easier.

## 7. Common Privilege Management Risks

- Giving administrator access to every user.
- Using shared administrator accounts.
- Weak passwords on privileged accounts.
- Leaving unused privileged accounts active.
- Running applications with unnecessary elevated privileges.
- Misconfigured sudo permissions.
- Failing to monitor privileged activities.

## 8. Privilege Management Best Practices

1. Use standard accounts for everyday activities.
2. Grant administrative access only when required.
3. Use separate administrator accounts where appropriate.
4. Review privileged group memberships regularly.
5. Protect administrator credentials.
6. Monitor privileged operations.
7. Remove unnecessary privileges.
8. Apply the principle of least privilege.

## 9. Practical Lab — Inspect User Privileges

Perform these checks without changing account permissions.

### Windows PowerShell

```
whoami
whoami /groups
whoami /priv
Get-LocalGroupMember -Group "Administrators"
```

Observe:

- Your current identity.
- Your group memberships.
- Assigned privileges.
- Members of the Administrators group.

### Kali Linux

```
whoami
id
id root
sudo -l
getent group sudo
```

Observe:

- Current user and UID.
- Group memberships.
- Root account UID.
- Available sudo permissions.
- Members of the sudo group.

Some commands may show different results depending on your account and system configuration.

## 10. Key Takeaways

- Privileges determine what operations users and processes can perform.
- Administrators and root users have elevated permissions.
- Windows uses UAC, security tokens, and groups.
- Linux uses root, sudo, users, and groups.
- Privilege escalation can be vertical or horizontal.
- Least privilege reduces the impact of compromised accounts.

## 11. Questions to Understand

1. What is Privilege Management?
2. What is the difference between a standard user and an administrator?
3. Explain vertical and horizontal privilege escalation.
4. What is UAC?
5. What is the purpose of sudo?
6. Explain the Principle of Least Privilege.

## Related Notes

- [[Operating System Security]]
- [[Access Control]]
- [[System Hardening]]
- [[User Account Management]]
- [[Windows Users and Groups]]
- [[Linux Users and Groups]]
- [[Windows Permissions]]
- [[Linux Permissions]]
- [[05 - Active Directory]]

---