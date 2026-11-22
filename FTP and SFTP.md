# FTP and SFTP

> Compare file-transfer protocols and understand why encrypted transfer matters.

## 1. FTP

**FTP (File Transfer Protocol)** transfers files between a client and server. Traditional FTP does not encrypt credentials or file contents.

Common FTP connections:
- TCP port **21** — control connection.
- TCP port **20** — traditionally used for the data connection in active mode.
- Passive mode negotiates a separate server-side data port.

Firewall behaviour differs between active and passive modes.

## 2. SFTP

**SFTP (SSH File Transfer Protocol)** is a file-transfer protocol that operates over SSH. It provides encrypted authentication and data transfer.

- Common default port: TCP **22**.
- It is not simply FTP with encryption; it is a different protocol built over SSH.

## 3. FTP vs SFTP

| FTP | SFTP |
|---|---|
| Traditional FTP is unencrypted | Encrypted through SSH |
| Uses separate control/data connections | Uses an SSH connection |
| Common control port TCP 21 | Common port TCP 22 |
| Credentials may be exposed | Credentials/data are protected in transit |

FTPS is another distinct option: FTP secured using TLS. Do not confuse FTPS with SFTP.

## 4. Security considerations

Avoid sending passwords or sensitive files through unencrypted FTP across untrusted networks. Use SFTP or correctly configured FTPS. Apply least-privilege accounts, restrict directories, validate file types, log access, and keep server software updated.

## 5. Safe practical lab

If you have an authorized SFTP server:

```bash
sftp username@server.example
```

Common interactive commands:

```text
pwd
ls
cd directory
put local-file.txt
get remote-file.txt
bye
```

Do not connect to systems without permission. If no SFTP server is available, review the command syntax without attempting a connection.

## Key points

- FTP and SFTP are different protocols.
- Traditional FTP is not encrypted.
- SFTP uses SSH and commonly TCP port 22.
- FTPS uses TLS and is distinct from SFTP.

## Related notes
- [[SSH Protocol]]
- [[TCP Protocol]]
- [[Common Network Ports]]
- [[Network Security Best Practices]]

## 6. FTP connection modes

FTP separates its control channel from its data channel. In active mode, the server initiates the data connection back toward the client. In passive mode, the client initiates both connections, which is often easier through client-side firewalls and NAT. Passive mode still requires the server's configured data-port range to be reachable.

## 7. Authentication and file permissions

A secure file-transfer service should use named accounts, restrict users to approved directories, and grant only the read/write permissions required for their role. Anonymous FTP, if enabled at all, should expose only intentionally public content. Upload directories require special care because attackers may try to place executable or malicious files there.

## 8. Choosing a transfer method

Use SFTP when SSH-based file transfer is supported. Use FTPS when an environment specifically requires FTP semantics protected by TLS. Avoid plain FTP for credentials or confidential data on untrusted networks. Check host keys or certificates so the client knows it is connecting to the intended server.

## Practical activity — understand the command sequence

On paper, write the SFTP sequence for connecting, listing a remote directory, changing directories, uploading a harmless text file, downloading it, and disconnecting. If you have an authorized lab server, perform the sequence and verify the transferred file.

## My understanding

Explain why SFTP is not simply FTP with a different port, and distinguish SFTP from FTPS.
