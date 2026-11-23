> **Overview:** Windows Command Prompt (CMD) is a command-line interpreter that allows users to interact with the Windows operating system using text-based commands. It is used for file management, system administration, networking, troubleshooting, and automation.

## 1. Introduction to Windows CMD

### What is CMD?

CMD stands for Command Prompt. It is a command-line interface (CLI) provided by Microsoft Windows.

It allows users to execute commands instead of performing operations through graphical interfaces.

The executable responsible for CMD is:

`cmd.exe`

### Why is CMD important?

- Manage files and directories.
- View system information.
- Troubleshoot network problems.
- Manage running processes.
- Automate repetitive tasks.
- Inspect user accounts and permissions.
- Perform basic cybersecurity investigations.

### CMD vs GUI

|CMD|GUI|
|---|---|
|Text-based interface|Graphical interface|
|Uses commands|Uses icons and menus|
|Supports scripting|Usually requires GUI automation for repetition|
|Lightweight|Uses graphical resources|
|Useful for administration|Useful for general interaction|

### CMD vs PowerShell

|CMD|PowerShell|
|---|---|
|Traditional Windows shell|Modern automation shell|
|Uses batch scripts|Uses PowerShell scripts|
|Primarily text-based output|Supports structured objects|
|Uses `.bat` and `.cmd`|Uses `.ps1`|

## 2. Opening Command Prompt

Three common methods:

**Method 1: Run Dialog**

1. Press `Win + R`.
2. Type `cmd`.
3. Press Enter.

**Method 2: Start Menu**

1. Open Start.
2. Search for Command Prompt.
3. Click the application.

**Method 3: Administrator CMD**

1. Search for Command Prompt.
2. Right-click it.
3. Select Run as administrator.

Administrator mode provides elevated permissions. Use it only when necessary.

## 3. Understanding the CMD Interface

Example:

```
C:\Users\Student>
```

Explanation:

- `C:` – Current drive.
- `Users` – Parent directory.
- `Student` – Current user directory.
- `>` – Command input separator.

General command structure:

```
command [options] [arguments]
```

Example:

```
dir /a
```

Here:

- `dir` is the command.
- `/a` is an option.

### Getting Help

```
help
help dir
dir /?
ipconfig /?
```

The `/?` option displays command-specific help for many CMD commands.

## 4. Basic CMD Commands

|Command|Description|
|---|---|
|`cls`|Clears the screen|
|`echo`|Displays text|
|`ver`|Displays Windows version|
|`date`|Displays or changes date|
|`time`|Displays or changes time|
|`hostname`|Displays computer name|
|`whoami`|Displays current user|
|`exit`|Closes CMD|
|`help`|Displays available commands|

Examples:

```
echo Hello World
hostname
whoami
ver
```

## 5. Directory Navigation

Directories are folders used to organize files.

|Command|Description|
|---|---|
|`cd`|Displays or changes directory|
|`cd ..`|Moves one directory backward|
|`cd \`|Moves to root directory|
|`dir`|Lists files and folders|
|`tree`|Displays directory structure|
|`D:`|Switches to drive D|
|`cd /d D:\Labs`|Changes drive and directory|

Example:

```
cd Desktop
mkdir CMD-Lab
cd CMD-Lab
dir
```

### Creating Multiple Directories

```
mkdir Notes Scripts Reports Evidence
```

This creates four directories.

## 6. File Management Commands

### Creating Files

```
echo Hello > file.txt
type nul > empty.txt
```

### Reading Files

```
type file.txt
more file.txt
```

### Copying Files

```
copy file.txt backup.txt
```

### Moving Files

```
move file.txt Reports\
```

### Renaming Files

```
ren old.txt new.txt
```

### Deleting Files

```
del file.txt
```

### Deleting Directories

```
rmdir EmptyFolder
rmdir /s FolderName
```

> **Warning:** Deletion commands can permanently remove files. Always verify the target path before executing them.

## 7. Advanced File Management

### Display Hidden Files

```
dir /a
```

### Display File Attributes

```
attrib
```

### Hide a File

```
attrib +h secret.txt
```

### Unhide a File

```
attrib -h secret.txt
```

**Important:** Hiding a file does not encrypt it or protect it from unauthorized access.

### Search for Files

```
dir /s filename.txt
```

### Search Within Files

```
find "ERROR" log.txt
findstr /i "failed" log.txt
```

## 8. System Information Commands

These commands help inspect the Windows environment.

|Command|Description|
|---|---|
|`systeminfo`|Detailed system information|
|`hostname`|Computer name|
|`whoami`|Current username|
|`whoami /all`|User security information|
|`ver`|Windows version|
|`set`|Environment variables|
|`tasklist`|Running processes|
|`driverquery`|Installed driver information|

Examples:

```
systeminfo
hostname
whoami /all
driverquery
```

## 9. Process Management

A process is a running instance of a program.

### View Running Processes

```
tasklist
```

### Find a Specific Process

```
tasklist | findstr /i chrome
```

### Terminate a Process by Name

```
taskkill /im notepad.exe
```

### Terminate a Process by PID

```
taskkill /pid 1234
```

### Force Termination

```
taskkill /f /im notepad.exe
```

A PID (Process ID) uniquely identifies a running process during its lifetime.

Avoid terminating unfamiliar system processes.

## 10. Networking Commands

CMD provides several commands for basic network troubleshooting and investigation.

### 10.1 IP Configuration

```
ipconfig
ipconfig /all
```

Displays:

- IPv4 address.
- IPv6 address.
- Subnet mask.
- Default gateway.
- DNS servers.
- Network adapter information.

### 10.2 Ping

```
ping 127.0.0.1
ping 8.8.8.8
ping google.com
```

Used to test network connectivity.

### 10.3 Traceroute

```
tracert google.com
```

Displays the network route taken by packets toward a destination.

### 10.4 DNS Lookup

```
nslookup google.com
```

Used to query DNS information.

### 10.5 DNS Cache

```
ipconfig /displaydns
ipconfig /flushdns
```

- `/displaydns` displays cached DNS records.
- `/flushdns` clears the DNS resolver cache.

### 10.6 Network Connections

```
netstat -ano
```

Displays network connections and listening ports.

|Option|Meaning|
|---|---|
|`-a`|Displays all connections and listening ports|
|`-n`|Displays numerical addresses|
|`-o`|Displays process IDs|

Find connections using port 443:

```
netstat -ano | findstr :443
```

Identify the associated process:

```
tasklist /fi "pid eq 1234"
```

### 10.7 ARP Table

```
arp -a
```

Displays the local ARP cache, mapping known IPv4 addresses to MAC addresses.

### 10.8 Routing Table

```
route print
```

Displays the Windows routing table.

## 11. Disk Management Commands

|Command|Description|
|---|---|
|`vol`|Displays volume information|
|`label`|Displays or changes volume label|
|`chkdsk`|Checks a disk|
|`fsutil volume diskfree C:`|Displays available disk space|

Example:

```
vol C:
chkdsk C:
```

Be careful with disk repair operations. Understand their effects and back up important data before using repair options.

## 12. User and Group Management

### Display Current User

```
whoami
```

### List Local Users

```
net user
```

### Display User Information

```
net user username
```

### List Local Groups

```
net localgroup
```

### Display Group Members

```
net localgroup Administrators
```

Some operations require administrator privileges.

## 13. File Permissions

Windows uses Access Control Lists (ACLs) to control access to files and directories.

The `icacls` command is used to inspect and modify permissions.

### Display Permissions

```
icacls file.txt
```

### Display Directory Permissions

```
icacls C:\CMD-Lab
```

Permissions determine whether users can read, write, execute, or modify resources.

Avoid changing permissions on system directories without understanding the consequences.

## 14. Environment Variables

Environment variables store information that programs and scripts can access.

Common variables:

|Variable|Description|
|---|---|
|`%USERNAME%`|Current username|
|`%USERPROFILE%`|User profile directory|
|`%COMPUTERNAME%`|Computer name|
|`%TEMP%`|Temporary directory|
|`%WINDIR%`|Windows directory|
|`%PATH%`|Executable search paths|

Examples:

```
echo %USERNAME%
echo %COMPUTERNAME%
echo %USERPROFILE%
echo %TEMP%
```

### Create a Temporary Variable

```
set LAB=Cybersecurity
echo %LAB%
```

The variable normally exists only in the current CMD session.

## 15. Command Redirection and Pipes

### Output Redirection

```
ipconfig > network.txt
```

Saves output to a file, replacing existing contents.

### Append Output

```
ipconfig >> network.txt
```

Adds output to the end of a file.

### Error Redirection

```
dir MissingFolder 2> errors.txt
```

Saves error output to a file.

### Pipes

A pipe sends the output of one command into another command.

```
tasklist | findstr chrome
ipconfig | more
```

### Command Operators

|Operator|Purpose|
|---|---|
|`&`|Executes commands sequentially|
|`&&`|Executes the next command if the previous succeeds|
|`||`|Executes the next command if the previous fails|
|`|`|Sends output to another command|

Example:

```
mkdir Test && echo Folder created
```

## 16. Batch Scripting

Batch scripting is the process of writing multiple CMD commands into a script file.

Batch files commonly use:

- `.bat`
- `.cmd`

They help automate repetitive Windows tasks.

### First Batch Script

Create `hello.bat`:

```
@echo off
echo Hello World
echo Welcome to Windows Batch Scripting
pause
```

### Important Batch Commands

|Command|Purpose|
|---|---|
|`@echo off`|Hides executed commands|
|`echo`|Displays text|
|`pause`|Waits for user input|
|`set`|Creates variables|
|`set /p`|Accepts user input|
|`if`|Performs conditional operations|
|`for`|Repeats commands|
|`goto`|Jumps to a label|
|`call`|Calls another batch script or label|
|`exit /b`|Exits the current batch script|

### Variables

```
@echo off
set NAME=Student
echo Hello %NAME%
pause
```

### User Input

```
@echo off
set /p NAME=Enter your name:
echo Welcome %NAME%
pause
```

### IF Condition

```
@echo off
set /p ANSWER=Enter YES or NO:

if /i "%ANSWER%"=="YES" (
    echo You selected YES
) else (
    echo You selected NO
)

pause
```

### FOR Loop

```
@echo off

for %%N in (1 2 3 4 5) do (
    echo Number %%N
)

pause
```

### GOTO Statement

```
@echo off

:menu
echo 1. Show date
echo 2. Exit

set /p choice=Select:

if "%choice%"=="1" goto date
if "%choice%"=="2" goto end

echo Invalid option
goto menu

:date
date /t
goto menu

:end
echo Goodbye
```

## 17. Practical Project: Windows System Information Collector

Create a file named:

`system_report.bat`

Code:

```
@echo off

set "REPORT_DIR=%USERPROFILE%\Desktop\CMD-Reports"

if not exist "%REPORT_DIR%" mkdir "%REPORT_DIR%"

set "REPORT=%REPORT_DIR%\system-report.txt"

echo WINDOWS SYSTEM REPORT > "%REPORT%"
echo ======================== >> "%REPORT%"

echo Date: %DATE% >> "%REPORT%"
echo Time: %TIME% >> "%REPORT%"
echo Computer: %COMPUTERNAME% >> "%REPORT%"
echo User: %USERNAME% >> "%REPORT%"

echo. >> "%REPORT%"

echo SYSTEM INFORMATION >> "%REPORT%"
systeminfo >> "%REPORT%"

echo. >> "%REPORT%"

echo NETWORK INFORMATION >> "%REPORT%"
ipconfig /all >> "%REPORT%"

echo Report generated successfully.
pause
```

### Project Explanation

This script:

1. Creates a report directory on the desktop.
2. Creates a text report.
3. Collects date and time.
4. Collects computer and username information.
5. Collects Windows system information.
6. Collects network configuration.
7. Saves everything in a single report.

**Cybersecurity application:** Basic system inventory and information collection during authorized security assessments.

Review the report before sharing it because it may contain sensitive system and network details.

## 18. CMD in Cybersecurity

CMD is useful for Windows reconnaissance, administration, troubleshooting, and basic forensic investigation.

|Security Task|Command|
|---|---|
|Identify current user|`whoami /all`|
|Inspect local users|`net user`|
|Inspect groups|`net localgroup`|
|View network configuration|`ipconfig /all`|
|Inspect network connections|`netstat -ano`|
|Identify running processes|`tasklist`|
|Inspect DNS cache|`ipconfig /displaydns`|
|Inspect file permissions|`icacls`|
|View routing table|`route print`|
|View ARP cache|`arp -a`|

### Basic Investigation Workflow

Run these commands on your own Windows lab system:

```
hostname
whoami /all
ipconfig /all
netstat -ano
tasklist
arp -a
route print
```

Record:

- Computer name.
- Current user.
- Network configuration.
- Active connections.
- Listening ports.
- Process IDs.
- Network routes.

Remember that a process or connection should not be classified as malicious based on one command alone.

## 19. Common CMD Errors

|Error|Possible Reason|Solution|
|---|---|---|
|Command not recognized|Incorrect command or PATH issue|Verify spelling and command availability|
|Access denied|Insufficient permissions|Check permissions|
|Path not found|Incorrect directory|Verify using `dir`|
|Syntax incorrect|Incorrect command arguments|Use `command /?`|
|File not found|Incorrect filename or location|Check current directory|
|Ping fails|Network issue or ICMP filtering|Test using other methods|

## 20. CMD Keyboard Shortcuts

|Shortcut|Function|
|---|---|
|Up Arrow|Previous command|
|Down Arrow|Next command in history|
|Tab|Auto-complete file and folder names|
|Ctrl + C|Interrupt current command|
|F7|Display command history in supported CMD versions|
|Esc|Clear current input line|
|Ctrl + L|Clear visible console in supported console hosts|

The `cls` command is the reliable method to clear the CMD screen.

## 21. Practical Exercises

### Beginner Level

- Open Command Prompt.
- Display your Windows version.
- Find your computer name.
- Find your current username.
- Create a folder called `CMD-Practice`.
- Create three subdirectories.
- Create a text file.
- Copy and rename the file.
- Display the contents of the file.

### Intermediate Level

- Display complete system information.
- Display IP configuration.
- Test connectivity using ping.
- Perform DNS lookup.
- Trace a network route.
- Display active network connections.
- Find the PID of a running application.
- Identify the process associated with that PID.
- Display local users and groups.
- Inspect file permissions.

### Advanced Level

- Create a batch file that accepts user input.
- Write an IF condition.
- Create a FOR loop.
- Create a menu-driven batch script.
- Generate a system report automatically.
- Add error handling to your script.

## 22. Knowledge Check

1. What is CMD?
2. What is the purpose of `cmd.exe`?
3. What is the difference between CMD and PowerShell?
4. Which command displays the current directory?
5. Which command displays all files?
6. What is the purpose of `ipconfig /all`?
7. What is the difference between `>` and `>>`?
8. What does `netstat -ano` display?
9. What is a PID?
10. What is the purpose of `taskkill`?
11. What is DNS?
12. What is the purpose of `tracert`?
13. What is batch scripting?
14. What does `@echo off` do?
15. What is the difference between `.bat` and `.cmd`?
16. What is an environment variable?
17. What is the purpose of `icacls`?
18. Why is hiding a file not the same as securing it?

## 23. Quick Revision Sheet

|Command|Purpose|
|---|---|
|`cls`|Clear screen|
|`dir`|List files|
|`cd`|Change directory|
|`mkdir`|Create directory|
|`rmdir`|Remove directory|
|`copy`|Copy files|
|`move`|Move files|
|`del`|Delete files|
|`ren`|Rename files|
|`type`|Read text files|
|`hostname`|Computer name|
|`whoami`|Current user|
|`systeminfo`|System information|
|`tasklist`|Running processes|
|`taskkill`|Terminate process|
|`ipconfig`|IP configuration|
|`ping`|Test connectivity|
|`tracert`|Trace network route|
|`nslookup`|DNS lookup|
|`netstat`|Network connections|
|`arp -a`|ARP cache|
|`route print`|Routing table|
|`icacls`|File permissions|
|`attrib`|File attributes|
|`findstr`|Search text|
|`echo`|Display text|
|`set`|Environment variables|

## 24. Related Topics

- [[Operating Systems]]
- [[Introduction to Computer Networking]]
- [[Cybersecurity]]
- [[Linux Command Line]]
- [[Introduction to Python]]
- [[Programming Fundamentals]]
- [[Batch Scripting]]

> **Learning Recommendation:** Master basic navigation and file management first. Then practice networking and system inspection commands. Finally, learn batch scripting to automate your Windows administration tasks.