# DNS — Pi-hole

## Setup

- IP: 192.168.8.2
- Admin: http://192.168.8.2/admin
- Upstream DNS: Cloudflare (1.1.1.1)
- Blocked domains: 84,752

## Configuration

The router does not support DHCP DNS override, so DNS is configured manually on each device.

## Authentication (Pi-hole v6)

Pi-hole v6 no longer uses an API key — it requires an app password.

Settings -> Web interface / API -> Configure app password

> Note: The Homepage widget requires `version: 6` in the configuration.

## Notes

- Comviq blocks some torrent domains at DNS level
- Fix: `chattr +i /etc/resolv.conf` prevents DHCP from overwriting DNS settings in the VM
