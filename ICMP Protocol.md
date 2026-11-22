# ICMP Protocol

> Understand how network devices report errors and exchange diagnostic information.

## 1. What is ICMP?

**ICMP (Internet Control Message Protocol)** supports error reporting and diagnostics in IP networks. It is carried inside IP packets and is not a transport protocol like TCP or UDP.

ICMPv4 is used with IPv4. ICMPv6 is an essential part of IPv6 operation and includes functions such as Neighbor Discovery.

## 2. Common ICMP message types

Examples for ICMPv4 include:
- **Echo Request** — commonly sent by `ping`.
- **Echo Reply** — response to an echo request.
- **Destination Unreachable** — packet could not reach its destination or service.
- **Time Exceeded** — TTL expired, commonly used by traceroute.
- **Redirect** — informs a host of a potentially better route; often restricted for security reasons.

ICMPv6 has corresponding and additional message types.

## 3. Ping

`ping` commonly sends ICMP Echo Requests and measures whether Echo Replies return. It can help assess reachability and round-trip time.

A failed ping does not prove a host is offline: firewalls may block ICMP while allowing application traffic.

Windows:

```powershell
ping example.com
```

Linux:

```bash
ping -c 4 example.com
```

## 4. Traceroute

Traceroute tools send probes with progressively increasing TTL (IPv4) or Hop Limit (IPv6). Routers may return Time Exceeded messages, allowing the tool to infer the path.

Windows:

```powershell
tracert example.com
```

Linux:

```bash
traceroute example.com
```

Different traceroute implementations may use ICMP, UDP, or TCP probes.

## 5. Security considerations

ICMP can be abused for reconnaissance, flooding, or covert signalling. Blocking all ICMP is not a universal solution and can break diagnostics or important IPv6 functions. Apply rate limits and filtering appropriate to the network, and permit necessary ICMPv6 messages.

## Key points

- ICMP reports network errors and supports diagnostics.
- Ping and traceroute use ICMP-related behaviour, but implementations vary.
- A blocked ping does not necessarily mean a host is down.

## Related notes
- [[IPv4 Addressing]]
- [[IPv6 Addressing]]
- [[TCP Protocol]]
- [[Network Troubleshooting Labs]]
