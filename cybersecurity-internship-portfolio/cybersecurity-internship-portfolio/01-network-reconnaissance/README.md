# Network Reconnaissance — Nmap & Dirb

## Objective
Perform active reconnaissance on a designated practice target
(`testphp.vulnweb.com`) to map open ports, running services, and hidden
directories before deeper vulnerability testing.

## Tools Used
- **Nmap** — host discovery, port scanning, service/OS fingerprinting, and
  the Nmap Scripting Engine (NSE) for vulnerability scripts
- **Dirb** — directory and file brute-forcing against the web server

## Methodology
1. **Aggressive scan** (`nmap -A <target>`) to enumerate open ports, detect
   service versions, and attempt OS fingerprinting in a single pass.
2. **NSE vulnerability scan** (`nmap --script=vuln <target>`) to flag known
   misconfigurations and CVEs associated with the detected service versions.
3. **Directory enumeration** with Dirb against the web root to surface
   admin panels, backup files, and unlinked directories not visible through
   normal browsing.

## Key Findings
- Port 80 (HTTP) was open, running an outdated Nginx version — a version
  mismatch that on its own is a low-severity finding but narrows down which
  known CVEs to check for.
- OS fingerprinting returned only low-confidence guesses, illustrating why
  active scan results should always be corroborated with other sources
  before being treated as fact.
- Directory enumeration revealed several non-linked paths worth manual
  follow-up (e.g. admin/config-related directories), which fed into later
  testing phases.

## Mitigation Recommendations
- Keep web server software patched and hide version banners where possible.
- Restrict or monitor access to administrative directories; don't rely on
  "security through obscurity" (unlinked ≠ inaccessible).
- Rate-limit or alert on high-volume scanning traffic at the firewall/IDS
  level.

## Skills Gained
Active vs. passive reconnaissance, reading and interpreting Nmap output,
NSE scripting basics, and using directory brute-forcing to expand the
attack surface map before exploitation.
