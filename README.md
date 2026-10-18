# Homelab

My Homelab is my favorite hobby. I use it to learn about network, UNIX, docker / podman. Moreover, it allows me to really own my data and know where and how it's stored. I enjoy experimenting on it and growing with it.

![Homelab architecture diagram](assets/Homelab_Architecture.png)

> **Note:** private IP addresses are replaced by `xx.xx.xx.xx` in the diagram and in all files.

## Rules

### Access
- **SSH:** key-based authentication only (password login disabled). Private keys are protected by a passphrase.
- **Firewall:** every VM and LXC container has its own strict firewall, with only the required ports open.
- **Network:** all VMs and LXC containers use static IP addresses.

### Updates
- Automatic security updates on all VMs, LXC containers and the Proxmox host.

### Backups
- Daily backup of all VMs and LXC containers at 2:00 AM, stored on a local dataset on the NAS HDD.
- Retention: 7 daily and 4 weekly backups.
- Backups are restored and tested regularly.
- 1 TB cold (offline) backup of the RAID 1 ZFS pool.

### Encryption
- All data is encrypted with AES-256.

### Exposure
- Only less sensitive services are exposed to the internet, through a Cloudflare Tunnel and protected by Cloudflare Access.

## How services are exposed

Internet → Cloudflare Tunnel (+ Cloudflare Access) → reverse proxy (Nginx Proxy Manager) → service

No inbound ports are open on my router. (But Headscale)

## To do

### Security
- [ ] Review and tighten firewall rules per service

### Backups
- [ ] Document the restore procedure and log the last test date

### Monitoring
- [ ] Mail alerts for downtime and disk health
- [ ] Central log review

### Documentation
- [ ] Short post-mortems of past incidents
- [ ] Changelog
