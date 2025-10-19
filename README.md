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
This penetration testing project was conducted to assess the security posture of a vulnerable 
system in a controlled lab environment. The primary objective was to simulate real-world 
attack scenarios using industry-standard tools and methodologies, with the aim of identifying 
security 
weaknesses, 
countermeasures. 
validating 
exploitability, 
and 
recommending appropriate 
The engagement followed a structured penetration testing lifecycle, beginning with 
reconnaissance and information gathering, followed by vulnerability identification, 
exploitation, and post-exploitation analysis. During the reconnaissance phase, Nmap was 
utilized with the nmap -A command to detect open ports, running services, operating system 
details, and possible service versions. This enabled a comprehensive mapping of the target’s 
attack surface. 
Subsequent exploitation was performed using the Metasploit Framework (MSF), leveraging 
its modular capabilities to identify and exploit known vulnerabilities. Once access was 
obtained, the focus shifted to maintaining persistence, privilege escalation, and gathering 
evidence of compromise. Screenshots and console outputs were documented throughout the 
process to validate findings and ensure reproducibility. 
Key findings from the assessment highlighted multiple exploitable misconfigurations and 
outdated services that could allow an attacker to gain unauthorized access. These weaknesses, 
while expected in a lab-based vulnerable machine, serve as critical lessons for securing 
production systems. 
Recommendations include implementing timely patch management, enforcing strict access 
controls, network segmentation, and deploying security monitoring solutions to detect 
abnormal activity. Adopting a defense-in-depth approach will significantly reduce the 
likelihood of a successful intrusion. 
In conclusion, this project provided practical, hands-on experience in conducting penetration 
testing using recognized tools such as Nmap and MSF. The exercise not only exposed 
vulnerabilities but also reinforced the importance of proactive security measures. The insights 
gained are directly applicable to both academic learning and real-world cybersecurity 
operations, supporting the development of stronger defenses against evolving threats.

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
