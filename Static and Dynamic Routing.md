> Compare manually configured routes with routes learned through routing protocols.

## 1. Static routing

A static route is configured manually by an administrator. It does not automatically adapt to topology changes unless the administrator or automation updates it.

Advantages:
- Predictable and simple in small networks.
- No routing-protocol update traffic.
- Useful for default routes and stub networks.

Limitations:
- Manual maintenance.
- Poor scalability in large, changing networks.
- A failed path may require manual intervention unless backup routes are configured.

## 2. Dynamic routing

Dynamic routing protocols allow routers to exchange reachability information and update routes when network topology changes.

Examples:
- **RIP:** distance-vector protocol; simple but limited.
- **OSPF:** link-state interior gateway protocol.
- **IS-IS:** link-state interior gateway protocol.
- **BGP:** path-vector protocol used between autonomous systems and for large-scale routing policy.

## 3. Comparison

| Static | Dynamic |
|---|---|
| Manually configured | Learned through routing protocols |
| Low protocol overhead | Uses protocol messages and processing |
| Good for simple/stable paths | Better suited to changing or larger networks |
| Updates require administration/automation | Can adapt to topology changes |

## 4. Choosing an approach

Small networks may use static routes effectively. Larger networks often use dynamic routing, sometimes combined with static routes for specific purposes. Design depends on scale, resilience, operational expertise, and policy.

## 5. Practical observation

On your own system:

```powershell
route print
```

```bash
ip route
```

These commands show installed routes, but they do not by themselves tell you whether a route was learned through a routing protocol on an upstream router.

## Key points

- Static routes are manually configured.
- Dynamic routing uses protocols to exchange route information.
- BGP, OSPF, and RIP solve different routing problems; they are not interchangeable.

## Related notes
- [[Introduction to Routing]]
- [[Routing Tables]]
- [[Packet Forwarding]]

## 5. Dynamic routing protocol families

Interior Gateway Protocols (IGPs), such as OSPF and IS-IS, exchange routing information within an autonomous system. RIP is a simpler distance-vector IGP. BGP is an Exterior Gateway Protocol used to exchange reachability information between autonomous systems and apply routing policy.

OSPF calculates paths using link-state information and a cost metric. BGP makes policy-driven path decisions using path attributes; it is not simply a shortest-distance protocol.

## 6. Route convergence

When a link or router fails, dynamic routing protocols detect changes and recalculate or advertise alternate paths. The time and stability of this process are part of convergence. During convergence, some traffic may be temporarily lost or misrouted.

## 7. Design trade-offs

Static routing is easier to reason about in a tiny stable network, but manual maintenance becomes difficult as networks grow. Dynamic routing improves adaptability but introduces protocol configuration, authentication, monitoring, and troubleshooting requirements.

## Practical activity

Inspect the routes on your own machine with `ip route` or `route print`. Identify which routes appear connected and which route is the default. Your endpoint may not run a routing protocol; explain why the presence of routes does not prove dynamic routing is in use.

## My understanding

Give one scenario where static routing is appropriate and one where dynamic routing is more practical. Justify each choice.
