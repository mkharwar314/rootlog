> Learn how operating systems identify users, manage groups, and control access to files and resources.

## 1. Lab Objectives

By completing these labs, I should be able to:

- Identify the current logged-in user.
- Inspect user accounts and groups.
- Understand file ownership.
- Read Windows and Linux permissions.
- Inspect Access Control Lists (ACLs).
- Safely modify permissions on test files.
- Understand the difference between authentication and authorization.

## 2. Important Concepts

|Concept|Meaning|
|---|---|
|User|An identity used to access a system.|
|Group|A collection of users managed together.|
|Ownership|Identifies the user or group associated with a file.|
|Permission|Defines what actions are allowed.|
|ACL|A list of access rules for an object.|
|Authentication|Verifies who a user is.|
|Authorization|Determines what an authenticated user can access.|
|Privilege|A level of authority to perform system operations.|

## 3. Windows User Inspection

Open PowerShell.

### Lab 1 — Identify Current User

```
whoami
```

Display group membership:

```
whoami /groups
```

**Observe:**

- Current username.
- Domain or computer name.
- Groups associated with the current account.

### Lab 2 — List Local Users

```
Get-LocalUser
```

Display details of a particular account:

```
Get-LocalUser -Name "Administrator"
```

The account may be disabled or renamed. Do not change its configuration.

### Lab 3 — Inspect Local Groups

```
Get-LocalGroup
```

Inspect members of a group:

```
Get-LocalGroupMember -Group "Administrators"
```

**Observe:**

- Group name.
- Group members.
- Whether your account belongs to an administrative group.

## 4. Windows File Permissions

### Lab 4 — Create a Test File

```
New-Item -ItemType Directory -Path "$HOME\PermissionLab" -Force
New-Item -ItemType File -Path "$HOME\PermissionLab\test.txt" -Force
```

Add sample content:

```
Set-Content "$HOME\PermissionLab\test.txt" "Permission testing"
```

### Lab 5 — Inspect Permissions

```
icacls "$HOME\PermissionLab\test.txt"
```

Alternative:

```
Get-Acl "$HOME\PermissionLab\test.txt" | Format-List
```

**Observe:**

- Owner of the file.
- Users and groups listed in the ACL.
- Allowed and denied permissions.
- Inherited permissions, if present.

Do not modify permissions on Windows system files or folders during this lab.

## 5. Linux User Inspection

Open your Kali Linux terminal.

### Lab 6 — Identify Current User

```
whoami
```

Display user and group IDs:

```
id
```

Display group membership:

```
groups
```

### Lab 7 — Inspect User and Group Records

```
getent passwd
```

Display group records:

```
getent group
```

**Observe:**

- Username.
- User ID (UID).
- Group ID (GID).
- Home directory.
- Default login shell.

Do not edit `/etc/passwd` or `/etc/group` manually.

## 6. Linux File Permissions

### Lab 8 — Create a Test Directory and File

```
mkdir -p ~/PermissionLab
cd ~/PermissionLab
touch test.txt
echo "Permission testing" > test.txt
```

### Lab 9 — Inspect File Permissions

```
ls -l test.txt
```

Inspect detailed metadata:

```
stat test.txt
```

If `getfacl` is installed:

```
getfacl test.txt
```

### Understanding Linux Permissions

Example:

```
-rw-r--r-- 1 user user 18 Nov 21 10:00 test.txt
```

|Part|Meaning|
|---|---|
|`-`|Regular file|
|`rw-`|Owner can read and write|
|`r--`|Group can read|
|`r--`|Others can read|

Linux permissions use three main categories:

- User (owner)
- Group
- Others

Permission symbols:

|Symbol|Meaning|Numeric value|
|---|---|---|
|`r`|Read|4|
|`w`|Write|2|
|`x`|Execute|1|
|`-`|No permission|0|

## 7. Modify Permissions Safely

Only perform these operations on your test file.

### Lab 10 — Change Permissions

Allow only the owner to read and write:

```
chmod 600 test.txt
```

Inspect the result:

```
ls -l test.txt
```

Restore normal read access for everyone:

```
chmod 644 test.txt
```

### Understand Permission Values

|Command|Owner|Group|Others|
|---|---|---|---|
|`chmod 777`|rwx|rwx|rwx|
|`chmod 755`|rwx|r-x|r-x|
|`chmod 700`|rwx|---|---|
|`chmod 644`|rw-|r--|r--|
|`chmod 600`|rw-|---|---|

Avoid using `777` as a general solution to permission problems. It grants broad access and can create security risks.

## 8. Understanding Umask

The `umask` determines which permission bits are removed from the default permissions when new files and directories are created.

Check your current setting:

```
umask
```

Create a test file and directory:

```
touch umask_test.txt
mkdir umask_test_dir
```

Inspect their permissions:

```
ls -ld umask_test.txt umask_test_dir
```

Record your observations.

## 9. Lab Documentation

For every lab, record:

|Field|Details|
|---|---|
|Lab Name||
|Operating System||
|Commands Used||
|Expected Result||
|Actual Result||
|Observations||
|Security Relevance||

## 10. Security Relevance

User and permission management is important in cybersecurity because it helps prevent unauthorized access.

Examples:

- Excessive privileges can allow attackers to perform administrative actions.
- Weak file permissions can expose sensitive information.
- Incorrect group membership can grant unnecessary access.
- Poor ACL configuration can create security weaknesses.
- Misconfigured service accounts can increase system risk.

## 11. Questions to Investigate

1. What is the difference between a user and a group?
2. What is the difference between authentication and authorization?
3. Why should ordinary users not have unnecessary administrator privileges?
4. What is the difference between Linux permissions and Windows ACLs?
5. What security risks can result from overly permissive file access?

## Related Notes

- [[Windows Users and Groups]]
- [[Windows Permissions]]
- [[Linux Users and Groups]]
- [[Linux Permissions]]
- [[Access Control]]
- [[Privilege Management]]
- [[Operating System Security]]
- [[System Hardening]]

---