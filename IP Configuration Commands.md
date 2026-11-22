# IP Configuration Commands

> Inspect and troubleshoot IP addressing, interfaces, routes, and DNS configuration.

## 1. Windows

Show detailed IP configuration:

```powershell
ipconfig /all
```

Show addresses and interfaces:

```powershell
Get-NetIPConfiguration
Get-NetIPAddress
```

Show routes:

```powershell
route print
Get-NetRoute
```

Clear the DNS resolver cache:

```powershell
ipconfig /flushdns
```

Renew a DHCP lease:

```powershell
ipconfig /renew
```

## 2. Linux

Show interfaces and addresses:

```bash
ip address
```

Show routes:

```bash
ip route
ip -6 route
```

Show link-layer neighbours:

```bash
ip neigh
```

Show DNS configuration (method varies by distribution):

```bash
resolvectl status
```

## 3. Troubleshooting order

1. Check whether the interface is up.
2. Check IP address and prefix/subnet mask.
3. Check the default gateway.
4. Check DNS server configuration.
5. Test local gateway reachability.
6. Test name resolution.
7. Test the actual application/service.

## 4. Important caution

Commands such as release/renew, interface resets, and route changes can interrupt connectivity. Use them only when you understand the effect and have permission.

## Key points

- `ipconfig` is common on Windows.
- `ip` is the standard modern Linux networking utility.
- Diagnose layer by layer instead of changing several settings at once.

## Related notes
- [[IPv4 Addressing]]
- [[IPv6 Addressing]]
- [[Default Gateway]]
- [[Network Troubleshooting Labs]]

## 5. Address, route, and DNS are separate configuration areas

An interface can have a valid IP address but an incorrect default gateway. It can have a correct route but an unavailable DNS resolver. It can resolve a hostname but fail to connect to the service. Diagnose each component independently rather than changing all settings together.

## 6. DHCP and static configuration

DHCP supplies configuration dynamically. Static configuration is entered manually and must match the network plan. A manually assigned address inside a DHCP pool can create an address conflict unless the server excludes or reserves it.

## 7. Safe command use

Read-only commands such as `ipconfig /all`, `ip address`, and `ip route` are good first steps. Commands that release leases, reset adapters, or alter routes can disconnect you. Record the original settings and ensure you have a recovery path before making changes.

## Practical activity

Create a short diagnostic record with four fields: interface/address, default route, DNS server, and test result. Use one Windows or Linux device and explain which command produced each value.

## My understanding

Explain how a device can have working IP connectivity but still fail to open a website because of DNS.
