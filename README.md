# Distributed Enterprise Network Infrastructure
---

**Institution:** Universidad Internacional del Ecuador (UIDE)  
**Course:** Network Information Communication Technologies  
**Semester:** Third Semester  
**Current phase:** Phase 2 - Packet Tracer Prototype (Week 9)

---

## Team Members
---
- Rafael Patin
- Luis Tenemaza

---

## Project Description
---
This repository contains the planning, design and implementation of the distributed network infrastructure for an enterprise with two sites interconnected using the OSPF dynamic routing protocol over OpenWrt routers. The solution includes segmentation via VLANs, VLSM addressing over the 10.10.0.0/16 block, link aggregation with EtherChannel, loop prevention with RSTP, and Layer 2 / Layer 3 security controls.

---

## Phase 2 Status - Packet Tracer Prototype
---
| Component | Status |
|---|---|
| Two-site topology (R-A, R-B, SW-A1/A2, SW-B1/B2, test PCs) | Implemented |
| VLSM addressing from 10.10.0.0/16 (active user segments) | Implemented |
| DHCP pools per site with excluded static ranges | Implemented |
| Inter-site routing over 192.168.100.0/24 (temporary static routes) | Implemented |
| SSHv2 secure management, unused ports disabled | Implemented |
| VLANs, 802.1Q trunks, Router-on-a-Stick | Planned (after week 10) |
| EtherChannel (LACP), RSTP | Planned |
| OSPFv2, NAT, firewall, OpenWrt on Raspberry Pi | Planned (week 11) |

Main files:
- `network/packet-tracer/Phase2_Prototype.pkt` - working simulation
- `network/configs/` - device configuration backups (secrets redacted)
- `network/addressing/` - VLSM table (Markdown and CSV)
- `network/testing/phase2-test-matrix.md` - preliminary test matrix
- `docs/phase2-schedule.md` - updated schedule for weeks 10-11

---

## Repository Structure
---

```text
3S-Integrative-Project/
├── network/
│   ├── packet-tracer/   # .pkt simulation files
│   ├── diagrams/        # topology diagrams
│   ├── configs/         # device configuration backups
│   ├── addressing/      # VLSM plan
│   └── testing/         # test matrices
├── app-go/
├── auth-service/
├── docs/
├── LICENSE
└── README.md
```

---

## How to Verify the Prototype
---
1. Open `network/packet-tracer/Phase2_Prototype.pkt` in Cisco Packet Tracer 9.0 or later.
2. Wait about 30 seconds for spanning tree to converge. Then on each PC go to Desktop > IP Configuration > DHCP, or run `ipconfig /renew`.
3. From PC-A1, run `ping` and `tracert` to the address of PC-B1.
4. On the routers, run `show ip route`, `show ip dhcp binding` and `show ip interface brief`.

---

## Security Note
---
No passwords, tokens or private keys are stored in this repository. Secrets in the configuration backups are replaced with `<REDACTED>`. Credentials are shared only privately between team members.

---

## Contributions
---
| Member | Share | Phase 2 contributions |
|---|---|---|
| Rafael Patin | 60% | Packet Tracer topology and device configuration (routers, switches, DHCP, static routing, SSH), troubleshooting, test execution and evidence, progress report |
| Luis Tenemaza | 40% | GitHub repository organization and maintenance (folder structure, README, configuration backups, VLSM table in Markdown/CSV, test matrix publication), VLSM review, updated schedule, OpenWrt migration notes |

---

## Technologies Used
---
- Cisco Packet Tracer 9.0
- OpenWrt (FRRouting) for OSPF, NAT, DHCP and firewall (planned hardware phase)
- Cisco Catalyst switches for VLANs, 802.1Q trunks, EtherChannel and RSTP

---

## Attribution and AI Assistance Disclosure
---
In accordance with UIDE academic integrity requirements, the team discloses that generative AI tools (Anthropic Claude and Google Gemini) were used to help review the assignment requirements, draft Cisco IOS configuration commands and documentation text. All configurations were applied, tested and verified by the team in Cisco Packet Tracer, and the team is responsible for the final content. Reference architecture: *Proyecto Integrador - Tercer Nivel*, UIDE.

---

## License
---
This project is licensed under the MIT License.
