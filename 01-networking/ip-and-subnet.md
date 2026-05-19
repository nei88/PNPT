# IP Addressing & Subnetting — PNPT Notes

> Networking concepts reviewed during PNPT training with focus on internal enumeration, segmentation, and Active Directory environments.

---

# Why Networking Matters in Pentesting

Strong networking knowledge improves:
- Internal host discovery
- Network mapping
- Lateral movement
- Pivoting between subnets
- Firewall and ACL analysis
- Active Directory enumeration

---

# Private IPv4 Ranges

| Range | CIDR | Common Usage |
|---|---|---|
| 10.0.0.0 | /8 | Large enterprise environments |
| 172.16.0.0 - 172.31.255.255 | /12 | Medium internal networks |
| 192.168.0.0 | /16 | Home and small office networks |

---

# Important Special Addresses

| Address | Purpose |
|---|---|
| 127.0.0.1 | Loopback |
| 0.0.0.0 | Default route |
| 169.254.x.x | APIPA / DHCP failure |
| 255.255.255.255 | Broadcast |

---

# CIDR Notation

## Example

```text
192.168.1.0/24
```

- `/24` = 24 network bits
- Remaining 8 bits are available for hosts

Subnet mask:

```text
255.255.255.0
```

---

# Common CIDR Sizes

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

Reserved addresses:
- Network address
- Broadcast address

---

# Example Calculation

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

# IPv4, IPv6 & NAT

IPv4 uses 32-bit addressing:

```text
2^32 = 4.3 billion addresses
```

Due to internet growth and large-scale infrastructure, IPv4 addresses became limited.

IPv6 was introduced using 128-bit addressing to provide a significantly larger address space.

IPv4 is still heavily used because NAT (Network Address Translation) allows multiple private devices to share a single public IP address.

---

# Practical Notes

- Used subnet calculations during internal lab enumeration
- Practiced host discovery against different subnet ranges
- Used `nmap -sn` to identify live hosts within internal networks
- Observed segmented subnet structures in Active Directory labs

---

# Important Networking Commands

## Linux

```bash
ip a
ip route
arp -a
```

## Windows

```powershell
ipconfig /all
route print
arp -a
```

---

# Key Takeaways

- CIDR notation defines network size
- Subnetting controls communication boundaries
- Smaller subnets improve segmentation and reduce broadcast traffic
- Understanding subnetting is critical for internal pentesting and Active Directory environments

---

# Tools Referenced

- Nmap
- Wireshark
- tcpdump
- netcat
