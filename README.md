# 🛡️ Cybersecurity Home Lab — Eria Mutasa

A hands-on cybersecurity home lab documenting a real attack simulation, 
threat detection, SIEM configuration, and vulnerability analysis.
Built to develop practical SOC analyst skills.

## 🖥️ Lab Environment

| Component | Details |
|---|---|
| Host OS | Windows 11 |
| Virtualization | VirtualBox |
| Attacker Machine | Kali Linux |
| Target Machine | Metasploitable2 (intentionally vulnerable) |
| SIEM | Splunk Enterprise (Free License) |
| Network | Isolated Host-Only (no internet exposure) |

## 📁 Exercises

| Day | Topic | Tools Used | Status |
|---|---|---|---|
| Day 02 | Network Reconnaissance | Nmap 7.95 | ✅ Complete |
| Day 03 | Traffic Analysis | Wireshark | ✅ Complete |
| Day 04 | SIEM Setup & Log Ingestion | Splunk | 🔄 In Progress |
| Day 05 | Attack Simulation & Detection | Hydra, Splunk | ⏳ Upcoming |
| Day 06 | Vulnerability Scanning | OpenVAS | ⏳ Upcoming |

## 🔍 Day 02 — Network Reconnaissance with Nmap

**Objective:** Perform full network reconnaissance against Metasploitable
to enumerate open ports, running services, software versions, and OS details.

**Key Findings:**
- 23 open TCP ports discovered
- 7 CRITICAL vulnerabilities identified including an open root shell (port 1524)
- 2 known backdoors found: vsftpd 2.3.4 (CVE-2011-2523) and UnrealIRCd (CVE-2010-2075)
- Multiple databases (MySQL, PostgreSQL) exposed directly on the network
- Legacy plain-text services running: Telnet, rsh, rexec, rlogin

**Commands Used:**
\```bash
# Host discovery
nmap -sn 192.168.56.101

# Basic port scan
nmap 192.168.56.101

# Version detection
nmap -sV 192.168.56.101

# Aggressive scan with OS detection
nmap -A -T4 192.168.56.101

# Full port scan
nmap -p- 192.168.56.101

# Save results
nmap -A -T4 -oN metasploitable_scan.txt 192.168.56.101
\```

**Deliverables:**
- 📄 [Full Nmap Scan Output](Day-02-Nmap-Reconnaissance/metasploitable_scan.txt)
- 📋 [Professional Recon Report (DOCX)](Day-02-Nmap-Reconnaissance/Day2_Recon_Report_Eria_Mutasa.docx)

## 🔍 Day 03 — Network Traffic Analysis with Wireshark

**Objective:** Capture and analyze live network traffic to demonstrate
the critical security difference between plain-text and encrypted protocols.

**Key Findings:**
- Telnet (port 23): Full credentials captured in plain text via TCP Stream
- FTP (port 21): Anonymous login with blank password — all activity visible
- HTTP (port 80): Server version Apache/2.2.8 exposed in response headers
- SSH (port 22): Complete encryption — TCP stream shows only gibberish
- SYN packets captured proving real-time detection of connection attempts

**Wireshark Filters Mastered:**
\```
icmp
telnet
ftp
http
tcp.port == 22
ip.addr == 192.168.56.101
tcp.flags.syn == 1 && tcp.flags.ack == 0
frame contains "password"
\```

**Deliverables:**
- 📄 [Packet Capture File](Day-03-Wireshark-Traffic-Analysis/day3_wireshark_capture.pcapng)
- 📋 [Professional Traffic Analysis Report](Day-03-Wireshark-Traffic-Analysis/Day3_Traffic_Analysis_Report_Eria_Mutasa.docx)
- 📝 [Observation Notes](Day-03-Wireshark-Traffic-Analysis/day3_observations.txt)
```

## 🎯 Skills Demonstrated

`Nmap` `Network Reconnaissance` `Port Scanning` `Service Enumeration`
`OS Detection` `CVE Research` `Vulnerability Assessment` `Technical Reporting`
`Splunk` `Wireshark` `Incident Response` `SOC Operations`

## 📜 Certifications
- ✅ CompTIA Security+ (SY0-701) — Feb 2026
- 🔄 CompTIA CySA+ (CS0-003) — In Progress
- ✅ Google Cybersecurity Professional Certificate — Jan 2025

## 📬 Contact
- 💼 [LinkedIn](https://www.linkedin.com/in/eria-mutasa-547929193)
- 📧 eriamutasa27@gmail.com
