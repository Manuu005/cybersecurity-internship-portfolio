# Cybersecurity Internship Portfolio — From Reconnaissance to Exploitation

Write-ups from a 2-month Cyber Security internship at **Cloudbox99**, covering
hands-on penetration testing across reconnaissance, vulnerability assessment,
web application exploitation, system exploitation, password security, and
social engineering. All activities were performed in isolated lab
environments (personal VMs, OWASP Juice Shop, DVWA) and on applications
explicitly provided for security testing practice (e.g. `testphp.vulnweb.com`).

> ⚠️ **Educational use only.** Every technique documented here was carried out
> in an authorized lab/practice environment. Nothing in this repository
> should be used against systems you do not own or have explicit permission
> to test.

## Skills Demonstrated

- Network reconnaissance & enumeration (`Nmap`, `Dirb`)
- Vulnerability assessment (`Nessus`)
- Web application security testing (`Burp Suite`)
- SQL Injection & authentication bypass
- Broken Access Control, XSS, and OWASP Top 10 exploitation (`OWASP Juice Shop`)
- System exploitation & post-exploitation (`Metasploit`, `msfvenom`)
- Password security auditing (`John the Ripper`)
- Social engineering / phishing simulation (`Zphisher`)

## Contents

| # | Topic | Tools |
|---|-------|-------|
| 01 | [Network Reconnaissance](./01-network-reconnaissance) | Nmap, Dirb |
| 02 | [Vulnerability Scanning](./02-vulnerability-scanning-nessus) | Nessus |
| 03 | [SQL Injection](./03-sql-injection) | Burp Suite, manual payloads |
| 04 | [Web App Testing with Burp Suite](./04-burp-suite-web-testing) | Burp Suite |
| 05 | [Metasploit Exploitation](./05-metasploit-exploitation) | Metasploit, msfvenom |
| 06 | [Password Cracking](./06-password-cracking) | John the Ripper |
| 07 | [Broken Access Control — Juice Shop](./07-broken-access-control-juice-shop) | OWASP Juice Shop |
| 08 | [Web Vulnerabilities — Juice Shop](./08-web-vulnerabilities-juice-shop) | OWASP Juice Shop |
| 09 | [Social Engineering / Phishing Simulation](./09-social-engineering-phishing) | Zphisher |

## About

Internship completed as part of the Internship Program (IP-201), ICFAI
Foundation for Higher Education, under the guidance of a mentor at Cloudbox99
(July 2025). Each folder contains a self-contained write-up: objective,
methodology, tools/commands used, findings, and mitigation recommendations.
