> A shell is a program that provides an interface between the user and the operating system.

## 1. What is a Shell?

A shell allows users to communicate with an operating system by entering commands or interacting through a graphical interface.

It interprets user requests and invokes the appropriate operating-system services or applications.

**Examples:**

- Windows PowerShell
- Windows Command Prompt (CMD)
- Bash
- Zsh

## 2. Functions of a Shell

A shell performs several functions:

- Accepts user commands.
- Interprets commands.
- Starts programs.
- Supports scripting and automation.
- Provides access to system utilities.
- Displays command output.

## 3. Types of Shells

### 3.1 Command-Line Shell (CLI)

A command-line shell allows users to interact with the OS through text commands.

**Examples:**

- PowerShell
- CMD
- Bash
- Zsh

### 3.2 Graphical Shell

A graphical shell provides a visual interface using windows, icons, menus, and other graphical elements.

**Example:** Windows Explorer shell.

## 4. Popular Command-Line Shells

|Shell|Operating System|Description|
|---|---|---|
|PowerShell|Windows, Linux, macOS|Object-oriented command shell and scripting language|
|CMD|Windows|Traditional Windows command interpreter|
|Bash|Linux, Unix-like systems|Popular Unix shell|
|Zsh|Linux, macOS|Extensible Unix shell|

## 5. Shell vs Kernel

The shell and kernel have different responsibilities.

|Shell|Kernel|
|---|---|
|Provides a user interface|Manages core system resources|
|Accepts and interprets commands|Handles privileged operations|
|Runs in user space in typical systems|Runs in kernel space|
|Example: PowerShell|Example: Linux kernel|

## 6. How Does a Shell Work?

Example: You enter the command:

```
Get-Process
```

The process is broadly:

1. The shell receives the command.
2. It interprets the command.
3. The relevant command or program executes.
4. The operating system provides the required services.
5. The shell displays the result.

## 7. Shell and Cybersecurity

Shells are important cybersecurity tools.

Security professionals use shells for:

- System administration.
- Security auditing.
- Log analysis.
- Process investigation.
- Network troubleshooting.
- Automation.
- Digital forensics.

**Important:** A compromised shell can provide an attacker with a way to execute commands under the privileges of the compromised account.

## 8. Practical Lab — Windows PowerShell

Open PowerShell and execute these commands:

**Display current location:**

```
Get-Location
```

**Display current username:**

```
whoami
```

**List files and directories:**

```
Get-ChildItem
```

**Display running processes:**

```
Get-Process
```

**Display available commands:**

```
Get-Command
```

## 9. My Understanding

Answer in your own words:

1. What is a shell?
2. Why do we need a shell?
3. What is the difference between PowerShell and CMD?
4. How is a shell different from a kernel?
5. Why are shells useful in cybersecurity?

## 10. Knowledge Check

1. Which shell is commonly used in Windows administration?
2. What is Bash?
3. Which command displays the current directory in PowerShell?
4. Is the kernel the same as the shell?
5. Name two cybersecurity activities that use shells.

## Related Notes

- [[02 - Operating Systems]]
- [[Introduction to Operating Systems]]
- [[Kernel]]
- [[System Calls]]
- [[Windows OS]]
- [[Linux OS]]
- [[Windows PowerShell]]
- [[Linux Commands]]
- [[Operating System Security]]

---

**Category:** Operating System Fundamentals

**Status:** Learning