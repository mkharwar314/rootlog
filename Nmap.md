# Nmap

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
