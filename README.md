# 🔐 Penetration Testing & Reconnaissance Lab

## Networkwalks — Week 02

> **Footprinting • OSINT • Web Reconnaissance • GHDB • Maltego • Network Discovery**

![Kali Linux](https://img.shields.io/badge/OS-Kali%20Linux-557C94?logo=kalilinux&logoColor=white)
![VirtualBox](https://img.shields.io/badge/Lab-Oracle%20VirtualBox-183A61?logo=virtualbox&logoColor=white)
![Cybersecurity](https://img.shields.io/badge/Focus-Cybersecurity-red)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 👤 About This Project

This repository documents my practical experience during **Week 02 of the Networkwalks Cybersecurity Program**.

The objective was to move from cybersecurity theory to practical reconnaissance by learning how to collect publicly available information, enumerate DNS infrastructure, fingerprint web technologies, analyze HTTP headers, detect WAFs, correlate OSINT information, perform GHDB reconnaissance, research vulnerabilities, and discover hosts on an authorized local network.

All activities were performed for educational purposes and within an authorized scope.

---

# ⚠️ Ethical & Legal Disclaimer

This repository is intended for **cybersecurity education, authorized security testing, and defensive research only**.

Activities were performed against:
1. **Networkwalks**, within the authorized training environment.
2. **My own local network**, for Nmap/Zenmap practice.

No unauthorized exploitation, credential bypass, destructive activity, or unauthorized access was performed.

Publicly accessible resources discovered during the GHDB exercise are not reproduced here where doing so could expose sensitive information, devices, or individuals.

> **Never scan, enumerate, exploit, or access systems without explicit authorization.**

---

# 🎯 Project Scope

| Phase | Activity |
|---|---|
| Phase 1 | Reconnaissance & Footprinting |
| Phase 2 | OSINT & Information Gathering |
| Phase 3 | Network Scanning & Discovery |

### Main Target
```text
networkwalks.com
```

### Authorized Local Network
```text
192.168.100.0/24
```

---

# 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Kali Linux** | Security assessment environment |
| **WHOIS** | Domain registration and name-server information |
| **WhatWeb** | Web technology fingerprinting |
| **Nslookup** | DNS resolution and IP discovery |
| **cURL** | HTTP response/header analysis |
| **WAFW00F** | WAF detection |
| **DNSRecon** | DNS record enumeration |
| **Maltego** | OSINT correlation and visualization |
| **theHarvester** | Open-source intelligence gathering |
| **GHDB** | Google dorking and search-engine reconnaissance |
| **Exploit-DB** | Vulnerability and exploit research |
| **Nmap / Zenmap** | Network discovery and host enumeration |

---

# 1. 🔎 Footprinting & Reconnaissance

I performed reconnaissance against `networkwalks.com` using several Kali Linux tools. Each tool provided a different perspective of the target's external footprint.

## 1.1 WHOIS

WHOIS was used to obtain publicly available domain registration information.

Observed information included:
- Registrar information
- Registration and expiration dates
- Domain status
- Name servers
- Abuse contact information

The investigation identified:

```text
Registrar: GoDaddy.com, LLC
Name Servers:
    NS6135.HOSTGATOR.COM
    NS6136.HOSTGATOR.COM
```

---

# 2. 🌐 Web Technology Fingerprinting — WhatWeb

WhatWeb was used to identify technologies exposed by the website.

Observed technologies included:

```text
WordPress 7.0.4
WP Download Manager 3.3.58
Apache
Bootstrap
jQuery
Google Tag Manager
WordPress REST API
```

Technology fingerprinting can help analysts understand the software stack and identify components that may require further security review.

> Technology identification alone does **not** prove a vulnerability.

---

# 3. 🧭 DNS Enumeration — Nslookup

### Command

```bash
nslookup networkwalks.com
```

### Result

```text
Name:    networkwalks.com
Address: 192.232.216.135
```

This provided the public IP address associated with the domain at the time of the assessment.

---

# 4. 📡 HTTP Header Analysis — cURL

### Command

```bash
curl -I https://networkwalks.com
```

The response exposed HTTP information including:

```text
HTTP/2 200
Server: Apache
Content-Type: text/html
```

It also exposed a WordPress REST API reference:

```text
/wp-json/
```

HTTP headers can provide useful information about server software, application technologies, caching, security policies, and API endpoints.

---

# 5. 🛡️ WAF Detection — WAFW00F

### Command

```bash
wafw00f https://networkwalks.com
```

### Observation

```text
ModSecurity (SpiderLabs)
```

This demonstrated how security infrastructure can sometimes be fingerprinted remotely.

---

# 6. 🧬 DNSRecon

### Command

```bash
dnsrecon -d networkwalks.com
```

The enumeration returned information relating to:

- SOA
- NS records
- MX records
- TXT/SPF records
- SRV records
- Mail infrastructure
- DNS software information

This helped build a broader picture of the domain's DNS and mail infrastructure.

---

# 7. 🕸️ Maltego OSINT Investigation

I used Maltego Graph to correlate information collected from different sources.

### Primary entity

```text
networkwalks.com
```

The resulting graph showed relationships including:

```text
networkwalks.com
├── mail.networkwalks.com
├── ns6135.hostgator.com
├── ns6136.hostgator.com
└── abuse@godaddy.com
```

Maltego demonstrated how individual pieces of information can be transformed into a visual relationship graph.

I also learned that Maltego transformations can depend on external APIs, search engines, credits, transform servers, and third-party data sources. Therefore, a failed transformation does not necessarily mean that no information exists.

---

# 8. 🔍 GHDB — Google Hacking Database

I worked with the **Google Hacking Database (GHDB)** to understand how search engines can expose information that has been publicly indexed.

Search operators practiced included:

```text
site:
intitle:
inurl:
filetype:
```

The objective was to understand search-engine reconnaissance without directly interacting with the underlying application.

## Public Webcam Discovery Exercise

As part of the GHDB exercise, I identified **10 publicly indexed live webcam interfaces** and documented the corresponding search techniques.

For responsible disclosure and privacy reasons, the actual webcam URLs and sensitive details are intentionally omitted from this public README.

### Security lesson

The exercise demonstrated how Internet-connected IoT devices can become part of an organization's external attack surface when they are unintentionally exposed or improperly secured.

> Public indexing does not imply authorization to access or exploit a device.

---

# 9. 💥 Exploit-DB Research

Exploit-DB was used as a vulnerability research resource.

The research focused on:
- Known vulnerabilities
- Software versions
- Historical exploits
- Proof-of-concept references
- Vulnerability-related information

Exploit-DB was used for research and learning rather than unauthorized exploitation.

---

# 10. 🖥️ Network Discovery with Nmap / Zenmap

The network-scanning exercise was performed against my own local network.

### Network

```text
192.168.100.0/24
```

### Command

```bash
nmap -sn 192.168.100.0/24
```

### Hosts discovered

```text
192.168.100.1
192.168.100.6
192.168.100.9
192.168.100.10
192.168.100.11
192.168.100.33
192.168.100.36
192.168.100.127
```

### Result

```text
8 hosts up
```

The scan also returned MAC-address information. Zenmap's Topology functionality was then used to visualize the discovered hosts.

---

# 11. 📊 Consolidated Findings

| # | Observation | Tool | Potential Impact | Risk |
|---|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb | Helps identify technologies requiring security review | Medium |
| 2 | Public server IP identifiable | Nslookup | Provides information about network location | Low |
| 3 | HTTP technical information exposed | cURL | May assist further fingerprinting | Low |
| 4 | WAF technology identifiable | WAFW00F | Reveals part of security architecture | Low |
| 5 | DNS infrastructure information exposed | DNSRecon | Helps build infrastructure profile | Medium |
| 6 | Multiple live hosts visible on local network | Nmap/Zenmap | Unknown devices may require investigation | Medium |
| 7 | OSINT relationships identified | Maltego | Enables correlation of public information | Medium |
| 8 | Public webcam interfaces identified during GHDB exercise | GHDB | Demonstrates potential IoT exposure | Critical |

> These findings represent **reconnaissance observations**, not confirmed vulnerabilities. No exploitation or unauthorized access was performed.

---

# 12. 🧠 Risk Analysis

A major lesson from this project was that a single piece of information may appear harmless, while the correlation of multiple pieces can significantly increase visibility into an organization's attack surface.

```text
WHOIS
   ↓
DNS Records
   ↓
IP Address
   ↓
Web Technologies
   ↓
HTTP Headers
   ↓
WAF
   ↓
Mail Infrastructure
   ↓
OSINT Relationships
   ↓
External Attack Surface
```

The GHDB exercise demonstrated another important concept:

```text
Public Search Engine Index
          ↓
   Exposed Resource
          ↓
   Internet Visibility
          ↓
 Potential Attack Surface
```

---

# 13. 🛡️ Recommendations

1. **Minimize information disclosure**  
   Review HTTP headers and publicly exposed application information.

2. **Keep software updated**  
   Regularly update WordPress, plugins, frameworks, and server software.

3. **Review DNS records**  
   Remove unnecessary, obsolete, or unintended DNS records.

4. **Protect Internet-facing IoT devices**  
   Cameras and other IoT devices should not be directly exposed unless there is a legitimate requirement and appropriate security controls.

5. **Enforce strong authentication**  
   Internet-connected devices should never rely on default credentials.

6. **Maintain WAF protection**  
   Keep the WAF enabled, correctly configured, and monitored.

7. **Monitor the external attack surface**  
   Regularly review public IPs, subdomains, DNS records, exposed services, and Internet-facing devices.

8. **Perform regular internal network discovery**  
   Periodically scan authorized networks to identify unknown devices.

9. **Investigate unexpected devices**  
   Unknown hosts discovered during an internal scan should be investigated.

10. **Conduct authorized security assessments**  
    Reconnaissance, scanning, and vulnerability testing must remain within an explicitly authorized scope.

---

# 14. 📚 What I Learned

This practical work significantly improved my understanding of reconnaissance and OSINT.

The most important lesson was that the real value does not come from collecting information alone. It comes from **correlating information from multiple sources**.

```text
WHOIS
 +
DNSRecon
 +
Nslookup
 +
cURL
 +
WhatWeb
 +
WAFW00F
 +
Maltego
 +
GHDB
      ↓
Broader Understanding of the Attack Surface
```

I also learned that every tool has limitations. For example, Maltego transformations may depend on external APIs, credits, search engines, transform servers, and third-party data sources.

The methodology I developed was:

```text
Identify
   ↓
Enumerate
   ↓
Verify
   ↓
Correlate
   ↓
Analyze
   ↓
Document
```

---

# 15. 📸 Evidence

Evidence collected during the practical work includes:

- WHOIS output
- WhatWeb results
- Nslookup output
- cURL HTTP headers
- WAFW00F results
- DNSRecon output
- Maltego relationship graph
- GHDB research
- Exploit-DB research
- Zenmap host-discovery results
- Zenmap network topology

Screenshots and supporting evidence can be organized in an `evidence/` directory.

---

# 16. 🏁 Conclusion

This project gave me the opportunity to move beyond theoretical cybersecurity concepts and apply reconnaissance techniques in a practical environment.

Using **WHOIS, WhatWeb, Nslookup, cURL, WAFW00F, DNSRecon, Maltego, theHarvester, GHDB, Exploit-DB, Nmap, and Zenmap**, I approached reconnaissance from multiple perspectives.

The most valuable lesson was that effective reconnaissance is not about collecting the largest amount of information. It is about **understanding, validating, correlating, and documenting information from different sources**.

The project also reinforced the importance of authorization and responsible security research. The ability to discover publicly accessible information does not imply permission to access or exploit it.

Overall, this experience strengthened my practical skills in:

- **OSINT**
- **Reconnaissance**
- **DNS enumeration**
- **Web fingerprinting**
- **Network discovery**
- **Attack-surface analysis**
- **Security documentation**
- **Responsible cybersecurity research**

> **Don't just collect information — understand what it means, verify it, correlate it, and document it.**

This project represents another step in my journey toward becoming a cybersecurity professional.

---
##  Evidences Collected

![](evidences/whois.png)
![](evidences/whatweb.png)
![](evidences/curl-i.png)
![](evidences/dnsrecon-d.png)
![](evidences/nslookup.png)
![](evidences/theHarvester.png)
![](evidences/wafw00f.png)
![](evidences/zenmapOUT.png)
![](evidences/zenmapGUI.png)


---
## 👤 Author

**Mohamed Salem Abdel Wedoud**

Cybersecurity Professional — B082

**Program:** Networkwalks Cybersecurity Program  
**Week:** 02  
**Focus:** Footprinting, OSINT & Network Scanning

---

## ⭐ Project Workflow

```text
Reconnaissance
      ↓
Footprinting
      ↓
DNS Enumeration
      ↓
Web Fingerprinting
      ↓
WAF Detection
      ↓
OSINT Correlation
      ↓
GHDB Research
      ↓
Exploit Research
      ↓
Network Discovery
      ↓
Risk Analysis
      ↓
Documentation
```

**Learn → Practice → Analyze → Document → Improve**
