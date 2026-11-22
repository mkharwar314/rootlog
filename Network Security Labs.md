# Network Security Labs

> Practice foundational defensive network-security checks in an isolated, authorized environment.

## Safety and scope

Use your own Windows/Kali VMs or a lab network you administer. Do not scan, intercept, disrupt, or attempt access to third-party systems.

## Lab 1 — Build an asset inventory

List each lab VM, operating system, IP address, role, and owner. Draw the network connections and identify trust boundaries.

## Lab 2 — Review listening services

Windows:

```powershell
Get-NetTCPConnection -State Listen
```

Linux:

```bash
ss -tuln
```

For each listener, identify the process/service and decide whether it is required.

## Lab 3 — Review firewall posture

Windows:

```powershell
Get-NetFirewallProfile
```

Linux with UFW:

```bash
sudo ufw status verbose
```

Do not disable a firewall to make a test work. Document intended inbound and outbound rules.

## Lab 4 — Authorized service discovery

Against a single lab VM:

```bash
nmap -sV <lab-target-ip>
```

Compare discovered services with the asset inventory. Investigate unexpected services without assuming they are vulnerable.

## Lab 5 — Network segmentation design

Create separate conceptual zones for workstation, server, and guest devices. Write an allowlist of required communication between them.

## Lab 6 — Monitoring

Capture a short DNS lookup in Wireshark and record the query and response. Keep the capture restricted to your own test traffic.

## Report template

- Objective:
- Scope and authorization:
- Lab topology:
- Tools and versions:
- Steps performed:
- Evidence/observations:
- Risks identified:
- Recommended remediation:
- Limitations:

## Completion criteria

You can inventory assets, inspect listening services, review firewall state, identify unexpected exposure, and propose a least-privilege network policy.

## Additional lab — create a least-privilege flow policy

For each pair of zones in your lab, write:
- Source zone and host role.
- Destination zone and service.
- Required protocol and port.
- Business or lab reason.
- Whether the flow should be logged.
- What should happen to all other traffic.

## Additional lab — verify a service exposure

Compare the listening sockets on a lab VM with an authorized Nmap scan from another lab VM. Explain why local socket output and remote scan results may differ because of host firewalls, routing, or interface binding.

## Final report quality

Separate evidence from interpretation. Include only relevant outputs, redact secrets, and provide remediation steps that are practical for the lab environment.

## My understanding

Describe one unnecessary exposed service you would remove or restrict, the risk it creates, and how you would verify that the change worked.
