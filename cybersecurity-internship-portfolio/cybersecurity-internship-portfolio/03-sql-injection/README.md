# SQL Injection — Authentication Bypass

## Objective
Demonstrate how an unsanitized login form can be exploited to bypass
authentication, using a practice login page (`testphp.vulnweb.com/login.php`).

## Tools Used
- **Burp Suite** (Proxy + Repeater) — to intercept, modify, and replay the
  login request

## Methodology
1. **Baseline request:** submitted a normal login attempt and intercepted
   the resulting HTTP POST request with Burp Suite's proxy.
2. **Payload crafting:** sent the intercepted request to Repeater and
   replaced the username field with a classic authentication-bypass
   condition designed to make the underlying SQL `WHERE` clause always
   evaluate to true, then commented out the rest of the original query.
3. **Observation:** replayed the modified request and observed that the
   application logic could be manipulated purely through unsanitized input,
   without knowing any valid credentials.

## Root Cause
The login form built its SQL query by directly concatenating user input
instead of using parameterized queries/prepared statements, allowing
attacker-controlled input to change the query's logic.

## Mitigation Recommendations
- Use parameterized queries / prepared statements for all database calls.
- Apply strict server-side input validation and allow-listing.
- Enforce least-privilege database accounts so even a successful injection
  has limited blast radius.
- Add a Web Application Firewall (WAF) as a defense-in-depth layer.

## Skills Gained
Understanding how SQL injection breaks query logic at a fundamental level,
using Burp Suite's Proxy/Repeater workflow to test and iterate on payloads,
and connecting a technical exploit back to a concrete secure-coding fix.
