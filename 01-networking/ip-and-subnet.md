# IP Addressing & Subnetting — PNPT Notes

> Focused networking notes from my Practical Network Penetration Tester (PNPT) studies.  
> Emphasis on subnetting, internal network enumeration, segmentation, and Active Directory environments.

---

# Why This Matters in Pentesting

Networking knowledge directly impacts:
- Internal enumeration
- Host discovery
- Lateral movement
- VLAN traversal
- Firewall analysis
- Active Directory attacks
- Pivoting between segmented networks

Misunderstanding subnetting can lead to:
- Missed hosts
- Incorrect scan scope
- Failed routing/pivoting
- Poor network visibility

---

# Private IP Ranges

| Range | CIDR | Usage |
|---|---|---|
| 10.0.0.0 | /8 | Large enterprise networks |
| 172.16.0.0 - 172.31.255.255 | /12 | Medium internal networks |
| 192.168.0.0 | /16 | Home/small office environments |

---

# Important Special Addresses

| Address | Purpose |
|---|---|
| 127.0.0.1 | Loopback interface |
| 0.0.0.0 | Default route / unspecified |
| 169.254.x.x | APIPA (DHCP failure) |
| 255.255.255.255 | Broadcast address |

---

# CIDR Notation

## Example

```text
192.168.1.0/24
```

- `/24` = 24 network bits
- Remaining 8 bits are host bits

Subnet mask:

```text
255.255.255.0
```

---

# Common CIDR Sizes

| CIDR | Subnet Mask | Total Addresses | Usable Hosts |
|---|---|---|---|
| /24 | 255.255.255.0 | 256 | 254 |
| /25 | 255.255.255.128 | 128 | 126 |
| /26 | 255.255.255.192 | 64 | 62 |
| /27 | 255.255.255.224 | 32 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /30 | 255.255.255.252 | 4 | 2 |

---

# Subnetting Formula

```text
2^(host bits) - 2
```

Reserved addresses:
- Network address
- Broadcast address

---

# Example Subnet Calculation

## Target Network

```text
192.168.1.0/27
```

## Calculation

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

Due to internet growth, cloud infrastructure, and billions of connected devices, IPv4 addresses became limited and began running out.

To solve this, IPv6 was introduced using 128-bit addressing, providing a massively larger address space.

Example IPv6 address:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

IPv4 is still heavily used because of NAT (Network Address Translation), which allows multiple private devices to share a single public IP address.

---

# Pentesting Relevance

## Internal Network Segmentation

Subnetting defines:
- Broadcast domains
- VLAN boundaries
- ACL/firewall scope
- Reachable hosts

---

## Enumeration Impact

Subnet awareness improves:
- Nmap scan accuracy
- Host discovery
- Route identification
- Internal pivoting
- Lateral movement strategy

---

# Important Networking Commands

## Linux

```bash
ifconfig
arpscan
netdiscover
ip a
```

---

## Windows

```powershell
ipconfig /all
route print
arp -a
```

---

# Quick Notes

- Routers operate at Layer 3
- ARP operates at Layer 2
- NAT translates private to public IPs
- Smaller subnets reduce broadcast traffic
- Enterprise environments commonly use segmented subnet structures

---

# Key Takeaways

- CIDR notation defines network size
- Subnetting controls communication boundaries
- Strong subnetting knowledge improves internal reconnaissance
- Understanding network segmentation is critical for Active Directory assessments

---

# Applied Knowledge

Topics reviewed and practiced throughout PNPT training and lab environments:

- IP addressing & subnetting
- CIDR calculations
- Network segmentation concepts
- TCP/IP fundamentals
- Common ports & protocols
- Internal network enumeration
- Host discovery methodologies
- Active Directory network fundamentals
- Routing & pivoting concepts
- Packet and traffic analysis basics
