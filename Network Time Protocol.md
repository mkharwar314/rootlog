# Network Time Protocol

> Understand how systems synchronize their clocks across networks.

## 1. What is NTP?

**Network Time Protocol (NTP)** synchronizes clocks of computers and network devices. Accurate time is essential for log correlation, authentication, certificates, incident response, and distributed systems.

NTP commonly uses UDP port **123**.

## 2. How synchronization works

An NTP client exchanges timestamps with a time server and estimates network delay and clock offset. Systems may use multiple time sources and select reliable sources according to NTP algorithms and configuration.

## 3. Stratum levels

Stratum describes distance from a reference clock:
- Stratum 0: reference clocks such as GPS or atomic clocks (not ordinary network servers).
- Stratum 1: servers directly connected to reference clocks.
- Higher strata: servers synchronized from lower-stratum servers.

A lower stratum is not automatically more accurate in every circumstance.

## 4. Security and reliability

Use trusted time sources, restrict who can query or administer time services as appropriate, monitor time drift, and keep time-service software updated. Incorrect time can undermine log timelines and certificate validation.

## 5. Practical checks

Windows:

```powershell
w32tm /query /status
w32tm /query /source
```

Linux:

```bash
timedatectl
```

## Key points

- NTP commonly uses UDP 123.
- Reliable time is critical for security logs and authentication.
- Stratum indicates hierarchy, not a simple guarantee of accuracy.

## Related notes
- [[Common Network Ports]]
- [[Windows Event Logs]]
- [[Digital Forensics]]
