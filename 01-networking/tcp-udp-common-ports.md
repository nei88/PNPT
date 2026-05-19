# TCP & UDP Common Ports (Pentesting Reference)

> High-frequency ports encountered during external and internal reconnaissance, focused on real enumeration value and attack paths.

---

## Priority-Based Classification

Not all open ports have equal importance. Prioritization depends on environment context (external vs internal, domain-joined vs standalone).

### Tier 1: High-Value Targets (Always Investigate First)

- 445 (SMB)
- 88 (Kerberos)
- 389 / 636 (LDAP / LDAPS)
- 3389 (RDP)
- 22 (SSH)
- 80 / 443 (HTTP / HTTPS)

These services are most commonly associated with:
- Initial access vectors
- Credential compromise
- Active Directory attack paths
- Lateral movement
- Remote code execution opportunities

---

## TCP Ports

### Web Services (External Attack Surface)

| Port | Service | Notes |
|------|--------|------|
| 80   | HTTP    | Common entry point; vulnerable to misconfigurations, injection flaws, auth bypass |
| 443  | HTTPS   | Same attack surface as HTTP but encrypted |
| 8080 | HTTP-alt | Often exposes admin panels, internal apps, dev services |
| 8443 | HTTPS-alt | Frequently Java/Tomcat/enterprise management interfaces |

Corrected note:
- Web ports are not inherently “attackable”; risk depends entirely on application logic and exposure.

---

### Remote Access

| Port | Service | Notes |
|------|--------|------|
| 22   | SSH     | Strongly secured by default, but vulnerable to weak credentials, key misuse |
| 23   | Telnet  | Insecure (cleartext), rarely used in modern environments |
| 3389 | RDP     | High-value internal access target; often exposed with weak credentials or reused passwords |

Added improvement:
- RDP is more valuable internally than externally in most real engagements.

---

### Active Directory / Windows Infrastructure

| Port | Service | Notes |
|------|--------|------|
| 445  | SMB     | Critical for enumeration, shares, NTLM relay, lateral movement |
| 139  | NetBIOS | Legacy service; useful for host discovery and enumeration |
| 88   | Kerberos | Ticket-based authentication; Kerberoasting / AS-REP roasting |
| 389  | LDAP    | Domain enumeration, user/group discovery |
| 636  | LDAPS   | Encrypted LDAP; still useful for authenticated queries |
| 3268 | Global Catalog | Forest-wide AD queries |
| 135  | MSRPC   | Used in many Windows RPC operations; often important in lateral movement |
| 593  | RPC over HTTP | Less common but still appears in enterprise environments |

Important correction:
- MSRPC (135) is missing from most beginner notes but is frequently relevant in real Windows enumeration.

---

### File Transfer / Legacy Services

| Port | Service | Notes |
|------|--------|--------|
| 21   | FTP     | Anonymous access, weak credentials, file exposure |
| 69   | TFTP    | Unauthenticated file transfer; often used in network devices |
| 111  | RPCBind | Linux service mapping; often leads to NFS exposure |
| 2049 | NFS     | File sharing; misconfigurations can expose full filesystem |

Added improvement:
- NFS (2049) is a major missing real-world attack surface in many notes.

---

### Databases

| Port | Service | Notes |
|------|--------|------|
| 3306 | MySQL   | Web backend compromise, credential reuse |
| 5432 | PostgreSQL | Misconfigured authentication or exposed DB |
| 1433 | MSSQL   | Can allow command execution depending on configuration |
| 27017 | MongoDB | Often exposed without authentication |

Correction:
- MSSQL exploitation is not “default RCE via xp_cmdshell”; it depends on permissions and configuration.

---

## UDP Ports

### Network Services & Discovery

| Port | Service | Notes |
|------|--------|------|
| 53   | DNS     | Zone transfers, internal host discovery, subdomain enumeration |
| 67/68 | DHCP   | Network assignment visibility |
| 69   | TFTP    | Firmware/config leaks |
| 123  | NTP     | Time-based attacks, amplification abuse |
| 161  | SNMP    | Device enumeration; weak community strings are common |
| 162  | SNMP Trap | Monitoring alerts (less useful offensively but still relevant) |

---

## Missing But Important Ports (Added)

These are frequently encountered in real engagements:

| Port | Service | Notes |
|------|--------|------|
| 25   | SMTP    | Email relay misconfigurations, enumeration |
| 110  | POP3    | Credential exposure in legacy systems |
| 143  | IMAP    | Email access, sometimes weak auth |
| 5985 | WinRM HTTP | Remote Windows management (PowerShell attacks) |
| 5986 | WinRM HTTPS | Secure version of WinRM |
| 5601 | Kibana  | Dashboard exposure (ELK stack misconfig) |
| 9200 | Elasticsearch | Sensitive data exposure if unauthenticated |

---

## Enumeration Mindset

Open ports should be treated as potential trust boundaries, not just services.

### Practical Workflow

1. Identify service and version (nmap -sV)
2. Determine authentication model
3. Test for anonymous or default access
4. Enumerate users, shares, endpoints, or metadata
5. Check for known misconfigurations or exploits
6. Map findings to an attack path (initial access → privilege escalation → lateral movement)

---

## Key Takeaways

- SMB, Kerberos, LDAP, and MSRPC are core Active Directory attack surfaces
- Web services are only as dangerous as their application logic and configuration
- UDP services are frequently under-scanned and often overlooked
- Real-world exploitation depends on configuration, not port numbers alone
- Internal network enumeration is significantly more powerful than external scanning

---

## Note

This document is intended as a field reference during reconnaissance and enumeration, not as introductory material.
