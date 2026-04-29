# Pi-hole (LXC 100)

DNS-based ad blocker.

## Info

| Key              | Value                   |
|------------------|-------------------------|
| Type             | LXC Container           |
| ID               | 100                     |
| IP               | 192.168.8.2             |
| Admin            | http://192.168.8.2/admin|
| Upstream DNS     | Cloudflare 1.1.1.1      |
| Blocked domains  | 84,752                  |

## Authentication

Pi-hole v6 uses an app password instead of an API key.

Settings -> Web interface / API -> Configure app password

## Homepage Widget

```yaml
- Pi-hole:
    icon: pi-hole.png
    href: http://192.168.8.2/admin
    widget:
      type: pihole
      version: 6
      url: http://192.168.8.2
      key: <app-password>
```
