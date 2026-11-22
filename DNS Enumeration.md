> Collect publicly available DNS information for an explicitly authorized domain.

## 1. What is DNS enumeration?

DNS enumeration is the process of identifying DNS records, name servers, mail servers, and related hostname information for a domain. It is used in administration, asset inventory, and authorized security assessments.

## 2. Common record queries

```bash
dig example.com A
dig example.com AAAA
dig example.com MX
dig example.com NS
dig example.com TXT
dig example.com SOA
```

Windows:

```powershell
Resolve-DnsName example.com
Resolve-DnsName -Type MX example.com
Resolve-DnsName -Type TXT example.com
```

## 3. Reverse lookup

A PTR query can map an IP address to a hostname when reverse DNS is configured:

```bash
dig -x 192.0.2.10
```

Reverse DNS is not guaranteed to exist or match the forward record.

## 4. Zone transfers

A DNS zone transfer replicates zone data between authorized DNS servers. An improperly exposed transfer may disclose hostnames and infrastructure details.

Do not attempt zone transfers against domains without explicit authorization. In an owned lab, configure a DNS server and verify that transfers are restricted to approved secondary servers.

## 5. Subdomain discovery

Subdomains may be found through certificate transparency, public datasets, DNS records, and approved wordlist-based checks. Results can be stale or point to third-party infrastructure. Verify ownership before testing.

## 6. Reporting

Record the domain, query type, time, resolver, response, TTL, and source. Distinguish confirmed DNS records from inferred or historical hostnames.

## Key points

- DNS enumeration collects records and hostnames.
- A DNS answer does not prove that a host is active or owned by the target.
- Restrict testing to authorized domains and infrastructure.

## Related notes
- [[DNS Protocol]]
- [[Domain Name System]]
- [[Nmap]]
- [[Network Security Labs]]

## 7. Enumeration versus vulnerability testing

DNS enumeration gathers information; it does not prove a weakness. Finding a subdomain does not authorize testing it, and a DNS record may point to a third-party provider. Confirm scope and ownership before performing port scans or application tests.

## 8. Common findings

An MX record reveals mail-routing infrastructure. NS records identify authoritative DNS providers. TXT records may reveal domain verification strings or email security policies. A and AAAA records identify IPv4 and IPv6 destinations. Historical or passive datasets may contain stale entries.

## 9. Documentation

For each finding, record the query, timestamp, resolver, response, and whether the result was authoritative or cached where known. Mark uncertain or historical results clearly. Avoid publishing internal hostnames or sensitive infrastructure details without permission.

## Practical activity

For `example.com`, query A, AAAA, MX, NS, and TXT records. Create a table describing what each record type reveals and what it does not prove.

## My understanding

Explain why a discovered hostname is an information-gathering result rather than proof that the host is live, vulnerable, or in scope.
