# TCP & UDP Common Ports (Pentesting Reference)

> Practical reference of commonly encountered TCP/UDP ports during reconnaissance, enumeration, and penetration testing.

---

## Overview

In penetration testing, identifying open ports and understanding their associated services is critical for:
- Attack surface mapping
- Service enumeration
- Vulnerability identification
- Exploitation planning

This document summarizes commonly encountered TCP/UDP ports and their security relevance.

---

## TCP vs UDP Summary

| Protocol | Key Property | Usage in Pentesting |
|----------|-------------|----------------------|
| TCP      | Connection-oriented, reliable | Most services (web, SSH, SMB, databases) |
| UDP      | Connectionless, faster, no guarantee | DNS, VoIP, streaming, discovery protocols |

---

## Common TCP Ports

### Web & Application Services

| Port | Service | Notes |
|------|--------|------|
| 80   | HTTP    | Unencrypted web traffic |
| 443  | HTTPS   | Encrypted web traffic (TLS) |
| 8080 | HTTP-alt | Common for web apps, proxies, admin panels |
| 8443 | HTTPS-alt | Alternative TLS web services |

---

### Remote Access

| Port | Service | Notes |
|------|--------|------|
| 22   | SSH     | Secure shell access (Linux/Unix) |
| 23   | Telnet  | Insecure remote access (cleartext) |
| 3389 | RDP     | Windows Remote Desktop Protocol |

---

### File Sharing & Enumeration Targets

| Port | Service | Notes |
|------|--------|------|
| 21   | FTP     | File transfer, often misconfigured |
| 139  | NetBIOS | Legacy Windows sharing |
| 445  | SMB     | Critical for Windows enumeration & AD attacks |

---

### Directory / Authentication Services

| Port | Service | Notes |
|------|--------|------|
| 88   | Kerberos | Authentication in Active Directory |
| 389  | LDAP     | Directory services (unencrypted) |
| 636  | LDAPS    | Secure LDAP (TLS) |
| 3268 | Global Catalog LDAP | AD forest-wide queries |

---

### Databases

| Port | Service | Notes |
|------|--------|------|
| 1433 | MSSQL    | Microsoft SQL Server |
| 3306 | MySQL    | Common web database backend |
| 5432 | PostgreSQL | Open-source database |
| 27017 | MongoDB | NoSQL database |

---

### Miscellaneous / Infrastructure

| Port | Service | Notes |
|------|--------|------|
| 53   | DNS     | Domain name resolution (TCP/UDP) |
| 25   | SMTP    | Email sending |
| 110  | POP3    | Email retrieval |
| 143  | IMAP    | Email synchronization |
| 111  | RPCBind | Linux RPC services (often enumerated) |

---

## Common UDP Ports

| Port | Service | Notes |
|------|--------|------|
| 53   | DNS     | Zone transfers, enumeration target |
| 67/68 | DHCP   | Network IP assignment |
| 69   | TFTP    | Simple file transfer (often misconfigured) |
| 123  | NTP     | Time synchronization (can be abused for amplification) |
| 161  | SNMP    | Network device enumeration |
| 162  | SNMP Trap | Monitoring alerts |

---

## High-Value Pentesting Targets

These services are often prioritized during enumeration:

- **445 (SMB)** → Windows shares, NTLM relay, enum users/groups
- **88 (Kerberos)** → Kerberoasting, AS-REP roasting
- **389 (LDAP)** → Domain enumeration
- **3389 (RDP)** → Brute force / credential reuse
- **22 (SSH)** → Credential-based access
- **161 (SNMP)** → Network info leakage

---

## Enumeration Strategy (Practical Use)

When a scan reveals open ports:

1. Identify service version (e.g., `nmap -sV`)
2. Check for anonymous access (FTP, SMB, LDAP)
3. Test default credentials
4. Enumerate shares / users / directories
5. Research service-specific exploits
6. Map findings to attack path (priv esc / lateral movement)

---

## Notes

- Open ports are only entry points — misconfiguration determines exploitability
- SMB, Kerberos, and LDAP are especially critical in Active Directory environments
- UDP services are often under-scanned but can leak important information

---
