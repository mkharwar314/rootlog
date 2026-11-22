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

## 6. Why hops may be missing

A router may forward traffic normally while refusing to send diagnostic ICMP responses, or it may rate-limit them. Some routers also use control-plane policies that treat traceroute probes differently from ordinary traffic. Therefore, asterisks in traceroute output are not proof of packet loss for application traffic.

## 7. Forward and return paths

Traceroute shows responses from routers along the probe path, but the return path for those responses may differ from the outbound path. Load balancing can also cause different probes to follow different paths.

## 8. Use with other tools

Combine traceroute with ping, route-table inspection, DNS checks, and application-specific connectivity tests. If a web service fails but traceroute reaches the destination network, inspect the service port and firewall policy.

## Practical activity

Run `tracert example.com` on Windows or `tracepath example.com` on Linux. Identify the first hop and any hops that do not respond. Write two possible explanations for a missing hop.

## My understanding

Explain how TTL/Hop Limit makes traceroute possible and why a missing response does not necessarily mean the router failed to forward traffic.
