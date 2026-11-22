> Understand how Network Address Translation changes IP address information as packets cross a network boundary.

## 1. What is NAT?

**Network Address Translation (NAT)** modifies IP address information in packet headers. It is commonly used at network boundaries to connect private IPv4 networks to public networks.

NAT is not the same thing as a firewall, although both functions may exist on the same device.

## 2. Common forms

- **Static NAT:** fixed one-to-one mapping between an internal and external address.
- **Dynamic NAT:** maps internal addresses from a pool of external addresses.
- **PAT/NAPT (often called NAT overload):** multiple internal devices share one public IPv4 address using transport-layer port numbers.

## 3. Example of PAT

Several private devices may access the Internet through one public IPv4 address. The NAT device tracks connection mappings so return traffic can be delivered to the correct internal device.

## 4. Port forwarding

Port forwarding maps traffic arriving at a public address and port to a selected internal host and port. It can expose an internal service to external networks, so it must be tightly controlled.

## 5. NAT and IPv6

IPv6 has a vastly larger address space and generally does not require NAT for address conservation. Firewalls still provide access control. NAT66 exists in some environments but is not a substitute for sound IPv6 network design.

## 6. Security considerations

NAT can hide internal addressing from external observers, but it does not provide complete security. Use stateful firewall policies, expose only necessary services, patch systems, and review forwarding rules.

## Key points

- NAT translates addressing information.
- PAT allows multiple internal devices to share an external IPv4 address.
- NAT is not a replacement for a firewall.

## Related notes
- [[IPv4 Addressing]]
- [[Firewalls]]
- [[Network Segmentation]]
- [[Packet Forwarding]]

## 7. How PAT tracks connections

When an internal host initiates a connection, the NAT device creates a translation entry that associates the internal address and source port with an external address and translated port. Return packets can then be mapped back to the correct internal host. The mapping is stateful and normally expires after inactivity.

## 8. NAT and inbound reachability

An internal host using a private address is not automatically reachable from the Internet. Port forwarding or another explicit mapping may be required. Exposing an internal service through port forwarding increases its attack surface and should be paired with authentication, patching, logging, and source restrictions where possible.

## 9. Troubleshooting NAT

Check the internal host's gateway, the NAT device's translation state, outbound firewall policy, port-forwarding rules, and the return route. A successful outbound connection does not prove that unsolicited inbound traffic can reach the host.

## Practical activity

Draw a packet flow from a private host to a public web server. Label the source/destination IP before NAT and the translated source address after PAT. Then show how the return packet is mapped to the internal host.

## My understanding

Explain the difference between routing, NAT, and firewall filtering. Give an example where a device performs all three functions.
