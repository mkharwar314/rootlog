> Inspect network connections, listening sockets, and protocol statistics.

## 1. What these tools show

`netstat` and `ss` display network socket information. They help identify listening services, established connections, local/remote endpoints, and socket states.

`ss` is the modern, commonly preferred Linux tool.

## 2. Windows commands

```powershell
netstat -ano
netstat -ano | findstr LISTENING
```

Find a process by PID:

```powershell
Get-Process -Id 1234
```

PowerShell alternatives:

```powershell
Get-NetTCPConnection
Get-NetUDPEndpoint
```

## 3. Linux commands

```bash
ss -tuln
ss -tunap
ss -s
```

Options commonly mean:
- `-t` TCP.
- `-u` UDP.
- `-l` listening sockets.
- `-n` numeric addresses/ports.
- `-a` all sockets.
- `-p` process information (may require elevated privileges).

## 4. TCP states

Common states include LISTEN, ESTABLISHED, TIME_WAIT, CLOSE_WAIT, and SYN_SENT. A state is a snapshot of a connection's lifecycle, not automatically evidence of an attack.

## 5. Practical task

List listening TCP ports on your own Windows or Kali system. Identify one service, its local port, and the process or service associated with it.

## Key points

- These tools inspect local socket state.
- A listening port is not automatically vulnerable.
- Correlate ports with process identity and expected system role.

## Related notes
- [[Common Network Ports]]
- [[Network Monitoring]]
- [[Nmap]]

## 6. Understanding listening vs established sockets

A listening TCP socket is waiting for incoming connections. An established socket represents an active TCP connection. UDP does not have a TCP-style connection state, so a UDP endpoint listing should not be interpreted as an established session in the same way.

## 7. Process correlation

A port should be correlated with the process ID and service that owns it. A port number alone is not enough to identify an application. On shared systems, several services may use dynamic ports, and process information may require administrator privileges.

## 8. Defensive use

Unexpected listeners can indicate an installed application, a development server, remote administration software, or potentially unwanted software. Verify the executable path, signature, service configuration, and business purpose before taking action.

## Practical activity

On Windows, run `netstat -ano`, choose one LISTENING entry, and use `Get-Process -Id <PID>`. On Kali, run `sudo ss -tulpen` and identify one listening service. Record the local address, port, and owning process.

## My understanding

Explain the difference between a listening socket and an established TCP connection, and why neither state alone proves malicious activity.
