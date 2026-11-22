# Packet Analysis

> Develop a repeatable method for interpreting packet captures.

## 1. What to inspect

Start with:
- Timestamp.
- Source and destination addresses.
- Protocol and ports.
- Packet length.
- TCP flags and sequence behaviour.
- DNS names and answers.
- ICMP errors.
- TLS handshake metadata where visible.

## 2. TCP handshake

A typical TCP connection begins with:
1. SYN
2. SYN-ACK
3. ACK

A normal connection then exchanges data and eventually closes using FIN/ACK sequences, although resets and retransmissions also occur.

## 3. Useful Wireshark display filters

```text
tcp.flags.syn == 1
tcp.analysis.retransmission
icmp
dns
tcp.port == 80
ip.addr == 192.0.2.10
```

## 4. Common observations

- Repeated SYN packets without a response may indicate filtering, loss, or an unavailable service.
- Retransmissions may indicate loss or congestion.
- DNS NXDOMAIN indicates the queried name does not exist according to the responding DNS server.
- TCP RST indicates a connection reset, but context determines why.

Do not jump from one packet pattern to an attack conclusion.

## 5. Analysis workflow

1. Preserve the original capture.
2. Record its hash if evidentiary integrity matters.
3. Establish the capture time, interface, and scope.
4. Filter to relevant endpoints and protocols.
5. Reconstruct sequences and compare both directions.
6. Correlate with host, firewall, DNS, and application logs.
7. Document alternative explanations and limitations.

## 6. Practical task

Capture a DNS lookup in your own lab, filter on `dns`, and write down the query, response code, record type, and answer. Save the capture only if needed and protect it.

## Key points

- Packet analysis requires context and sequence, not isolated packets.
- Retransmissions, resets, and timeouts have multiple possible causes.
- Preserve original evidence and document methods.

## Related notes
- [[Wireshark]]
- [[Introduction to Network Analysis]]
- [[Network Monitoring]]
- [[Digital Forensics]]
