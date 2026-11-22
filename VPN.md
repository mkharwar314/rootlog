# VPN

> Understand how Virtual Private Networks create protected network connectivity over another network.

## 1. What is a VPN?

A **Virtual Private Network (VPN)** creates a logical private connection across an underlying network. Many VPNs use cryptography to protect traffic between endpoints.

Common uses:
- Remote access for employees.
- Site-to-site connectivity between offices.
- Secure access to internal services while travelling.

## 2. Common VPN technologies

- **IPsec:** a suite of protocols commonly used for network-layer VPNs.
- **WireGuard:** a modern, streamlined VPN protocol.
- **OpenVPN:** a widely used VPN solution based on TLS technologies.
- **SSL/TLS VPN products:** vendor implementations that use TLS for remote access.

## 3. Remote-access vs site-to-site

- **Remote-access VPN:** connects an individual device/user to an organization network.
- **Site-to-site VPN:** connects networks, such as two office LANs.

## 4. What a VPN does not guarantee

A VPN does not make a user completely anonymous, prevent phishing, or protect a compromised endpoint. The VPN provider or organization operating the endpoint may have visibility into traffic. HTTPS remains important for end-to-end application protection.

## 5. Security considerations

Use strong authentication and MFA, modern cryptography, patched clients and gateways, least-privilege routes, device posture controls, and logging. Avoid split-tunnel or full-tunnel assumptions without understanding the policy.

## 6. Practical observation

On Windows:

```powershell
Get-VpnConnection
```

This lists configured VPN connections for the current user where supported.

## Key points

- VPNs create logical connectivity across an underlying network.
- Remote-access and site-to-site VPNs solve different use cases.
- A VPN is not a substitute for endpoint security or HTTPS.

## Related notes
- [[Proxy Servers]]
- [[Firewalls]]
- [[Network Segmentation]]
