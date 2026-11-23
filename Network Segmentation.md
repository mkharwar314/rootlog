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

## 7. Segmentation policy matrix

A useful design tool is a matrix with source zones on one axis and destination zones on the other. For each pair, record required protocols and business justification. For example, workstations may need HTTPS to an application server, while guest devices should have no route to internal server networks.

## 8. Containment value

If one workstation is compromised, segmentation can prevent direct access to domain controllers, backups, and management interfaces. It does not eliminate risk: attackers may use allowed application paths, stolen credentials, or misconfigured exceptions.

## 9. Validation

Test both allowed and denied paths. Confirm that the network enforces the intended policy and that logs show blocked attempts. Review rules after application changes because new dependencies can create broad exceptions.

## Practical activity

Create a three-zone diagram: user, server, and guest. Write at least two allowed flows and two denied flows. Explain what should happen if a guest device attempts to connect to an administrative service.

## My understanding

Explain why a VLAN is useful for separation but does not, by itself, guarantee that devices in different VLANs are securely isolated.
