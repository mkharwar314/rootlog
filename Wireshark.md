# Wireshark

> Use Wireshark to capture and inspect network packets in an authorized lab.

## 1. What is Wireshark?

Wireshark is a network protocol analyzer. It captures packets from selected interfaces or opens saved capture files, then decodes supported protocols for inspection.

## 2. Main interface areas

- **Packet list:** one row per packet.
- **Packet details:** decoded protocol layers for the selected packet.
- **Packet bytes:** raw packet bytes in hexadecimal and ASCII.
- **Display filter bar:** filters packets currently displayed.

## 3. Useful display filters

```text
ip
ipv6
dns
tcp
udp
icmp
http
tls
ip.addr == 192.168.1.10
tcp.port == 443
dns.qry.name contains "example"
```

Display filters are not the same as capture filters.

## 4. Basic workflow

1. Open Wireshark.
2. Select an interface you are authorized to monitor.
3. Start capture.
4. Generate a small amount of test traffic, such as visiting a test page or running a DNS lookup.
5. Stop capture.
6. Apply a display filter.
7. Inspect packet details and record observations.

## 5. Follow a stream

For supported TCP traffic, use **Follow → TCP Stream** to view reconstructed stream data. HTTPS application content is encrypted unless you have appropriate authorized decryption material; packet metadata may still be visible.

## 6. Security and evidence handling

Do not capture other people's traffic without permission. Save captures securely, limit access, document the interface and capture time, and hash evidence files when integrity matters.

## 7. Practical lab

Run:

```powershell
nslookup example.com
```

Capture on your own active interface and apply:

```text
dns
```

Identify the query, response, record type, and returned address. DNS over HTTPS or TLS may prevent ordinary DNS queries from appearing as readable DNS packets.

## Key points

- Wireshark decodes packet captures.
- Display filters narrow what is shown.
- Encrypted traffic limits application-content visibility.

## Related notes
- [[Introduction to Network Analysis]]
- [[Packet Analysis]]
- [[Network Monitoring]]
- [[DNS Protocol]]
