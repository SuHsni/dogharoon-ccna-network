# Dogharoon CCNA Network Simulation

## 📋 Project Type

Educational Network Simulation / CCNA Portfolio Project

## 📖 Project Context

This project is a fictional educational network simulation inspired by the general operational context of Dogharoon Free Zone.

It does **not** represent the real network infrastructure, architecture, equipment, security configuration, or internal information of Dogharoon Free Zone.

All organizational details, user counts, network requirements, equipment assumptions, and technical requirements used in this project are fictional and created for educational purposes.

## 🎯 Objective

The objective of this project is to design, implement, test, troubleshoot, and document a small organizational network at a CCNA level.

The project demonstrates the ability to work through a complete network project lifecycle:

**Requirements → Design → Implementation → Testing → Troubleshooting → Documentation**

## 🗺️ Network Topology

[Insert topology image here]

## ✨ Features

- **VLAN Segmentation:** 13 VLANs for different departments
- **Router-on-a-Stick:** Inter-VLAN routing using router subinterfaces
- **OSPF:** Dynamic routing between the two buildings
- **DHCP Relay:** Centralized DHCP server with `ip helper-address`
- **DNS & Web Services:** Internal DNS and Web Server for administrative systems
- **NAT/PAT:** Internet access for authorized users
- **ACL-Based Security:** Guest WiFi isolation, Management VLAN protection
- **SSH Management:** Secure remote device management
- **Inter-Building Connectivity:** Fiber link between R1 and R2

## 📁 Repository Structure

dogharoon-ccna-network/
├── README.md # This file
├── addressing/ # IP addressing plan and VLAN design
├── configs/ # Device configurations (R1, R2, ISP, SW-\*)
├── diagrams/ # Network diagrams and topology
├── docs/ # Full project documentation
├── packet-tracer/ # Cisco Packet Tracer project file
├── screenshots/ # Test screenshots and verification
└── testing/ # Test plans and results

## 📚 Documentation

All project documentation is available in the [`docs/`](docs/) directory:

- [Project Overview](docs/01-project-overview.md)
- [Requirements](docs/02-requirements.md)
- [User and Device Inventory](docs/03-user-and-device-inventory.md)
- [Logical Network Design](docs/04-logical-network-design.md)
- [VLAN Design](docs/05-vlan-design.md)
- [IP Addressing Plan](docs/06-ip-addressing.md)
- [Network Topology and Device Design](docs/07-network-topology-and-device-design.md)
- [Testing and Verification](docs/08-testing-and-verification.md)

## ⚙️ Configurations

All device configurations are available in the [`configs/`](configs/) directory:

- `R1-Building-A.txt`
- `R2-Building-B.txt`
- `ISP-Router.txt`
- `SW-A1.txt` ... `SW-A6.txt`
- `SW-B1.txt` ... `SW-B3.txt`

## 🛠️ Tools

- **Cisco Packet Tracer** — Network simulation
- **draw.io** — Network diagrams
- **Notepad** — Configuration editing
- **Excel** — IP addressing plan

## 🚀 How to Use

1. Open `packet-tracer/dogharoon-network.pkt` in **Cisco Packet Tracer**.
2. Review the documentation in [`docs/`](docs/).
3. Check device configurations in [`configs/`](configs/).
4. Review test results in [`testing/`](testing/).

## 📐 Scope

The simulated organization consists of:

- An administrative building
- An operational building
- Multiple organizational departments
- Internal network services (DHCP, DNS, Web, File)
- Staff Wi-Fi
- Guest Wi-Fi
- Internet connectivity
- Controlled communication between network segments

## 🎓 Skill Level

The project is intentionally limited to **CCNA-level networking concepts**.

The goal is not to simulate a production Enterprise network, but to create a realistic and technically explainable learning project.

## 📝 License

This project is for **educational purposes only**.

## 👤 Author

https://github.com/SuHsni
