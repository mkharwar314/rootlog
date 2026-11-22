# Network Segmentation

> Understand how dividing a network limits exposure and controls communication.

## 1. What is segmentation?

Network segmentation divides a network into smaller logical or physical zones. Examples include user, server, guest, management, and lab networks.

## 2. Why segment?

- Reduce unnecessary communication.
- Limit lateral movement after compromise.
- Protect sensitive assets.
- Apply different policies to different device groups.
- Reduce broadcast scope and simplify operations.

## 3. Segmentation mechanisms

Common mechanisms include VLANs, subnets, routers, firewalls, ACLs, and software-defined network policies.

A VLAN creates Layer 2 separation, but inter-VLAN routing policies must still be configured. Separate subnets without filtering do not automatically provide strong security.

## 4. Example design

A small organization might separate:
- Employee workstations.
- Public guest Wi-Fi.
- Servers.
- Network-management interfaces.
- Security testing lab.

Only required flows should be allowed between zones.

## 5. Microsegmentation

Microsegmentation applies fine-grained policy around individual workloads or groups of workloads, often in virtualized or cloud environments.

## 6. Practical lab

Draw a simple network with three VLANs. For each pair of zones, document whether communication should be allowed and why. Then translate the design into firewall or ACL rules in an authorized lab.

## Key points

- Segmentation limits reachability and helps contain incidents.
- VLANs alone do not guarantee security.
- Explicit inter-zone policy is essential.

## Related notes
- [[VLAN]]
- [[Firewalls]]
- [[Network Access Control]]
- [[Active Directory]]
