# Nmap Labs

> Learn basic host discovery and port scanning against your own lab systems.

## Authorization

Only scan systems you own or have explicit permission to assess. Keep the target scope small and documented.

## Lab 1 — Identify your lab IP range

On Windows:

```powershell
ipconfig
```

On Kali:

```bash
ip address
ip route
```

Determine the lab subnet from the address and prefix. Do not assume it is the same as the example range below.

## Lab 2 — Discover hosts

```bash
nmap -sn 192.168.56.0/24
```

Replace the range with your own isolated lab subnet.

## Lab 3 — Scan selected ports on your own VM

```bash
nmap -p 22,80,443 <lab-target-ip>
```

## Lab 4 — Identify service versions

```bash
nmap -sV -p 22,80,443 <lab-target-ip>
```

## Lab 5 — Save results

```bash
nmap -oN nmap-lab-results.txt <lab-target-ip>
```

## Report

Record scope, target, command, date/time, discovered hosts, port states, service guesses, and limitations. An open port is not proof of a vulnerability.
