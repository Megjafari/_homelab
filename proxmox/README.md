# Proxmox VE

## Info

| Key    | Value           |
|--------|-----------------|
| Version | 8.4.19         |
| Kernel | 6.8.12-20-pve   |
| Node   | pve             |
| IP     | 192.168.8.50:8006 |

## Setup

- Installed on mSATA SSD
- Enterprise repo replaced with free no-subscription repo
- VMs and LXCs managed via web UI and CLI

## API Token (Homepage)

Token: root@pam!homepage

Created for Homepage integration. Used in services.yaml.

## Glances

System monitoring installed directly on the Proxmox host.

- Port: 61208
- URL: http://192.168.8.50:61208
- Installed via: pip3
- Service: /etc/systemd/system/glances.service
- Shows: CPU, RAM, temperature, disk, network

## VMs and LXCs

| ID  | Type | Name     | IP            | Purpose  |
|-----|------|----------|---------------|----------|
| 100 | LXC  | pihole   | 192.168.8.2   | DNS      |
| 101 | VM   | jellyfin | 192.168.8.138 | Media    |
| 103 | LXC  | homepage | 192.168.8.141 | Dashboard|
| 104 | VM   | coolify  | 192.168.8.142 | PaaS     |
