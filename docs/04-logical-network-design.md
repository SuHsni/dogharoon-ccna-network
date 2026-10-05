# Logical Network Design

## 1. Design Objective

The logical network is designed to provide segmentation, controlled communication, service access, and basic security while remaining within the scope of a CCNA-level educational project.

The design is based on the business and technical requirements defined by the fictional client.

---

## 2. Logical Network Segments

The logical design consists of the following network segments:

### Administrative Building (Building A)

- Management
- Administration & HR
- Finance
- Commerce
- IT
- Customer Services
- Servers
- Staff Wi-Fi
- Guest Wi-Fi
- Network Management

### Operational Building (Building B)

- Operations
- Traffic Control & Coordination
- Operational Support
- Staff Wi-Fi
- Guest Wi-Fi
- Network Management

### Shared Infrastructure

- Server Network (VLAN 100)
- Network Management Network (VLAN 130 for Building A, VLAN 131 for Building B)

### Wireless

- Staff Wi-Fi (VLAN 110)
- Guest Wi-Fi (VLAN 120)

---

## 3. Segmentation Strategy

Different organizational departments are logically separated to:

- Reduce unnecessary broadcast traffic
- Improve network organization
- Support controlled communication
- Provide a foundation for access control
- Simplify network management

Each department is assigned a dedicated VLAN with its own IPv4 subnet.

---

## 4. Server Network

Internal servers are placed in a dedicated logical network (VLAN 100).

The server requirements are:

- DHCP
- DNS
- Web Server
- File Server

Access to these services is controlled according to business requirements.

---

## 5. Guest Network

Guest Wi-Fi uses a dedicated logical network (VLAN 120).

Guest users:

- Have Internet access
- Do not have access to internal organizational networks

The technical enforcement is implemented using an extended ACL (ACL 100) applied on the Guest VLAN subinterface.

---

## 6. Staff Wi-Fi

Staff Wi-Fi is logically separated from Guest Wi-Fi (VLAN 110).

Staff users receive access according to organizational requirements.

---

## 7. Network Management

A dedicated management network is used for network device management:

- **VLAN 130** — Network Management (Building A)
- **VLAN 131** — Network Management (Building B)

Normal users do not have direct access to network management interfaces. An extended ACL (BLOCK-MGMT) is applied on all user-facing subinterfaces to prevent unauthorized access to the management VLANs.

---

## 8. Inter-Building Communication

The Administrative Building and Operational Building communicate through a routed fiber connection between R1 and R2.

Users in the Operational Building receive access only to the resources required for their work.

Routing between the two buildings is implemented using **OSPF** in a single area (Area 0).

---

## 9. Internet Connectivity

Internal users requiring Internet access use the organization's Internet connection through R1.

The implementation uses:

- **NAT/PAT** on R1 for address translation
- A default route toward the simulated ISP router
- **OSPF default-information originate** to propagate the default route to R2

---

## 10. Design Decisions

| ID    | Decision                                                         | Reason                                        |
| ----- | ---------------------------------------------------------------- | --------------------------------------------- |
| LD-01 | Departments are logically segmented.                             | Reduce broadcasts and support access control. |
| LD-02 | Servers use a dedicated logical network (VLAN 100).              | Simplify service access control.              |
| LD-03 | Guest Wi-Fi is isolated from internal networks (VLAN 120).       | Security requirement.                         |
| LD-04 | Staff and Guest Wi-Fi are separated (VLAN 110 / VLAN 120).       | Different access requirements.                |
| LD-05 | Dedicated management VLANs are used (VLAN 130 / VLAN 131).       | Protect network device management access.     |
| LD-06 | The two buildings communicate through a routed fiber connection. | Required inter-building connectivity.         |
| LD-07 | OSPF is used for dynamic routing between buildings.              | Simplify routing and support scalability.     |
| LD-08 | DHCP Relay is used for centralized DHCP service.                 | Centralized management of IP addressing.      |

---

## 11. Design Constraints

The design must:

- Remain within CCNA scope.
- Be implementable in Cisco Packet Tracer.
- Avoid unnecessary Enterprise-level complexity.
- Support the stated business requirements.
- Remain understandable and explainable as a beginner portfolio project.
