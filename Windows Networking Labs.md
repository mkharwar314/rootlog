> Perform basic network inspection and troubleshooting on your own Windows machine.

## Lab rules

Use your own computer or an authorized lab. Do not scan or capture traffic from networks without permission.

## Lab 1 — Inspect IP configuration

```powershell
ipconfig /all
```

Record:
- Interface name.
- IPv4 and IPv6 addresses.
- Subnet mask/prefix.
- Default gateway.
- DNS servers.
- DHCP enabled status.

## Lab 2 — Test connectivity

```powershell
ping 127.0.0.1
ping <your-default-gateway>
ping example.com
```

Compare the results. A blocked ping does not prove a service is unavailable.

## Lab 3 — Inspect DNS

```powershell
Resolve-DnsName example.com
Resolve-DnsName -Type MX example.com
```

Record the record type and answer.

## Lab 4 — Inspect routes

```powershell
route print
Get-NetRoute
```

Identify the default route and its interface.

## Lab 5 — Inspect listening ports

```powershell
netstat -ano
Get-NetTCPConnection -State Listen
```

Choose one PID and identify it:

```powershell
Get-Process -Id <PID>
```

## Lab report

Record objective, environment, commands, observations, interpretation, and limitations. Do not paste private IPs or other sensitive details into public posts.

## Completion criteria

You can explain your own IP configuration, identify the default gateway, resolve a DNS name, and identify at least one listening service.

## Additional lab — test a specific service

Use `Test-NetConnection` to test a known, authorized service:

```powershell
Test-NetConnection example.com -Port 443
```

Record `TcpTestSucceeded`, the resolved remote address, and the interface/source address if shown. This is more relevant than ping when the question is whether a particular TCP service is reachable.

## Additional lab — inspect DNS cache

```powershell
ipconfig /displaydns
```

Find a cached entry and explain why a cached answer may remain available until its TTL expires. Avoid sharing the full cache because it can reveal browsing and application activity.

## Observation template

- Question being tested:
- Command:
- Relevant output:
- What the output proves:
- What it does not prove:
- Next diagnostic step:

## My understanding

Write a short troubleshooting report for one test. Include the hypothesis, result, and next step rather than copying the entire terminal output.
