> Understand secure remote administration and encrypted command-line access.

## 1. What is SSH?

**SSH (Secure Shell)** is a protocol for secure remote login, command execution, and tunnelling over an untrusted network. It replaces insecure remote-login methods such as Telnet in most modern environments.

SSH commonly uses TCP port **22**.

## 2. What SSH provides

- **Confidentiality:** encrypts session traffic.
- **Integrity:** detects unauthorized modification.
- **Authentication:** verifies the server and authenticates the client.
- **Port forwarding:** can tunnel other application traffic.

## 3. Authentication methods

- **Password authentication:** user supplies a password.
- **Public-key authentication:** client proves possession of a private key corresponding to an authorized public key.
- **Other methods:** may include certificates or multi-factor mechanisms, depending on configuration.

The private key must remain secret. A passphrase can protect a private key stored on disk.

## 4. Host-key verification

On first connection, an SSH client may ask whether to trust the server's host key. Verify the fingerprint through a trusted channel before accepting it, especially in sensitive environments. A changed host key can indicate a legitimate rebuild or a possible interception; investigate rather than blindly deleting the warning.

## 5. Basic commands

Connect:

```bash
ssh username@192.0.2.10
```

Specify a port:

```bash
ssh -p 2222 username@192.0.2.10
```

Generate an Ed25519 key pair:

```bash
ssh-keygen -t ed25519
```

Copy a public key to a server where authorized:

```bash
ssh-copy-id username@server.example
```

Windows includes an OpenSSH client on many current installations:

```powershell
ssh username@server.example
```

## 6. Security best practices

- Prefer strong key-based authentication where appropriate.
- Protect private keys with restrictive permissions and a passphrase.
- Disable direct root login where operationally possible.
- Restrict who can connect and from where.
- Keep the SSH server patched.
- Use MFA or additional access controls for sensitive systems.
- Monitor authentication logs and remove unused accounts/keys.

Do not disable password authentication until key-based access has been tested and recovery access is available.

## 7. Safe practical lab

Use SSH only against your own VM or a system for which you have explicit permission. From Kali, connect to your own Linux VM and verify the host-key fingerprint before logging in.

## Key points

- SSH provides encrypted remote access.
- Default port is TCP 22.
- Host-key verification protects against connecting to an impersonated server.
- Never share a private key.

## Related notes
- [[FTP and SFTP]]
- [[TCP Protocol]]
- [[Linux Services]]
- [[Common Network Ports]]

---