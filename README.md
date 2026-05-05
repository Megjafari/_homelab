# Homelab 

Personal homelab running on a ThinkPad T430s with Proxmox VE 8.4.

## Quick Links

- [Hardware](hardware/README.md)
- [Network](network/README.md)
- [Proxmox](proxmox/README.md)
- [Services](services/README.md)
- [Storage](storage/README.md)
- [Runbooks](runbooks/)
- [Lessons Learned](lessons-learned.md)

## Addresses & Ports

| Service      | Local URL                         | Public / Tailscale URL                 |
|--------------|-----------------------------------|----------------------------------------|
| Proxmox      | https://192.168.1.50:8006         | —                                      |
| Pi-hole      | http://192.168.1.2/admin          | —                                      |
| Jellyfin     | http://192.168.1.138:8096         | https://jellyfin.meghdadjafari.dev     |
| Homepage     | http://192.168.1.141:3000         | —                                      |
| Coolify      | http://192.168.1.142:8000         | —                                      |
| Radarr       | http://192.168.1.138:7878         | http://100.64.0.1:7878 (Tailscale) |
| Sonarr       | http://192.168.1.138:8989         | http://100.64.0.1:8989 (Tailscale) |
| Prowlarr     | http://192.168.1.138:9696         | http://100.64.0.1:9696 (Tailscale) |
| qBittorrent  | http://192.168.1.138:8080         | http://100.64.0.1:8080 (Tailscale) |
| Glances      | http://192.168.1.50:61208         | —                                      |
