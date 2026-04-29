# Jellyfin VM (VM 101)

Media server with full automation stack via Docker Compose.

## Info

| Key        | Value                              |
|------------|------------------------------------|
| Type       | VM (Debian 13)                     |
| ID         | 101                                |
| IP         | 192.168.8.138                      |
| CPU        | 2 cores                            |
| RAM        | 4GB                                |
| OS disk    | 40GB                               |
| Public URL | https://jellyfin.meghdadjafari.dev |

## SSH

```bash
ssh meg@192.168.8.138
sudo su
```

## Docker Stack

File: /opt/media/docker-compose.yml

| Service      | Port       | Purpose          |
|--------------|------------|------------------|
| Jellyfin     | 8096       | Media server     |
| qBittorrent  | 8080, 6881 | Torrent client   |
| Radarr       | 7878       | Movie automation |
| Sonarr       | 8989       | Show automation  |
| Prowlarr     | 9696       | Indexer manager  |

## Volumes

| Container path | Host path                      |
|----------------|--------------------------------|
| /config        | /opt/media/\<service\>/config  |
| /media         | /media (NFS mount from Proxmox)|
| /downloads     | /media/downloads               |

## Common Commands

```bash
cd /opt/media

docker compose up -d       # Start all containers
docker compose down        # Stop all containers
docker ps                  # List running containers
docker logs <container>    # View logs
docker system df           # Docker disk usage
```

## NFS Mount

Proxmox shares /mnt/media — VM mounts it as /media.

```bash
# If mount is lost:
mount -t nfs 192.168.8.50:/mnt/media /media

# Check status:
df -h /media
```

## Library Structure

```
/media/
├── movies/
├── series/
├── music/
└── downloads/
```

> Always use specific paths in Jellyfin — never /media as root.

## Cloudflare Tunnel

- Service: cloudflared
- Config: /etc/cloudflared/config.yml
- Tunnel: homelab -> jellyfin.meghdadjafari.dev
