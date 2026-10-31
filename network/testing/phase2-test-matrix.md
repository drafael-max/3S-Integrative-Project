# Phase 2 - Preliminary Test Matrix (Packet Tracer prototype)

Rule: a planned feature that is not available yet is marked **Pending**, not Pass.

| Test ID | Source | Destination | Procedure | Expected result | Observed result | Evidence | Status |
|---|---|---|---|---|---|---|---|
| TC-01 | PC-A1, PC-B1 | R-A / R-B DHCP | `ipconfig /all` on the clients | Address from the correct pool, mask /26, correct gateway | PC-A1: 10.10.0.11/26, gw 10.10.0.1, suffix sitea.uide.local. PC-B1: 10.10.0.75/26, gw 10.10.0.65. Bindings: R-A .11/.12, R-B .75/.76 (first addresses after the excluded ranges) | Fig. ipconfig + `show ip dhcp binding` / `show ip dhcp pool` | Pass |
| TC-02 | PC-A1 | 10.10.0.1 (R-A Gi0/0) | `ping 10.10.0.1` | 4/4 replies | 4/4 replies, 0% loss, TTL=255, avg 3 ms | Fig. ping gateway | Pass |
| TC-03 | PC-A1 (SW-A1) | PC-A2 (SW-A2) | `ping <PC-A2 IP>` | Local L2 connectivity across SW-A1-SW-A2 | Replies received | Fig. local ping | Pass |
| TC-04 | PC-A1 (Site A) | PC-B1 (Site B) | `ping` + `tracert <PC-B1 IP>` | Replies; path 10.10.0.1 -> 192.168.100.11 -> PC-B1 | `ping 10.10.0.75`: 4/4, 0% loss, TTL=126 (two router hops). `tracert`: 1) 10.10.0.1 2) 192.168.100.11 3) 10.10.0.75 | Fig. ping/tracert | Pass |
| TC-05 | R-A, R-B | - | `show ip route` | Remote user subnet learned as static (S) via WAN next hop | R-A: S 10.10.0.64/26 via 192.168.100.11; R-B: S 10.10.0.0/26 via 192.168.100.10 | Fig. routing tables | Pass |
| TC-06 | SW-A1 | - | `show mac address-table` after the pings | Dynamic entries for R-A Gi0/0 on Gi0/1, PC-A1 on Fa0/1, PC-A2 on Gi0/2 | Entries learned on the expected ports | Fig. MAC table | Pass |
| TC-07 | PC-A1 | R-A (10.10.0.1) | `ssh -l netadmin 10.10.0.1` | SSHv2 login succeeds; Telnet not accepted on VTY | Login as netadmin, MOTD banner shown, `R-A#` prompt (privilege 15) reached over SSH | Fig. SSH | Pass |
| TC-08 | Hosts in VLAN 10/20/30/99 | Gateways .1/.193/.129/.209 | 802.1Q trunk + Router-on-a-Stick | Inter-VLAN routing | Not implemented (planned after week 10) | - | Pending |
| TC-09 | SW-A1 | SW-A2 | `show etherchannel summary` | Po1 up with LACP | Not implemented (single link today) | - | Pending |
| TC-10 | All switches | - | `show spanning-tree` (RSTP) | rapid-pvst, one Alternate port | Default PVST running; RSTP pending | - | Pending |
| TC-11 | R-A | R-B | `show ip ospf neighbor` | FULL adjacency in Area 0 | Static routes are used today; OSPF is planned for Phase 3 | - | Pending |
| TC-12 | Site A Users | Internet | NAT / masquerade on wlan0 | Translated outbound traffic | Not implemented | - | Pending |
| TC-13 | Guests VLAN 30 | Servers VLAN 20 | Firewall policy | Traffic dropped | Not implemented | - | Pending |
