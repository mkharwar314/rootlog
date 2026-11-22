> A service-level view of DHCP scopes, options, leases, and administration.

## 1. DHCP server responsibilities

A DHCP server manages address pools (scopes) and supplies clients with configuration. Common options include subnet mask, default gateway, DNS servers, domain search information, and lease time.

## 2. Scope planning

A well-designed scope should:
- Match the subnet and address plan.
- Exclude addresses used by infrastructure or static devices.
- Avoid overlapping pools.
- Define suitable lease durations.
- Provide correct gateway and DNS options.
- Have capacity for expected growth.

## 3. Relay agents

DHCP broadcasts normally remain within a local broadcast domain. A DHCP relay agent forwards client requests to a DHCP server on another network, allowing centralized DHCP service across multiple subnets.

## 4. Reservations and exclusions

A reservation associates a predictable lease with a client identifier. An exclusion prevents the server from leasing a specified range. These mechanisms help avoid conflicts with manually configured infrastructure addresses.

## 5. Security and availability

Use DHCP snooping where supported, trusted relay/server paths, monitoring, backups, and redundant server design. Rogue servers can redirect clients by supplying malicious gateway or DNS settings.

## 6. Client-side checks

Windows:

```powershell
ipconfig /all
ipconfig /renew
```

Linux:

```bash
ip address
ip route
```

## Key points

- A DHCP scope defines the address pool and options for a subnet.
- Relay agents forward DHCP requests across routed networks.
- Reservations and exclusions help manage address allocation.

## Related notes
- [[DHCP Protocol]]
- [[IPv4 Addressing]]
- [[Default Gateway]]
- [[Network Services]]

## 6. Address-pool planning example

Suppose a lab subnet is `192.168.10.0/24`. The network and broadcast addresses are not normally leased to hosts. An administrator might reserve low addresses for routers and infrastructure, then define a DHCP pool for client devices. The exact range should be documented and checked against static addresses to prevent conflicts.

## 7. Failover and availability

A DHCP outage may not immediately disconnect clients with valid leases, but new devices may fail to obtain configuration and existing clients may eventually lose their leases. Redundant DHCP servers or failover arrangements reduce this risk. The design must avoid two independent servers leasing overlapping addresses without coordination.

## 8. DHCP security

DHCP snooping on supported switches can distinguish trusted server-facing ports from untrusted access ports and block unauthorized DHCP server messages. It can also build bindings used by other protections. Correct switch configuration is essential; an incorrectly trusted port can defeat the control.

## Practical activity

Create a small address plan for a `/24` lab network. Mark the gateway, infrastructure reservations, DHCP pool, and excluded addresses. Check that no ranges overlap.

## My understanding

Explain how a DHCP scope, reservation, exclusion, and relay agent differ.
