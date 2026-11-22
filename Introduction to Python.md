## 1. What Is Python?

Python is a high-level, general-purpose programming language known for its simple syntax and readability.

It was created by **Guido van Rossum** and first released in 1991.

Python is widely used in:

- Web development
    
- Automation and scripting
    
- Artificial intelligence
    
- Machine learning
    
- Data analysis
    
- Cybersecurity
    
- Digital forensics
    
- Software development
    

Python allows developers to write programs using relatively simple and readable instructions.

## 2. Why Is Python Popular?

Python is popular because:

1. **Easy to Read:** Its syntax is relatively close to everyday English.
    
2. **Beginner-Friendly:** It is suitable for learning programming fundamentals.
    
3. **Cross-Platform:** Python programs can run on Windows, Linux, and macOS.
    
4. **Large Standard Library:** It provides built-in modules for many common tasks.
    
5. **Large Ecosystem:** Thousands of third-party packages are available.
    
6. **Versatile:** It supports multiple programming paradigms.
    
7. **Community Support:** It has a large developer community.
    

## 3. Features of Python

|Feature|Explanation|
|---|---|
|High-Level|Hides many low-level hardware details|
|Interpreted|Commonly executed through an interpreter and runtime|
|Dynamically Typed|Variable types are determined at runtime|
|Object-Oriented|Supports classes, objects, inheritance, and polymorphism|
|Portable|Available on multiple operating systems|
|Open Source|Its implementation is freely available|
|Extensive Libraries|Provides modules for many programming tasks|
|Automatic Memory Management|Manages memory allocation and object cleanup|

**Important:** Python is often called an interpreted language, but its implementation involves compilation to bytecode in common implementations such as CPython. It is more accurate to understand Python as a language executed through an interpreter/runtime rather than assuming every line is directly interpreted from source code.

## 4. Applications of Python

### A. Web Development

Python can be used to develop web applications and backend services.

Popular frameworks:

- Django
    
- Flask
    
- FastAPI
    

### B. Automation

Python can automate repetitive tasks such as:

- Renaming files
    
- Organizing folders
    
- Processing documents
    
- Generating reports
    
- Monitoring system activity
    

### C. Artificial Intelligence and Machine Learning

Python provides libraries for machine learning and AI.

Examples:

- TensorFlow
    
- PyTorch
    
- scikit-learn
    

### D. Data Analysis

Python is used to process and analyze large datasets.

Popular libraries:

- NumPy
    
- Pandas
    
- Matplotlib
    

### E. Cybersecurity

Python is useful for developing security tools and automating security tasks.

Examples:

- Network scanning
    
- Log analysis
    
- File integrity monitoring
    
- Security report generation
    
- API interaction
    
- Digital forensic automation
    

### F. Digital Forensics

Python can help investigators:

- Calculate file hashes.
    
- Extract file metadata.
    
- Analyze logs.
    
- Process evidence files.
    
- Search for patterns in collected data.
    

## 5. Python Versions

Python has two historically important major versions:

|Version|Description|
|---|---|
|Python 2|Older version; officially discontinued|
|Python 3|Current major version family|

Python 2 reached end of life in January 2020.

For new projects and learning, use Python 3.

To check your installed Python version:

```
python --version
```

On some systems, use:

```
python3 --version
```

Example output:

```
Python 3.x.x
```

The exact version depends on your installation.

## 6. Installing Python

### Windows

1. Visit the official Python website.
    
2. Download the Python 3 installer.
    
3. Run the installer.
    
4. Select the option to add Python to PATH, if available.
    
5. Complete the installation.
    

Official website:

[https://www.python.org/](https://www.python.org/)

Verify installation in Windows CMD or PowerShell:

```
python --version
```

You can also check:

```
py --version
```

### Linux

On Debian-based distributions such as Kali Linux, check whether Python is already installed:

```
python3 --version
```

If it is missing, install it using the package manager:

```
sudo apt update
sudo apt install python3
```

Verify:

```
python3 --version
```

Avoid replacing the system-managed Python installation on Kali Linux. Some operating-system tools depend on it.

## 7. Writing Your First Python Program

Create a file named:

`hello.py`

Write the following code:

```
print("Hello, World!")
```

Run it from the terminal:

**Windows:**

```
python hello.py
```

**Linux:**

```
python3 hello.py
```

Output:

```
Hello, World!
```

The `print()` function displays information on the screen.

## 8. How Python Executes a Program

In a typical CPython implementation, execution involves several stages:

1. **Source Code:** The programmer writes Python instructions.
    
2. **Parsing and Compilation:** Python processes the source code and compiles it into bytecode.
    
3. **Bytecode Execution:** The Python Virtual Machine executes the bytecode.
    
4. **Output:** The program produces its result.
    

Simplified flow:

```
Python Source Code
        |
        v
   Python Parser
        |
        v
 Bytecode Compilation
        |
        v
Python Virtual Machine
        |
        v
      Output
```

The exact implementation details can differ between Python implementations.

## 9. Python Programming Modes

Python provides two common ways to execute code.

### A. Interactive Mode

Interactive mode allows you to execute Python instructions one at a time.

Open a terminal and run:

```
python
```

Or on Linux:

```
python3
```

You will see the Python prompt:

```
>>>
```

Enter:

```
>>> print("Hello")
```

Output:

```
Hello
```

Exit using:

```
exit()
```

**Use case:** Testing small expressions and experimenting with Python syntax.

### B. Script Mode

Script mode allows you to write multiple instructions in a `.py` file and execute them together.

Example: `calculator.py`

```
a = 10
b = 20

result = a + b

print("Result:", result)
```

Run:

```
python calculator.py
```

Output:

```
Result: 30
```

**Use case:** Building complete programs, automation scripts, and security tools.

## 10. Python Development Environments

A development environment provides tools for writing, running, and debugging programs.

Common options include:

|Tool|Description|
|---|---|
|IDLE|Basic Python development environment|
|VS Code|Code editor with Python extensions|
|PyCharm|Python-focused IDE|
|Jupyter Notebook|Interactive environment for code and data analysis|
|Terminal|Run Python directly from the command line|

For learning Python and developing cybersecurity scripts, VS Code and the terminal are useful choices.

## 11. Python Standard Library

The Python Standard Library is a collection of modules included with Python.

It provides functionality without requiring separate third-party installations.

Examples:

|Module|Purpose|
|---|---|
|`os`|Operating-system interactions|
|`sys`|Python runtime and interpreter information|
|`math`|Mathematical operations|
|`datetime`|Date and time operations|
|`json`|JSON data processing|
|`re`|Regular expressions|
|`hashlib`|Cryptographic hash functions|
|`subprocess`|Running external processes|
|`pathlib`|Working with filesystem paths|

Example using the `datetime` module:

```
import datetime

current_time = datetime.datetime.now()

print(current_time)
```

## 12. Python in Cybersecurity

Python is especially useful in cybersecurity because it supports automation, data processing, and interaction with operating-system and network interfaces.

### A. File Hashing

Calculate a SHA-256 hash of a file to help verify its integrity.

```
import hashlib

data = b"Cybersecurity Lab"

file_hash = hashlib.sha256(data).hexdigest()

print(file_hash)
```

### B. Log Analysis

Python can read log files and search for suspicious patterns.

Example:

```
with open("sample.log", "r") as file:
    for line in file:
        if "FAILED" in line:
            print(line.strip())
```

This example searches a sample log file for failed events.

### C. Network Programming

Python provides modules such as:

- `socket`
    
- `urllib`
    
- `http.client`
    

These can be used to build network applications and communicate with services.

### D. Automation

Python can automate repetitive tasks such as checking file hashes, organizing logs, and generating security reports.

**Important:** Automation does not replace understanding. Learn the underlying networking, operating-system, and security concepts before relying on scripts.

## 13. Advantages of Python

1. Simple and readable syntax.
    
2. Large ecosystem of libraries.
    
3. Cross-platform support.
    
4. Useful for rapid development.
    
5. Strong support for automation.
    
6. Suitable for cybersecurity and data analysis.
    
7. Supports procedural, object-oriented, and functional programming styles.
    

## 14. Limitations of Python

1. Often slower than compiled languages such as C and C++ for CPU-intensive workloads.
    
2. Can consume more memory for certain applications.
    
3. Dynamic typing can allow some errors to appear only at runtime.
    
4. Not usually the first choice for low-level operating-system development.
    
5. The Global Interpreter Lock in conventional CPython builds can limit parallel execution of Python bytecode using threads in CPU-bound workloads.
    

The appropriate language depends on the requirements of the project.

## 15. Practical Exercises

### Exercise 1: Hello World

Create a Python file that displays:

```
Welcome to ROOTLOG
Learning Python for Cybersecurity
```

### Exercise 2: Basic Information

Write a program that displays:

- Your learning platform
    
- Your programming language
    
- Your current learning topic
    

Use `print()` statements.

### Exercise 3: Python Environment

Run these commands and record their outputs:

```
python --version
```

```
python -c "print('Python is working')"
```

On Linux, use `python3` if necessary.

### Exercise 4: Cybersecurity Application

Write a small program that calculates the SHA-256 hash of the following text:

```
import hashlib

message = b"ROOTLOG"

result = hashlib.sha256(message).hexdigest()

print("SHA-256:", result)
```

Observe the output and understand what the `hashlib` module does.

## 16. Key Takeaways

- Python is a high-level, general-purpose programming language.
    
- It was created by Guido van Rossum.
    
- Python 3 is the version family used for modern development.
    
- Python supports multiple programming paradigms.
    
- It is widely used in automation, web development, AI, and cybersecurity.
    
- Python code can be executed interactively or through script files.
    
- The Standard Library provides many built-in modules.
    
- Python is useful for security automation, log analysis, and digital forensics.
    

## 17. Related Topics

- [[Programming Languages]]
    
- [[Compiler and Interpreter]]
    
- [[Python Syntax]]
    
- [[Python Variables and Data Types]]
    
- [[Python Control Flow]]
    
- [[Python Functions]]
    
- [[Python Data Structures]]
    
- [[Python File Handling]]
    
- [[Python Modules]]
    
- [[Python for Cybersecurity]]
    
- [[Automation and Scripting]]