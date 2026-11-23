> Security Auditing is the process of examining and evaluating system activities, configurations, permissions, and security controls to identify weaknesses and verify that security policies are being followed.

## 1. What Is Security Auditing?

Security auditing helps determine whether a system is properly protected.

It examines:

- User accounts and permissions.
- Login activities.
- Running services.
- System configurations.
- Security events.
- Network connections.
- Software updates.
- Administrative activities.

**Example:**

An organization reviews failed login attempts to identify suspicious authentication activity.

## 2. Objectives of Security Auditing

The main objectives are:

1. Identify security weaknesses.
2. Detect suspicious activities.
3. Verify access permissions.
4. Monitor administrative actions.
5. Check compliance with security policies.
6. Improve the overall security posture.

## 3. Types of Security Audits

|Audit Type|Purpose|
|---|---|
|User Account Audit|Reviews user accounts and privileges.|
|Permission Audit|Checks file and resource permissions.|
|Configuration Audit|Identifies insecure system settings.|
|Network Audit|Reviews network connections and exposure.|
|Log Audit|Examines system and security events.|
|Compliance Audit|Checks whether policies and standards are followed.|

## 4. Security Logs and Events

A security log is a record of activities and events relevant to system security.

Examples:

- Successful logins.
- Failed login attempts.
- Account creation.
- Account deletion.
- Permission changes.
- Administrative activities.
- Service failures.

Security logs help administrators investigate suspicious activity and reconstruct events.

## 5. Windows Security Auditing

Windows provides Event Viewer and PowerShell for examining system events.

### Important Windows Event IDs

|Event ID|Meaning|
|---|---|
|4624|Successful logon.|
|4625|Failed logon.|
|4634|Account logged off.|
|4648|Logon attempted using explicit credentials.|
|4720|User account created.|
|4726|User account deleted.|
|4732|Member added to a security-enabled local group.|

### Useful PowerShell Commands

**View recent security events**

```
Get-WinEvent -LogName Security -MaxEvents 20
```

**Find failed logon events**

```
Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4625
} -MaxEvents 10
```

**Check available event logs**

```
Get-WinEvent -ListLog *
```

Some Security log queries require administrator permissions.

## 6. Linux Security Auditing

Linux provides several tools and log files for examining system activity.

Important locations:

|File|Purpose|
|---|---|
|`/var/log/auth.log`|Authentication and authorization events on Debian-based systems when configured.|
|`/var/log/syslog`|General system messages on systems using traditional syslog.|
|`/var/log/kern.log`|Kernel-related messages on systems that maintain this file.|
|`journalctl`|Examines logs collected by systemd-journald.|

### Useful Commands

**View recent system logs**

```
journalctl -n 50
```

**View authentication-related logs**

```
sudo journalctl | grep -iE 'authentication|sudo|failed'
```

**View logs from the current boot**

```
journalctl -b
```

**View login history**

```
last
```

**View failed login attempts, if supported**

```
sudo lastb
```

Log locations and available records depend on the Linux distribution and logging configuration.

## 7. Security Auditing vs Monitoring

These concepts are related but different.

|Security Auditing|Security Monitoring|
|---|---|
|Evaluates security controls and recorded activities.|Continuously observes system activity.|
|Often performed periodically or during investigations.|Usually operates continuously or near real time.|
|Identifies weaknesses and policy violations.|Helps detect suspicious behavior and incidents.|
|Produces audit findings and recommendations.|Produces alerts and operational events.|

Both are important for maintaining system security.

## 8. Security Audit Process

A typical security audit follows these steps:

1. **Define scope:** Decide which systems and resources will be examined.
2. **Collect evidence:** Gather logs, configurations, permissions, and system information.
3. **Analyze:** Identify weaknesses and suspicious activities.
4. **Evaluate:** Compare findings against security policies and requirements.
5. **Report:** Document observations and risks.
6. **Remediate:** Recommend and implement appropriate corrective actions.
7. **Verify:** Confirm that identified issues have been addressed.

## 9. Common Security Auditing Mistakes

- Ignoring failed login attempts.
- Not reviewing privileged accounts.
- Keeping logs for insufficient periods.
- Allowing unauthorized access to logs.
- Failing to synchronize system clocks.
- Collecting logs without analyzing them.
- Making conclusions from isolated events without sufficient evidence.

**Important:** A single failed login does not prove an attack. Investigate patterns, context, source addresses, timestamps, and related events before drawing conclusions.

## 10. Security Auditing Best Practices

1. Review security logs regularly.
2. Protect logs against unauthorized modification.
3. Restrict access to sensitive audit information.
4. Synchronize system clocks.
5. Monitor privileged activities.
6. Document audit findings.
7. Investigate suspicious patterns.
8. Retain logs according to organizational requirements.

## 11. Practical Lab — Inspect Security Events

### Windows PowerShell

Run:

```
Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4624, 4625
} -MaxEvents 20
```

Observe:

- Event ID.
- Event timestamp.
- Account name.
- Logon information.
- Source network address, when available.

### Kali Linux

Run:

```
journalctl -n 50
```

Then:

```
last
```

And:

```
sudo journalctl | grep -iE 'authentication|sudo|failed'
```

Observe:

- Login activit
- Authentication failure
- Administrative command activit
- Event timestamp

Some logs may be unavailable because of permissions or logging configuration.

## 12. Key Takeaways

- Security auditing evaluates the security of systems and activities.
- Logs provide evidence of system events.
- Windows uses Event Viewer and Windows Event Logs.
- Linux commonly uses systemd-journald and system log files.
- Auditing helps identify weaknesses and investigate incidents.
- Evidence must be interpreted carefully before reaching conclusions.

## 13. Questions to Understand

1. What is Security Auditing?
2. Why are security logs important?
3. What do Windows Event IDs 4624 and 4625 represent?
4. Which Linux command displays systemd logs?
5. What is the difference between auditing and monitoring?
6. Why should audit logs be protected?

## Related Notes

- [[Operating System Security]]
- [[Access Control]]
- [[Privilege Management]]
- [[System Hardening]]
- [[Patch Management]]
- [[Windows Event Logs]]
- [[Digital Forensics]]
- [[07 - Practical Labs]]
- [[08 - Research Papers]]

---