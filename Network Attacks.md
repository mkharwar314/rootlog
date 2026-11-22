# Network Attacks

> Recognize common network attack categories and understand their defensive implications.

## 1. Reconnaissance

Attackers may identify hosts, ports, services, DNS records, and network topology before attempting access. Defences include reducing unnecessary exposure, monitoring scans, and limiting information disclosure.

## 2. Spoofing and poisoning

- **IP spoofing:** falsifying a packet's source IP address.
- **ARP spoofing:** sending misleading ARP messages on a local network.
- **DNS poisoning:** causing incorrect DNS data to be used.

Use network segmentation, secure switching controls, DNS protections, and monitoring.

## 3. Man-in-the-middle (MitM)

An attacker positions themselves between communicating parties to observe or alter traffic. Use correctly validated TLS, secure Wi-Fi, certificate verification, and protected routing.

## 4. Denial of Service

DoS attacks attempt to make a service unavailable. Distributed DoS (DDoS) uses multiple sources. Defences include rate limiting, upstream mitigation, resilient architecture, filtering, and provider coordination.

## 5. Credential and service attacks

Password spraying, brute-force attempts, exploitation of exposed services, and session theft can lead to unauthorized access. Use MFA, rate limits, strong authentication, patching, and alerting.

## 6. Lateral movement

After compromising one device, an attacker may attempt to reach other systems. Segmentation, least privilege, endpoint monitoring, and restricted administrative protocols reduce this risk.

## 7. Defensive analysis

For each suspected attack, identify:
- Source and destination.
- Time window.
- Protocol and port.
- Affected asset.
- Observed evidence.
- Potential impact.
- Containment and recovery actions.

## Key points

- Network attacks target availability, confidentiality, integrity, or access.
- Layered controls reduce attack paths.
- Good incident analysis is evidence-based; a single unusual packet is not proof of compromise.

## Related notes
- [[Network Monitoring]]
- [[IDS and IPS]]
- [[Packet Analysis]]
- [[Firewalls]]
