> Understand the principles used to protect network infrastructure, traffic, and services.

## 1. Definition

Network security is the combination of policies, architecture, controls, and monitoring used to protect networked systems and data against unauthorized access, misuse, disruption, or modification.

## 2. Security objectives

- **Confidentiality:** prevent unauthorized disclosure.
- **Integrity:** prevent or detect unauthorized changes.
- **Availability:** keep systems and services accessible.
- **Authentication:** verify identities.
- **Authorization:** determine permitted actions.
- **Accountability:** record actions so they can be reviewed.

## 3. Defence in depth

Use multiple complementary controls rather than relying on one product:
- Firewalls and network ACLs.
- Segmentation and least privilege.
- Secure protocols and encryption.
- Endpoint protection and patching.
- Authentication and access control.
- Logging, monitoring, and incident response.

## 4. Threats

Examples include phishing, malware, credential theft, denial of service, spoofing, man-in-the-middle attacks, lateral movement, and exploitation of exposed services.

## 5. Risk-based design

Identify assets, threats, vulnerabilities, likelihood, and impact. Prioritize controls based on risk and business requirements. No network can be made risk-free; the goal is to reduce risk to an acceptable level and detect failures quickly.

## 6. Practical review

For a small lab, draw the network, list devices and services, identify trust boundaries, and record which traffic should be allowed between each segment.

## Key points

- Network security protects confidentiality, integrity, and availability.
- Defence in depth combines technical and operational controls.
- Security design should be risk-based and monitored.

## Related notes
- [[Firewalls]]
- [[IDS and IPS]]
- [[Network Segmentation]]
- [[Network Security Best Practices]]

## 7. Security controls mapped to objectives

Encryption supports confidentiality, integrity checks help detect modification, authentication verifies identities, and authorization limits actions. Logging and monitoring support accountability and detection. Availability requires resilience, capacity planning, backups, and response procedures. No single control satisfies every objective.

## 8. Threat modelling a small network

Start by listing assets such as user laptops, servers, routers, and identity services. Identify trust boundaries and likely threats. For example, a compromised guest device should not be able to connect to a file server or management interface. Translate that threat into segmentation and firewall requirements.

## 9. Measuring security

Useful measures include the number of unnecessary exposed services, patch age, MFA coverage, time to detect suspicious activity, and time to recover from an incident. Metrics should guide action rather than become targets that encourage superficial compliance.

## Practical activity

Draw your own lab topology. Mark assets, trust boundaries, exposed services, and the controls protecting each boundary. Identify the single most important risk and justify your choice.

## My understanding

Choose one threat and explain how prevention, detection, containment, and recovery controls work together.
