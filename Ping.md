# Ping

> Use ping to test basic IP reachability and measure round-trip time.

## 1. What ping does

`ping` commonly sends ICMP Echo Request messages and waits for Echo Replies. It reports response time and packet loss.

Ping tests a limited part of connectivity. It does not prove that a specific application or TCP port is working.

## 2. Windows commands

```powershell
ping 127.0.0.1
ping 192.168.1.1
ping example.com
ping -n 4 example.com
```

## 3. Linux commands

```bash
ping -c 4 127.0.0.1
ping -c 4 192.168.1.1
ping -c 4 example.com
```

## 4. Interpreting results

- Replies indicate that echo responses returned.
- Timeouts may indicate packet loss, filtering, routing problems, or an unavailable host.
- High latency can indicate congestion, long distance, or processing delays.
- Name-resolution errors point toward DNS or resolver configuration rather than ICMP itself.

A host may block ping while its web or SSH service remains available.

## 5. Troubleshooting sequence

Test loopback, local address, default gateway, and then a permitted remote destination. Compare results to narrow the likely fault domain.

## Key points

- Ping commonly uses ICMP Echo.
- A failed ping is not proof that a host is offline.
- Ping does not test application-layer availability.

## Related notes
- [[ICMP Protocol]]
- [[Traceroute]]
- [[Network Troubleshooting Labs]]
