# Firewalls

> Understand how firewalls enforce traffic policies between systems and networks.

## 1. What is a firewall?

A firewall monitors and controls network traffic according to defined rules. Rules may consider source/destination addresses, ports, protocols, connection state, application identity, or other attributes.

## 2. Common firewall types

- **Packet-filtering firewall:** evaluates packet header fields.
- **Stateful firewall:** tracks connection state and permits traffic based on connection context.
- **Application-layer firewall / proxy:** understands application protocols and can apply higher-level policies.
- **Next-generation firewall:** may combine stateful filtering with application awareness, intrusion prevention, and other functions.

## 3. Inbound and outbound rules

Inbound rules control traffic entering a system or network boundary. Outbound rules control traffic leaving it. Both directions matter for security.

## 4. Default-deny and least privilege

A common secure approach is to deny traffic by default and explicitly allow only required flows. Rules should be specific, documented, reviewed, and removed when no longer needed.

## 5. Host firewall vs network firewall

A host firewall protects an individual endpoint. A network firewall controls traffic between networks or security zones. Both can be used together.

## 6. Practical inspection

Windows:

```powershell
Get-NetFirewallProfile
Get-NetFirewallRule -Enabled True
```

Linux systems using UFW:

```bash
sudo ufw status verbose
```

Do not change firewall rules on a remote machine unless you have a safe recovery path.

## Key points

- Firewalls enforce traffic policy.
- Stateful firewalls track connection state.
- Default-deny and least privilege reduce unnecessary exposure.

## Related notes
- [[Network Security]]
- [[Network Segmentation]]
- [[Network Access Control]]
- [[Common Network Ports]]

## 7. Rule evaluation and state

Firewall rules are evaluated according to the product's policy model and rule ordering. Stateful firewalls track connection information, so return traffic for an allowed session may be permitted without a separate broad reverse-direction rule. Exact behaviour differs by platform and configuration.

## 8. Rule design example

If a workstation subnet needs HTTPS access to a server, a narrow rule should specify the source subnet, destination server, TCP protocol, and destination port 443. A rule allowing all traffic from every network to every server is much broader than required.

## 9. Logging and change control

Log denied traffic where it helps investigation, but avoid excessive logging that obscures important events. Every significant rule should have an owner, purpose, scope, and review date. Test changes carefully because an incorrect remote firewall rule can lock administrators out.

## Practical activity

Write three example policies for a lab: allow workstation-to-web-server TCP 443, deny guest-to-management access, and allow DNS only to an approved resolver. Do not apply rules to a production firewall for this exercise.

## My understanding

Explain why a stateful firewall can allow return packets for an established connection and why that does not mean all inbound traffic is allowed.
