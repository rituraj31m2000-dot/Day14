# Task 14: Common Network Ports Reference Sheet

**Internship:** Veda Technology, Cyber Security Track (Level 1, Day 14)
**Intern:** Ritu Raj
**Tools used:** Browser, Google Sheets

## Objective
Understand common network services by building a quick reference sheet of commonly used ports and protocols.

## Approach
1. Researched well-known ports using the IANA service name and port number registry and protocol documentation (RFCs).
2. Grouped ports by service category (web, email, remote access, name services, directory/authentication, databases, VPN).
3. Recorded for each port: port number, protocol, transport (TCP/UDP), purpose, and whether traffic is encrypted.
4. Built the sheet in Google Sheets and exported it as `common_ports.csv`.
5. Added security notes on risky, cleartext services.

## Port Reference Sheet

### Web
| Port | Protocol | Transport | Purpose | Secure? |
|------|----------|-----------|---------|---------|
| 80 | HTTP | TCP | Web traffic | No |
| 443 | HTTPS | TCP (UDP for QUIC/HTTP3) | Encrypted web traffic | Yes (TLS) |
| 8080 / 8443 | HTTP-alt / HTTPS-alt | TCP | Proxies, dev and alternate web servers | No / Yes |

### Remote access and file transfer
| Port | Protocol | Transport | Purpose | Secure? |
|------|----------|-----------|---------|---------|
| 20/21 | FTP | TCP | File transfer (data/control) | No |
| 22 | SSH / SFTP / SCP | TCP | Secure remote shell and file transfer | Yes |
| 23 | Telnet | TCP | Remote shell | No |
| 69 | TFTP | UDP | Simple file transfer | No |
| 445 | SMB | TCP | Windows file sharing | Depends on version |
| 3389 | RDP | TCP/UDP | Windows remote desktop | Yes (if configured) |
| 5900 | VNC | TCP | Remote desktop | Weak by default |

### Email
| Port | Protocol | Transport | Purpose | Secure? |
|------|----------|-----------|---------|---------|
| 25 | SMTP | TCP | Mail server to server | No |
| 587 | SMTP submission | TCP | Client sends mail (STARTTLS) | Yes |
| 465 | SMTPS | TCP | SMTP over TLS | Yes |
| 110 / 995 | POP3 / POP3S | TCP | Retrieve mail | No / Yes |
| 143 / 993 | IMAP / IMAPS | TCP | Retrieve mail | No / Yes |

### Name, address and time services
| Port | Protocol | Transport | Purpose | Secure? |
|------|----------|-----------|---------|---------|
| 53 | DNS | UDP (queries), TCP (zone transfers, large replies) | Domain name resolution | No (unless DoT/DoH) |
| 67/68 | DHCP | UDP | Automatic IP assignment | No |
| 123 | NTP | UDP | Time synchronization | No |
| 161/162 | SNMP | UDP | Network device monitoring | v3 only |
| 514 | Syslog | UDP | Log forwarding | No |

### Directory and authentication
| Port | Protocol | Transport | Purpose | Secure? |
|------|----------|-----------|---------|---------|
| 88 | Kerberos | TCP/UDP | Ticket-based authentication | Yes |
| 389 / 636 | LDAP / LDAPS | TCP | Directory services | No / Yes |
| 1812/1813 | RADIUS | UDP | Network access authentication/accounting | Partial |
| 49 | TACACS+ | TCP | Device administration authentication | Yes |

### Databases
| Port | Service |
|------|---------|
| 1433 | Microsoft SQL Server |
| 1521 | Oracle |
| 3306 | MySQL / MariaDB |
| 5432 | PostgreSQL |
| 6379 | Redis |
| 27017 | MongoDB |

### VPN and tunneling
| Port | Protocol | Transport |
|------|----------|-----------|
| 500 | IKE (IPsec) | UDP |
| 4500 | IPsec NAT-T | UDP |
| 1194 | OpenVPN | UDP/TCP |
| 51820 | WireGuard | UDP |
| 1723 | PPTP | TCP |

### Port ranges
- **0-1023:** well-known (system) ports
- **1024-49151:** registered ports
- **49152-65535:** dynamic / ephemeral ports

## Interview Questions

**What is port 443?**
The default port for HTTPS, which is HTTP secured with TLS encryption.

**What is port 53?**
The default port for DNS. It uses UDP for normal queries and TCP for zone transfers and responses too large for UDP.

**What is SSH?**
Secure Shell is an encrypted protocol (TCP port 22) for remote command-line login, secure file transfer (SFTP/SCP), and tunneling. It replaces insecure Telnet.

## Security Notes
- Telnet, FTP, HTTP, POP3 and SNMPv1/v2 send data (often credentials) in cleartext. Use SSH, SFTP, HTTPS, POP3S and SNMPv3 instead.
- SMB (445), RDP (3389) and Telnet (23) are heavily targeted by attackers and should not be exposed directly to the internet.
- Closing unused ports and filtering with a firewall reduces the attack surface.

## Outcome
Created a categorized reference sheet of common ports and protocols, covering HTTP, HTTPS, DNS, SSH and SMTP along with other widely used services, and learned which ports are secure and which are risky.

## Files
- `README.md`: approach and port reference
- `Task14_Report.md`: task report
- `common_ports.csv`: sheet exported from Google Sheets

## References
- IANA Service Name and Transport Protocol Port Number Registry
- 
