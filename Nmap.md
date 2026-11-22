> Learn to discover hosts and identify exposed services on systems you are authorized to assess.

## 1. What is Nmap?

Nmap (Network Mapper) is a network discovery and security auditing tool. It can identify live hosts, open ports, service versions, and—in some cases—operating-system characteristics.

Use it only on systems and networks for which you have explicit permission.

## 2. Basic commands

Scan one lab host:

```bash
nmap 192.0.2.10
```

Scan selected ports:

```bash
nmap -p 22,80,443 192.0.2.10
```

Detect service versions:

```bash
nmap -sV 192.0.2.10
```

TCP SYN scan (requires suitable privileges):

```bash
sudo nmap -sS 192.0.2.10
```

TCP connect scan:

```bash
nmap -sT 192.0.2.10
```

Scan a small authorized lab subnet:

```bash
nmap -sn 192.168.56.0/24
```

Replace example ranges with your own lab range.

## 3. Port states

- **open:** an application is accepting connections.
- **closed:** reachable, but no application is listening on that port.
- **filtered:** Nmap cannot determine whether the port is open because filtering or network conditions prevent a clear result.
- Other states include `open|filtered` and `closed|filtered`.

## 4. Service detection limitations

Service/version detection uses probes and response analysis. Results can be incomplete or misleading when services are filtered, proxied, customized, or intentionally deceptive. Validate important findings.

## 5. Safe workflow

1. Confirm written or explicit authorization.
2. Define the target range and permitted scan intensity.
3. Start with host discovery or a small port list.
4. Record the command and timestamp.
5. Validate results manually.
6. Avoid intrusive scripts or aggressive scans unless specifically authorized.

## Key points

- Nmap is for network discovery and auditing.
- Port states describe what the scanner can infer, not whether a service is vulnerable.
- Always define scope and obtain permission.

## Related notes
- [[Common Network Ports]]
- [[Introduction to Network Analysis]]
- [[Network Security Labs]]
- [[Network Troubleshooting Labs]]

## 6. Scan techniques and trade-offs

A TCP connect scan (`-sT`) uses the operating system's connect call and completes a TCP connection when a port is open. A SYN scan (`-sS`) sends SYN probes and interprets responses without completing the full connection in the same way; it generally requires raw-packet privileges. UDP scans are harder to interpret because many services do not respond to arbitrary probes.

## 7. Host discovery is not certainty

Nmap may use ICMP, TCP, or other probes to determine whether a host appears online. Firewalls can block discovery probes, so a host may be marked down even though it is active. In an authorized assessment, use appropriate discovery options and validate important targets through known services.

## 8. Service detection

Nmap's version detection sends probes and compares responses with its service database. It can provide useful service guesses, but banners may be hidden, customized, or misleading. Confirm findings with service configuration or a second source.

## 9. Reporting responsibly

Record the exact target scope, time, scan options, source network, and tool version. Avoid scanning outside the agreed range. Do not describe an open port as a vulnerability without evidence of a weakness.

## Practical activity

Run a small scan against your own lab VM using `nmap -sT -sV -p 22,80,443 <lab-target-ip>`. Compare the result with the services actually installed and listening on the target.

## My understanding

Explain the difference between an open port, a detected service, and a confirmed vulnerability.
