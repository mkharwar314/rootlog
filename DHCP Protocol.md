> Understand how devices automatically receive network configuration.

## 1. What is DHCP?

**DHCP (Dynamic Host Configuration Protocol)** automatically provides network configuration to clients. This commonly includes an IP address, subnet mask or prefix, default gateway, DNS server addresses, and lease duration.

Without DHCP, an administrator may need to configure these values manually.

## 2. DHCPv4 DORA process

The common initial allocation sequence is remembered as **DORA**:

1. **Discover** — client broadcasts to find DHCP servers.
2. **Offer** — a server offers an address and configuration.
3. **Request** — client requests the offered configuration.
4. **Acknowledge** — server confirms the lease.

The client normally starts without a usable IPv4 address, so early messages use broadcast communication.

## 3. Ports

DHCPv4 uses:
- UDP port **67** — server.
- UDP port **68** — client.

DHCPv6 uses UDP port 547 for servers/relays and 546 for clients.

## 4. Leases and renewal

An assigned address is generally leased for a period. A client attempts renewal before the lease expires. If renewal fails, it may try to rebind with any available server. When the lease expires, the client must stop using that address unless it obtains a valid lease.

## 5. DHCP reservation vs static addressing

- **Reservation:** the DHCP server consistently assigns a chosen address to a particular client identity.
- **Static configuration:** the address is manually configured on the device.

Reservations simplify central management. Static settings can be useful for infrastructure but must be planned to avoid address conflicts.

## 6. DHCP security risks

- **Rogue DHCP server:** an unauthorized server supplies malicious gateway or DNS settings.
- **DHCP starvation:** an attacker exhausts the available address pool.
- **Misconfiguration:** incorrect scopes or options disrupt connectivity.

Defences include DHCP snooping on supported switches, port security, trusted server ports, network segmentation, monitoring, and careful scope management.

## 7. Safe practical lab

Windows:

```powershell
ipconfig /all
ipconfig /release
ipconfig /renew
```

Use `/release` and `/renew` only on a network where you are authorized; this temporarily interrupts connectivity.

Linux:

```bash
ip address
ip route
```

Identify the assigned address, default gateway, and DNS servers.

## Key points

- DHCP automates host configuration.
- DHCPv4 commonly uses DORA and UDP 67/68.
- A lease is time-limited; reservations and static configuration are different.

## Related notes
- [[IPv4 Addressing]]
- [[Default Gateway]]
- [[DNS Protocol]]
- [[Network Devices]]

## 8. DHCP lease lifecycle

A lease is not a permanent ownership claim over an address. A client typically attempts renewal when the lease reaches its renewal time. If the original server cannot be contacted, the client may later attempt rebinding with any available DHCP server. When the lease expires without renewal, the client must stop using that address.

This lifecycle explains why a device can temporarily retain an address during a brief server outage, but may lose connectivity if the outage lasts too long.

## 9. DHCP options

DHCP does more than allocate an IP address. Options can provide the subnet mask, router, DNS servers, domain name, lease duration, and other configuration. A wrong router option can send traffic to the wrong gateway; a malicious DNS option can redirect name resolution.

## 10. DHCP relay

Routers do not normally forward local broadcast packets unchanged. A DHCP relay receives client broadcasts and forwards the requests to a configured DHCP server on another network. This permits a central DHCP service to serve multiple routed subnets.

## Practical activity — inspect your lease

Run `ipconfig /all` on Windows. Identify the DHCP server, lease obtained time, lease expiry time, default gateway, and DNS servers. Do not publish your full output because it may reveal internal network details.

## My understanding

Explain why a DHCP server on another subnet generally needs a relay agent, and describe what could happen if an unauthorized DHCP server supplied a false gateway.
