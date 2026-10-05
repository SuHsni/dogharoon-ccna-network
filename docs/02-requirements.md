# Network Requirements

## 1. Business Requirements

| ID    | Requirement                                                                                                           | Priority | Verification               |
| ----- | --------------------------------------------------------------------------------------------------------------------- | -------- | -------------------------- |
| BR-01 | The network must connect the office building and the operational building.                                            | High     | Connectivity Test          |
| BR-02 | Users in the operational building must be able to access the work-related resources they need in the office building. | High     | Inter-Building Access Test |
| BR-03 | Users from different departments must have access to network resources based on their business needs.                 | High     | Access Control Tests       |
| BR-04 | The network must provide Internet access for authorized users.                                                        | High     | Internet Connectivity Test |
| BR-05 | Guest users must be able to access the Internet but must not have access to the organization's internal resources.    | High     | Guest Isolation Test       |
| BR-06 | The network must be scalable to accommodate approximately 20–30% growth in the number of users in the future.         | Medium   | Design Review              |
| BR-07 | The network structure must be documented and understandable to the manager or technical administrator.                | Medium   | Documentation Review       |

## 2. Network Requirements

| ID     | Requirement                                                                                                | Priority | Verification                |
| ------ | ---------------------------------------------------------------------------------------------------------- | -------- | --------------------------- |
| NET-01 | Users from different departments should not be placed in the same Broadcast Domain without a valid reason. | High     | VLAN/Segmentation Review    |
| NET-02 | The office building and the operational building must have network connectivity.                           | High     | Connectivity Test           |
| NET-03 | IP addressing must be structured and documented.                                                           | High     | IP Plan Review              |
| NET-04 | Users must be able to obtain an IP address when required.                                                  | High     | DHCP Test                   |
| NET-05 | Network devices must have a defined naming and management structure.                                       | Medium   | Device Documentation Review |
| NET-06 | The design should make maximum use of the existing equipment and avoid adding unnecessary devices.         | Medium   | Design Review               |

## 3. Service Requirements

| ID     | Requirement                                                                              | Priority | Verification             |
| ------ | ---------------------------------------------------------------------------------------- | -------- | ------------------------ |
| SRV-01 | A DHCP service must be provided to assign IP addresses to required clients.              | High     | DHCP Test                |
| SRV-02 | An internal DNS service should be designed and made available if required.               | Medium   | DNS Resolution Test      |
| SRV-03 | An internal Web Server for the hypothetical administrative system must be accessible.    | High     | HTTP/Service Test        |
| SRV-04 | An internal File Server for shared resources must be available on the network.           | High     | Server Connectivity Test |
| SRV-05 | Authorized users must be able to access the internal services they require.              | High     | Service Access Tests     |
| SRV-06 | Authorized users must be able to access the Internet through the organization's network. | High     | Internet Test            |

## 4. Security Requirements

| ID     | Requirement                                                                                             | Priority | Verification               |
| ------ | ------------------------------------------------------------------------------------------------------- | -------- | -------------------------- |
| SEC-01 | The Guest network must be isolated from the organization's internal network.                            | High     | Guest Isolation Test       |
| SEC-02 | Guests must not be able to access the organization's internal resources.                                | High     | ACL/Connectivity Test      |
| SEC-03 | Access between different departments must be controlled based on business requirements.                 | High     | Inter-Network Access Tests |
| SEC-04 | Administrative access to network devices must be controlled.                                            | Medium   | Management Access Test     |
| SEC-05 | Passwords and administrative access controls for network devices must be included in the configuration. | Medium   | Configuration Review       |

## 5. Growth Requirements

| ID      | Requirement                                                                     | Priority | Verification             |
| ------- | ------------------------------------------------------------------------------- | -------- | ------------------------ |
| GROW-01 | The design must account for approximately 20–30% growth in the number of users. | Medium   | Addressing/Design Review |
| GROW-02 | Adding new users should not require a complete redesign of the network.         | Medium   | Design Review            |
