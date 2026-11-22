> Build familiarity with commonly encountered ports during administration and network assessment.

## 1. What is a port?

A port number identifies an application endpoint associated with a transport protocol. TCP and UDP have separate port spaces. A port being open does not by itself prove that a service is vulnerable.

## 2. Common TCP and UDP ports

| Service / protocol | Typical port | Transport | Purpose |
|---|---:|---|---|
| FTP control | 21 | TCP | Traditional FTP control |
| SSH / SFTP | 22 | TCP | Secure remote access / file transfer |
| Telnet | 23 | TCP | Insecure remote terminal |
| SMTP relay | 25 | TCP | Mail transfer between servers |
| DNS | 53 | UDP/TCP | Name resolution |
| DHCPv4 server/client | 67/68 | UDP | Dynamic IPv4 configuration |
| HTTP | 80 | TCP | Web traffic |
| POP3 | 110 | TCP | Email retrieval |
| NTP | 123 | UDP | Time synchronization |
| IMAP | 143 | TCP | Email access |
| SNMP | 161/162 | UDP | Network management / traps |
| HTTPS | 443 | TCP | HTTP over TLS |
| SMB | 445 | TCP | Windows file and printer sharing |
| SMTP submission | 587 | TCP | Authenticated mail submission |
| LDAPS | 636 | TCP | LDAP over TLS |
| IMAPS | 993 | TCP | IMAP over implicit TLS |
| POP3S | 995 | TCP | POP3 over implicit TLS |
| SQL Server | 1433 | TCP | Common Microsoft SQL Server default |
| MySQL | 3306 | TCP | Common MySQL default |
| RDP | 3389 | TCP/UDP | Remote Desktop |
| PostgreSQL | 5432 | TCP | Common PostgreSQL default |
| VNC | 5900 | TCP | Remote desktop protocol family |
| HTTP/3 | 443 | UDP | HTTP over QUIC |

Ports are defaults, not guarantees. Services can be configured to listen on other ports.

## 3. Well-known port ranges

- **0–1023:** well-known ports.
- **1024–49151:** registered ports.
- **49152–65535:** dynamic/private ports (commonly used as ephemeral ports on modern systems).

The exact ephemeral range can vary by operating system.

## 4. Inspect listening ports

Windows:

```powershell
Get-NetTCPConnection -State Listen
Get-NetUDPEndpoint
```

Linux:

```bash
ss -tulpen
```

To inspect a host you own or are authorized to assess:

```bash
nmap -sT -sV 192.0.2.10
```

Do not scan public systems without permission.

## 5. Security perspective

- Expose only services that are required.
- Restrict management ports to trusted networks.
- Patch and securely configure services.
- Prefer encrypted protocols over insecure legacy alternatives.
- Confirm service identity; do not assume a port number tells you exactly what is running.
- Review firewall rules and logs regularly.

## Key points

- TCP and UDP use separate port spaces.
- Port numbers identify endpoints, not vulnerability status.
- Verify the actual service and its configuration.

## Related notes
- [[TCP Protocol]]
- [[UDP Protocol]]
- [[Network Devices]]
- [[Nmap]]
- [[Firewalls]]

---