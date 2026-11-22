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

## 6. Connected, static, and default routes

A connected route is installed when an interface has an address and prefix configured and is active. A static route is added by an administrator. A default route is a catch-all route used when no more specific entry matches. Dynamic routing protocols can also install routes learned from neighbouring routers.

## 7. Why a route can exist but still fail

A route entry does not guarantee end-to-end reachability. The next-hop router may be unavailable, a firewall may drop traffic, return routing may be missing, or the destination service may be down. Routing is only one part of the communication path.

## 8. Route lookup example

For a destination `10.20.30.40`, the system compares the destination against route prefixes. If both `10.0.0.0/8` and `10.20.0.0/16` exist, the `/16` route wins because it is more specific.

## Practical activity

Use `ip route get 1.1.1.1` in Linux. Record the selected interface and gateway. Then compare it with the default route shown by `ip route`.

## My understanding

Explain the difference between a route's destination prefix, next hop, outgoing interface, and metric.
