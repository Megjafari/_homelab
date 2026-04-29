# Runbook: NFS Mount Lost

## Symptoms

- Jellyfin shows no files
- Radarr/Sonarr marks files as "missing"
- `df -h /media` shows wrong size or missing mount

## Fix

```bash
ssh meg@192.168.8.138
sudo su

# Remount all fstab entries
mount -a

# Or manually:
mount -t nfs 192.168.8.50:/mnt/media /media

# Verify
df -h /media

# Restart Docker stack
cd /opt/media
docker compose restart
```

Then: Jellyfin -> Libraries -> Scan Library

## Permanent Fix 

Added to /etc/fstab on the Jellyfin VM so the mount survives reboots:

```
192.168.8.50:/mnt/media  /media  nfs  defaults  0  0
```
