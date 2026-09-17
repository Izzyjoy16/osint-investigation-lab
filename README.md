# 🔎 OSINT Investigation Lab

A practical Open Source Intelligence (OSINT) investigation lab demonstrating OSINT reconnaissance, DNS enumeration, public-domain intelligence gathering, technology discovery, infrastructure correlation, evidence collection, and security-focused analysis.

## 🎯 Project Objective

The objective of this project is to demonstrate a structured OSINT investigation against an authorized security-testing target using publicly available information.

The investigation focuses on identifying externally observable information without exploitation, credential attacks, brute-force activity, or unauthorized access.

## 🧪 Investigation Target

**Primary Domain:** `nmap.org`
**Training Host:** `scanme.nmap.org`

The target is an Nmap-provided security-testing resource intended for learning and experimentation.

## 🛠️ Tools & Technologies

* 🐧 Kali Linux
* 🔍 WHOIS
* 🌐 `dig`
* 🌐 `nslookup`
* 🌐 `host`
* 🔎 theHarvester
* 🕵️ WhatWeb
* 💻 `curl`
* 📝 Git & GitHub

## 🔬 Investigation Areas

### 1. Domain Reconnaissance

* WHOIS information
* Domain registration details
* Registrar information
* Name servers
* Domain status
* DNSSEC status

### 2. DNS Enumeration

* A records
* NS records
* MX records
* TXT records
* SOA records
* Hostname-to-IP resolution
* Infrastructure correlation

### 3. Public-Domain OSINT

* Search-engine intelligence
* Publicly indexed hostnames
* Publicly observable infrastructure
* Email-related DNS information

### 4. Technology Discovery

* Web server identification
* Operating-system indicators
* HTTP response analysis
* Technology fingerprinting

### 5. Evidence Collection

Investigation results are preserved as raw evidence and documented with their corresponding methodology and security relevance.

## 📊 Key Findings

| ID        | Category       | Finding                                                       |
| --------- | -------------- | ------------------------------------------------------------- |
| OSINT-001 | Domain         | `nmap.org` registration information was identified            |
| OSINT-002 | DNS            | Five Linode name servers were identified                      |
| OSINT-003 | Mail           | Google mail infrastructure was identified through MX records  |
| OSINT-004 | Email Security | An SPF record was publicly available                          |
| OSINT-005 | DNS            | WHOIS reported DNSSEC as unsigned                             |
| OSINT-006 | Web            | Apache 2.4.7 on Ubuntu was identified on the training host    |
| OSINT-007 | Host Discovery | Three public hostnames were identified through theHarvester   |
| OSINT-008 | Infrastructure | `svn.nmap.org` resolved to `50.116.1.184`                     |
| OSINT-009 | Infrastructure | `2Fsvn.nmap.org` resolved to `50.116.1.184`                   |
| OSINT-010 | HTTPS          | Connection to TCP/443 was refused during technology discovery |

## 📁 Project Structure

```text
osint-investigation-lab/
│
├── analysis/
│   └── findings.md
│
├── evidence/
│   ├── collected-data/
│   └── screenshots/
│
├── reconnaissance/
│   ├── domain-enumeration.md
│   ├── dns-enumeration.md
│   ├── email-osint.md
│   └── technology-discovery.md
│
├── remediation/
│   └── recommendations.md
│
├── reporting/
│   └── final-report.md
│
└── scope/
    └── scope.md
```

## 📚 Methodology

The investigation followed a structured process:

```text
Scope Definition
       ↓
Domain Reconnaissance
       ↓
DNS Enumeration
       ↓
Public OSINT Collection
       ↓
Technology Discovery
       ↓
DNS / Infrastructure Correlation
       ↓
Evidence Preservation
       ↓
Analysis
       ↓
Security Recommendations
       ↓
Final Report
```

## ⚖️ Scope & Ethics

This project was conducted for educational and portfolio purposes against an authorized security-testing resource.

The investigation was limited to publicly available information and lightweight reconnaissance techniques.

No:

* ❌ Credential attacks
* ❌ Brute-force attacks
* ❌ Exploitation
* ❌ Unauthorized access
* ❌ Disruptive testing
* ❌ Collection of private personal information

was performed.

## 📖 Documentation

Detailed investigation records can be found in:

* [`scope/`](scope/)
* [`reconnaissance/`](reconnaissance/)
* [`evidence/`](evidence/collected-data/)
* [`analysis/`](analysis/)
* [`reporting/`](reporting/)
* [`remediation/`](remediation/)

## 👨‍💻 Skills Demonstrated

This project demonstrates practical experience with:

**OSINT • Passive Reconnaissance • DNS Enumeration • Domain Intelligence • Technology Discovery • Infrastructure Mapping • Evidence Collection • Security Analysis • Technical Documentation • Git/GitHub**

## ⚠️ Disclaimer

This repository is an educational cybersecurity project. Techniques and tools demonstrated here should only be used against systems and resources where explicit authorization has been granted.
