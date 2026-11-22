# Domain Name System

> A service-level view of DNS: zones, delegation, caching, and operational roles.

## 1. DNS hierarchy

DNS is hierarchical:
- Root zone at the top.
- Top-level domains (TLDs), such as `.com` and `.org`.
- Registered domains and subdomains.
- Authoritative zones that publish records.

A domain name is not necessarily identical to a DNS zone; a zone can delegate part of its namespace to another set of name servers.

## 2. Resolver roles

- **Stub resolver:** client-side component that sends queries to a configured resolver.
- **Recursive resolver:** obtains an answer on behalf of a client and may cache it.
- **Authoritative name server:** answers from data for the zones it serves.

## 3. Zones and delegation

A zone contains DNS data and is served by authoritative name servers. NS records identify delegated name servers. SOA records contain zone-level administrative metadata.

Zone transfers replicate zone data between authorized DNS servers. They should be restricted to approved secondary servers.

## 4. Caching

TTL controls how long a record may be cached. Negative caching can also cache the fact that a name or record does not exist for a defined period.

## 5. Operational security

Use redundant authoritative servers, restrict zone transfers, monitor query patterns, maintain accurate records, and protect registrar and DNS-provider accounts with MFA. Consider DNSSEC for signed zones.

## 6. Practical commands

```powershell
Resolve-DnsName example.com
Resolve-DnsName -Type NS example.com
```

```bash
dig example.com
dig NS example.com
dig SOA example.com
```

## Key points

- DNS is hierarchical and distributed.
- Recursive resolvers and authoritative servers have different roles.
- DNSSEC validates signed DNS data; it does not encrypt queries.

## Related notes
- [[DNS Protocol]]
- [[DNS Enumeration]]
- [[Network Services]]
