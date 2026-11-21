## 1. What Is User Account Management?

User account management is the process of creating, configuring, monitoring, and maintaining user accounts on a computer system.

It allows administrators to control who can access a system and what actions they can perform.

Every user account is associated with an identity that the operating system uses to manage access.

## 2. Why Is User Account Management Important?

It helps administrators:

- Control access to systems.
    
- Assign permissions.
    
- Separate user activities.
    
- Protect sensitive information.
    
- Manage administrative privileges.
    
- Disable unused accounts.
    
- Monitor account activity.
    

## 3. Types of User Accounts

### A. Standard User

A standard user can perform everyday tasks but has limited administrative permissions.

Examples:

- Browsing the internet.
    
- Running applications.
    
- Creating personal files.
    

### B. Administrator

An administrator has elevated privileges to perform system-level operations.

Examples:

- Installing software.
    
- Managing users.
    
- Changing system configurations.
    
- Managing services.
    

**Security principle:** Use a standard account for everyday work and elevate privileges only when necessary.

## 4. Local Accounts vs Domain Accounts

### Local Account

A local account exists on an individual computer.

It is managed by that computer's operating system.

### Domain Account

A domain account is managed centrally through a directory service such as Microsoft Active Directory.

It can be used to access multiple domain-joined systems, subject to assigned permissions and policies.

|Local Account|Domain Account|
|---|---|
|Managed on one computer.|Centrally managed through a domain.|
|Usually used on an individual device.|Can provide access across domain resources.|
|Credentials are managed locally.|Authentication is handled through domain infrastructure.|

Related: [[Active Directory]]

## 5. Windows User Account Management

Windows provides several tools for managing user accounts.

### A. Computer Management

1. Press `Win + R`.
    
2. Enter `compmgmt.msc`.
    
3. Open Local Users and Groups.
    
4. Select Users.
    

You can inspect local accounts and groups.

Note: Local Users and Groups may not be available in some Windows editions, including Windows Home.

### B. PowerShell Commands

List local user accounts:

```
Get-LocalUser
```

Get details about a specific account:

```
Get-LocalUser -Name "Administrator"
```

List local groups:

```
Get-LocalGroup
```

List members of the Administrators group:

```
Get-LocalGroupMember -Group "Administrators"
```

These commands are for inspection.

## 6. Linux User Account Management

Linux supports multiple user accounts with different permissions.

### A. List Users

```
cat /etc/passwd
```

This file contains account information, not users' plaintext passwords.

### B. Display Current User

```
whoami
```

### C. Display User Identity and Groups

```
id
```

### D. Display Logged-in Users

```
who
```

### E. Inspect Account Information

```
getent passwd
```

## 7. Important Linux Account Files

|File|Purpose|
|---|---|
|`/etc/passwd`|Stores account information.|
|`/etc/shadow`|Stores password hashes and password-aging information.|
|`/etc/group`|Stores group information.|
|`/etc/gshadow`|Stores protected group information.|

Access to sensitive account files is restricted.

## 8. User Account Security

Good account management practices include:

- Use strong, unique passwords.
    
- Enable multi-factor authentication where supported.
    
- Avoid sharing accounts.
    
- Disable unused accounts.
    
- Review administrator membership.
    
- Follow the principle of least privilege.
    
- Monitor suspicious login activity.
    

## 9. Common Security Risks

### Excessive Privileges

Giving users more permissions than necessary increases security risk.

### Weak Passwords

Weak or reused passwords can make accounts easier to compromise.

### Unused Accounts

Old accounts may remain active even when they are no longer needed.

### Shared Accounts

Shared accounts make it difficult to identify which individual performed an action.

### Privilege Escalation

An attacker may attempt to gain higher privileges after compromising a lower-privileged account.

Related: [[Privilege Management]], [[Access Control]], [[Operating System Security]]

## 10. Practical Lab — Inspect User Accounts

### Lab A: Windows PowerShell

Run:

```
Get-LocalUser
```

Then:

```
Get-LocalGroup
```

Finally:

```
Get-LocalGroupMember -Group "Administrators"
```

Record:

- Number of local user accounts.
    
- Names of local groups.
    
- Members of the Administrators group.
    

### Lab B: Kali Linux

Run:

```
whoami
```

Then:

```
id
```

Then:

```
getent passwd
```

Finally:

```
getent group
```

Record:

- Your current username.
    
- Your user ID (UID).
    
- Your primary group ID (GID).
    
- Some group names present on your system.
    

## 11. Practical Tasks

1. Inspect local users in Windows.
    
2. Identify the Windows administrator account.
    
3. Inspect local groups.
    
4. Identify your current Kali Linux user.
    
5. Find your UID and GID.
    
6. Compare Windows and Linux account management.
    

Do not create, delete, or modify accounts during this introductory lab.

## 12. My Understanding

Answer in your own words:

1. What is user account management?
    
2. What is the difference between a standard user and an administrator?
    
3. What is the difference between a local account and a domain account?
    
4. What information is stored in `/etc/passwd`?
    
5. Why should administrator privileges be limited?
    
6. What is the principle of least privilege?
    

## 13. Related Notes

- [[Windows Users and Groups]]
    
- [[Linux Users and Groups]]
    
- [[Windows Permissions]]
    
- [[Linux Permissions]]
    
- [[Privilege Management]]
    
- [[Access Control]]
    
- [[Active Directory]]
    
- [[Operating System Security]]
    

---

**Key Takeaway:** User account management controls system identities and privileges. Proper account management reduces unauthorized access and limits security risks.