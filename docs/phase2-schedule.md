# Updated Schedule - Full Simulation and Initial Hardware Deployment

| Week | Activity | Responsible | Deliverable |
|---|---|---|---|
| 9 | Phase 2 Packet Tracer prototype: addressing, DHCP, static inter-site routing, SSH, preliminary tests | Rafael Patin (lead), Luis Tenemaza (repository) | Phase2_Prototype.pkt, configs, VLSM table, test matrix, progress report |
| 10 | Switching content: create VLANs 10/20/30/99, 802.1Q trunks, access ports, move management to VLAN 99 | Rafael Patin | Updated .pkt + `show vlan brief`, `show interfaces trunk` |
| 10 | Equipment pickup: Raspberry Pi + OpenWrt flashing, baseline backup | Luis Tenemaza | OpenWrt base install, `sysupgrade -b` backup in repo (no secrets) |
| 10-11 | Router-on-a-Stick subinterfaces, per-VLAN DHCP pools, LACP EtherChannel and RSTP in simulation | Rafael Patin | Full simulation, updated test matrix |
| 11 | Replace static routes with OSPFv2 Area 0 (simulation and FRRouting on OpenWrt) | Rafael Patin | `show ip ospf neighbor` / `vtysh` evidence |
| 11 | Initial hardware deployment: OpenWrt eth0.X VLAN interfaces, wlan0 WAN, NAT masquerade, fw4 zones | Luis Tenemaza | `/etc/config/network`, `firewall`, `dhcp` backups (redacted) |
| 11 | Re-run the test matrix on hardware, update GitHub | Both | Test evidence, tagged commit |
