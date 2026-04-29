# Hardware

## ThinkPad T430s

| Component   | Spec                                          |
|-------------|-----------------------------------------------|
| CPU         | Intel Core i5-3320M 2.60GHz                   |
| RAM         | 16GB (upgraded)                               |
| mSATA SSD   | 256GB LiteOn — Proxmox, VMs, LXCs             |
| HDD         | 500GB in UltraBay caddy — media storage via NFS |
| Thermal paste | Arctic MX-4                                 |

## BIOS Settings

- Boot order: mSATA SSD prioritized
- Intel VT-x: enabled (required for Proxmox)
- Lid close action: disabled (server runs with lid closed)
- Power On with AC Attach: enabled (auto-starts after power outage)

## Notes

- SSD is almost full — 3.7GB remaining (April 2026)
- All media must be stored on the HDD via NFS, **not** on the SSD
- See [Storage](../storage/README.md) for storage structure
