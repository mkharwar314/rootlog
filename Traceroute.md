# Traceroute

> Learn how traceroute estimates the path packets take through routers.

## 1. What traceroute does

Traceroute sends probes with increasing TTL (IPv4) or Hop Limit (IPv6). Each router that reduces the value to zero may return an ICMP Time Exceeded message. The tool displays the responding hops.

## 2. Commands

Windows:

```powershell
tracert example.com
```

Linux:

```bash
traceroute example.com
```

Some Linux systems may require installing the traceroute package. `tracepath` is another option on many systems.

## 3. Reading output

Each row represents a hop and usually shows response times. A `*` means no response was received within the timeout; it does not necessarily mean the router is broken.

## 4. Limitations

- Routers may filter or rate-limit probes.
- Load balancing can produce different paths.
- Return paths may differ from forward paths.
- Some implementations use UDP, ICMP, or TCP probes.

## 5. Practical task

Trace a route to a permitted public hostname. Record the first hop, number of visible hops, and any non-responsive hops. Do not interpret every `*` as an outage.

## Key points

- Traceroute infers a path using TTL/Hop Limit behaviour.
- Missing hop responses are common.
- The displayed route may not represent the exact return path.

## Related notes
- [[ICMP Protocol]]
- [[Ping]]
- [[Routing Tables]]
