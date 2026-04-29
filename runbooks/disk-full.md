# Runbook: SSD Is Full

## Symptoms

- VMs or LXCs fail to start
- `df -h` shows 100% on the Proxmox host
- Files ended up on the SSD instead of the HDD

## Check What's Taking Space

```bash
df -h
du -sh /mnt/*
docker system df
```

## Common Cause

Radarr/Sonarr has the wrong import path — files get downloaded to the SSD instead of the HDD.

**Fix in Radarr/Sonarr:** Settings -> Media Management -> Root Folders -> must point to /media/movies or /media/series (the NFS disk).

## Clean Up Docker

```bash
# Safe — only removes unused resources
docker system prune

# NEVER run this when containers are stopped:
# docker system prune -af  <-- removes ALL images
```
