---

## MAC Address Fundamentals (Layer 2 Concept)

A MAC (Media Access Control) address is a unique hardware identifier assigned to a network interface card (NIC).

It operates at Layer 2 (Data Link Layer) and is used for communication inside a local network (LAN).

Format:

00:1A:2B:3C:4D:5E

---

## MAC Address Structure

A MAC address is 48 bits (6 bytes), split into two parts:

| Part | Description |
|------|-------------|
| First 24 bits | Vendor identifier (OUI - Organizationally Unique Identifier) |
| Last 24 bits  | Device-specific identifier |

The OUI can reveal the hardware manufacturer (e.g., Cisco, Intel, VMware).

---

## How MAC Addresses Work in Networking

Inside a local network, devices communicate using MAC addresses rather than IP addresses.

When a device wants to communicate with another device on the same network:

1. It checks if the destination IP is local
2. If yes, it uses ARP (Address Resolution Protocol)
3. ARP resolves the IP address to a MAC address
4. Communication happens using Ethernet frames (Layer 2)

Mapping:

IP address → MAC address (via ARP)

---

## ARP (Address Resolution Protocol)

ARP is the mechanism that links Layer 3 (IP) to Layer 2 (MAC).

It maintains a local cache of IP-to-MAC mappings.

### Pentesting relevance:
- ARP spoofing / poisoning (Man-in-the-Middle attacks)
- Traffic interception inside LANs
- Host impersonation

---

## MAC Address in Pentesting

### 1. Local Network Identification
MAC addresses are required for communication within a LAN. Without them, devices cannot exchange frames.

---

### 2. MAC Spoofing

MAC addresses can be modified to impersonate another device.

Use cases:
- Bypassing MAC filtering
- Impersonating trusted devices
- Evading basic network access controls

Example (Linux):

ifconfig eth0 down  
macchanger -r eth0  
ifconfig eth0 up  

---

### 3. Network Reconnaissance Value

MAC addresses can provide useful intelligence during internal enumeration:

- Vendor identification (via OUI lookup)
- Detection of virtual machines (VMware, VirtualBox, Hyper-V)
- Network segmentation clues
- Device type inference

---

## Key Takeaways

- MAC addresses operate at Layer 2 (Data Link Layer)
- They are only used within local networks (not routable)
- IP addresses are translated into MAC addresses via ARP
- ARP is a key target for MITM attacks in internal environments
- MAC spoofing is a common technique in local network attacks
