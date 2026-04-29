# Runbook: SSH Root Access on New Machine

## Symptoms

Debian and LXC containers block root login via SSH by default.

```
Permission denied (publickey)
```

## Fix

```bash
# Log in as a regular user or via Proxmox console
TERM=xterm-256color nano /etc/ssh/sshd_config

# Change:
PermitRootLogin yes

# Save and restart SSH
systemctl restart sshd
```

## xterm-kitty Issue

The Kitty terminal is not recognized by remote servers.

```bash
# Prefix the command with TERM override:
TERM=xterm-256color nano <file>
```
