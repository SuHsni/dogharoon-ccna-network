# Network Topology and Device Design

## 1. Purpose

This document defines the physical and logical equipment structure for the simulated organizational network.

The design is intended for implementation in Cisco Packet Tracer and remains within CCNA-level scope.

---

## 2. Design Objectives

The topology provides:

- Connectivity between the two organizational buildings.
- Connectivity between users and network services.
- Support for the VLAN structure.
- Inter-VLAN routing.
- Inter-building communication.
- Internet connectivity through a simulated ISP.
- Staff and Guest wireless networks.
- Implementation of access-control policies.
- A simplified, CCNA-level design without enterprise-level complexity.

---

## 3. Building Structure

### Building A — Administrative Building

Contains:

- Management
- Administration & HR
- Finance
- Commerce
- IT
- Customer Services
- Internal servers
- Network infrastructure

### Building B — Operational Building

Contains:

- Operations
- Traffic Control & Coordination
- Operational Support
- Network infrastructure

---

## 4. Core Network Devices

| Device     | Role                                                | Location   |
| ---------- | --------------------------------------------------- | ---------- |
| R1         | Main router / Inter-VLAN routing / Internet edge    | Building A |
| R2         | Router for Building B / Inter-building connectivity | Building B |
| ISP-Router | Simulated Internet provider                         | External   |
| SW-A1      | Core switch (Building A)                            | Building A |
| SW-A2      | Access switch (Management, Admin-HR)                | Building A |
| SW-A3      | Access switch (Finance, Commerce)                   | Building A |
| SW-A4      | Access switch (Commerce, IT, Customer Service)      | Building A |
| SW-A5      | Access switch (Customer Service, Guest WiFi)        | Building A |
| SW-A6      | Access switch (Servers, Staff WiFi)                 | Building A |
| SW-B1      | Core switch (Building B)                            | Building B |
| SW-B2      | Access switch (Operations, Staff WiFiو Guest WiFi)  | Building B |
| SW-B3      | Access switch (Traffic Control, Op-Support)         | Building B |

---

## 5. Routing Architecture

The network uses routers for Layer 3 routing.

- **R1** provides routing for Building A and acts as the Internet edge.
- **R2** provides routing for Building B.
- Inter-VLAN routing is implemented using **router subinterfaces** and **802.1Q trunking** (Router-on-a-Stick).
- Inter-building routing is implemented using **OSPF** in a single area (Area 0).

This approach provides practical CCNA-level experience with:

- VLANs
- Trunking
- Router subinterfaces
- Inter-VLAN routing
- OSPF dynamic routing
- ACLs

---

## 6. Building A Topology

```text
                         R1
                         |
                    802.1Q Trunk
                         |
                       SW-A1
          ┌───────┬───────┼───────┬───────┐
          │       │       │       │       │
        SW-A2   SW-A3   SW-A4   SW-A5   SW-A6
          │       │       │       │       │
     Management  Finance Commerce  CS   Servers
      Admin-HR          IT        Guest  Staff
                                     WiFi   WiFi
```
