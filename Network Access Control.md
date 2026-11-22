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

## 6. 802.1X authentication flow

In a common wired 802.1X deployment, the endpoint supplicant communicates with the authenticator (such as a switch). The authenticator relays authentication messages to a RADIUS server. If authentication succeeds, the switch applies the returned access policy. The endpoint does not directly communicate with the RADIUS server in the normal relay model.

## 7. Authentication outcomes

A policy may grant normal access, place a device in a restricted VLAN, or provide remediation access. Guest access may use a separate workflow. A device being authenticated does not automatically mean every resource should be reachable; authorization and segmentation still apply.

## 8. Operational risks

Misconfigured certificates, unavailable RADIUS servers, incorrect switch trust settings, and weak fallback policies can disrupt access or create bypasses. Test certificate renewal and failure scenarios before deployment.

## Practical activity

Draw the supplicant–authenticator–RADIUS relationship. Label the role of each component and explain what policy might be applied after successful authentication.

## My understanding

Explain the difference between authenticating a device to the network and authorizing that device to access a particular server.
