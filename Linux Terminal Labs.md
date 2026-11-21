> A collection of practical exercises for learning Linux administration, terminal commands, networking, and cybersecurity fundamentals.

## 1. Lab Environment

**Requirements:**

- Kali Linux or another Debian-based Linux distribution.
- Terminal access.
- A standard user account.
- sudo access for selected exercises.

Open the terminal and check your identity:

```
whoami
```

Check your Linux distribution:

```
cat /etc/os-release
```

## 2. Lab 01 — Basic Terminal Navigation

### Objective

Understand how to navigate the Linux filesystem.

### Commands

```
pwd
```

Displays the current directory.

```
ls
```

Lists files and directories.

```
ls -la
```

Displays detailed information, including hidden files.

```
cd Desktop
```

Enters the Desktop directory, if it exists.

```
cd ..
```

Moves one directory level up.

```
mkdir Linux_Lab
```

Creates a directory.

```
cd Linux_Lab
```

Enters the new directory.

### Tasks

1. Display your current directory.
2. List its contents.
3. Create `Linux_Lab`.
4. Enter the directory.
5. Verify your location.

## 3. Lab 02 — File Management

### Objective

Create, read, copy, move, and delete files.

### Commands

```
touch notes.txt
```

Creates an empty file.

```
echo "Learning Linux" > notes.txt
```

Writes text into the file.

```
cat notes.txt
```

Displays file contents.

```
echo "Practicing terminal commands" >> notes.txt
```

Appends text.

```
cp notes.txt backup.txt
```

Copies the file.

```
mv backup.txt old-notes.txt
```

Renames the copy.

```
rm old-notes.txt
```

Deletes the copy.

### Tasks

1. Create a text file.
    
2. Write two lines.
    
3. Display its contents.
    
4. Copy and rename the file.
    
5. Delete only the copy.
    

## 4. Lab 03 — System Information

### Objective

Collect information about the Linux system.

### Commands

```
hostname
```

Displays the computer name.

```
uname -a
```

Displays kernel and system information.

```
cat /etc/os-release
```

Displays distribution information.

```
lscpu
```

Displays CPU information.

```
free -h
```

Displays memory usage.

```
df -h
```

Displays filesystem disk usage.

```
uptime
```

Displays system uptime and load averages.

### Tasks

Record:

- Hostname.
    
- Linux distribution.
    
- Kernel version.
    
- CPU architecture.
    
- Total memory.
    
- Available disk space.
    

## 5. Lab 04 — User and Group Management

### Objective

Understand Linux users and groups.

### Commands

```
whoami
```

Displays the current username.

```
id
```

Displays UID, GID, and group memberships.

```
getent passwd
```

Displays account entries from the configured user database.

```
getent group
```

Displays group entries.

```
groups
```

Displays your group memberships.

```
getent passwd root
```

Displays the root account entry.

### Tasks

1. Identify your current user.
    
2. Record your UID and GID.
    
3. Identify your groups.
    
4. Inspect the root account entry.
    

## 6. Lab 05 — File Permissions

### Objective

Understand Linux file permissions.

### Commands

```
ls -l
```

Displays file permissions.

```
stat notes.txt
```

Displays detailed file information.

```
umask
```

Displays the current file creation permission mask.

```
namei -l /etc/passwd
```

Displays permissions along a directory path.

### Understanding Permissions

Example:

```
-rwxr-xr--
```

|Category|Permissions|
|---|---|
|Owner|Read, write, execute|
|Group|Read, execute|
|Others|Read only|

### Tasks

1. Create a test file.
    
2. Inspect its permissions.
    
3. Identify its owner and group.
    
4. Explain the meaning of `r`, `w`, and `x`.
    

Do not change permissions on system files.

## 7. Lab 06 — Process Management

### Objective

Inspect running processes.

### Commands

```
ps
```

Displays processes associated with the current terminal.

```
ps aux
```

Displays detailed information about running processes.

```
top
```

Displays live process and resource information.

```
pgrep bash
```

Searches for processes matching `bash`.

```
pstree
```

Displays processes in a tree structure, if installed.

```
free -h
```

Displays memory usage.

### Tasks

1. Display running processes.
    
2. Identify three process names.
    
3. Record their PIDs.
    
4. Identify a process using significant CPU or memory resources.
    

## 8. Lab 07 — Service Management

### Objective

Inspect Linux system services.

### Commands

```
systemctl --type=service
```

Lists service units.

```
systemctl --type=service --state=running
```

Lists running services.

```
systemctl status ssh
```

Displays SSH service status, if available.

```
systemctl list-unit-files --type=service
```

Lists installed service unit files and their enablement states.

### Tasks

1. List running services.
    
2. Inspect the SSH service.
    
3. Record its current state.
    
4. Research the purpose of one running service.
    

Do not stop or disable services during this exercise.

## 9. Lab 08 — Network Inspection

### Objective

Inspect Linux network configuration.

### Commands

```
ip addr
```

Displays network interfaces and IP addresses.

```
ip route
```

Displays routing information.

```
ip link
```

Displays network interfaces.

```
ping -c 4 127.0.0.1
```

Tests loopback connectivity.

```
ss -tuln
```

Displays listening TCP and UDP sockets.

```
ss -tulpen
```

Displays additional process and socket information; some details may require sudo.

```
getent hosts google.com
```

Looks up a hostname using configured name-service sources.

### Tasks

1. Identify your IPv4 address.
    
2. Identify your default gateway.
    
3. Inspect network interfaces.
    
4. Identify listening ports.
    
5. Test loopback connectivity.
    

## 10. Lab 09 — Package Management

### Objective

Understand package management in Debian-based Linux distributions.

### Commands

```
apt list --installed
```

Lists installed packages.

```
apt search nmap
```

Searches for packages matching Nmap.

```
apt policy nmap
```

Displays package version information and repository details.

```
sudo apt update
```

Refreshes package information.

```
apt list --upgradable
```

Lists packages with available upgrades.

### Tasks

1. Search for Nmap.
    
2. Inspect its package information.
    
3. Identify the installed version, if installed.
    
4. Check whether updates are available.
    

Do not install or remove packages during this inspection lab.

## 11. Lab 10 — Log Inspection

### Objective

Understand Linux system logs.

### Commands

```
journalctl -n 50
```

Displays the latest 50 journal entries.

```
journalctl -b
```

Displays logs from the current boot.

```
journalctl -p warning
```

Displays warning-level and more severe messages.

```
last
```

Displays recorded login sessions.

```
sudo journalctl | grep -iE 'authentication|sudo|failed'
```

Searches journal entries for selected authentication-related terms.

### Tasks

1. Display recent system logs.
    
2. Inspect current boot logs.
    
3. Review login history.
    
4. Identify one warning or authentication-related event.
    

## 12. Lab 11 — Basic Security Inspection

### Objective

Inspect basic Linux security settings.

### Commands

```
whoami
```

Displays the current user.

```
id
```

Displays identity and group information.

```
sudo -l
```

Displays sudo permissions available to your account.

```
sudo ss -tulpen
```

Inspects listening network sockets.

```
sudo ufw status
```

Displays UFW firewall status, if UFW is installed.

```
systemctl --type=service --state=running
```

Lists running services.

### Tasks

1. Identify your current user.
    
2. Review sudo permissions.
    
3. Inspect listening ports.
    
4. Check firewall status.
    
5. Identify running services.
    

## 13. Lab 12 — Basic Bash Scripting

### Objective

Create and execute a simple Bash script.

Create a file:

```
nano system-info.sh
```

Add:

```
#!/bin/bash

echo "SYSTEM INFORMATION"

echo "Hostname:"
hostname

echo "Current User:"
whoami

echo "Operating System:"
cat /etc/os-release

echo "Current Date:"
date
```

Save the file.

Make it executable:

```
chmod +x system-info.sh
```

Execute it:

```
./system-info.sh
```

### Tasks

1. Create the script.
    
2. Execute it.
    
3. Understand every command.
    
4. Add a command that displays your IP addresses.
    

## 14. Lab Documentation Template

### Lab Name

**Objective:**

What am I trying to learn?

**Commands Used:**

List the commands executed.

**Observations:**

What output did I receive?

**Analysis:**

What does the output mean?

**Result:**

What did I successfully verify?

**Questions:**

What do I still need to understand?

## 15. Learning Principles

- Understand commands before executing them.
    
- Use test files for file-management exercises.
    
- Avoid unnecessary root privileges.
    
- Do not execute unknown scripts.
    
- Record important observations.
    
- Compare Linux commands with Windows CMD and PowerShell.
    
- Practice in an authorized lab environment.
    

## Related Notes

- [[02 - Operating Systems]]
    
- [[Introduction to Linux]]
    
- [[Linux Commands]]
    
- [[Linux Users and Groups]]
    
- [[Linux Permissions]]
    
- [[Linux Processes]]
    
- [[Linux Services]]
    
- [[Linux Package Management]]
    
- [[Operating System Security]]
    
- [[Windows PowerShell Labs]]
    
- [[Windows CMD Labs]]
    
- [[07 - Practical Labs]]