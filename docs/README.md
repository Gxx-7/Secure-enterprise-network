# Secure Enterprise Network Design with Segmentation & Access Control

## Overview

This project presents the design and implementation of a **secure enterprise network architecture** that enforces segmentation and access control between different organizational departments.

The network is structured based on **security zones** and follows core cybersecurity principles such as:

* Least Privilege
* Network Segmentation
* Defense in Depth
* Basic Zero Trust concepts

---

## Architecture Summary

The network is divided into four VLANs representing different departments:

| VLAN | Department | Security Zone |
| ---- | ---------- | ------------- |
| 10   | HR         | Sensitive     |
| 20   | IT         | Trusted       |
| 30   | Finance    | Sensitive     |
| 40   | Guest      | Untrusted     |

* A Layer 2 switch is used for VLAN segmentation
* A router is used for **inter-VLAN routing (Router-on-a-Stick)**
* ACLs are applied to enforce access control policies

---

## Security Design

### Security Zones

* **Trusted Zone (IT):** Full access to all internal resources
* **Sensitive Zone (HR & Finance):** Restricted access, protected from unauthorized users
* **Untrusted Zone (Guest):** Completely isolated from internal networks

---

### Access Control Policy

| Source | Destination | Action    |
| ------ | ----------- | --------- |
| Guest  | HR          | ❌ Denied  |
| Guest  | Finance     | ❌ Denied  |
| Guest  | IT          | ❌ Denied  |
| IT     | All VLANs   | ✅ Allowed |

---

### Security Objective

The design prevents:

* Unauthorized access to sensitive data
* Lateral movement from untrusted networks
* Internal network abuse

---

## Implementation Details

### VLAN Configuration

* VLANs created and assigned to switch ports
* Access ports configured per department

### Trunking

* 802.1Q trunk configured between switch and router

### Inter-VLAN Routing

* Router-on-a-Stick implemented using subinterfaces
* Each VLAN assigned a default gateway

### ACL Configuration

* Extended ACL applied on Guest VLAN interface
* Traffic filtered at entry point to enforce security policies

---

## Testing & Validation

Connectivity tests were performed to validate security behavior:

* Guest → HR ❌ Blocked
* Guest → Finance ❌ Blocked
* Guest → IT ❌ Blocked
* IT → HR ✅ Allowed
* IT → Finance ✅ Allowed

**Result:**

* Network segmentation enforced
* Access control functioning correctly
* Unauthorized lateral movement prevented

---

## Project Structure

```
secure-enterprise-network/
│
├── README.md
├── LICENSE
│
├── docs/
│   ├── architecture-diagram.png
│   ├── topology.png
│
├── configs/
│   ├── router-config.txt
│   ├── switch-config.txt
│
├── simulation/
│   ├── enterprise-network.pkt
│
├── tests/
│   ├── connectivity-tests.md
│   ├── acl-validation.md
│
└── assets/
    └── screenshots/
```

---

## Tools & Technologies

* Cisco Packet Tracer
* VLANs (802.1Q)
* Router-on-a-Stick
* Access Control Lists (ACLs)

---

## Threat Model

This project addresses common internal network threats:

* Insider threats
* Unauthorized lateral movement
* Guest network abuse

---

## Future Enhancements

* VPN integration for secure remote access
* Intrusion Detection System (IDS)
* DHCP implementation for dynamic IP management
* Role-Based Access Control (RBAC)

---

## Key Skills Demonstrated

* Network Design & Architecture
* Network Segmentation & VLANs
* Access Control Implementation
* Security Policy Enforcement
* Troubleshooting & Debugging

---

## Project Summary

“I designed a secure enterprise network based on security zones and implemented centralized access control using ACLs. The architecture prevents unauthorized lateral movement, especially from untrusted guest networks to sensitive departments, following least privilege and defense-in-depth principles.”

---
