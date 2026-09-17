# DNS Enumeration

## Target

**Domain:** nmap.org

## Objective

Identify publicly available DNS information associated with the authorized training domain using passive DNS queries.

## Methodology

DNS records were queried using the `dig` utility. The investigation focused on:

- NS records
- MX records
- TXT records
- SOA records

No exploitation or unauthorized access was performed.

---

## NS Records

The domain returned five authoritative nameservers:

- ns1.linode.com
- ns2.linode.com
- ns3.linode.com
- ns4.linode.com
- ns5.linode.com

### Interpretation

The NS records indicate that the authoritative DNS infrastructure for `nmap.org` is delegated to Linode nameservers.

---

## MX Records

The domain returned the following mail-exchange records:

- ASPMX.L.GOOGLE.COM — Priority 1
- ALT1.ASPMX.L.GOOGLE.COM — Priority 5
- ALT2.ASPMX.L.GOOGLE.COM — Priority 5
- ASPMX2.GOOGLEMAIL.COM — Priority 10
- ASPMX3.GOOGLEMAIL.COM — Priority 10

### Interpretation

The MX records indicate that Google mail infrastructure is configured to receive email for the domain.

The numeric values represent mail-exchange priority, with lower values receiving higher priority.

---

## TXT Records

Two TXT records were identified.

### SPF

The domain publishes an SPF record containing:

- Authorized A records
- Authorized MX records
- A published IPv4 address
- Published IPv6 addresses
- Google's SPF infrastructure through `_spf.google.com`
- A soft-fail policy using `~all`

### Google Site Verification

A Google site-verification TXT record was also identified.

### Interpretation

TXT records can expose information about email-security configuration, third-party services, domain verification, and other public infrastructure relationships.

The SPF record provides useful information about systems and services associated with the domain's email-sending policy.

---

## SOA Record

The SOA record returned:

- **Primary nameserver:** ns1.linode.com
- **Responsible mailbox:** hostmaster.nmap.com
- **Serial:** 2021000018
- **Refresh:** 14400 seconds
- **Retry:** 14400 seconds
- **Expire:** 1209600 seconds
- **Negative TTL:** 3600 seconds

### Interpretation

The SOA record provides administrative and DNS zone-management information for the domain.

---

## Security Relevance

Public DNS records provide valuable information during external reconnaissance.

The records identified during this investigation reveal:

- DNS hosting infrastructure
- Mail-service infrastructure
- Publicly declared email-sending infrastructure
- Domain verification information
- DNS zone-management information

These findings demonstrate how passive DNS enumeration can contribute to external attack-surface mapping without directly exploiting the target.

## Evidence

Raw DNS query results are stored in:

- `evidence/collected-data/dns-ns.txt`
- `evidence/collected-data/dns-mx.txt`
- `evidence/collected-data/dns-txt.txt`
- `evidence/collected-data/dns-soa.txt`

## Hostname Validation

TheHarvester identified the following hostnames through DuckDuckGo:

- 2Fsvn.nmap.org
- scanme.nmap.org
- svn.nmap.org

DNS validation was subsequently performed against the discovered hostnames.

### Results

| Hostname | IPv4 Address | DNS Status |
|---|---|---|
| scanme.nmap.org | 45.33.32.156 | NOERROR |
| svn.nmap.org | 50.116.1.184 | NOERROR |
| 2Fsvn.nmap.org | 50.116.1.184 | NOERROR |

### Infrastructure Correlation

Both `svn.nmap.org` and `2Fsvn.nmap.org` resolve to:

**50.116.1.184**

This demonstrates that multiple hostnames can point to the same publicly resolvable IPv4 address.

This observation does not by itself establish that the hostnames represent separate systems or that a security vulnerability exists.

### Evidence

- `evidence/collected-data/dns-svn.txt`
- `evidence/collected-data/dns-2Fsvn.txt`
