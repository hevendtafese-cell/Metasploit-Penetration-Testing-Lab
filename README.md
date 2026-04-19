# Metasploit Framework Penetration Testing Lab
> **Target:** Metasploitable 2  
> **Attacker OS:** Kali Linux  
> **Environment:** VirtualBox NAT Network  

---

## Overview

This repository documents a full penetration test conducted against **Metasploitable 2** using the **Metasploit Framework**. The assessment follows a real-world penetration testing lifecycle across seven phases from initial reconnaissance through to privilege escalation, pivoting, and persistent backdoor creation.

The goal of this project is to evaluate the Metasploit Framework's architectural capabilities, demonstrate its effectiveness as an integrated security platform, and identify its limitations in a controlled environment.

---

## Environment

| Role     | OS               | Application                      | IP Address  |
|----------|------------------|-----------------------------------|-------------|
| Attacker | Kali Linux       | Metasploit Framework              | `10.0.2.6`  |
| Target   | Metasploitable 2 | Multiple Vulnerable Services      | `10.0.2.7`  |

Both machines were deployed in **VirtualBox** using a **NAT Network** to ensure network isolation.

---

## Table of Contents

| Phase | File | Description |
|-------|------|-------------|
| Phase 1 | [01-reconnaissance.md](./01-reconnaissance.md) | Host discovery, db_nmap scanning, SYN scan |
| Phase 2 | [02-enumeration.md](./02-enumeration.md) | FTP, SMB, HTTP, SMTP service enumeration |
| Phase 3 | [03-credential-discovery.md](./03-credential-discovery.md) | Brute-force login across FTP, SMB, SSH, VNC, Tomcat |
| Phase 4 | [04-exploitation.md](./04-exploitation.md) | Six successful exploits against Metasploitable 2 |
| Phase 5 | [05-privilege-escalation.md](./05-privilege-escalation.md) | Local exploit suggester and root escalation |
| Phase 6 | [06-pivoting.md](./06-pivoting.md) | Internal network pivoting via autoroute |
| Phase 7 | [07-persistence.md](./07-persistence.md) | Hash extraction, John the Ripper, SSH backdoor |

---

## Exploits Demonstrated

| Vulnerability | CVE | Service | Result |
|---|---|---|---|
| vsftpd 2.3.4 Backdoor | CVE-2011-2523 | FTP | Root shell |
| Samba usermap_script | CVE-2007-2447 | SMB | Reverse shell |
| PHP CGI Argument Injection | CVE-2012-1823 | HTTP | Meterpreter session |
| Java RMI Server | — | RMI (1099) | Meterpreter session |
| PostgreSQL Payload Execution | — | PostgreSQL (5432) | Meterpreter session |
| Apache Tomcat WAR Upload | — | Tomcat (8180) | Meterpreter session |

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Metasploit Framework | Core exploitation and post-exploitation platform |
| Nmap / `db_nmap` | Reconnaissance and service version scanning |
| Nessus | Vulnerability scanning and CVE identification |
| VNCViewer | Graphical access verification |
| John the Ripper | Offline password hash cracking |
| Hydra | FTP brute-force comparison with MSF |

---

## Key Findings

- **6 services** successfully exploited on Metasploitable 2
- **Root-level access** achieved via vsftpd backdoor and privilege escalation (CVE-2009-1185)
- **Password hashes** extracted from `/etc/shadow` and cracked with John the Ripper
- **SSH backdoor** created and verified via passwordless key-based authentication
- **Internal network pivoting** demonstrated through MSF autoroute

---

## Disclaimer

> This project was conducted in a fully isolated virtual lab environment for academic purposes only. All testing was performed against intentionally vulnerable systems (Metasploitable 2). No real systems or networks were targeted at any point. Unauthorised use of these techniques against live systems without explicit permission is illegal and unethical.
