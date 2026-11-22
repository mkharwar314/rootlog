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

## 6. Proxy authentication and policy

An enterprise forward proxy may authenticate users or devices and apply category, destination, or data-loss policies. It can log requested destinations and block prohibited traffic. These controls should be transparent to users through documented policies and privacy safeguards.

## 7. Reverse-proxy deployment

A reverse proxy may terminate TLS, inspect requests, apply rate limits, and distribute traffic across backend servers. If the backend trusts forwarding headers from arbitrary clients, an attacker may spoof the original client IP or scheme. The proxy should remove untrusted incoming forwarding headers and set its own trusted values.

## 8. Proxy troubleshooting

Check whether the client is configured to use a proxy, whether proxy DNS resolution is working, whether authentication is required, and whether the proxy can reach the destination. A browser may use different proxy settings from system services.

## Practical activity

Inspect WinHTTP proxy settings with `netsh winhttp show proxy`. Compare the output with your browser's proxy configuration and explain why they may differ.

## My understanding

Draw a forward-proxy flow and a reverse-proxy flow. Label which side of the connection each proxy represents.
