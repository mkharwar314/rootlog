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

## 6. Tunnelling and routing

A VPN encapsulates traffic so it can travel through an underlying network between tunnel endpoints. Depending on configuration, the client may send only selected private-network traffic through the tunnel (split tunnel) or route most/all traffic through it (full tunnel). DNS routing and IPv6 handling must also be considered to avoid unintended traffic paths.

## 7. Authentication and trust

A VPN tunnel may authenticate devices, users, gateways, or a combination. Strong cryptography is not enough if credentials are weak, endpoints are compromised, or access policy is overly broad. MFA and device posture checks can reduce risk.

## 8. Common troubleshooting points

Check credentials, MFA, client version, gateway reachability, time synchronization, DNS, routes installed by the VPN, and firewall policy. A tunnel can show as connected while a particular internal service remains unreachable due to missing routes or access controls.

## Practical activity

On your own Windows device, inspect configured connections with `Get-VpnConnection`. If you have a legitimate VPN profile, compare the routes before and after connecting. Do not alter organizational VPN settings without authorization.

## My understanding

Explain the difference between a VPN tunnel being established and an application being reachable through that tunnel.
