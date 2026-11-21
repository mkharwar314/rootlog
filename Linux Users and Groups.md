> Understand how Linux identifies users, organizes permissions, and controls access to system resources.

## 1. What Are Users in Linux?

Linux is a multi-user operating system. Multiple users can access the same system, each with their own identity and permissions.

A user account determines:

- Which files a user can access.
- Which commands a user can execute.
- Which system resources a user can use.
- What administrative privileges a user has.

### Types of Users

|User type|Purpose|
|---|---|
|Root user|Superuser with extensive administrative privileges|
|Regular user|Normal account for everyday activities|
|System user|Account used by services and system processes|

The root user has UID `0`.

## 2. What Is UID?

UID stands for **User Identifier**.

Linux assigns a numeric UID to every user account.

Example:

```
id
```

This displays your current user's UID and group information.

## 3. What Are Groups?

A group is a collection of users.

Groups make permission management easier because administrators can assign permissions to a group instead of configuring every user individually.

Example:

- `student1`
- `student2`
- `student3`

All three users could belong to a group called `students`.

### What Is GID?

GID stands for **Group Identifier**.

Linux assigns a numeric GID to each group.

## 4. Primary and Supplementary Groups

**Primary group:** The default group associated with a user's files and processes.

**Supplementary groups:** Additional groups that provide extra access or permissions.

A user can belong to multiple groups.

Check your groups:

```
groups
```

Display detailed identity information:

```
id
```

## 5. Important Linux Account Files

Linux stores user and group account information in specific system files.

|File|Purpose|
|---|---|
|`/etc/passwd`|User account information|
|`/etc/shadow`|Password hashes and password-aging information|
|`/etc/group`|Group information|
|`/etc/gshadow`|Protected group information|

**Security note:** `/etc/shadow` contains sensitive authentication data. Never share its contents or expose password hashes.

Inspect file permissions without displaying sensitive contents:

```
ls -l /etc/passwd /etc/shadow /etc/group /etc/gshadow
```

## 6. Important Linux User Commands

|Command|Purpose|
|---|---|
|`whoami`|Displays the current username|
|`id`|Displays UID, GID and group membership|
|`groups`|Displays group membership|
|`useradd`|Creates a user account|
|`usermod`|Modifies a user account|
|`userdel`|Deletes a user account|
|`passwd`|Changes a user's password|
|`getent passwd`|Retrieves user account entries|
|`getent group`|Retrieves group entries|

Examples:

```
whoami
```

```
id
```

```
getent passwd "$(whoami)"
```

```
getent group
```

## 7. Understanding sudo

`sudo` allows an authorized user to execute a command with elevated privileges.

Example:

```
sudo apt update
```

The command runs with elevated privileges according to the system's sudo policy.

### Important points

- Root has UID `0`.
- Not every user can use `sudo`.
- Sudo permissions are controlled by system policy.
- On standard Kali/Debian configurations, membership in the `sudo` group commonly grants administrative access.
- Administrators should use `visudo` to edit sudoers configuration safely.

## 8. Cybersecurity Importance

User and group management is important for system security.

Security risks include:

1. Unauthorized user accounts.
2. Weak or compromised passwords.
3. Excessive administrative privileges.
4. Incorrect group membership.
5. Misconfigured sudo permissions.

### Example: Privilege Escalation

Suppose an attacker compromises a regular user account.

If that account has unnecessary administrative privileges, the attacker may gain greater control over the system.

This is why administrators follow the **Principle of Least Privilege**: users should receive only the permissions necessary for their work.

## 9. Practical Lab — Inspect Users and Groups

Run these commands in your Kali Linux terminal:

**Task 1 — Identify your current user**

```
whoami
```

**Task 2 — Display your UID and GID**

```
id
```

**Task 3 — Display your group membership**

```
groups
```

**Task 4 — Retrieve your account entry**

```
getent passwd "$(whoami)"
```

**Task 5 — View available group entries**

```
getent group
```

**Task 6 — Inspect account-file permissions**

```
ls -l /etc/passwd /etc/shadow /etc/group /etc/gshadow
```

Do not create, delete, or modify accounts during this introductory lab.

## 10. Key Takeaways

- Linux supports multiple users.
- UID identifies a user.
- GID identifies a group.
- Users can belong to primary and supplementary groups.
- `/etc/passwd` stores account information.
- `/etc/shadow` stores sensitive authentication information.
- `sudo` provides controlled administrative access.
- Least privilege reduces security risks.

## 11. My Understanding

Write your own answers:

1. What is the difference between UID and GID?
2. Why does Linux use groups?
3. What is the purpose of the root account?
4. What is the difference between `/etc/passwd` and `/etc/shadow`?
5. Why is unnecessary sudo access dangerous?

## Related Notes

- [[Linux Permissions]]
- [[Linux Processes]]
- [[Operating System Security]]
- [[Access Control]]
- [[Privilege Management]]
- [[Active Directory]]

---

**Category:** Linux Operating System

**Status:** Learning