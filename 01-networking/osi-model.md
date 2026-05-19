# OSI Model (Pentesting Reference)

> Structured breakdown of the OSI model with correct layer responsibilities and their relevance in penetration testing, network enumeration, and security analysis.

---

## OSI Model Overview

The OSI (Open Systems Interconnection) model is a 7-layer conceptual framework that describes how data moves from one system to another over a network.

In penetration testing, it is used to:
- Understand where attacks occur in the communication stack
- Map tools and techniques to network behavior
- Identify where security controls operate (firewalls, proxies, encryption, segmentation)
- Structure reconnaissance and exploitation workflows

---

## Layer 7 – Application

### What it is
This is the layer closest to the user. It includes network services and applications that directly interact with data.

Common protocols:
- HTTP / HTTPS
- DNS
- SMB
- FTP
- SSH (application-level behavior)
- APIs (REST, GraphQL)

### Why it matters in pentesting
Most real vulnerabilities exist here because this is where logic is implemented.

Attack surface includes:
- Web applications
- APIs
- Authentication systems
- File upload/download systems

Common attacks:
- SQL injection
- Command injection
- SSRF
- Authentication bypass
- File upload exploitation
- API abuse

---

## Layer 6 – Presentation

### What it is
Responsible for data formatting, encoding, compression, and encryption.

Includes:
- TLS / SSL encryption
- Encoding formats (Base64, UTF-8)
- Serialization formats (JSON, XML, YAML)

### Why it matters in pentesting
This layer affects how data is interpreted and secured in transit.

Security relevance:
- TLS misconfigurations (weak ciphers, invalid certificates)
- Data encoding bypass techniques
- Encryption weaknesses or improper implementation

---

## Layer 5 – Session

### What it is
Manages sessions between systems, including maintaining, opening, and closing communication sessions.

Includes:
- Session tokens
- Authentication sessions
- Connection persistence mechanisms

### Why it matters in pentesting
Session handling flaws often lead to authentication compromise.

Common attacks:
- Session hijacking
- Cookie theft
- Token replay attacks
- Broken session management

---

## Layer 4 – Transport

### What it is
Responsible for end-to-end communication between hosts.

Protocols:
- TCP (reliable, connection-based)
- UDP (fast, connectionless)

Common ports (examples):
- 22 SSH
- 80 HTTP
- 443 HTTPS
- 445 SMB
- 3389 RDP
- 53 DNS

### Why it matters in pentesting
This layer is heavily involved in scanning, enumeration, and filtering detection.

Used for:
- Port scanning (Nmap)
- Service fingerprinting
- Firewall rule analysis
- TCP vs UDP behavior testing

Important distinction:
Transport layer defines how data is delivered, not what service is running.

---

## Layer 3 – Network

### What it is
Responsible for logical addressing and routing between networks.

Protocols:
- IP (IPv4 / IPv6)
- ICMP
- ARP (boundary protocol between Layer 2 and Layer 3)

### Why it matters in pentesting
This layer is key for discovering and mapping networks.

Used for:
- Host discovery (ping sweeps)
- Subnet enumeration
- Routing analysis (traceroute)
- Network segmentation mapping

---

## Layer 2 – Data Link

### What it is
Handles communication inside a local network using MAC addresses.

Core concepts:
- MAC addressing
- Ethernet switching
- Frame delivery within LANs

### Why it matters in pentesting
Critical for local network attacks and internal reconnaissance.

Attack techniques:
- ARP spoofing / poisoning
- MAC spoofing
- Local traffic sniffing (promiscuous mode)
- VLAN boundary testing

Important concept:
MAC addresses only function within the same local network segment (broadcast domain).

---

## Layer 1 – Physical

### What it is
Represents physical transmission of data over hardware.

Includes:
- Cables (Ethernet, fiber)
- Wireless signals (Wi-Fi)
- Network hardware (routers, switches, NICs)

### Why it matters in pentesting
Mostly relevant in physical or wireless security assessments.

Attack surface:
- Rogue access points
- Wi-Fi cracking
- Physical network access
- Cable tapping (advanced scenarios)

---
