# Cybersecurity-intern-week2
# 🔎 Cybersecurity Reconnaissance & OSINT Lab

![Kali Linux](https://img.shields.io/badge/OS-Kali%20Linux-557C94?logo=kalilinux&logoColor=white)
![VirtualBox](https://img.shields.io/badge/Virtualization-VirtualBox-183A61?logo=virtualbox&logoColor=white)
![Maltego](https://img.shields.io/badge/OSINT-Maltego-orange)
![Nmap](https://img.shields.io/badge/Network-Nmap-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview

This project was carried out as part of my cybersecurity training and practical lab work.

The objective was to understand and practice **reconnaissance, OSINT, DNS enumeration, web technology identification, WAF detection, WHOIS analysis, and network discovery** using Kali Linux.

All activities were performed in a controlled learning environment and focused on understanding how different reconnaissance tools collect and correlate publicly available information.

---

# 🎯 Objectives

The main objectives of this practical lab were:

- Understand the reconnaissance phase of a cybersecurity assessment.
- Collect publicly available information about a domain.
- Perform DNS enumeration.
- Identify IP addresses and DNS records.
- Identify web technologies and frameworks.
- Detect the presence of Web Application Firewalls (WAF).
- Perform WHOIS lookups.
- Discover hosts on a local network.
- Visualize relationships between collected information using Maltego.
- Understand how different reconnaissance tools complement each other.

---

# 🖥️ Lab Environment

## Operating System

- **Kali Linux**

## Virtualization

- **Oracle VirtualBox**

## Tools Used

| Tool | Purpose |
|------|---------|
| `curl` | HTTP headers and server information |
| `nslookup` | DNS queries |
| `dnsrecon` | DNS enumeration |
| `whois` | Domain registration information |
| `WhatWeb` | Web technology identification |
| `WAFW00F` | WAF detection |
| `theHarvester` | OSINT and information gathering |
| `Maltego` | OSINT visualization and relationship mapping |
| `Nmap` | Network discovery and enumeration |
| `Zenmap` | Graphical interface for Nmap |

---

# 🔍 1. HTTP Header Enumeration — cURL

The first step was to inspect the HTTP response headers of the target domain.

### Command

```bash
curl -I https://networkwalks.com
