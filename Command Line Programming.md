> Understand how to interact with operating systems through command-line interfaces, automate tasks, execute programs, and build command-line tools.

## 1. Introduction

Command Line Programming involves interacting with a computer through text-based commands rather than relying entirely on a graphical user interface.

A Command-Line Interface (CLI) allows users to:

- Execute programs.
    
- Manage files and directories.
    
- Configure system settings.
    
- Automate repetitive tasks.
    
- Run scripts.
    
- Troubleshoot problems.
    
- Interact with development tools.
    

Command-line skills are particularly important in system administration, software development, and cybersecurity.

## 2. What Is a Command-Line Interface?

A Command-Line Interface is a text-based environment where users enter commands and receive output.

Examples:

- Windows Command Prompt (CMD).
    
- Windows PowerShell.
    
- Linux Terminal.
    
- macOS Terminal.
    

Basic interaction:

```
User enters command
        |
        v
Command-line interpreter
        |
        v
Operating system or program
        |
        v
Output displayed
```

## 3. CLI vs GUI

|CLI|GUI|
|---|---|
|Uses text commands|Uses graphical elements|
|Can automate repetitive tasks easily|Often requires manual interaction|
|Requires command knowledge|Generally easier for beginners|
|Useful for scripting|Useful for visual interaction|
|Often consumes fewer resources|May require more graphical resources|

Both interfaces are useful. The best choice depends on the task.

## 4. Shell and Terminal

These terms are related but different.

### Terminal

A terminal is an interface used to interact with a command-line environment.

### Shell

A shell is a program that interprets commands and executes them or invokes other programs.

Examples of shells:

|Shell|Platform|
|---|---|
|Command Prompt|Windows|
|PowerShell|Windows|
|Bash|Linux and other systems|
|Zsh|Linux and macOS|
|Fish|Linux and other systems|

A terminal application can run different shells.

## 5. Basic Command-Line Operations

### 5.1 Display Current Directory

Windows CMD:

```
cd
```

PowerShell:

```
Get-Location
```

Linux:

```
pwd
```

### 5.2 List Files and Directories

Windows CMD:

```
dir
```

PowerShell:

```
Get-ChildItem
```

Linux:

```
ls
```

### 5.3 Change Directory

Windows CMD and PowerShell:

```
cd Documents
```

Linux:

```
cd Documents
```

Move to the parent directory:

```
cd ..
```

Move to the home directory in Linux:

```
cd ~
```

### 5.4 Create a Directory

Windows CMD:

```
mkdir projects
```

PowerShell:

```
New-Item -ItemType Directory -Name projects
```

Linux:

```
mkdir projects
```

### 5.5 Create a File

Windows CMD:

```
type nul > notes.txt
```

PowerShell:

```
New-Item notes.txt -ItemType File
```

Linux:

```
touch notes.txt
```

### 5.6 Remove a File

Windows CMD:

```
del notes.txt
```

PowerShell:

```
Remove-Item notes.txt
```

Linux:

```
rm notes.txt
```

**Warning:** Removal commands can permanently delete files. Check the target path before executing them.

## 6. Command-Line Arguments

Command-line arguments allow users to provide information to a program when starting it.

Example:

```
python greet.py Mohit
```

The program receives `Mohit` as an argument.

Python example:

```
import sys

name = sys.argv[1]

print("Hello", name)
```

Save this as `greet.py`.

Run:

```
python greet.py Mohit
```

Output:

```
Hello Mohit
```

This basic example assumes an argument is supplied. A production script should validate its arguments before accessing them.

## 7. Command-Line Input and Output in Python

Python provides `input()` to receive input from the user.

Example:

```
name = input("Enter your name: ")

print("Welcome", name)
```

Output can be displayed using `print()`.

```
print("ROOTLOG CLI Lab")
```

These functions allow interactive command-line programs to communicate with users.

## 8. Building a Simple CLI Program

A command-line program can provide a menu of operations.

Example:

```
while True:

    print("\nROOTLOG CLI TOOL")
    print("1. Show message")
    print("2. Show current status")
    print("3. Exit")

    choice = input("Choose an option: ")

    if choice == "1":
        print("Welcome to ROOTLOG")

    elif choice == "2":
        print("System status: Running")

    elif choice == "3":
        print("Exiting...")
        break

    else:
        print("Invalid option")
```

This program repeatedly displays a menu until the user selects Exit.

## 9. Command-Line Argument Parsing

For more advanced Python CLI applications, use the `argparse` module.

It supports:

- Named arguments.
    
- Optional arguments.
    
- Help messages.
    
- Input validation.
    
- Default values.
    

Example:

```
import argparse

parser = argparse.ArgumentParser(
    description="ROOTLOG command-line tool"
)

parser.add_argument(
    "--name",
    required=True,
    help="Enter your name"
)

args = parser.parse_args()

print("Hello", args.name)
```

Run:

```
python app.py --name Mohit
```

Display help:

```
python app.py --help
```

## 10. Environment Variables

Environment variables store configuration values that programs can read at runtime.

Examples include:

- Application environment.
    
- Executable search paths.
    
- Configuration locations.
    
- API credentials.
    

Python example:

```
import os

username = os.getenv("USERNAME")

print(username)
```

To set an environment variable temporarily in Windows CMD:

```
set LAB_MODE=testing
```

In PowerShell:

```
$env:LAB_MODE = "testing"
```

In Linux Bash:

```
export LAB_MODE=testing
```

These examples set variables for the current command-line session or its child processes.

Do not place real passwords or API keys directly in scripts or commit them to Git.

## 11. Input and Output Redirection

Command-line environments support redirecting program input and output.

### Output Redirection

Windows CMD and Linux shells:

```
python app.py > output.txt
```

Writes standard output to a file, replacing its existing contents.

### Append Output

```
python app.py >> output.txt
```

Appends standard output to the file.

### Error Redirection

```
python app.py 2> errors.txt
```

Redirects standard error to a file.

### Input Redirection

```
python app.py < input.txt
```

Redirects a file to standard input.

The exact syntax and behavior can vary between shells.

## 12. Pipes

A pipe passes the output of one command to another command as input.

Example in Linux:

```
ls -l | grep ".txt"
```

This lists files and filters the output for lines containing `.txt`.

Windows CMD:

```
dir | findstr ".txt"
```

PowerShell:

```
Get-ChildItem | Where-Object Name -Like "*.txt"
```

Pipes are useful for combining smaller operations into larger workflows.

## 13. Exit Codes

A program returns an exit code when it finishes.

Conventionally:

- `0` means success.
    
- A non-zero value indicates an error or another outcome.
    

Windows CMD:

```
echo %ERRORLEVEL%
```

PowerShell:

```
$LASTEXITCODE
```

Linux Bash:

```
echo $?
```

Python example:

```
import sys

sys.exit(0)
```

Exit codes allow scripts to determine whether another command succeeded.

## 14. Process Execution from Python

Python can execute external programs using the `subprocess` module.

Example:

```
import subprocess

result = subprocess.run(
    ["python", "--version"],
    capture_output=True,
    text=True,
    check=True
)

print(result.stdout)
```

This executes the Python version command and captures its output.

### Security Considerations

- Prefer argument lists over constructing shell command strings.
    
- Avoid `shell=True` with untrusted input.
    
- Validate any user-controlled arguments.
    
- Use appropriate timeouts.
    
- Check return codes.
    
- Avoid running programs with unnecessary privileges.
    

Unsafe command construction can introduce command injection vulnerabilities.

## 15. Command-Line Programming in Cybersecurity

Command-line programming is widely used in cybersecurity.

### 15.1 Security Automation

Automate repetitive security tasks using Python and shell scripts.

### 15.2 Log Analysis

Search and filter log files to identify suspicious events.

### 15.3 Network Diagnostics

Execute network utilities and process their output.

### 15.4 Digital Forensics

Use command-line tools to inspect files, calculate hashes, and collect evidence.

### 15.5 System Administration

Manage accounts, processes, services, and system configurations.

### 15.6 Security Tool Development

Build custom command-line utilities for authorized security testing.

## 16. CLI Security Risks

Command-line programs can introduce security vulnerabilities.

### 16.1 Command Injection

Command injection occurs when untrusted input is interpreted as part of an operating-system command.

Example of unsafe Python:

```
import os

user_input = input("Enter a command: ")

os.system(user_input)
```

This gives user input direct influence over a shell command.

**Prevention:**

- Avoid executing arbitrary user-supplied commands.
    
- Use safe APIs instead of shell commands where possible.
    
- Use `subprocess.run()` with argument lists.
    
- Validate inputs.
    
- Apply least privilege.
    

### 16.2 Path Traversal

Untrusted file paths may allow access outside an intended directory.

Validate and restrict file paths before opening files.

### 16.3 Excessive Privileges

Running a script as administrator or root unnecessarily increases the impact of a vulnerability.

### 16.4 Sensitive Information Exposure

Command arguments and terminal output may expose passwords, tokens, or other confidential information.

Avoid passing secrets through command-line arguments when safer alternatives are available.

## 17. Practical Lab

**Objective:** Build and operate a basic command-line application using Python.

Create a file named:

```
cli_lab.py
```

### Lab A — Display System Information

```
import platform

print("System:", platform.system())
print("Release:", platform.release())
print("Machine:", platform.machine())
```

### Lab B — Create a CLI Menu

```
while True:

    print("\nROOTLOG SYSTEM TOOL")
    print("1. Display message")
    print("2. Display system information")
    print("3. Exit")

    choice = input("Select: ")

    if choice == "1":
        print("Learning Command Line Programming")

    elif choice == "2":
        import platform

        print("System:", platform.system())
        print("Release:", platform.release())

    elif choice == "3":
        print("Exiting...")
        break

    else:
        print("Invalid selection")
```

### Lab C — Use Command-Line Arguments

Create `argument_lab.py`:

```
import argparse

parser = argparse.ArgumentParser()

parser.add_argument(
    "--username",
    required=True
)

args = parser.parse_args()

print("Username:", args.username)
```

Run:

```
python argument_lab.py --username student
```

### Lab D — Save Output to a File

Run the following from your terminal:

```
python cli_lab.py > output.txt
```

Inspect the generated file.

### Lab E — Check an Exit Code

Create `exit_lab.py`:

```
import sys

print("Program completed")

sys.exit(0)
```

Run:

```
python exit_lab.py
```

Then check the exit code using the command appropriate for your shell.

## 18. Key Takeaways

- CLI allows users to interact with systems through text commands.
    
- A terminal provides access to a shell.
    
- Shells interpret commands and execute programs.
    
- Command-line arguments provide runtime input.
    
- Python supports CLI development through `argparse`.
    
- Environment variables provide runtime configuration.
    
- Pipes and redirection connect command-line operations.
    
- Exit codes communicate program outcomes.
    
- Python's `subprocess` module executes external programs.
    
- Command injection and path traversal are important CLI security risks.
    

## 19. Related Topics

- [[Introduction to Python]]
    
- [[Python Functions]]
    
- [[Python Modules]]
    
- [[Python File Handling]]
    
- [[Python Exception Handling]]
    
- [[Operating Systems]]
    
- [[Linux Commands]]
    
- [[Windows CMD Labs]]
    
- [[Automation and Scripting]]
    
- [[Secure Coding]]
    
- [[Input Validation]]
    
- [[Git and Version Control]]