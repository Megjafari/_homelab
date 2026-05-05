# Lessons Learned

Mistakes made and lessons learned while building the homelab.

---

## IPTV in Jellyfin

**Mistake:** Added a large M3U IPTV list directly to Jellyfin.

**What happened:** EPG indexing filled the entire VM disk (38GB in 9 hours). jellyfin.db-wal grew to 6.4GB and corrupted the database. Had to delete the entire Jellyfin config and start over.

**Lesson:** Use OTT Navigator or TiviMate for IPTV — not Jellyfin.

---

## qBittorrent Download Path

**Mistake:** Default Save Path was /downloads (inside the container) but Radarr/Sonarr expected /media/downloads.

**What happened:** Files ended up in the wrong place. Duplicates appeared in Jellyfin.

**Lesson:** Always set Default Save Path to /media/downloads immediately after installing qBittorrent.

---

## Jellyfin Library Paths

**Mistake:** Added /media as the music library root.

**What happened:** Jellyfin scanned the entire media folder including downloads. Duplicates and mixed catalogs.

**Lesson:** Always use specific paths — Movies: /media/movies, Shows: /media/series, Music: /media/music

---

## NFS and Media Storage

**Mistake:** Assumed /media in the VM pointed to the HDD.

**What happened:** The VM's 40GB OS disk filled up quickly with downloaded movies.

**Lesson:** Plan storage before installation. VMs do not automatically share Proxmox disks — NFS must be set up explicitly.

---

## Torrent Trackers and DNS

**Mistake:** TorrentGalaxy indexer failed in Prowlarr due to SSL/DNS issues.

**Cause:** Comviq blocks some torrent domains at DNS level.

**Fix:** `chattr +i /etc/resolv.conf` prevents DHCP from overwriting DNS settings in the VM.

---

## docker system prune -af

**Mistake:** Ran `docker system prune -af` while the Jellyfin container was stopped.

**What happened:** Permanently deleted the Jellyfin image.

**Lesson:** Use `docker system prune` without `-a` to only remove unused resources.

---

## Homarr v1

**Mistake:** Community script installed Homarr but env variables were missing (SECRET_ENCRYPTION_KEY, URL).

**What happened:** Unstable installation. Proxmox integration crashed everything.

**Lesson:** Switch to Homepage — better documented and more stable.

---

## Dashdot

**Mistake:** Installed Dashdot as a dashboard.

**What happened:** Requires real hardware, does not work in a virtualized environment. Showed "Invalid or incomplete static data loaded".

**Lesson:** Use Homepage + Glances instead.

---

## Pi-hole v6 API

**Mistake:** Tried to use an API key with Pi-hole v6.

**What happened:** v6 no longer uses API keys.

**Fix:** Settings -> Web interface / API -> Configure app password. Homepage widget requires `version: 6`.

---

## Proxmox SSL Certificate

**Mistake:** Proxmox uses a self-signed certificate.

**What happened:** SSL errors in Homepage and Homarr (write EPROTO SSL routines wrong version number).

**Fix:** Manually trust the certificate in the browser.

---

## qBittorrent WebUI Blocking Homepage

**Cause:** The WebUI rejected requests from a different subnet.

**Fix:** qBittorrent -> Options -> Web UI -> whitelist 192.168.1.0/24

---

## YAML Indentation in Homepage

**Mistake:** Radarr, Sonarr, Prowlarr widgets showed no data.

**Cause:** type, url, and key were missing the correct 2-space indentation under the widget block.

**Lesson:** YAML is extremely sensitive to indentation. Always use 2 spaces per level, never tabs.

---

## Glances Widget in Homepage Topbar

**Observation:** Glances widgets in the topbar always show CPU+RAM regardless of the metric setting.

**Workaround:** One widget in the topbar, the rest as service cards under the System section. This is a Homepage limitation.

---

## What Was Difficult

- YAML indentation
- Understanding the practical difference between LXC and VM
- NFS mount disappearing
- Pi-hole v6 API authentication
- Proxmox SSL certificates and API tokens
- Homarr v1 being unstable and poorly documented
- Finding config files across different machines
- SSH root access on new machines
