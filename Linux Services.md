> Understand how Linux manages background services, service startup, and system processes.

## 1. What Is a Service?

A service is a program that runs in the background to provide a specific function.

Examples:

- SSH service — provides remote login access.
- Cron service — schedules tasks.
- Network services — support network communication.
- Logging services — collect system logs.
- Web server — delivers web content.

Services often operate without direct interaction from a user.

## 2. What Is a Daemon?

A daemon is a background process that provides a service or performs a system task.

Examples:

|Daemon|Purpose|
|---|---|
|`sshd`|Handles SSH connections|
|`cron`|Executes scheduled tasks|
|`systemd`|Manages system initialization and services|
|`rsyslogd`|Handles system logging|

A daemon is a type of background process, but not every background process is a system service.

## 3. What Is systemd?

`systemd` is a system and service manager used by many Linux distributions, including Kali Linux.

It is responsible for:

- Starting system services.
- Managing service dependencies.
- Controlling service states.
- Handling system initialization.
- Managing system targets.

It commonly acts as PID 1, the first userspace process.

Check your system's init process:

```
ps -p 1 -o pid,comm,args
```

## 4. Understanding systemctl

`systemctl` is the command-line tool used to interact with systemd.

Important commands:

|Command|Purpose|
|---|---|
|`systemctl status`|Displays service or system status|
|`systemctl start`|Starts a service|
|`systemctl stop`|Stops a service|
|`systemctl restart`|Restarts a service|
|`systemctl reload`|Requests a service configuration reload|
|`systemctl enable`|Configures a service to start automatically|
|`systemctl disable`|Removes automatic startup configuration|
|`systemctl list-units`|Lists loaded systemd units|

## 5. Checking Service Status

Example:

```
systemctl status ssh
```

This displays information about the SSH service.

Common service states include:

|State|Meaning|
|---|---|
|Active (running)|Service is currently running|
|Inactive (dead)|Service is not running|
|Failed|Service encountered an error|
|Activating|Service is starting|
|Deactivating|Service is stopping|

A service can be enabled but currently inactive. Enabled means configured to start automatically, not necessarily running now.

## 6. Starting and Stopping Services

Start a service:

```
sudo systemctl start ssh
```

Stop a service:

```
sudo systemctl stop ssh
```

Restart a service:

```
sudo systemctl restart ssh
```

Reload configuration when supported:

```
sudo systemctl reload ssh
```

These commands change system state. Use them only when you understand the effect and have authorization.

## 7. Enable and Disable Services

Enable automatic startup:

```
sudo systemctl enable ssh
```

Disable automatic startup:

```
sudo systemctl disable ssh
```

Check whether a service is enabled:

```
systemctl is-enabled ssh
```

Remember:

- `start` runs a service now.
- `stop` stops a running service.
- `enable` configures automatic startup.
- `disable` removes automatic startup configuration.

## 8. Listing Services

List active services:

```
systemctl list-units --type=service --state=running
```

List all loaded service units:

```
systemctl list-units --type=service --all
```

List installed service unit files:

```
systemctl list-unit-files --type=service
```

## 9. Service Logs

Logs help administrators investigate service failures and suspicious activity.

View logs for SSH:

```
journalctl -u ssh
```

View recent service logs:

```
journalctl -u ssh -n 20
```

Follow new log entries:

```
journalctl -u ssh -f
```

Press `Ctrl + C` to stop following logs.

## 10. Cybersecurity Importance

Service management is an important part of Linux security.

Security analysts examine services to identify:

1. Unnecessary services.
2. Unauthorized services.
3. Unexpected network-facing services.
4. Services running with excessive privileges.
5. Suspicious service configurations.
6. Failed or unusual service activity.

### Example: Unnecessary SSH Service

Suppose a workstation does not need remote SSH access, but its SSH server is running.

This may expose an additional network entry point.

An administrator should assess whether the service is necessary, restrict access appropriately, and disable it if it is not required.

Do not assume that every running service is dangerous.

## 11. Practical Lab — Inspect Linux Services

Use your Kali Linux terminal.

### Task 1 — Check PID 1

```
ps -p 1 -o pid,comm,args
```

### Task 2 — Check SSH service status

```
systemctl status ssh
```

If SSH is not installed or the unit is unavailable, record that result. Do not install or enable it just for this exercise.

### Task 3 — Check whether SSH is enabled

```
systemctl is-enabled ssh
```

### Task 4 — List running services

```
systemctl list-units --type=service --state=running
```

### Task 5 — List available service unit files

```
systemctl list-unit-files --type=service
```

### Task 6 — Inspect SSH logs

```
journalctl -u ssh -n 20 --no-pager
```

If SSH has no logs, record that observation.

### Task 7 — Inspect a service without changing it

Choose a service from your running-services list and run:

```
systemctl status SERVICE_NAME
```

Replace `SERVICE_NAME` with its actual unit name.

**Safety:** This lab is inspection-only. Do not start, stop, enable, disable, or restart services.

## 12. Key Takeaways

- Services provide background functionality.
- Daemons are background processes.
- `systemd` manages services on many Linux distributions.
- `systemctl` controls systemd units.
- `journalctl` helps inspect system logs.
- Enabled and running are different states.
- Unnecessary services can increase attack surface.

## 13. My Understanding

Answer in your own words:

1. What is a Linux service?
2. What is a daemon?
3. What is the purpose of systemd?
4. What is the difference between `start` and `enable`?
5. How can an administrator inspect service logs?
6. Why should unnecessary services be disabled?

## Related Notes

- [[Linux Processes]]
- [[Linux Users and Groups]]
- [[Linux Permissions]]
- [[Linux Package Management]]
- [[System Hardening]]
- [[Security Auditing]]
- [[Digital Forensics]]

---

**Category:** Linux Operating System

**Status:** Learning