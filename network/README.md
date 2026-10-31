# Network Configurations and Infrastructure

## Phase 2 - Packet Tracer prototype (Week 9)

| Folder | Content |
|---|---|
| `packet-tracer/` | `Phase2_Prototype.pkt` - working simulation (Cisco Packet Tracer 9.0) |
| `configs/` | Configuration backups for R-A, R-B, SW-A1, SW-A2, SW-B1, SW-B2 (secrets redacted) |
| `addressing/` | VLSM plan derived from 10.10.0.0/16 (`vlsm-table.md`, `vlsm-table.csv`) |
| `testing/` | Preliminary test matrix (`phase2-test-matrix.md`) |
| `diagrams/` | Topology diagrams |

### Topology summary

```
 PC-A1--Fa0/1[SW-A1]Gi0/1--Gi0/0[R-A]Gi0/1==WAN 192.168.100.0/24==Gi0/1[R-B]Gi0/0--Gi0/1[SW-B1]Fa0/1--PC-B1
                Gi0/2                .10                                .11                   Gi0/2
                  |                                                                             |
                Gi0/2                                                                         Gi0/2
 PC-A2--Fa0/1[SW-A2]                                                                        [SW-B2]Fa0/1--PC-B2
       Site A Users 10.10.0.0/26 (gw .1)                       Site B Users 10.10.0.64/26 (gw .65)
```

### Implemented vs planned

| Feature | Status |
|---|---|
| Hostnames, interface addressing, switch management SVIs | Implemented |
| DHCP for the active user segment of each site | Implemented |
| Inter-site routing (temporary static routes) | Implemented, replaced by OSPFv2 in Phase 3 |
| SSHv2 management, local user, encrypted secrets, unused ports shut down | Implemented |
| VLANs 10/20/30/99, 802.1Q trunks, Router-on-a-Stick | Planned (after week 10) |
| LACP EtherChannel, RSTP | Planned |
| OSPFv2 Area 0, NAT, firewall, OpenWrt hardware | Planned (week 11) |

> The WAN link represents the shared Wi-Fi segment of the reference architecture. Packet Tracer emulates it with a direct Ethernet cable between Gi0/1 interfaces.
