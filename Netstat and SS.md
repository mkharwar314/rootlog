# Netstat and SS

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
