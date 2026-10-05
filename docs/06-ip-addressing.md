# IP Addressing Plan

## 1. Purpose

This document defines the IPv4 addressing strategy for the simulated organizational network.

The addressing plan is based on the VLAN structure defined in the VLAN Design document.

The main objectives are:

- Provide a separate IPv4 subnet for each VLAN.
- Support the current number of users and devices.
- Provide reasonable capacity for future growth.
- Keep the addressing scheme structured and easy to document.
- Make troubleshooting and network management easier.

---

## 2. Address Space

The project uses the private IPv4 address space:

`10.10.0.0/16`

This address space is used only for the educational simulation.

It does not represent the actual addressing scheme of any real organization.

---

## 3. Addressing Principles

The following principles are used:

1. Each VLAN receives a separate IPv4 subnet.
2. Each subnet has a dedicated default gateway.
3. Subnet sizes are selected according to endpoint requirements and expected growth.
4. The addressing scheme follows a consistent pattern.
5. Infrastructure addresses are documented separately from dynamically assigned client addresses.
6. DHCP is used for appropriate client networks.
7. Servers and network infrastructure use controlled addressing according to the service design.
8. Address space is reserved for future expansion where practical.

---

## 4. Growth Consideration

The client requirements specify an expected user growth of approximately 20–30%.

Therefore, subnet sizes are not based only on the current number of workstations.

The design provides sufficient usable addresses for:

- Current users
- Expected future users
- Default gateway
- Additional endpoints where appropriate
- Reasonable operational expansion

---

## 5. Subnet Allocation

| VLAN | Name             | Current Users / Devices | Network     | Prefix | Usable Hosts | Default Gateway |
| ---: | ---------------- | ----------------------: | ----------- | ------ | -----------: | --------------- |
|   10 | MANAGEMENT-USERS |                       5 | 10.10.10.0  | /28    |           14 | 10.10.10.1      |
|   20 | ADMIN-HR         |                      15 | 10.10.20.0  | /27    |           30 | 10.10.20.1      |
|   30 | FINANCE          |                      12 | 10.10.30.0  | /27    |           30 | 10.10.30.1      |
|   40 | COMMERCE         |                      18 | 10.10.40.0  | /27    |           30 | 10.10.40.1      |
|   50 | IT               |                       6 | 10.10.50.0  | /28    |           14 | 10.10.50.1      |
|   60 | CUSTOMER-SERVICE |                      20 | 10.10.60.0  | /26    |           62 | 10.10.60.1      |
|   70 | OPERATIONS       |                      15 | 10.10.70.0  | /27    |           30 | 10.10.70.1      |
|   80 | TRAFFIC-CONTROL  |                      10 | 10.10.80.0  | /27    |           30 | 10.10.80.1      |
|   90 | OP-SUPPORT       |                       8 | 10.10.90.0  | /28    |           14 | 10.10.90.1      |
|  100 | SERVERS          |                      4+ | 10.10.100.0 | /28    |           14 | 10.10.100.1     |
|  110 | STAFF-WIFI       |                     TBD | 10.10.110.0 | /24    |          254 | 10.10.110.1     |
|  120 | GUEST-WIFI       |                     TBD | 10.10.120.0 | /25    |          126 | 10.10.120.1     |
|  130 | NETWORK-MGMT (A) |                     TBD | 10.10.130.0 | /28    |           14 | 10.10.130.1     |
|  131 | NETWORK-MGMT (B) |                     TBD | 10.10.131.0 | /28    |           14 | 10.10.131.1     |

---

## 6. Subnetting Rationale

### Management Users

Current users: 5

A `/28` subnet provides 14 usable addresses, which provides room for the current users and a small amount of additional capacity.

### Administration and HR

Current users: 15

A `/27` subnet provides 30 usable addresses and therefore provides additional capacity for future users and devices.

### Finance

Current users: 12

A `/27` subnet provides 30 usable addresses.

This is larger than the current requirement and provides room for future growth.

### Commerce

Current users: 18

A `/27` subnet provides 30 usable addresses and allows additional capacity without immediately requiring another subnet.

### IT

Current users: 6

A `/28` subnet provides 14 usable addresses.

The subnet can accommodate the current users and additional IT endpoints.

### Customer Services

Current users: 20

A `/26` subnet provides 62 usable addresses.

This provides additional capacity for future growth and potentially additional client devices.

### Operational Departments

The Operations, Traffic Control, and Operational Support networks are sized according to their current endpoint counts and expected growth.

### Wireless Networks

- **STAFF-WIFI:** `/24` provides 254 usable addresses, sufficient for the expected number of employee devices.
- **GUEST-WIFI:** `/25` provides 126 usable addresses, sufficient for visitor devices.

### Management Networks

- **VLAN 130 (Building A):** `/28` provides 14 usable addresses for Building A infrastructure.
- **VLAN 131 (Building B):** `/28` provides 14 usable addresses for Building B infrastructure.

---

## 7. Address Allocation Convention

The following convention is used:

- `.1` — Default gateway
- `.2` – `.4` — Reserved for infrastructure
- `.5` – onward — DHCP range for client addresses
- Higher addresses — Reserved for future infrastructure or static assignments where appropriate

---

## 8. Server Addressing

Servers use controlled static addresses within the SERVER VLAN (VLAN 100):

| Server   | IP Address   | Subnet Mask     | Gateway     | Service |
| -------- | ------------ | --------------- | ----------- | ------- |
| SRV-DHCP | 10.10.100.10 | 255.255.255.240 | 10.10.100.1 | DHCP    |
| SRV-DNS  | 10.10.100.11 | 255.255.255.240 | 10.10.100.1 | DNS     |
| SRV-WEB  | 10.10.100.12 | 255.255.255.240 | 10.10.100.1 | HTTP    |
| SRV-FILE | 10.10.100.13 | 255.255.255.240 | 10.10.100.1 | FTP     |

---

## 9. Network Infrastructure Addressing

Network infrastructure devices use static addresses within the management VLANs:

### Building A (VLAN 130)

| Device | IP Address  | Subnet Mask     | Gateway     |
| ------ | ----------- | --------------- | ----------- |
| R1     | 10.10.130.1 | 255.255.255.240 | —           |
| SW-A1  | 10.10.130.3 | 255.255.255.240 | 10.10.130.1 |
| SW-A2  | 10.10.130.4 | 255.255.255.240 | 10.10.130.1 |
| SW-A3  | 10.10.130.5 | 255.255.255.240 | 10.10.130.1 |
| SW-A4  | 10.10.130.6 | 255.255.255.240 | 10.10.130.1 |
| SW-A5  | 10.10.130.7 | 255.255.255.240 | 10.10.130.1 |
| SW-A6  | 10.10.130.8 | 255.255.255.240 | 10.10.130.1 |

### Building B (VLAN 131)

| Device | IP Address  | Subnet Mask     | Gateway     |
| ------ | ----------- | --------------- | ----------- |
| R2     | 10.10.131.1 | 255.255.255.240 | —           |
| SW-B3  | 10.10.131.2 | 255.255.255.240 | 10.10.131.1 |
| SW-B1  | 10.10.131.3 | 255.255.255.240 | 10.10.131.1 |
| SW-B2  | 10.10.131.4 | 255.255.255.240 | 10.10.131.1 |

### WAN Links

| Link            | Device | Interface | IP Address  | Subnet Mask     |
| --------------- | ------ | --------- | ----------- | --------------- |
| R1 ↔ R2 (Fiber) | R1     | g0/2/0    | 10.0.0.1    | 255.255.255.252 |
| R1 ↔ R2 (Fiber) | R2     | g0/2/0    | 10.0.0.2    | 255.255.255.252 |
| R1 ↔ ISP        | R1     | g0/1      | 203.0.113.2 | 255.255.255.252 |
| R1 ↔ ISP        | ISP    | g0/0      | 203.0.113.1 | 255.255.255.252 |
| ISP (Simulated) | ISP    | Loopback0 | 8.8.8.8     | 255.255.255.255 |

---

## 10. DHCP Ranges

DHCP is used for client networks. The DHCP server is located at `10.10.100.10`.

| VLAN | DHCP Range                  | Excluded Addresses        |
| ---: | --------------------------- | ------------------------- |
|   10 | 10.10.10.5 – 10.10.10.14    | 10.10.10.1 – 10.10.10.4   |
|   20 | 10.10.20.5 – 10.10.20.30    | 10.10.20.1 – 10.10.20.4   |
|   30 | 10.10.30.5 – 10.10.30.30    | 10.10.30.1 – 10.10.30.4   |
|   40 | 10.10.40.5 – 10.10.40.30    | 10.10.40.1 – 10.10.40.4   |
|   50 | 10.10.50.5 – 10.10.50.14    | 10.10.50.1 – 10.10.50.4   |
|   60 | 10.10.60.5 – 10.10.60.62    | 10.10.60.1 – 10.10.60.4   |
|   70 | 10.10.70.5 – 10.10.70.30    | 10.10.70.1 – 10.10.70.4   |
|   80 | 10.10.80.5 – 10.10.80.30    | 10.10.80.1 – 10.10.80.4   |
|   90 | 10.10.90.5 – 10.10.90.14    | 10.10.90.1 – 10.10.90.4   |
|  110 | 10.10.110.5 – 10.10.110.254 | 10.10.110.1 – 10.10.110.4 |
|  120 | 10.10.120.5 – 10.10.120.126 | 10.10.120.1 – 10.10.120.4 |

---

## 11. Future Expansion

The `10.10.x.0` addressing pattern leaves substantial unused space within the `10.10.0.0/16` private address range.

This allows additional networks or VLANs to be introduced later without redesigning the entire addressing scheme.

---

## 12. Important Design Note

This addressing plan is a design proposal for the educational simulation.

It is not intended to represent the real network or real IP addressing of Dogharoon Free Zone.

Final IP assignments are validated during Packet Tracer implementation and testing.
