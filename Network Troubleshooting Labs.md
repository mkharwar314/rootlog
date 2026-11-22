> Apply a structured method to diagnose common connectivity problems.

## Troubleshooting sequence

1. Check physical or virtual link state.
2. Check IP address and prefix.
3. Check default gateway.
4. Check DNS resolution.
5. Check route to destination.
6. Check firewall policy.
7. Check whether the target service is listening.

## Lab 1 — Local configuration

Run `ipconfig /all` on Windows or `ip address` and `ip route` on Linux. Identify address, prefix, gateway, and DNS.

## Lab 2 — Gateway reachability

```powershell
ping <gateway-ip>
```

or:

```bash
ping -c 4 <gateway-ip>
```

If no reply, consider ICMP filtering before concluding the gateway is down.

## Lab 3 — DNS failure vs connectivity failure

```powershell
Resolve-DnsName example.com
ping 1.1.1.1
```

If IP connectivity works but name resolution fails, investigate DNS. Ping to a public IP may itself be filtered, so use multiple tests.

## Lab 4 — Route inspection

Windows:

```powershell
tracert example.com
route print
```

Linux:

```bash
tracepath example.com
ip route
```

## Lab 5 — Service availability

For a permitted web service:

```powershell
Test-NetConnection example.com -Port 443
```

## Lab report

For each test, write the hypothesis, command, result, interpretation, next test, and final conclusion. Change one variable at a time.

## Additional lab — distinguish DNS from HTTPS failure

First resolve the hostname:

```powershell
Resolve-DnsName example.com
```

Then test the TCP service:

```powershell
Test-NetConnection example.com -Port 443
```

Finally inspect the HTTP response:

```powershell
curl.exe -I https://example.com
```

These tests examine different stages. A DNS answer does not prove TCP connectivity; a successful TCP connection does not prove that the web application returns a valid response.

## Incident-style record

For one failure, write a timeline of tests and results. State which layer appears to be working, where the failure occurs, and what additional evidence is required before concluding root cause.

## My understanding

Explain why troubleshooting should proceed from interface configuration through routing and DNS to the application layer.
