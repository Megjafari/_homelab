# Network

## IP Addresses

| Device/Service       | IP              |
|----------------------|-----------------|
| Router               | 192.168.8.1     |
| Proxmox              | 192.168.8.50    |
| Pi-hole              | 192.168.8.2     |
| Jellyfin VM          | 192.168.8.138   |
| Homepage LXC         | 192.168.8.141   |
| Coolify VM           | 192.168.8.142   |
| Tailscale (Proxmox)  | 100.71.217.116  |

## Tailscale

Private VPN network for secure remote access to internal services.

- Installed on: Proxmox host
- Planned: Homepage LXC, Coolify VM, and T14
- Used for remote access to Radarr, Sonarr, qBittorrent

## Cloudflare Tunnel

Jellyfin is publicly accessible via Cloudflare Tunnel without exposing the home network.

- Domain: meghdadjafari.dev (Namecheap, DNS via Cloudflare)
- Tunnel name: homelab (cloudflared service)
- Config: /etc/cloudflared/config.yml
- Public URL: https://jellyfin.meghdadjafari.dev

## DNS

See [dns.md](dns.md) for Pi-hole configuration.
