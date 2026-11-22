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
