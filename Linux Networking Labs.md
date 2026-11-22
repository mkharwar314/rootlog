> Practice network inspection and troubleshooting in your own Linux/Kali VM.

## Lab rules

Use your own VM or an explicitly authorized lab network.

## Lab 1 — Inspect interfaces

```bash
ip address
ip link
```

Identify active interfaces and assigned addresses.

## Lab 2 — Inspect routes

```bash
ip route
ip -6 route
```

Identify the default route and gateway.

## Lab 3 — Inspect neighbours

```bash
ip neigh
```

Observe neighbour entries learned through ARP or IPv6 Neighbor Discovery.

## Lab 4 — Test connectivity and DNS

```bash
ping -c 4 127.0.0.1
ping -c 4 example.com
dig example.com
```

A failed ping may be caused by filtering.

## Lab 5 — Inspect sockets

```bash
ss -tuln
ss -tunap
```

Identify listening ports and, where permitted, associated processes.

## Lab 6 — Trace a route

```bash
tracepath example.com
```

If unavailable, use an installed traceroute implementation.

## Lab report

Record the VM network mode, interface, commands, outputs summarized in your own words, and any limitations.

## Completion criteria

You can inspect interfaces, routes, neighbours, DNS, and local listening sockets without changing network configuration.

## Additional lab — test a TCP service

If `curl` is installed, test an authorized HTTPS endpoint:

```bash
curl -I --connect-timeout 5 https://example.com
```

Record whether DNS resolution, connection establishment, TLS negotiation, and the HTTP response succeeded. A failure message can help locate the stage where the request stopped.

## Additional lab — inspect a neighbour entry

After communicating with your gateway, run:

```bash
ip neigh
```

Identify the gateway's neighbour entry and its state. States such as REACHABLE, STALE, or DELAY describe neighbour-cache status; they are not direct security verdicts.

## Observation template

Document the command, interface, target, result, interpretation, and limitation. Avoid copying sensitive output such as internal hostnames or public IP details into public repositories.

## My understanding

Explain how the `ip address`, `ip route`, and `ip neigh` commands answer three different networking questions.
