# SMTP and Email Protocols

> Understand the protocols used to send, retrieve, and synchronize email.

## 1. Email protocol roles

Email delivery involves multiple components:
- A **Mail User Agent (MUA)** is the user's email application.
- A **Mail Transfer Agent (MTA)** transfers messages between mail servers.
- A **Mail Delivery Agent (MDA)** places incoming messages into a mailbox.

## 2. SMTP

**SMTP (Simple Mail Transfer Protocol)** is used to submit and relay outgoing email.

Common ports:
- TCP **25** — server-to-server SMTP relay.
- TCP **587** — message submission, commonly with STARTTLS.
- TCP **465** — message submission over implicit TLS, commonly used today.

Port 25 is often restricted for end-user submission to reduce abuse.

## 3. POP3 and IMAP

SMTP sends email; POP3 and IMAP are used by clients to retrieve or access mailboxes.

| Protocol | Common ports | Purpose |
|---|---|---|
| POP3 | TCP 110; implicit TLS commonly 995 | Downloads messages, often with limited server-side synchronization |
| IMAP | TCP 143; implicit TLS commonly 993 | Accesses and synchronizes messages stored on the server |

Encrypted variants and server configuration matter; a port number alone does not prove encryption is correctly enabled.

## 4. Email delivery at a high level

1. A user composes a message in an email client.
2. The client submits it to an outgoing mail server.
3. The sending server looks up the recipient domain's MX record.
4. Mail servers transfer the message using SMTP.
5. The receiving system stores the message.
6. The recipient accesses it using IMAP, POP3, or webmail.

## 5. Email security

Common threats include phishing, spoofing, malicious attachments, business email compromise, and credential theft.

Important controls:
- **SPF:** publishes which sending hosts are authorized for a domain.
- **DKIM:** adds a cryptographic signature that recipients can verify.
- **DMARC:** tells receivers how to handle messages that fail aligned SPF/DKIM checks and provides reporting.
- TLS protects mail transport between participating systems but does not guarantee end-to-end message encryption.
- Use MFA, attachment scanning, user awareness, and domain monitoring.

SPF, DKIM, and DMARC reduce certain forms of domain spoofing; they do not make every message trustworthy.

## 6. Safe practical lab

Inspect DNS mail records for a domain you are allowed to examine:

```powershell
Resolve-DnsName -Type MX example.com
```

Or:

```bash
dig MX example.com
```

Do not send test messages to strangers or attempt to access another person's mailbox.

## Key points

- SMTP sends and relays email.
- IMAP and POP3 provide mailbox access.
- SPF, DKIM, and DMARC are complementary email-domain protections.

## Related notes
- [[DNS Protocol]]
- [[TCP Protocol]]
- [[Common Network Ports]]
- [[Network Security Best Practices]]

## 7. SMTP conversation

SMTP is a command-and-response protocol. A simplified session may include a greeting, `EHLO`, sender declaration, recipient declaration, message-data phase, and completion. Real deployments add authentication, policy checks, TLS, spam filtering, and message handling.

The sending server uses DNS MX records to identify mail exchangers for the recipient domain. If a domain has multiple MX records, preference values help determine which server should be tried first.

## 8. Email authentication limitations

SPF checks whether a sending host is authorized by a domain's published policy. DKIM verifies a cryptographic signature associated with a domain. DMARC evaluates alignment and tells receivers how to handle failures. These mechanisms improve domain-level authenticity, but a compromised legitimate mailbox can still send malicious messages.

## 9. Practical analysis

Inspect MX and TXT records for a domain using `dig MX example.com` and `dig TXT example.com`. When reviewing a real email in an authorized mailbox, examine the message headers for the sending path and authentication results. Do not treat a display name or visible From address as proof of sender identity.

## My understanding

Explain the difference between SMTP, IMAP, and POP3. Then describe what SPF, DKIM, and DMARC each contribute and one limitation of each.
