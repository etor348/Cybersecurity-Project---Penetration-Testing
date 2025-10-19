# Cybersecurity-Project---Penetration-Testing
Performed a scoped penetration test against the target(s) to identify vulnerabilities, assess impact, and provide prioritized remediation. Findings include low→high severity issues across authentication, configuration, and information disclosure. No destructive exploitation performed.
# Penetration Test — Brief Project Summary

**Project name:** An Internal Penetration Test on Nova Ltd.’s Corporate Network  
**Author:** Loveland Dzah  
**Date:** 2025-09-26  
**Target(s):** `10.0.0.5` / `example.com`  
**Scope:** Internal web app + network  
**Rules of engagement:** Written authorization obtained; testing window defined; no destructive actions; out-of-scope assets listed.

---

## Executive summary
Performed a scoped penetration test against the target(s) to identify vulnerabilities, assess impact, and provide prioritized remediation. Findings include low→high severity issues across authentication, configuration, and information disclosure. No destructive exploitation performed.

---

## Objectives
- Identify vulnerabilities in in-scope systems and web apps.  
- Validate exploitability and impact (non-destructive).  
- Provide actionable remediation and risk ratings.

---

## Methodology
Testing followed a standard black/gray-box flow:

1. **Reconnaissance** — passive (OSINT, DNS, WHOIS) and active (host discovery).  
2. **Scanning & Enumeration** — port/service scans, web content discovery.  
3. **Vulnerability Analysis** — automated + manual verification.  
4. **Exploitation (proof-of-concept, non-destructive)**.  
5. **Post-exploitation & pivoting** (limited to scope).  
6. **Reporting** — findings, impact, remediation, evidence.

---

## Tools used
- `nmap`, `masscan`  
- `gobuster`, `dirb`  
- `Burp Suite`, `Nikto`, `sqlmap`  
- `Metasploit`, `hydra`, `john`  
- `curl`, `wget`, `tcpdump`, `wireshark`

---

## Sample commands / reproducible steps
> Only run these against authorized targets.

```bash
# quick nmap service scan
nmap -sC -sV -oA nmap/initial 10.0.0.5

# directory brute force
gobuster dir -u https://example.com -w /usr/share/wordlists/dirb/common.txt -t 50

# non-destructive SQLi check with sqlmap
sqlmap -u "https://example.com/product?id=1" --batch --level=2 --risk=1 --dbs
