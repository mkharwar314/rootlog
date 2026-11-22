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

## Lab 5 — identify special-use IPv4 ranges

Review these ranges:
- `10.0.0.0/8`, `172.16.0.0/12`, and `192.168.0.0/16`: private IPv4.
- `127.0.0.0/8`: loopback.
- `169.254.0.0/16`: IPv4 link-local.
- `100.64.0.0/10`: shared address space often used by carrier-grade NAT.

Do not assume that every address that is not private is globally reachable; special-purpose ranges exist.

## Lab 6 — prefix reasoning

For `192.168.20.10/24`, explain how many bits identify the network and how many identify the host. Repeat for `/26` and describe how the smaller host portion changes the number of addresses per subnet.

## My understanding

Choose an address from your own lab and explain its prefix, network portion, likely address category, and how the host uses the default gateway to reach another network.
