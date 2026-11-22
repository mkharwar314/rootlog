# Linux Networking Labs

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
