# IDS and IPS

> Compare systems that detect suspicious network activity with systems that can actively block it.

## 1. IDS

An **Intrusion Detection System (IDS)** monitors activity and raises alerts when it identifies suspicious patterns or policy violations. A network IDS often analyzes traffic from a monitoring point.

## 2. IPS

An **Intrusion Prevention System (IPS)** is deployed inline or integrated with enforcement controls so it can block or modify traffic judged malicious.

## 3. Detection approaches

- **Signature-based:** matches known patterns.
- **Anomaly-based:** identifies deviations from a baseline.
- **Behaviour-based:** evaluates sequences or behaviours that may indicate an attack.

Signature detection is effective for known patterns but may miss novel attacks. Anomaly detection can find unusual activity but may produce false positives.

## 4. IDS vs IPS

| IDS | IPS |
|---|---|
| Primarily detects and alerts | Detects and can block |
| Often deployed out-of-band | Commonly deployed inline |
| Does not normally stop traffic itself | Can affect availability if misconfigured |

## 5. Operational considerations

Tune rules, update signatures, investigate alerts, monitor false positives, and test fail-open/fail-closed behaviour. An IPS outage or false positive can interrupt legitimate traffic.

## 6. Example tools

Suricata and Snort can be used in IDS/IPS roles depending on configuration. Zeek is commonly used for network security monitoring and protocol analysis.

## Key points

- IDS detects and alerts.
- IPS can actively prevent traffic.
- Detection quality depends on visibility, tuning, and ongoing investigation.

## Related notes
- [[Network Monitoring]]
- [[Wireshark]]
- [[Packet Analysis]]
- [[Network Security Best Practices]]

## 6. Alert triage

An alert should be treated as an investigative lead, not an automatic conclusion. Validate the source and destination, time window, rule that triggered, packet or flow evidence, asset role, and related endpoint logs. Determine whether the event is malicious, benign, or inconclusive.

## 7. False positives and false negatives

A false positive flags benign activity as suspicious. A false negative fails to detect malicious activity. Tuning should reduce noise without creating blind spots. Suppressions should be narrow, documented, and reviewed.

## 8. Deployment trade-offs

An out-of-band IDS can monitor traffic without directly interrupting it, but it cannot normally block packets by itself. An inline IPS can block traffic, but misclassification or failure may affect availability. Critical deployments require testing, redundancy, and a clear fail-open/fail-closed design.

## Practical activity

Review a sample alert from a lab IDS or study a documented rule. Write what evidence triggered it, what additional data you would collect, and what would make you classify it as a true positive.

## My understanding

Explain the operational difference between detection and prevention, including one availability risk introduced by inline blocking.
