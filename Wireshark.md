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

## 7. Capture filters and display filters

Capture filters use a syntax designed to decide which packets are saved. Display filters use Wireshark's protocol-aware syntax to select packets from a capture already loaded. A capture filter that is too restrictive can permanently omit evidence; a display filter can be changed later without altering the original capture.

## 8. Reading packet layers

Select a packet and expand the protocol tree. For an ordinary TCP web connection, you may see Ethernet, IP, TCP, and TLS or HTTP layers. Each layer adds information needed by the next layer. Compare the packet details with the raw bytes to understand that Wireshark is decoding the original captured data.

## 9. Common limitations

A local capture may miss traffic that does not traverse the selected interface. Hardware offloading can affect how packets appear. Encrypted application data is not normally readable. Packet timestamps depend on the capture system's clock.

## Practical activity — TCP handshake

Capture a connection to a test site and apply `tcp.flags.syn == 1`. Find the initial SYN and, if visible, the SYN-ACK and ACK. Record source/destination addresses and ports. Explain which side initiated the connection.

## My understanding

Explain the difference between a capture filter and a display filter, and why encrypted HTTPS traffic can still reveal some connection metadata.
