# Distributed Enterprise Network Infrastructure - Phase 1
---

**Institution:** Universidad Internacional del Ecuador (UIDE)  
**Course:** Network Information Communication Technologies  
**Semester:** Third Semester  

---

## Team Members
---
- Rafael Patin
- Luis Tenemaza

---

## Project Description
---
This repository contains the planning and design of the distributed network infrastructure for an enterprise with two sites interconnected using the OSPF dynamic routing protocol over OpenWrt routers. The solution includes segmentation via VLANs, VLSM addressing over the 10.10.0.0/16 block, link aggregation with EtherChannel, loop prevention with RSTP, and Layer 2 / Layer 3 security controls.

---

## Repository Structure
---
3S-Integrative-Project/
├── network/          
│   ├── diagrams/     
│   ├── configs/      
│   └── addressing/   
├── app-go/           
├── auth-service/     
├── docs/             
├── LICENSE           
└── README.md         

---

## Technologies Used
---
- Cisco Packet Tracer / GNS3
- OpenWrt (FRRouting) for OSPF, NAT, DHCP, and Firewall
- Cisco Catalyst Switches for VLANs, 802.1Q Trunks, EtherChannel, and RSTP

---

## License
---
This project is licensed under the MIT License.
