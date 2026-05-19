# Networking Fundamentals — PNPT Notes

> Concise networking notes focused on practical pentesting and Active Directory environments.

---

# IP Addressing

## Important Private Ranges

| Range | CIDR |
|---|---|
| 10.0.0.0 | /8 |
| 172.16.0.0 - 172.31.255.255 | /12 |
| 192.168.0.0 | /16 |

---

## Key Concepts

- CIDR notation defines network size (`/24`, `/16`, etc.)
- Subnetting controls broadcast domains and segmentation
- Routing determines packet paths between networks
- APIPA (`169.254.x.x`) often indicates DHCP failure

---

## Pentesting Relevance

- Host discovery
- Network mapping
- Pivoting/lateral movement
- Firewall and ACL analysis

---
