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

## 7. Packet, flow, and log visibility

Packet capture provides detailed communication content when it is not encrypted, but requires substantial storage and careful privacy controls. Flow records summarize conversations and are useful for identifying traffic patterns at scale. Logs explain events recorded by devices and applications. Combining these sources gives stronger context than relying on one alone.

## 8. Baselines

A baseline describes normal traffic for a system or network during expected operating periods. A sudden increase in outbound connections, DNS queries, or traffic to unusual destinations may justify investigation. However, software updates, backups, and business events can also cause spikes.

## 9. Retention and integrity

Define who can access monitoring data, how long it is retained, and how it is protected. For incident response, preserve relevant logs promptly because some devices rotate or overwrite them quickly. Ensure clocks are synchronized.

## Practical activity

Create a small monitoring plan for your lab: choose one packet source, one log source, and three metrics. State what each can tell you and one limitation.

## My understanding

Explain when you would choose packet capture, flow records, or device logs for a particular investigation question.
