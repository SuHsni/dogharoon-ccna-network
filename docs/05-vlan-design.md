# VLAN Design

## 1. Purpose

This document defines the VLAN structure for the simulated organizational network.

Each department is assigned a dedicated VLAN to provide logical segmentation, reduce broadcast traffic, and support access control.

---

## 2. VLAN Allocation

| VLAN ID | VLAN Name        | Purpose                                      | Location                | Current Endpoints |
| ------: | ---------------- | -------------------------------------------- | ----------------------- | ----------------: |
|      10 | MANAGEMENT-USERS | Management department                        | Administrative Building |                 5 |
|      20 | ADMIN-HR         | Administration and HR                        | Administrative Building |                15 |
|      30 | FINANCE          | Finance department                           | Administrative Building |                12 |
|      40 | COMMERCE         | Commerce department                          | Administrative Building |                18 |
|      50 | IT               | IT department                                | Administrative Building |                 6 |
|      60 | CUSTOMER-SERVICE | Customer Services                            | Administrative Building |                20 |
|      70 | OPERATIONS       | Operations department                        | Operational Building    |                15 |
|      80 | TRAFFIC-CONTROL  | Traffic Control and Coordination             | Operational Building    |                10 |
|      90 | OP-SUPPORT       | Operational Support                          | Operational Building    |                 8 |
|     100 | SERVERS          | Internal servers and infrastructure services | Administrative Building |                4+ |
|     110 | STAFF-WIFI       | Wireless network for employees               | Both buildings          |               TBD |
|     120 | GUEST-WIFI       | Guest wireless network                       | Both buildings          |               TBD |
|     130 | NETWORK-MGMT     | Network-device management (Building A)       | Network infrastructure  |               TBD |
|     131 | NETWORK-MGMT-B   | Network-device management (Building B)       | Network infrastructure  |               TBD |

---

## 3. VLAN Purpose

### User VLANs (10–90)

Each department is assigned a dedicated VLAN to:

- Separate broadcast domains
- Provide logical organization
- Support departmental access control

### Server VLAN (100)

The server VLAN hosts all internal servers:

- SRV-DHCP
- SRV-DNS
- SRV-WEB
- SRV-FILE

Access to the server VLAN is controlled based on business requirements.

### Wireless VLANs (110, 120)

- **VLAN 110 (STAFF-WIFI):** Used by authorized employees
- **VLAN 120 (GUEST-WIFI):** Used by visitors and guests

Guest Wi-Fi is isolated from internal networks using an extended ACL.

### Management VLANs (130, 131)

- **VLAN 130:** Network device management (Building A)
- **VLAN 131:** Network device management (Building B)

Normal users do not have access to the management VLANs.

---

## 4. VLAN Distribution per Switch

| Switch | VLANs Configured                           |
| ------ | ------------------------------------------ |
| SW-A1  | 10, 20, 30, 40, 50, 60, 100, 110, 120, 130 |
| SW-A2  | 10, 20, 110, 130                           |
| SW-A3  | 30, 40, 130                                |
| SW-A4  | 40, 50, 60, 130                            |
| SW-A5  | 60, 120, 130                               |
| SW-A6  | 100, 110, 130                              |
| SW-B1  | 70, 80, 90, 110, 130                       |
| SW-B2  | 70, 110, 130                               |
| SW-B3  | 80, 90, 130                                |

---

## 5. VLAN-to-Subnet Mapping

| VLAN ID | Subnet         | Gateway     | Location   |
| ------: | -------------- | ----------- | ---------- |
|      10 | 10.10.10.0/28  | 10.10.10.1  | Building A |
|      20 | 10.10.20.0/27  | 10.10.20.1  | Building A |
|      30 | 10.10.30.0/27  | 10.10.30.1  | Building A |
|      40 | 10.10.40.0/27  | 10.10.40.1  | Building A |
|      50 | 10.10.50.0/28  | 10.10.50.1  | Building A |
|      60 | 10.10.60.0/26  | 10.10.60.1  | Building A |
|      70 | 10.10.70.0/27  | 10.10.70.1  | Building B |
|      80 | 10.10.80.0/27  | 10.10.80.1  | Building B |
|      90 | 10.10.90.0/28  | 10.10.90.1  | Building B |
|     100 | 10.10.100.0/28 | 10.10.100.1 | Building A |
|     110 | 10.10.110.0/24 | 10.10.110.1 | Both       |
|     120 | 10.10.120.0/25 | 10.10.120.1 | Both       |
|     130 | 10.10.130.0/28 | 10.10.130.1 | Building A |
|     131 | 10.10.131.0/28 | 10.10.131.1 | Building B |

---

## 6. Design Notes

- VLAN 130 and VLAN 131 use the same VLAN tag (130) on the trunk, but are assigned different IP subnets on each router to avoid overlap between buildings.
- Staff and Guest Wi-Fi VLANs are present in both buildings.
- The management VLANs are used exclusively for network device management.
