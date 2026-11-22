# IP Addressing Labs

> Practice identifying IPv4/IPv6 addresses, prefixes, gateways, and address categories.

## Lab 1 — Identify your local configuration

Windows:

```powershell
ipconfig /all
```

Linux:

```bash
ip address
ip route
```

Record one interface's address, prefix/subnet mask, and gateway.

## Lab 2 — Classify addresses

Classify these examples:

| Address | Category |
|---|---|
| 10.10.5.20 | Private IPv4 |
| 172.20.1.8 | Private IPv4 |
| 192.168.4.12 | Private IPv4 |
| 8.8.8.8 | Public IPv4 |
| 127.0.0.1 | IPv4 loopback |
| 169.254.10.5 | IPv4 link-local |
| ::1 | IPv6 loopback |
| fe80::1 | IPv6 link-local |

## Lab 3 — Identify network and host portions

For `192.168.10.25/24`, identify:
- Network address: `192.168.10.0`
- Broadcast address: `192.168.10.255`
- Usable host range in a conventional subnet: `192.168.10.1`–`192.168.10.254`

## Lab 4 — Observe IPv6

Find an IPv6 address on your system. Identify whether it is link-local, global unicast, or another special-use type. Do not assume every interface has global IPv6 connectivity.

## Lab report

Explain how the prefix length determines the network portion. Record any address categories that were unfamiliar and review [[IPv4 Addressing]] and [[IPv6 Addressing]].
