# Domain Enumeration

## Target

**Domain:** scanme.nmap.org

## Objective

Identify publicly available domain information using passive OSINT techniques.

## Scope

This investigation is limited to publicly available information and authorized security-testing resources.

## Tools

- WHOIS
- DNS utilities
- theHarvester
- WhatWeb
- curl

## Methodology

The investigation begins with passive domain reconnaissance. No exploitation or credential attacks will be performed.
## WHOIS Findings

A WHOIS query was performed against the registrable domain `nmap.org`.

### Domain Registration

- **Domain:** nmap.org
- **Creation Date:** 1999-01-18
- **Updated Date:** 2026-08-12
- **Registry Expiry Date:** 2029-01-18
- **Registrar:** Dynadot Inc
- **Domain Status:** clientTransferProhibited

### Name Servers

The domain uses the following authoritative name servers:

- ns1.linode.com
- ns2.linode.com
- ns3.linode.com
- ns4.linode.com
- ns5.linode.com

### DNSSEC

The WHOIS record reports:

**DNSSEC: unsigned**

### Interpretation

The WHOIS record provides registration and DNS infrastructure information associated with the `nmap.org` domain.

The presence of multiple Linode name servers indicates that the domain's authoritative DNS infrastructure is hosted through Linode's DNS service.

The `clientTransferProhibited` status indicates that the domain has a registrar-level transfer restriction applied.

The WHOIS record reports that DNSSEC is unsigned. This is a configuration observation and does not, by itself, establish that the domain is vulnerable to DNS attacks.

### Evidence

The complete WHOIS output has been preserved in:

`evidence/collected-data/whois-nmap.txt`
