> Understand how domain names are translated into information such as IP addresses.

## 1. What is DNS?

**DNS (Domain Name System)** is a distributed naming system. It allows users and applications to use names such as `example.com` instead of remembering IP addresses.

DNS is often described as the Internet's phonebook, but it stores several kinds of records, not just address mappings.

## 2. How name resolution works

1. An application asks the operating system to resolve a hostname.
2. The system checks local sources such as its cache and hosts file.
3. If needed, a recursive resolver is queried.
4. The resolver may contact root, top-level-domain (TLD), and authoritative name servers.
5. The answer is returned and may be cached for its Time to Live (TTL).

A recursive resolver performs the lookup on behalf of the client. An authoritative server holds the definitive records for a DNS zone.

## 3. Common DNS record types

| Record | Purpose |
|---|---|
| A | Maps a name to an IPv4 address |
| AAAA | Maps a name to an IPv6 address |
| CNAME | Alias from one name to another |
| MX | Mail exchanger for a domain |
| NS | Name servers for a zone |
| TXT | Text data, often used for verification and email security |
| PTR | Reverse lookup, address to name |
| SOA | Start-of-authority information for a zone |
| SRV | Identifies a service host and port |

## 4. Ports and transport

Traditional DNS usually uses port **53** over UDP for ordinary queries. TCP port **53** is also used, including for zone transfers and responses that require TCP. DNS over TLS commonly uses TCP 853; DNS over HTTPS commonly uses HTTPS on TCP 443.

## 5. DNS caching and TTL

A resolver caches answers for the record's TTL. Caching reduces lookup delay and traffic. A cached answer can remain available until its TTL expires, even after a record is changed.

## 6. Security concerns

- **DNS spoofing/cache poisoning:** misleading DNS data causes a client to reach an unintended address.
- **DNS tunnelling:** DNS queries or responses are abused to carry data.
- **Zone-transfer exposure:** a misconfigured server may disclose zone contents.
- **DDoS amplification:** poorly controlled DNS infrastructure can be abused in reflection attacks.

Defences include restricting zone transfers, patching DNS software, monitoring unusual query patterns, using trusted resolvers, and deploying DNSSEC where appropriate. DNSSEC provides data-origin authentication and integrity for signed DNS data; it does not encrypt DNS queries.

## 7. Safe practical lab

Windows:

```powershell
nslookup example.com
nslookup -type=MX example.com
Resolve-DnsName example.com
```

Linux/Kali:

```bash
dig example.com
dig MX example.com
dig +short A example.com
```

Record the queried name, record type, answer, and TTL. Query only domains you are permitted to investigate.

## Key points

- DNS translates names into records such as IP addresses.
- UDP and TCP port 53 are both important.
- DNSSEC protects the authenticity and integrity of signed DNS data, not query confidentiality.

## Related notes
- [[Introduction to Network Protocols]]
- [[IPv4 Addressing]]
- [[IPv6 Addressing]]
- [[DHCP Protocol]]
- [[DNS Enumeration]]

---