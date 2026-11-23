>The **Windows Registry** is a hierarchical database that stores configuration settings and options for the Windows operating system, hardware, software, and user accounts.

Windows uses the Registry to retrieve configuration information while running.

**Example:** When you install software, it may create registry entries to store its configuration.

## 2. Why Does Windows Need the Registry?

The Registry helps Windows:

- Store operating system configuration.
- Manage hardware and device settings.
- Store application preferences.
- Maintain user-specific settings.
- Configure startup behaviour.
- Manage certain security-related settings.

## 3. Registry Structure

The Registry is organised into:

1. Hives
2. Keys
3. Subkeys
4. Values
5. Value data

Think of it like a directory structure:

- Hive = Main branch
- Key = Directory
- Subkey = Subdirectory
- Value = Configuration entry
- Data = Stored information

## 4. Main Registry Hives

|Hive|Description|
|---|---|
|HKEY_LOCAL_MACHINE (HKLM)|System-wide configuration|
|HKEY_CURRENT_USER (HKCU)|Settings for the currently logged-in user|
|HKEY_CLASSES_ROOT (HKCR)|File associations and COM-related information|
|HKEY_USERS (HKU)|Configuration for loaded user profiles|
|HKEY_CURRENT_CONFIG (HKCC)|Current hardware profile information|

These are the main logical registry hives exposed by Windows.

## 5. Registry Value Types

|Type|Description|
|---|---|
|REG_SZ|Text string|
|REG_DWORD|32-bit integer|
|REG_QWORD|64-bit integer|
|REG_BINARY|Binary data|
|REG_MULTI_SZ|Multiple strings|
|REG_EXPAND_SZ|Text containing expandable environment variables|

## 6. Common Registry Locations

|Registry Path|Purpose|
|---|---|
|HKLM\SOFTWARE|System-wide software settings|
|HKLM\SYSTEM|System and hardware configuration|
|HKCU\Software|Current user's application settings|
|HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run|Common system-wide startup configuration|
|HKCU\Software\Microsoft\Windows\CurrentVersion\Run|Current user's startup configuration|

**Important:** Startup registry locations can be abused by malware to maintain persistence. Their presence alone does not prove malicious activity.

## 7. Registry and Cybersecurity

The Registry is important in cybersecurity because it can help investigators:

- Examine application configuration.
- Investigate suspicious startup entries.
- Identify possible malware persistence.
- Review system configuration changes.
- Support Windows digital forensics.

### Malware Persistence

Persistence means maintaining access to a system even after events such as a reboot or user logoff.

Some malware may create or modify registry entries to execute automatically.

A registry entry should never be classified as malicious based on its location alone. Investigate its data, executable path, digital signature, timestamps, and surrounding evidence.

## 8. Practical: Inspect the Registry Using PowerShell

PowerShell provides a Registry provider that allows you to inspect registry keys like filesystem paths.

### Task 1: View Registry Drives

```
Get-PSDrive -PSProvider Registry
```

### Task 2: View Software Configuration

```
Get-ChildItem HKLM:\SOFTWARE
```

### Task 3: Read Windows Version Information

```
Get-ItemProperty 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion'
```

### Task 4: Inspect Current User Settings

```
Get-ChildItem HKCU:\Software
```

### Task 5: Read a Specific Registry Key

```
Get-Item 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion'
```

These commands inspect registry information without intentionally changing it.

## 9. Safety Precautions

- Do not randomly modify registry values.
- Do not delete unfamiliar registry keys.
- Export a key before making any authorised changes.
- Understand the purpose of a key before modifying it.
- Use read-only inspection while learning.

Incorrect registry modifications can cause application failures or Windows instability.

## 10. My Understanding

Answer these questions in your own words:

1. What is the Windows Registry?
2. What is the difference between HKLM and HKCU?
3. What is a registry key?
4. What is a registry value?
5. How can malware abuse the Registry?
6. Why should we avoid modifying unfamiliar registry entries?

## 11. Practical Observations

Record your observations:

- Number of Registry drives shown by PowerShell:
- One registry key you inspected:
- One value you found:
- What information did it contain?

## Related Topics

- [[Introduction to Windows]]
- [[Windows Architecture]]
- [[Windows File System]]
- [[Windows Users and Groups]]
- [[Windows Permissions]]
- [[Windows Services]]
- [[Windows Event Logs]]
- [[Digital Forensics]]

---
**Category:** Windows Operating System

**Status:** Learning