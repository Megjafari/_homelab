# Storage

## Overview

| Disk          | Size  | Purpose                   |
|---------------|-------|---------------------------|
| mSATA SSD     | 256GB | Proxmox, VMs, LXCs        |
| HDD (UltraBay)| 500GB | Media storage via NFS     |

> SSD is almost full — 3.7GB remaining (April 2026). All media must go on the HDD.

## NFS

Proxmox shares the HDD with the Jellyfin VM via NFS.

| Host (Proxmox) | VM (Jellyfin) |
|----------------|---------------|
| /mnt/media     | /media        |

### Media Structure

```
/media/
├── movies/
├── series/
├── music/
└── downloads/
```

### Temporary Mount

```bash
mount -t nfs 192.168.8.50:/mnt/media /media
```

### Permanent Mount

Add to /etc/fstab on the Jellyfin VM:

```
192.168.8.50:/mnt/media  /media  nfs  defaults,_netdev,auto  0  0
```

## Check Disk Usage

```bash
df -h /          # OS disk
df -h /media     # NFS/media disk
docker system df # Docker disk usage
```
