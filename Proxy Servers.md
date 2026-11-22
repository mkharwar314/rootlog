# Proxy Servers

> Understand how proxy systems mediate traffic between clients and destinations.

## 1. Forward proxy

A forward proxy acts on behalf of clients. It can enforce browsing policy, filter requests, cache content, or centralize outbound access.

## 2. Reverse proxy

A reverse proxy acts on behalf of servers. It accepts client requests and forwards them to backend systems. Common uses include load balancing, TLS termination, caching, and application-layer filtering.

## 3. Transparent and explicit proxies

- **Explicit proxy:** the client is configured to use the proxy.
- **Transparent/intercepting proxy:** traffic is redirected or intercepted by network infrastructure, often without per-client proxy configuration.

The exact meaning of transparent varies by deployment.

## 4. Security and privacy considerations

A proxy may see metadata and, depending on TLS configuration, application content. TLS interception requires careful certificate management and creates significant trust and privacy implications. Proxies can also become bottlenecks or single points of failure.

## 5. Practical checks

Review proxy settings on your own device:

```powershell
netsh winhttp show proxy
```

Browser proxy settings may be managed separately from WinHTTP settings.

## Key points

- Forward proxies mediate client traffic.
- Reverse proxies mediate access to backend services.
- A proxy changes traffic flow but does not automatically make it secure or anonymous.

## Related notes
- [[Web Servers]]
- [[VPN]]
- [[HTTP and HTTPS]]
- [[Network Security Best Practices]]
