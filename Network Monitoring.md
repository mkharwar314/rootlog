# Network Monitoring

> Understand how network telemetry helps detect faults, performance problems, and security incidents.

## 1. What is network monitoring?

Network monitoring collects and analyzes information about devices, links, protocols, traffic, and service health. It supports troubleshooting, capacity planning, compliance, and security operations.

## 2. Common data sources

- Packet captures.
- Flow records such as NetFlow/IPFIX.
- Device logs and syslog.
- SNMP metrics.
- DNS and proxy logs.
- Firewall and IDS/IPS alerts.
- Application and server telemetry.

## 3. Metrics

Useful metrics include bandwidth utilization, latency, packet loss, jitter, interface errors, connection counts, DNS response time, and service availability.

## 4. Monitoring approaches

- **Packet-level:** detailed inspection of captured packets.
- **Flow-level:** summarizes who communicated with whom, when, and how much.
- **Device-level:** tracks interface, CPU, memory, and health metrics.
- **Log-level:** correlates events from devices and services.

## 5. Baselines and alerts

Establish normal patterns before setting alerts. Poorly tuned alerts create noise; thresholds should reflect operational needs and be reviewed over time.

## 6. Privacy and authorization

Capture only traffic you are authorized to inspect. Packet captures can contain personal data, credentials, and sensitive business information. Restrict access and retention.

## Key points

- Monitoring combines packets, flows, logs, and metrics.
- Baselines help distinguish normal variation from suspicious behaviour.
- Packet captures require careful authorization and handling.

## Related notes
- [[Wireshark]]
- [[Packet Analysis]]
- [[IDS and IPS]]
- [[Network Troubleshooting Labs]]
