# Web Application Testing with Burp Suite

## Objective
Use Burp Suite as an intercepting proxy to analyze and manipulate HTTP/HTTPS
traffic between the browser and two practice targets: `testphp.vulnweb.com`
and the TestFire demo banking application.

## Tools Used
- **Burp Suite** — Proxy, Repeater, and Intruder modules

## Methodology
1. Configured the browser to route traffic through Burp Suite's local proxy
   and installed Burp's CA certificate to inspect HTTPS traffic.
2. Walked through the target application's functionality while capturing
   every request in the Proxy history, looking for parameters that reflect
   or process user input.
3. Sent interesting requests to **Repeater** to manually tamper with
   parameters, headers, and cookies and observe how the server responded.
4. On the TestFire banking demo, tested how the application handled
   parameter tampering and session/cookie manipulation to probe for
   business-logic and access-control weaknesses typical of financial
   applications.

## Key Findings
- Multiple endpoints reflected user input without adequate sanitization.
- Session/cookie handling on the banking demo app revealed points where
  client-side trust assumptions could be abused if not properly validated
  server-side.

## Mitigation Recommendations
- Never trust client-side/browser-supplied data for authorization decisions.
- Validate and sanitize all input server-side, regardless of what the
  front-end already checks.
- Use secure, `HttpOnly`, `SameSite` cookies and short session lifetimes for
  sensitive applications like banking portals.

## Skills Gained
End-to-end proxy-based web traffic analysis, manual request tampering with
Repeater, and applying the same testing methodology across two different
target applications to compare findings.
