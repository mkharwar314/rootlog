>Linux is an open-source, Unix-like operating system family built around the Linux kernel.

It is widely used in:

- Servers
- Desktop computers
- Cloud infrastructure
- Embedded systems
- Supercomputers
- Cybersecurity environments

Linux is known for its flexibility, stability, security features, and customisation.

## 2. History of Linux

- **1983:** Richard Stallman started the GNU Project.
- **1991:** Linus Torvalds released the first Linux kernel.
- **1992:** Linux became available under the GNU General Public License.
- **Today:** Linux powers servers, cloud platforms, embedded devices, and many other systems.

Linux distributions commonly combine the Linux kernel with GNU utilities and other software.

## 3. Linux Architecture

Linux has several important layers:

```
+---------------------------+
|       Applications        |
+---------------------------+
|       Shell / Tools       |
+---------------------------+
|       System Libraries    |
+---------------------------+
|        Linux Kernel       |
+---------------------------+
|          Hardware         |
+---------------------------+
```

### Main Components

|Component|Description|
|---|---|
|Kernel|Manages hardware and system resources|
|Shell|Provides a command-line interface|
|System Libraries|Provide interfaces to operating system functionality|
|Applications|Programs used by users|
|File System|Organises and stores files and directories|

## 4. Linux Distributions

A Linux distribution is an operating system built around the Linux kernel, along with software, utilities, package management, and configuration.

Popular distributions include:

|Distribution|Common Use|
|---|---|
|Ubuntu|Desktop, servers, development|
|Debian|Stable servers and general computing|
|Kali Linux|Penetration testing and security research|
|Fedora|Development and modern Linux technologies|
|Arch Linux|Customisable Linux environment|
|Linux Mint|Beginner-friendly desktop computing|
|Red Hat Enterprise Linux|Enterprise environments|

## 5. What Is Kali Linux?

Kali Linux is a Debian-based Linux distribution maintained by Offensive Security.

It is designed for:

- Penetration testing.
- Security auditing.
- Digital forensics.
- Vulnerability assessment.
- Security research.

It includes tools such as:

- Nmap
- Wireshark
- Burp Suite
- Metasploit Framework
- John the Ripper

**Important:** Kali Linux is a specialised security distribution. It is not necessary for every Linux task, and installing Kali does not automatically make someone a penetration tester.

## 6. Linux vs Windows

|Feature|Linux|Windows|
|---|---|---|
|Kernel|Linux kernel|Windows NT kernel|
|Source code|Open-source kernel|Proprietary operating system|
|Interface|CLI and GUI|GUI and CLI|
|Software management|Package managers|Installers and package managers|
|File system|Commonly ext4, XFS, Btrfs|Commonly NTFS|
|Customisation|Highly customisable|More controlled|
|Common use|Servers, cloud, development, security|Desktop, business, gaming|

## 7. Why Linux Is Important in Cybersecurity

Linux is widely used in cybersecurity because it provides:

- Powerful command-line tools.
- Network analysis utilities.
- Flexible scripting environments.
- Access to system configuration.
- Security testing tools.
- Server administration capabilities.

Security professionals use Linux for reconnaissance, network analysis, vulnerability assessment, system hardening, and forensic investigations.

## 8. Practical: Identify Your Linux System

Open your Kali Linux terminal.

### Task 1: Display the Kernel Version

```
uname -r
```

### Task 2: Display System Information

```
uname -a
```

### Task 3: Identify the Distribution

```
cat /etc/os-release
```

### Task 4: Display the Current Username

```
whoami
```

### Task 5: Display the Hostname

```
hostname
```

### Task 6: Display the Current Directory

```
pwd
```

## 9. My Understanding

Answer these questions in your own words:

1. What is Linux?
2. Who created the Linux kernel?
3. What is a Linux distribution?
4. What is Kali Linux?
5. What is the difference between Linux and Windows?
6. Why is Linux important in cybersecurity?

## 10. Practical Observations

Record your findings:

- Linux distribution:
- Kernel version:
- Current username:
- Hostname:
- Current working directory:
- One thing you observed about Kali Linux:

## Related Topics

- [[Operating System Fundamentals]]
- [[Kernel]]
- [[Shell]]
- [[Linux Architecture]]
- [[Linux File System]]
- [[Linux Commands]]
- [[Practical Labs]]
- [[Cybersecurity]]

---

**Category:** Linux Operating System

**Status:** Learning