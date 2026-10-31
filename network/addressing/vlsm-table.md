# VLSM Addressing Plan - Phase 2 (derived from 10.10.0.0/16)

Subnets are allocated in descending order of host requirements. VLAN IDs are the same at both sites but each site uses its own subnet, so each VLAN is a separate broadcast domain per site.

| Site | Purpose | VLAN | Hosts req. | Network | Prefix | Mask | Usable range | Broadcast | Gateway | Assignment | Phase 2 status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A | Users | 10 | 60 | 10.10.0.0 | /26 | 255.255.255.192 | 10.10.0.1 - 10.10.0.62 | 10.10.0.63 | 10.10.0.1 | DHCP .11-.62 (static .1-.10) | **Implemented** |
| B | Users | 10 | 50 | 10.10.0.64 | /26 | 255.255.255.192 | 10.10.0.65 - 10.10.0.126 | 10.10.0.127 | 10.10.0.65 | DHCP .75-.126 (static .65-.74) | **Implemented** |
| A | Guests | 30 | 20 | 10.10.0.128 | /27 | 255.255.255.224 | 10.10.0.129 - 10.10.0.158 | 10.10.0.159 | 10.10.0.129 | DHCP (planned) | Reserved - Planned |
| B | Guests | 30 | 15 | 10.10.0.160 | /27 | 255.255.255.224 | 10.10.0.161 - 10.10.0.190 | 10.10.0.191 | 10.10.0.161 | DHCP (planned) | Reserved - Planned |
| A | Servers | 20 | 10 | 10.10.0.192 | /28 | 255.255.255.240 | 10.10.0.193 - 10.10.0.206 | 10.10.0.207 | 10.10.0.193 | Static | Reserved - Planned |
| A | Management | 99 | 10 | 10.10.0.208 | /28 | 255.255.255.240 | 10.10.0.209 - 10.10.0.222 | 10.10.0.223 | 10.10.0.209 | Static | Reserved - Planned |
| B | Management | 99 | 10 | 10.10.0.224 | /28 | 255.255.255.240 | 10.10.0.225 - 10.10.0.238 | 10.10.0.239 | 10.10.0.225 | Static | Reserved - Planned |
| B | Servers | 20 | 5 | 10.10.0.240 | /28 | 255.255.255.240 | 10.10.0.241 - 10.10.0.254 | 10.10.0.255 | 10.10.0.241 | Static | Reserved - Planned |
| Both | Inter-site WAN (shared Wi-Fi) | - | 3 | 192.168.100.0 | /24 | 255.255.255.0 | 192.168.100.1 - 192.168.100.254 | 192.168.100.255 | AP .1 | Static: R-A .10, R-B .11 | Implemented (cable emulation) |
| Both | Future growth | - | - | 10.10.1.0 - 10.10.255.255 | /24 blocks | - | - | - | - | - | Reserved |

## Static assignments in the active segments

| Device | Interface | IP address | Notes |
|---|---|---|---|
| R-A | Gi0/0 | 10.10.0.1/26 | Site A Users gateway (future eth0.10 on OpenWrt) |
| R-A | Gi0/1 | 192.168.100.10/24 | WAN (future wlan0) |
| SW-A1 | VLAN 1 SVI | 10.10.0.2/26 | Temporary management, moves to VLAN 99 |
| SW-A2 | VLAN 1 SVI | 10.10.0.3/26 | Temporary management, moves to VLAN 99 |
| R-B | Gi0/0 | 10.10.0.65/26 | Site B Users gateway (future eth0.10 on OpenWrt) |
| R-B | Gi0/1 | 192.168.100.11/24 | WAN (future wlan0) |
| SW-B1 | VLAN 1 SVI | 10.10.0.66/26 | Temporary management, moves to VLAN 99 |
| SW-B2 | VLAN 1 SVI | 10.10.0.67/26 | Temporary management, moves to VLAN 99 |

## Changes from Phase 1

1. **WAN usable range corrected.** Phase 1 listed `192.168.100.1 - 192.168.100.2` for a /24, which was wrong. The usable range is `.1 - .254`. Addresses now follow the reference architecture: AP `.1`, R-A `.10`, R-B `.11`.
2. **Growth space reserved.** The eight Phase 1 subnets use all of 10.10.0.0/24, so `10.10.1.0/24` onward is reserved for new VLANs or services.
3. **Static ranges reserved inside the DHCP subnets** for gateways, switch management and future fixed hosts.
