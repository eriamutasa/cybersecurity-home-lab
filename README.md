# 🛡️ Cybersecurity Home Lab — Eria Mutasa

> *"A SOC Analyst doesn't clock out at midnight. Threats don't wait for business hours — and neither do I."*

A hands-on cybersecurity home lab documenting real-world attack simulation, threat detection, SIEM configuration, and vulnerability analysis — built from zero to demonstrate practical SOC analyst skills that go beyond the classroom.

---

## 🖥️ Lab Environment

| Component | Details |
|---|---|
| Host OS | Windows 11 |
| Virtualization | Oracle VirtualBox |
| Attacker Machine | Kali Linux 2025.4 |
| Target Machine | Metasploitable2 (intentionally vulnerable) |
| SIEM Platform | Splunk Enterprise (Free License) |
| Network Type | Isolated Host-Only — zero internet exposure |

---

## 📁 Exercises & Progress

| # | Topic | Tools Used | Status |
|---|---|---|---|
| 01 | Lab Setup & Environment Configuration | VirtualBox, Kali, Metasploitable2, Splunk | ✅ Complete |
| 02 | Network Reconnaissance | Nmap 7.95 | ✅ Complete |
| 03 | Network Traffic Analysis | Wireshark | ✅ Complete |
| 04 | SIEM Setup & Log Ingestion | Splunk | 🔄 In Progress |
| 05 | Attack Simulation & Detection | Hydra, Splunk | ⏳ Upcoming |
| 06 | Vulnerability Scanning | OpenVAS | ⏳ Upcoming |

---

## 🔍 Day 02 — Network Reconnaissance with Nmap

**Objective:** Perform full network reconnaissance against Metasploitable2 to enumerate open ports, running services, software versions, and OS details — exactly as an attacker would before launching an exploit.

**Key Findings:**
- 🔴 **7 CRITICAL** vulnerabilities identified including an open root shell on port 1524 — no credentials required
- 🔴 2 known backdoors: vsftpd 2.3.4 `CVE-2011-2523` and UnrealIRCd `CVE-2010-2075`
- 🟠 Multiple databases (MySQL port 3306, PostgreSQL port 5432) exposed directly on the network
- 🟡 Legacy plain-text services running: Telnet, rsh, rexec, rlogin
- 📡 23 open TCP ports discovered in under 60 seconds

**Commands Used:**
```bash
# Host discovery
nmap -sn 192.168.56.101

# Basic port scan
nmap 192.168.56.101

# Service & version detection
nmap -sV 192.168.56.101

# Aggressive scan with OS detection
nmap -A -T4 192.168.56.101

# Full port scan — all 65,535 ports
nmap -p- 192.168.56.101

# Save results to file
nmap -A -T4 -oN metasploitable_scan.txt 192.168.56.101
```

**Deliverables:**
- 📄 [Full Nmap Scan Output](Day-02-Nmap-Reconnaissance/metasploitable_scan.txt)
- 📋 [Professional Recon Report](Day-02-Nmap-Reconnaissance/Day2_Recon_Report_Eria_Mutasa.docx)

---

## 📡 Day 03 — Network Traffic Analysis with Wireshark

**Objective:** Capture and analyze live network traffic to produce visual, irrefutable proof of the security difference between plain-text and encrypted protocols — and demonstrate credential interception techniques used by real attackers.

**Key Findings:**
- 🔴 **Telnet (port 23):** Full username and password captured in plain text via TCP Stream — zero decryption needed
- 🟠 **FTP (port 21):** Anonymous login accepted with a blank password — all file activity visible on the network
- 🟡 **HTTP (port 80):** Apache/2.2.8 server version exposed in response headers — aids attacker enumeration
- ✅ **SSH (port 22):** TCP stream shows only encrypted gibberish — credentials and commands completely unreadable
- 🔵 **SYN packets:** Real-time connection attempts captured — proving Nmap scan detection is possible

**Wireshark Filters Mastered:**
```
icmp                                        → Host discovery traffic
telnet                                      → Plain-text remote sessions
ftp                                         → Unencrypted file transfers
http                                        → Web traffic analysis
tcp.port == 22                              → SSH encrypted sessions
ip.addr == 192.168.56.101                   → Isolate one host
tcp.flags.syn == 1 && tcp.flags.ack == 0   → Detect port scanning
frame contains "password"                   → Hunt for credential exposure
```

**Deliverables:**
- 📦 [Wireshark Packet Capture (.pcapng)](Day-03-Wireshark-Traffic-Analysis/day3_wireshark_capture.pcapng)
- 📋 [Professional Traffic Analysis Report](Day-03-Wireshark-Traffic-Analysis/Day3_Traffic_Analysis_Report_Eria_Mutasa.docx)
- 📝 [Analyst Observation Notes](Day-03-Wireshark-Traffic-Analysis/day3_observations.txt)

---

## 🎯 Skills Demonstrated

**Security Operations**

![Nmap](https://img.shields.io/badge/Nmap-Reconnaissance-blue)
![Wireshark](https://img.shields.io/badge/Wireshark-Traffic%20Analysis-blue)
![Splunk](https://img.shields.io/badge/Splunk-SIEM-blue)
![OpenVAS](https://img.shields.io/badge/OpenVAS-Vulnerability%20Scanning-blue)

**Technical Skills**

`Network Reconnaissance` `Port Scanning` `Service Enumeration` `OS Detection`
`Packet Analysis` `Protocol Analysis` `CVE Research` `Vulnerability Assessment`
`Incident Response` `Log Analysis` `SOC Operations` `Technical Report Writing`

---

## 📜 Certifications

| Certification | Status | Date |
|---|---|---|
| CompTIA Security+ (SY0-701) | ✅ Certified | Feb 2026 |
| CompTIA CySA+ (CS0-003) | 🔄 In Progress | 2026 |
| Google Cybersecurity Professional Certificate | ✅ Certified | Jan 2025 |

---

## 🎓 Education

| Degree | Institution | Status |
|---|---|---|
| MS in Cybersecurity — GPA 4.0 | Quinnipiac University, CT | 🔄 In Progress |
| BSc (Hons) Information Technology | Chinhoyi University of Technology | ✅ First Class |

---

## 📬 Contact & Links

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Eria%20Mutasa-blue?logo=linkedin)](https://www.linkedin.com/in/eria-mutasa-547929193)
[![Email](https://img.shields.io/badge/Email-eriamutasa27%40gmail.com-red?logo=gmail)](mailto:eriamutasa27@gmail.com)

---

*This lab is actively being built. New exercises added regularly.*
*All activities performed in an isolated environment — no real systems affected.*
