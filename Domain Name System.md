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

## 6. Delegation and zone boundaries

A parent zone can delegate a subdomain to a different set of authoritative servers. This lets separate teams or providers administer different parts of a namespace. Delegation records in the parent zone point resolvers toward the child zone's name servers.

## 7. Primary and secondary servers

A primary (or source) server is where zone changes are maintained in a traditional primary/secondary model. Secondary servers obtain zone data through transfers and provide authoritative answers as well. Modern DNS hosting can use different management models, but redundancy remains important.

## 8. Operational failure scenarios

A stale A record can direct users to an old host. Incorrect MX records can interrupt email delivery. Missing glue records in certain delegation arrangements can prevent resolvers from locating authoritative servers. Incorrect TTL expectations can make changes appear inconsistent while cached answers remain valid.

## Practical activity

Query `NS`, `SOA`, and `A` records for a test domain. Explain which records identify the authoritative name servers, which provide zone metadata, and which map a host to an IPv4 address.

## My understanding

Draw the DNS hierarchy from root to TLD to authoritative zone. Explain how delegation differs from a simple CNAME alias.
