# Wireless Network Security

> Understand how to protect Wi-Fi networks and wireless clients.

## 1. Wireless LAN basics

Wi-Fi uses IEEE 802.11 standards. Wireless access points connect wireless clients to a LAN. Radio signals extend beyond physical walls, so access control and encryption are important.

## 2. Security modes

- **WPA2-Personal:** commonly uses a pre-shared passphrase with AES-CCMP.
- **WPA3-Personal:** uses SAE and improves resistance to offline password guessing.
- **WPA2/WPA3-Enterprise:** commonly uses 802.1X and an authentication server.

Avoid obsolete WEP and legacy WPA/TKIP configurations.

## 3. Common threats

- Weak or reused Wi-Fi passwords.
- Evil-twin access points impersonating legitimate networks.
- Rogue access points.
- Deauthentication disruption.
- Misconfigured guest networks.
- Unpatched access-point firmware.

## 4. Best practices

- Use WPA3 where compatible, otherwise WPA2-AES.
- Use strong unique credentials or enterprise authentication.
- Change default administrator credentials.
- Update access-point firmware.
- Separate guest and internal networks.
- Disable insecure legacy features.
- Monitor for rogue access points.
- Verify network identity before entering credentials.

Hiding an SSID or filtering by MAC address is not a meaningful substitute for encryption and authentication.

## 5. Safe practical review

On Windows:

```powershell
netsh wlan show interfaces
netsh wlan show profiles
```

Do not disclose saved Wi-Fi passwords or capture traffic from networks without permission.

## Key points

- Wireless signals can be received outside the intended room or building.
- Prefer WPA3 or WPA2-AES; avoid WEP and obsolete modes.
- Guest segmentation and firmware updates are important.

## Related notes
- [[Network Access Control]]
- [[Network Segmentation]]
- [[Network Security Best Practices]]
