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

## Additional lab — compare port states

On your own isolated lab VM, scan one port known to be listening and one port where no service is configured:

```bash
nmap -sT -p 22,65000 <lab-target-ip>
```

Compare the reported states. A firewall may cause a port to appear filtered, so results depend on network policy as well as the target's local service state.

## Additional lab — save evidence

Use `-oN` to save normal output and record the exact command used. Do not edit the original scan output; make a separate working copy for annotations.

## Reporting checklist

Include authorization, target scope, scan time, Nmap version, options, port state, service/version result, validation, and limitations. Avoid claiming that a service is vulnerable based only on its banner.

## My understanding

Explain how you would validate an unexpected open port without immediately running intrusive scripts or exploiting the service.
