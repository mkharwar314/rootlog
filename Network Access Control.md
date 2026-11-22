# Network Access Control

> Understand how organizations decide which devices and users may connect to network resources.

## 1. What is NAC?

**Network Access Control (NAC)** enforces policies about who or what may connect to a network. Decisions may consider user identity, device identity, authentication, security posture, location, and policy.

## 2. Common components

- **Supplicant:** client device requesting access.
- **Authenticator:** switch or wireless access point controlling the port/access.
- **Authentication server:** commonly a RADIUS server that validates credentials and returns policy.

IEEE 802.1X is a common port-based network access-control framework.

## 3. Posture assessment

Some NAC systems check whether a device meets requirements such as supported OS version, endpoint protection, encryption, or patch level. Devices may be granted full access, restricted access, or remediation access.

## 4. NAC vs firewall

NAC controls admission and access based on identity/device policy. A firewall controls permitted traffic flows. They complement one another.

## 5. Security considerations

Use strong identity verification, certificate-based authentication where appropriate, secure RADIUS communication, clear guest policies, and monitoring. Plan fallback access carefully to avoid turning outages into unrestricted access.

## Key points

- NAC makes access decisions based on identity and device policy.
- 802.1X is commonly used for network admission.
- NAC and firewalls address related but different control points.

## Related notes
- [[Network Segmentation]]
- [[Wireless Network Security]]
- [[Firewalls]]
- [[Active Directory]]
