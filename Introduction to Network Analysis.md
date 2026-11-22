# Introduction to Network Analysis

> Learn how to observe, interpret, and troubleshoot network communication.

## 1. What is network analysis?

Network analysis examines network behaviour using packet captures, flow records, logs, and diagnostic tools. It can answer questions about connectivity, protocol behaviour, performance, and suspicious activity.

## 2. Core workflow

1. Define the question and scope.
2. Confirm authorization.
3. Select a suitable data source.
4. Capture or collect only the necessary data.
5. Filter and inspect relevant traffic.
6. Build a timeline and identify endpoints/protocols.
7. Validate findings with additional evidence.
8. Document limitations and conclusions.

## 3. Important fields

For each packet or flow, consider timestamp, source/destination IP, source/destination port, protocol, packet length, TCP flags, DNS name, and application-layer metadata where available.

## 4. Capture filters vs display filters

A **capture filter** controls what is collected. A **display filter** controls what is shown from an existing capture. They use different syntax in Wireshark.

## 5. Ethical and privacy considerations

Only capture networks and devices within your authorization. Captures may contain credentials, private messages, or personal information. Protect evidence, preserve original files, and record hashes when used in an investigation.

## Key points

- Start with a clear question and authorized scope.
- Capture and display filters are different.
- Validate conclusions using more than one indicator.

## Related notes
- [[Wireshark]]
- [[Packet Analysis]]
- [[Network Monitoring]]
- [[Network Troubleshooting Labs]]

## 6. Choosing the right evidence source

Use packet capture when you need protocol-level detail. Use flow records when you need broad communication patterns. Use device logs for configuration changes and security events. Use application logs to understand what the service did with a request. The best source depends on the question being investigated.

## 7. Establishing context

Before interpreting a capture, identify the network interface, capture point, time zone, clock accuracy, network topology, and whether traffic is mirrored or locally generated. A capture taken on one endpoint may not show packets dropped elsewhere in the path.

## 8. Reporting findings

Separate observed facts from interpretation. For example: “The capture contains repeated SYN packets to TCP port 443 with no observed SYN-ACK” is an observation. “The server is down” is an interpretation that requires additional validation.

## Practical activity

Write one investigation question, such as “Why can this VM resolve DNS but not reach a web service?” List the evidence sources and commands you would use before changing configuration.

## My understanding

Explain why the location of a packet capture point affects what an analyst can conclude.
