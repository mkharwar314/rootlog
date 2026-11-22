> Apply practical controls to reduce the attack surface and improve network resilience.

## 1. Asset and exposure management

- Maintain an inventory of devices, services, and network ranges.
- Remove unused services and exposed ports.
- Keep network diagrams and ownership records current.
- Review external exposure regularly.

## 2. Secure configuration

- Change default credentials.
- Use secure management protocols such as SSH and HTTPS.
- Disable obsolete protocols and weak cryptography.
- Patch routers, switches, firewalls, access points, and servers.
- Back up configurations and test restoration.

## 3. Access control

- Apply least privilege.
- Use MFA for administrative and remote access.
- Restrict management interfaces to trusted networks.
- Remove stale accounts and credentials.
- Use 802.1X/NAC where appropriate.

## 4. Network architecture

- Segment users, servers, guests, and management systems.
- Use explicit inter-zone firewall rules.
- Protect critical infrastructure.
- Design redundancy for important services.
- Document allowed traffic flows.

## 5. Monitoring and response

- Centralize relevant logs.
- Monitor authentication failures and unusual traffic.
- Maintain time synchronization.
- Define incident-response procedures.
- Test alerting and recovery processes.

## 6. Wireless security

Use WPA3 or WPA2-AES, strong authentication, guest isolation, firmware updates, and rogue-access-point monitoring.

## 7. Review checklist

- [ ] Asset inventory is current.
- [ ] Unnecessary services are disabled.
- [ ] Administrative access uses MFA where possible.
- [ ] Firmware and software are patched.
- [ ] Network zones have documented access rules.
- [ ] Logs are collected and time-synchronized.
- [ ] Backups are protected and restoration-tested.
- [ ] Wireless networks use modern security.
- [ ] Incident-response contacts and procedures are known.

## Key points

Network security is an ongoing operational process, not a one-time configuration. Combine prevention, detection, response, and recovery.

## Related notes
- [[Introduction to Network Security]]
- [[Firewalls]]
- [[Network Segmentation]]
- [[Network Monitoring]]

## 8. Prioritization

Start with controls that reduce major, common risks: remove unnecessary exposure, patch internet-facing systems, protect administrative access with MFA, and ensure backups can be restored. Then improve segmentation, monitoring, configuration management, and incident response. Priorities should reflect the actual assets and threat model.

## 9. Change management

Network changes can create outages or security gaps. Document the reason, expected impact, rollback plan, approval, implementation time, and verification steps. Review firewall rules and remote-access policies periodically.

## 10. Continuous improvement

Use vulnerability findings, incident lessons, access reviews, and configuration audits to update the network security baseline. A checklist is useful only if someone owns the actions and verifies completion.

## Practical activity

Perform a defensive review of your own lab. List five services, whether each is required, how access is restricted, and how activity would be logged. Prioritize one improvement and explain its risk reduction.

## My understanding

Choose three controls and map each to the risk it reduces, the evidence that it is working, and a possible limitation.
