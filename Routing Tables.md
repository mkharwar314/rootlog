# Routing Tables

> Learn how hosts and routers store paths to destination networks.

## 1. What is a routing table?

A routing table is a set of entries that tells a system where to send packets for particular destination networks. A route commonly contains:
- Destination network/prefix.
- Next-hop gateway, if required.
- Outgoing interface.
- Metric or preference.
- Route source or type.

## 2. Example

A simplified table might contain:

| Destination | Next hop | Interface |
|---|---|---|
| 192.168.1.0/24 | On-link | Ethernet |
| 10.10.0.0/16 | 192.168.1.1 | Ethernet |
| 0.0.0.0/0 | 192.168.1.1 | Ethernet |

The default route `0.0.0.0/0` matches any IPv4 destination not matched by a more specific route.

## 3. Route selection

Routers generally use **longest-prefix match** first. If multiple routes have the same prefix length, route preference, administrative distance, metric, or protocol-specific rules may determine the selected route.

## 4. Inspect routes

Windows:

```powershell
route print
Get-NetRoute -AddressFamily IPv4
```

Linux:

```bash
ip route
ip route get 8.8.8.8
```

The `ip route get` command shows the route the local Linux kernel would use for a destination.

## 5. Troubleshooting

Check:
1. Is the destination network directly connected?
2. Is a specific route present?
3. Is the default gateway correct?
4. Is the next hop reachable?
5. Are firewall or policy-routing rules affecting traffic?

## Key points

- A routing table maps destination prefixes to forwarding decisions.
- The default route is used when no more specific route matches.
- Longest-prefix match is central to route selection.

## Related notes
- [[Introduction to Routing]]
- [[Static and Dynamic Routing]]
- [[Default Gateway]]
- [[Network Troubleshooting Labs]]
