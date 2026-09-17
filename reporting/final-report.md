
# 🔎 OSINT Investigation Final Report

## 1. Executive Summary

This report documents a structured Open Source Intelligence (OSINT) investigation conducted against the authorized Nmap security-testing domain `nmap.org` and its training host `scanme.nmap.org`.

The investigation focused on publicly observable information, including domain registration data, DNS records, publicly indexed hostnames, web technology information, and infrastructure relationships.

The assessment did not involve exploitation, credential attacks, brute-force activity, or unauthorized access.

The investigation demonstrated how publicly available information can be correlated to develop an external view of an organization's internet-facing infrastructure.

---

## 2. Investigation Scope

### Primary Domain

`nmap.org`

### Training Host

`scanme.nmap.org`

### Scope

The investigation covered:

* Domain registration information
* DNS infrastructure
* Mail infrastructure
* Publicly available TXT records
* Publicly indexed hostnames
* Web technology identification
* Hostname-to-IP relationships
* Evidence collection and documentation

### Out of Scope

The following activities were not performed:

* Exploitation
* Credential attacks
* Password attacks
* Brute-force activity
* Unauthorized access
* Denial-of-service activity
* Collection of private personal information
* Attempts to bypass security controls

---

## 3. Methodology

The investigation followed a structured OSINT workflow:

```text
Scope Definition
       ↓
WHOIS Enumeration
       ↓
DNS Enumeration
       ↓
Public Host Discovery
       ↓
Technology Discovery
       ↓
Infrastructure Correlation
       ↓
Evidence Collection
       ↓
Analysis
       ↓
Security Recommendations
```

The following tools were used:

| Tool         | Purpose                                       |
| ------------ | --------------------------------------------- |
| WHOIS        | Domain registration and registrar information |
| dig          | DNS record enumeration                        |
| nslookup     | DNS resolution                                |
| host         | Hostname resolution                           |
| theHarvester | Public-domain host discovery                  |
| WhatWeb      | Web technology identification                 |
| curl         | HTTP interaction where required               |
| Git          | Evidence and documentation version control    |

---

## 4. Domain Intelligence

WHOIS information was collected for the parent domain `nmap.org`.

Observed information included:

* Domain creation date: `1999-01-18`
* Registrar: `Dynadot Inc`
* Registry expiry date: `2029-01-18`
* Domain status: `clientTransferProhibited`
* Multiple Linode name servers
* DNSSEC reported as unsigned

### Security Relevance

Domain registration and configuration information can provide useful contextual intelligence during external reconnaissance.

The presence of `clientTransferProhibited` represents a domain-management control rather than a vulnerability.

The observation that DNSSEC was reported as unsigned is documented as a configuration observation. It should not, by itself, be treated as evidence of an exploitable vulnerability.

**Evidence:** `evidence/collected-data/whois-nmap.txt`

---

## 5. DNS Enumeration

DNS enumeration identified several publicly available records associated with `nmap.org`.

### Name Servers

The following name servers were identified:

* `ns1.linode.com`
* `ns2.linode.com`
* `ns3.linode.com`
* `ns4.linode.com`
* `ns5.linode.com`

### Mail Exchange Records

The MX records indicated the use of Google mail infrastructure, including:

* `ASPMX.L.GOOGLE.COM`
* `ALT1.ASPMX.L.GOOGLE.COM`
* `ALT2.ASPMX.L.GOOGLE.COM`
* `ASPMX2.GOOGLEMAIL.COM`
* `ASPMX3.GOOGLEMAIL.COM`

### TXT Records

An SPF record was publicly identified.

The DNS TXT records also contained a Google site-verification record.

### SOA Record

The SOA record identified:

* Primary name server: `ns1.linode.com`
* Responsible administrative mailbox representation
* DNS serial number
* Refresh interval
* Retry interval
* Expiration interval
* Negative caching TTL

### Security Relevance

DNS records provide useful information about external infrastructure, DNS providers, email providers, and domain-management configuration.

**Evidence:**

* `evidence/collected-data/dns-ns.txt`
* `evidence/collected-data/dns-mx.txt`
* `evidence/collected-data/dns-txt.txt`
* `evidence/collected-data/dns-soa.txt`

---

## 6. Public Host Discovery

TheHarvester was used to identify publicly indexed hosts associated with `nmap.org`.

The DuckDuckGo search source returned three hostnames:

```text
2Fsvn.nmap.org
scanme.nmap.org
svn.nmap.org
```

No public email addresses or people were returned by the search.

### Security Relevance

Publicly indexed hostnames can contribute to external attack-surface mapping by revealing infrastructure that may otherwise be difficult to identify from the primary domain alone.

The discovery of a hostname does not establish that the associated service is vulnerable.

**Evidence:** `evidence/collected-data/theharvester-duckduckgo.txt`

---

## 7. Hostname and Infrastructure Correlation

DNS resolution was performed to validate the discovered hostnames.

### Observed Relationships

| Hostname          | Resolved IPv4 Address |
| ----------------- | --------------------- |
| `scanme.nmap.org` | `45.33.32.156`        |
| `svn.nmap.org`    | `50.116.1.184`        |
| `2Fsvn.nmap.org`  | `50.116.1.184`        |

The results show that `svn.nmap.org` and `2Fsvn.nmap.org` resolved to the same IPv4 address during the investigation.

### Security Relevance

Multiple hostnames resolving to the same address can reveal relationships within externally observable infrastructure.

This does not necessarily mean that the hostnames represent separate physical systems or that the shared address represents a vulnerability.

**Evidence:**

* `evidence/collected-data/dns-svn.txt`
* `evidence/collected-data/dns-2Fsvn.txt`
* `evidence/collected-data/dns-scanme.txt`

---

## 8. Technology Discovery

WhatWeb was used against the HTTP service exposed by `scanme.nmap.org`.

The observed response included:

* HTTP status: `200 OK`
* Web server: Apache
* Apache version: `2.4.7`
* Operating-system indicator: Ubuntu Linux
* HTML5
* Google Analytics Universal identifier
* Public IPv4 address: `45.33.32.156`
* Page title: `Go ahead and ScanMe!`

An HTTPS connection attempt to port 443 resulted in a connection refusal.

### Security Relevance

Technology fingerprinting can expose software and platform information that may assist external reconnaissance.

Version disclosure is not automatically a vulnerability. Determining whether a specific version is vulnerable requires additional validation, including consideration of patches, configuration, deployment context, and affected components.

The HTTPS connection refusal is recorded as a service-availability observation rather than a vulnerability determination.

**Evidence:** `evidence/collected-data/whatweb-scanme.txt`

---

## 9. Findings Summary

| ID        | Finding                                        | Security Relevance               |
| --------- | ---------------------------------------------- | -------------------------------- |
| OSINT-001 | Domain registration information identified     | Domain intelligence              |
| OSINT-002 | Five Linode name servers identified            | DNS infrastructure mapping       |
| OSINT-003 | Google mail infrastructure identified          | Email infrastructure mapping     |
| OSINT-004 | SPF record publicly available                  | Email-security configuration     |
| OSINT-005 | DNSSEC reported as unsigned                    | DNS configuration observation    |
| OSINT-006 | Apache/Ubuntu technology information disclosed | Technology fingerprinting        |
| OSINT-007 | Three public hostnames identified              | External attack-surface mapping  |
| OSINT-008 | `svn.nmap.org` mapped to `50.116.1.184`        | Infrastructure correlation       |
| OSINT-009 | `2Fsvn.nmap.org` mapped to `50.116.1.184`      | Infrastructure correlation       |
| OSINT-010 | HTTPS connection refused                       | Service-availability observation |

---

## 10. Security Assessment

The investigation demonstrates that publicly available information can provide a significant amount of externally observable intelligence about a domain.

The collected information included:

* Domain lifecycle information
* DNS infrastructure
* Email infrastructure
* Public hostnames
* IP address relationships
* Web-server technology
* Operating-system indicators
* Publicly exposed service information

These observations can be useful during legitimate security assessments because they help establish an external view of an organization's digital footprint.

However, the presence of publicly observable information does not automatically indicate a security vulnerability.

Further assessment would be required before assigning vulnerability severity to individual observations.

---

## 11. Recommendations

Organizations conducting external security reviews should consider:

### DNS Management

* Review publicly exposed DNS records periodically.
* Remove obsolete DNS records and hostnames.
* Maintain an accurate inventory of externally resolvable assets.
* Review DNSSEC requirements according to organizational risk and infrastructure design.

### Technology Disclosure

* Maintain supported versions of externally exposed software.
* Review unnecessary server and framework version disclosure.
* Apply security updates through an established patch-management process.

### Attack-Surface Management

* Regularly inventory publicly accessible hostnames and services.
* Investigate unexpected or obsolete subdomains.
* Monitor DNS and certificate transparency sources for newly exposed assets.

### Email Security

* Regularly review SPF configuration.
* Consider additional email authentication controls such as DKIM and DMARC where appropriate.
* Periodically validate third-party mail-service dependencies.

### Monitoring

* Continuously monitor externally observable assets.
* Investigate unexpected infrastructure changes.
* Maintain documented ownership for internet-facing systems.

---

## 12. Limitations

This investigation was intentionally limited to OSINT and lightweight reconnaissance.

The assessment did not attempt to:

* Exploit identified software
* Authenticate to systems
* Perform credential attacks
* Conduct brute-force testing
* Test application vulnerabilities
* Perform intrusive port scanning
* Verify exploitable vulnerabilities
* Access private information

Some OSINT sources may also provide incomplete, outdated, or duplicated information.

The findings therefore represent observations collected during the investigation and should not be interpreted as a complete security assessment of the target infrastructure.

---

## 13. Evidence Repository

Raw investigation evidence is stored in:

```text
evidence/collected-data/
```

Supporting reconnaissance documentation is stored in:

```text
reconnaissance/
```

The project analysis is stored in:

```text
analysis/
```

Defensive recommendations are stored in:

```text
remediation/
```

---

## 14. Conclusion

This OSINT investigation demonstrated a repeatable process for collecting, validating, correlating, and documenting publicly available intelligence.

The project combines technical reconnaissance with evidence-based analysis and demonstrates how information from WHOIS, DNS, search engines, and web technology fingerprinting can be organized into a structured security assessment.

The investigation remained within the defined authorization and scope and avoided exploitation or unauthorized access.
