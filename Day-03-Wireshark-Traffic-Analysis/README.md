# Day 03 — Network Traffic Analysis with Wireshark

## Overview
Captured and analyzed live network traffic using Wireshark to demonstrate
the critical security difference between plain-text and encrypted protocols.

## Files in This Folder
| File | Description |
|---|---|
| `day3_wireshark_capture.pcapng` | Full Wireshark packet capture file |
| `Day3_Traffic_Analysis_Report_Eria_Mutasa.docx` | Professional analysis report |
| `day3_observations.txt` | Analyst observation notes |
| Screenshots | Wireshark filter and capture screenshots |

## Key Findings
- 🔴 Telnet credentials captured in plain text
- 🟠 FTP anonymous login with blank password
- 🟡 HTTP server version exposed in headers
- ✅ SSH traffic fully encrypted — unreadable
