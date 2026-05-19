# IP Addressing & Subnetting — PNPT Notes

> Practical networking notes focused on internal pentesting, segmentation, and enumeration.

---

# IP Addressing

## Important Private Ranges

| Range | CIDR |
|---|---|
| 10.0.0.0 | /8 |
| 172.16.0.0 - 172.31.255.255 | /12 |
| 192.168.0.0 | /16 |

---

## Important Special Addresses

| Address | Purpose |
|---|---|
| 127.0.0.1 | Loopback |
| 0.0.0.0 | Default route |
| 169.254.x.x | APIPA |
| 255.255.255.255 | Broadcast |

---

## Key Concepts

- IP addresses identify hosts on a network
- CIDR notation defines network size
- Routers operate at Layer 3
- NAT allows multiple hosts to share one public IP

---

# CIDR Notation

## Example

```text
192.168.1.0/24
```

- `/24` = 24 network bits
- Remaining 8 bits are for hosts

Subnet mask:

```text
255.255.255.0
```

---

## Common CIDR Sizes

| CIDR | Subnet Mask | Usable Hosts |
|---|---|---|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /30 | 255.255.255.252 | 2 |

---

# Subnetting Formula

```text
2^(host bits) - 2
```

---

## Example Calculation

```text
192.168.1.0/27
```

```text
32 - 27 = 5 host bits
2^5 = 32 total addresses
32 - 2 = 30 usable hosts
```

---

# Network & Broadcast Addresses

## Example

```text
192.168.1.0/24
```

| Type | Address |
|---|---|
| Network Address | 192.168.1.0 |
| First Host | 192.168.1.1 |
| Last Host | 192.168.1.254 |
| Broadcast Address | 192.168.1.255 |

---

# Pentesting Relevance

Subnetting impacts:
- Internal segmentation
- VLAN boundaries
- Scan scope
- Firewall rules
- Lateral movement opportunities

Understanding subnetting improves:
- Host discovery
- Network mapping
- Pivoting
- Internal enumeration

---

# Important Commands

## Linux

```bash
ip a
ip route
arp -a
```

---

## Windows

```powershell
ipconfig /all
route print
arp -a
```

---

# Key Takeaways

- CIDR defines network size
- Subnetting controls communication boundaries
- Smaller subnets improve segmentation and security
- Strong subnetting knowledge is essential for internal pentesting

---

# Author

Gegi — PNPT Progress Portfolio
