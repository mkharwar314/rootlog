> Understand how Virtual LANs logically separate devices on switched networks.

## 1. What is a VLAN?

A **Virtual Local Area Network (VLAN)** creates a logical Layer 2 broadcast domain within a switched network. Devices can be grouped by role, department, or security requirement without needing separate physical switches for every group.

## 2. Access and trunk ports

- **Access port:** normally carries traffic for one VLAN and connects to an end device.
- **Trunk port:** carries traffic for multiple VLANs between network devices, commonly using IEEE 802.1Q tags.

An 802.1Q tag identifies the VLAN associated with an Ethernet frame on a trunk. Native VLAN handling is platform/configuration-dependent and should be consistent.

## 3. Inter-VLAN routing

Devices in different VLANs generally need a Layer 3 device to communicate. This may be a router or a Layer 3 switch. Access-control lists or firewall rules can control which VLANs may communicate.

## 4. Benefits

- Limits broadcast scope.
- Supports logical separation.
- Helps apply different policies to different device groups.
- Can improve network organization.

A VLAN alone is not a complete security boundary. Misconfiguration or permissive inter-VLAN routing can undermine separation.

## 5. Security practices

Use deliberate VLAN assignments, restrict trunk VLAN lists, disable unused ports, avoid unnecessary native-VLAN use, and enforce inter-VLAN access policies. Monitor for unexpected VLAN changes.

## Key points

- VLANs create logical Layer 2 broadcast domains.
- Access ports typically carry one VLAN; trunks carry multiple VLANs.
- Inter-VLAN communication requires Layer 3 routing and should be controlled.

## Related notes
- [[Introduction to Switching]]
- [[Network Segmentation]]
- [[NAT]]
- [[Network Access Control]]

## 6. VLAN tagging

IEEE 802.1Q inserts a VLAN tag into an Ethernet frame on a trunk link. The tag includes a VLAN identifier (VID). The receiving switch uses this information to keep traffic associated with the correct VLAN. Frames on an access link are commonly sent untagged to the end device.

## 7. VLAN design example

A small lab might use VLAN 10 for workstations, VLAN 20 for servers, and VLAN 30 for guests. A Layer 3 switch or router provides gateways for these networks. Firewall or ACL rules can allow workstations to reach approved server ports while preventing guest devices from accessing internal management systems.

## 8. Common misconfigurations

- An access port assigned to the wrong VLAN.
- A trunk allowing more VLANs than required.
- Mismatched native VLAN settings.
- An overly permissive inter-VLAN routing policy.
- Management interfaces exposed to ordinary user networks.

## Practical activity

Create a small topology diagram with two access switches and one trunk. Label the VLANs allowed on the trunk. Write down which devices should communicate and which flows should be denied.

## My understanding

Explain why two devices in different VLANs normally cannot communicate directly at Layer 2 and what component enables controlled communication between them.
