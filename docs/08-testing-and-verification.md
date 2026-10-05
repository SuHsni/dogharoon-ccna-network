# Testing and Verification

## 1. Purpose

This document describes the testing and verification process carried out for the Dogharoon network simulation.

The purpose is to confirm that the implemented network meets the defined business, network, service, security, and growth requirements.

---

## 2. Test Environment

| Item            | Description                            |
| --------------- | -------------------------------------- |
| Simulation Tool | Cisco Packet Tracer                    |
| Routers         | R1, R2, ISP-Router                     |
| Switches        | SW-A1 – SW-A6, SW-B1 – SW-B3           |
| Servers         | SRV-DHCP, SRV-DNS, SRV-WEB, SRV-FILE   |
| Clients         | PCs, Laptops, Smartphones, Tablets     |
| Wireless        | Access Points (Staff-WiFi, Guest-WiFi) |

---

## 3. Test Categories

| Category        | Description                                           |
| --------------- | ----------------------------------------------------- |
| Connectivity    | End-to-end connectivity between devices and buildings |
| DHCP            | Client IP assignment through the DHCP server          |
| DNS             | Internal name resolution                              |
| Web Service     | Access to the internal web server                     |
| File Service    | Access to the internal file server                    |
| Internet Access | NAT/PAT and Internet connectivity                     |
| ACL Security    | Guest isolation and management access control         |
| SSH Management  | Secure remote device management                       |

---

## 4. Connectivity Tests

| Test ID | Description                               | Expected Result  | Actual Result | Status |
| ------- | ----------------------------------------- | ---------------- | ------------- | ------ |
| CON-01  | Ping R1 from a PC in Building A           | Successful reply | Successful    | Pass   |
| CON-02  | Ping R2 from a PC in Building B           | Successful reply | Successful    | Pass   |
| CON-03  | Ping between Building A and Building B    | Successful reply | Successful    | Pass   |
| CON-04  | Ping from a PC to its default gateway     | Successful reply | Successful    | Pass   |
| CON-05  | Switch-to-switch trunk connectivity       | Trunk up / VLANs | Trunk up      | Pass   |
| CON-06  | Inter-building OSPF neighbor relationship | FULL state       | FULL          | Pass   |

---

## 5. DHCP Tests

| Test ID | Description                                   | Expected Result | Actual Result | Status |
| ------- | --------------------------------------------- | --------------- | ------------- | ------ |
| DHCP-01 | PC in VLAN 10 receives an IP address          | 10.10.10.x      | 10.10.10.5    | Pass   |
| DHCP-02 | PC in VLAN 20 receives an IP address          | 10.10.20.x      | 10.10.20.5    | Pass   |
| DHCP-03 | PC in VLAN 70 receives an IP address          | 10.10.70.x      | 10.10.70.5    | Pass   |
| DHCP-04 | Smartphone in VLAN 120 receives an IP address | 10.10.120.x     | 10.10.120.6   | Pass   |
| DHCP-05 | DHCP Relay functioning on R2                  | IP assigned     | IP assigned   | Pass   |

---

## 6. DNS Tests

| Test ID | Description                            | Expected Result  | Actual Result | Status |
| ------- | -------------------------------------- | ---------------- | ------------- | ------ |
| DNS-01  | Resolve web.dogharoon.local from a PC  | 10.10.100.12     | 10.10.100.12  | Pass   |
| DNS-02  | Resolve file.dogharoon.local from a PC | 10.10.100.13     | 10.10.100.13  | Pass   |
| DNS-03  | DNS server reachable from Building B   | Successful reply | Successful    | Pass   |

---

## 7. Web Service Tests

| Test ID | Description                               | Expected Result | Actual Result | Status |
| ------- | ----------------------------------------- | --------------- | ------------- | ------ |
| WEB-01  | Open http://web.dogharoon.local from a PC | Page loads      | Page loads    | Pass   |
| WEB-02  | Open http://10.10.100.12 directly         | Page loads      | Page loads    | Pass   |
| WEB-03  | Access web server from Building B         | Page loads      | Page loads    | Pass   |

---

## 8. File Service Tests

| Test ID | Description                          | Expected Result  | Actual Result | Status |
| ------- | ------------------------------------ | ---------------- | ------------- | ------ |
| FTP-01  | FTP login to 10.10.100.13 as suadmin | Login successful | Successful    | Pass   |
| FTP-02  | List files on the file server        | File list shown  | File list     | Pass   |

---

## 9. Internet Access Tests

| Test ID | Description                             | Expected Result     | Actual Result | Status |
| ------- | --------------------------------------- | ------------------- | ------------- | ------ |
| INT-01  | Ping 8.8.8.8 from a PC in Building A    | Successful reply    | Successful    | Pass   |
| INT-02  | Ping 8.8.8.8 from a PC in Building B    | Successful reply    | Successful    | Pass   |
| INT-03  | NAT translations on R1                  | Entries present     | Entries       | Pass   |
| INT-04  | Default route propagated to R2 via OSPF | O\*E2 route present | Present       | Pass   |

---

## 10. ACL Security Tests

### 10.1 Guest Wi-Fi Isolation (ACL 100)

| Test ID | Description                                 | Expected Result   | Actual Result | Status |
| ------- | ------------------------------------------- | ----------------- | ------------- | ------ |
| ACL-01  | Guest → internal DHCP server (10.10.100.10) | Blocked (Timeout) | Blocked       | Pass   |
| ACL-02  | Guest → internal DNS server (10.10.100.11)  | Blocked (Timeout) | Blocked       | Pass   |
| ACL-03  | Guest → internal Web server (10.10.100.12)  | Blocked (Timeout) | Blocked       | Pass   |
| ACL-04  | Guest → internal File server (10.10.100.13) | Blocked (Timeout) | Blocked       | Pass   |
| ACL-05  | Guest → user VLANs (10, 20, 70)             | Blocked (Timeout) | Blocked       | Pass   |
| ACL-06  | Guest → Management VLAN (130)               | Blocked (Timeout) | Blocked       | Pass   |
| ACL-07  | Guest → Internet (8.8.8.8)                  | Successful reply  | Successful    | Pass   |

### 10.2 Management VLAN Protection (BLOCK-MGMT)

| Test ID | Description                           | Expected Result   | Actual Result | Status |
| ------- | ------------------------------------- | ----------------- | ------------- | ------ |
| ACL-08  | User VLAN 10 → VLAN 130 (10.10.130.1) | Blocked (Timeout) | Blocked       | Pass   |
| ACL-09  | User VLAN 70 → VLAN 131 (10.10.131.1) | Blocked (Timeout) | Blocked       | Pass   |
| ACL-10  | NetAdmin-PC (VLAN 130) → R1, switches | Successful reply  | Successful    | Pass   |

### 10.3 Department Access Control (ACL 102)

| Test ID | Description                            | Expected Result   | Actual Result | Status |
| ------- | -------------------------------------- | ----------------- | ------------- | ------ |
| ACL-11  | Admin-HR (VLAN 20) → Finance (VLAN 30) | Blocked (Timeout) | Blocked       | Pass   |
| ACL-12  | Admin-HR (VLAN 20) → Internal servers  | Successful reply  | Successful    | Pass   |

---

## 11. SSH Management Tests

| Test ID | Description                                 | Expected Result  | Actual Result | Status |
| ------- | ------------------------------------------- | ---------------- | ------------- | ------ |
| SSH-01  | SSH from NetAdmin-PC to SW-A1 (10.10.130.3) | Login successful | Successful    | Pass   |
| SSH-02  | SSH from NetAdmin-PC to SW-B1 (10.10.131.3) | Login successful | Successful    | Pass   |
| SSH-03  | SSH from NetAdmin-PC to R1 (10.10.130.1)    | Login successful | Successful    | Pass   |

---

## 12. Inter-Building Tests

| Test ID | Description                                        | Expected Result  | Actual Result | Status |
| ------- | -------------------------------------------------- | ---------------- | ------------- | ------ |
| IBT-01  | PC in Building A → PC in Building B                | Successful reply | Successful    | Pass   |
| IBT-02  | PC in Building B → Internal servers in Building A  | Successful reply | Successful    | Pass   |
| IBT-03  | PC in Building A → Operations gateway (10.10.70.1) | Successful reply | Successful    | Pass   |

---

## 13. Test Results Summary

| Category        | Total Tests | Passed | Failed |
| --------------- | ----------: | -----: | -----: |
| Connectivity    |           6 |      6 |      0 |
| DHCP            |           5 |      5 |      0 |
| DNS             |           3 |      3 |      0 |
| Web Service     |           3 |      3 |      0 |
| File Service    |           2 |      2 |      0 |
| Internet Access |           4 |      4 |      0 |
| ACL Security    |          12 |     12 |      0 |
| SSH Management  |           3 |      3 |      0 |
| Inter-Building  |           3 |      3 |      0 |
| **Total**       |      **41** | **41** |  **0** |

---

## 14. Conclusion

All tests passed successfully.

The implemented network:

- Meets the defined business and technical requirements.
- Provides segmentation, controlled communication, and service access.
- Enforces Guest isolation and Management VLAN protection.
- Supports inter-building communication through OSPF.
- Provides secure device management through SSH.
- Is documented, reproducible, and explainable within a CCNA-level scope.
