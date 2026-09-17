# OSINT Findings

## Target

**Primary Domain:** nmap.org

## Investigation Summary

The investigation combined WHOIS, DNS enumeration, WhatWeb technology discovery, and search-engine OSINT using theHarvester.

The following publicly observable information was identified.

## Findings Matrix

| ID | Category | Finding | Evidence | Security Relevance |
|---|---|---|---|---|
| OSINT-001 | Domain | nmap.org registered since 1999 | whois-nmap.txt | Domain history |
| OSINT-002 | DNS | Five Linode nameservers identified | dns-ns.txt | DNS infrastructure |
| OSINT-003 | Email | Google mail infrastructure identified | dns-mx.txt | Mail infrastructure |
| OSINT-004 | Email Security | SPF record publicly published | dns-txt.txt | Email-security configuration |
| OSINT-005 | DNS | DNSSEC reported as unsigned | whois-nmap.txt | DNS configuration observation |
| OSINT-006 | Web | Apache 2.4.7 on Ubuntu identified | whatweb-scanme.txt | Technology disclosure |
| OSINT-007 | Host Discovery | Three public hostnames identified | theHarvester-duckduckgo.txt | External attack-surface mapping |
| OSINT-008 | DNS Correlation | svn.nmap.org resolves to 50.116.1.184 | dns-svn.txt | Infrastructure mapping |
| OSINT-009 | DNS Correlation | 2Fsvn.nmap.org resolves to 50.116.1.184 | dns-2Fsvn.txt | Infrastructure mapping |
| OSINT-010 | HTTPS | Connection to port 443 was refused | WhatWeb test | Service availability observation |

## Key Observations

### Public DNS Infrastructure

The investigation identified the authoritative DNS infrastructure, mail infrastructure, SPF configuration, and SOA information associated with the domain.

### Public Hostnames

Search-engine OSINT identified three hostnames:

- 2Fsvn.nmap.org
- scanme.nmap.org
- svn.nmap.org

Two of these hostnames were subsequently validated through DNS.

### Technology Disclosure

The HTTP service for `scanme.nmap.org` exposed:

**Apache/2.4.7 (Ubuntu)**

This represents publicly observable technology information. Version disclosure alone does not establish a vulnerability.

### Infrastructure Relationship

`svn.nmap.org` and `2Fsvn.nmap.org` both resolve to `50.116.1.184`.

This demonstrates an observable relationship between multiple hostnames and the same IPv4 address.

## Limitations

The findings represent information available through the selected sources and at the time of collection.

A lack of information from a particular OSINT source does not prove that the information does not exist elsewhere.

No exploitation, credential attacks, brute force, or unauthorized access was performed.
