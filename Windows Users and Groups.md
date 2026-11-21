>Windows uses user accounts and groups to control who can access a computer and what actions they can perform.

A **user account** represents an individual or service that can access the system.

A **group** is a collection of user accounts that share permissions and access rights.

## 2. Types of Windows User Accounts

### Administrator Account

- Has elevated privileges.
- Can install software and manage system settings.
- Can create and manage user accounts.
- Can modify system-wide configurations.

### Standard User Account

- Used for everyday activities.
- Can run applications.
- Has limited system-level privileges.
- Usually cannot make protected system changes without administrator approval.

### Guest Account

Historically provided limited temporary access. It is disabled by default in modern Windows configurations and should not be treated as a normal recommended account.

### Service Accounts

Accounts used by Windows services and applications to run background tasks.

Examples include built-in service identities such as:

- Local System
- Local Service
- Network Service

## 3. Local Accounts and Microsoft Accounts

### Local Account

- Exists on a particular Windows computer.
- Can be used without a Microsoft account.
- Is managed locally.

### Microsoft Account

- Uses Microsoft account credentials.
- Can integrate with Microsoft services.
- May synchronise certain settings across devices.

## 4. Windows Groups

Groups simplify permission management by allowing administrators to assign rights to multiple users together.

Common local groups include:

|Group|Purpose|
|---|---|
|Administrators|Members have administrative privileges|
|Users|Standard local users|
|Guests|Limited guest-related access|
|Remote Desktop Users|Members can connect through Remote Desktop when other requirements are met|
|Backup Operators|Special backup and restore privileges|

Group membership does not automatically grant access to every resource. Resource permissions and other security controls also apply.

## 5. User Account Security

Important security principles:

- Use standard accounts for everyday activities.
- Avoid unnecessary administrator privileges.
- Use strong, unique passwords.
- Enable multifactor authentication where available.
- Disable or remove unused accounts through authorised administration.
- Review group membership regularly.

## 6. Cybersecurity Importance

User accounts and groups are important in cybersecurity because attackers may attempt to:

- Steal user credentials.
- Create unauthorised accounts.
- Add accounts to privileged groups.
- Abuse administrator privileges.
- Access resources using compromised accounts.

### Privilege Escalation

Privilege escalation occurs when an attacker gains permissions beyond those initially available.

Example:

An attacker compromises a standard user account and exploits a vulnerability to gain administrator-level privileges.

## 7. Practical: Inspect Users and Groups Using PowerShell

### Task 1: Display Current User

```
whoami
```

### Task 2: Display Current User's Group Memberships

```
whoami /groups
```

### Task 3: List Local User Accounts

```
Get-LocalUser
```

### Task 4: List Local Groups

```
Get-LocalGroup
```

### Task 5: Inspect Administrators Group

```
Get-LocalGroupMember -Group "Administrators"
```

### Task 6: Inspect a Specific User

```
Get-LocalUser -Name "Administrator"
```

If the account does not exist or is renamed, PowerShell may return an error. That is a valid observation.

## 8. Important Commands

|Command|Purpose|
|---|---|
|`whoami`|Displays the current identity|
|`whoami /groups`|Displays group memberships|
|`Get-LocalUser`|Lists local users|
|`Get-LocalGroup`|Lists local groups|
|`Get-LocalGroupMember`|Displays members of a group|

## 9. My Understanding

Answer these questions in your own words:

1. What is a Windows user account?
2. What is a Windows group?
3. What is the difference between an administrator and a standard user?
4. What is privilege escalation?
5. Why should everyday activities use a standard account?

## 10. Practical Observations

Record your findings:

- Current username:
- Number of local user accounts:
- Number of local groups:
- Members of the Administrators group:
- One security observation:

## Related Topics

- [[Introduction to Windows]]
- [[Windows Architecture]]
- [[Windows Registry]]
- [[Windows Permissions]]
- [[Windows Services]]
- [[Windows Event Logs]]
- [[Active Directory]]
- [[Digital Forensics]]

---

**Category:** Windows Operating System

**Status:** Learning