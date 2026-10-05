# Test Plan

## 1. Purpose

This document defines the test plan for the Dogharoon network simulation.

## 2. Test Objectives

Verify that the network meets:

- Business requirements
- Network requirements
- Service requirements
- Security requirements
- Growth requirements

## 3. Test Categories

| Category | Description |
| --- | --- |
| Connectivity | End-to-end connectivity |
| DHCP | IP address assignment |
| DNS | Name resolution |
| Web Service | Internal web access |
| File Service | Internal file access |
| Internet Access | NAT/PAT |
| ACL Security | Guest isolation, management protection |
| SSH Management | Secure remote access |

## 4. Test Environment

- Cisco Packet Tracer
- R1, R2, ISP-Router
- SW-A1 to SW-A6, SW-B1 to SW-B3
- SRV-DHCP, SRV-DNS, SRV-WEB, SRV-FILE

## 5. Test Procedure

For each test category:

1. Prepare the test environment.
2. Execute the test commands.
3. Record the results.
4. Compare with expected results.
5. Mark as Pass or Fail.

## 6. Pass Criteria

A test is considered Passed if:

- The actual result matches the expected result.
- No unexpected behavior is observed.