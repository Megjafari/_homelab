# Homepage (LXC 103)

Dashboard for all homelab services.

## Info

| Key       | Value                    |
|-----------|--------------------------|
| Type      | LXC Container            |
| ID        | 103                      |
| IP        | 192.168.1.141            |
| Port      | 3000                     |
| Config    | /opt/homepage/config/    |
| Installed | community-script         |
| Service   | systemd (auto-start)     |

## services.yaml Structure

| Section   | Services                          |
|-----------|-----------------------------------|
| Media     | Jellyfin, Radarr, Sonarr, Prowlarr|
| Downloads | qBittorrent                       |
| Network   | Pi-hole, Proxmox                  |
| System    | CPU Temp, Disk SSD, Disk HDD (via Glances) |
| Developer | Coolify                           |

## widgets.yaml

- Glances CPU widget (Proxmox host, port 61208)

## API Keys

| Service     | Where to find the key                              |
|-------------|----------------------------------------------------|
| Jellyfin    | Dashboard -> API Keys                              |
| Radarr      | Settings -> General                                |
| Sonarr      | Settings -> General                                |
| Prowlarr    | Settings -> General                                |
| qBittorrent | username/password                                  |
| Pi-hole v6  | Settings -> Web interface / API -> app password    |
| Proxmox     | API token: root@pam!homepage                       |

## YAML Tips

YAML is extremely sensitive to indentation. Every level = 2 spaces.

```yaml
- Radarr:
    icon: radarr.png
    href: http://192.168.1.138:7878
    widget:
      type: radarr
      url: http://192.168.1.138:7878
      key: <api-key>
```

## Known Limitations

- Glances widgets in the topbar always show CPU+RAM regardless of the metric setting
- Workaround: one widget in topbar, the rest as service cards under the System section
