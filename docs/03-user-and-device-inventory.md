# User and Device Inventory

## 1. Administrative Building (Building A)

| Department          | Users | Workstations |
| ------------------- | ----: | -----------: |
| Management          |     5 |            5 |
| Administration & HR |    15 |           15 |
| Finance             |    12 |           12 |
| Commerce            |    18 |           18 |
| IT                  |     6 |            6 |
| Customer Services   |    20 |           20 |

### Total

- Users: 76
- Workstations: 76

---

## 2. Operational Building (Building B)

| Department                     | Users | Workstations |
| ------------------------------ | ----: | -----------: |
| Operations                     |    15 |           15 |
| Traffic Control & Coordination |    10 |           10 |
| Operational Support            |     8 |            8 |

### Total

- Users: 33
- Workstations: 33

---

## 3. Overall User Count

- Administrative Building: 76
- Operational Building: 33
- Total: 109 users
- Total workstations: 109

---

## 4. Additional Endpoints

The project also includes:

- Staff laptops
- Network printers
- Staff Wi-Fi clients
- Guest Wi-Fi clients
- Smartphones and tablets (for Wi-Fi testing)

The exact number of these endpoints will be determined during the design phase.

---

## 5. Servers

The project includes the following dedicated servers, placed in the Server VLAN (VLAN 100):

| Server   | Role                           |
| -------- | ------------------------------ |
| SRV-DHCP | DHCP Server                    |
| SRV-DNS  | Internal DNS Server            |
| SRV-WEB  | Internal Web Server            |
| SRV-FILE | Internal File Server (FTP/SMB) |

---

## 6. Network Infrastructure

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
| SW-B2      | Access switch (Operations, Staff WiFi, Guest WiFi)  | Building B |
| SW-B3      | Access switch (Traffic Control, Op-Support)         | Building B |

---

## 7. Wireless Infrastructure

| Device        | SSID       | VLAN | Location   |
| ------------- | ---------- | ---- | ---------- |
| Access Point1 | Guest-WiFi | 120  | Building A |
| Access Point2 | Staff-WiFi | 110  | Building A |
| Access Point3 | Staff-WiFi | 110  | Building B |
| Access Point4 | Guest-WiFi | 120  | Building B |
