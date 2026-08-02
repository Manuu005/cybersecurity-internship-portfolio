# Broken Access Control — OWASP Juice Shop

## Objective
Exploit Broken Access Control (OWASP Top 10) in OWASP Juice Shop, a
deliberately vulnerable web application built for security training, to
demonstrate both vertical and horizontal privilege escalation.

## Tools Used
- **OWASP Juice Shop** (local instance)
- **Burp Suite** — request interception/tampering

## Methodology

### 1. Vertical Privilege Escalation (SQL Injection → Admin Panel)
Bypassed the login form using a classic SQL injection payload in the email
field, which caused the underlying query to authenticate as the first user
in the database (typically the admin account). Since the application only
checks *whether* a session exists — not *what role* that session holds —
navigating directly to the admin dashboard URL granted full administrative
access with visibility into all registered users.

### 2. Horizontal Privilege Escalation (Another User's Basket)
Logged in as a normal, low-privilege user, then used Burp Suite to
intercept and modify the request used to view a shopping basket, changing
the basket ID to another user's. The application returned that user's cart
contents without verifying the requester actually owned it.

## Root Cause
In both cases, the application authenticated *that a session exists* but
never re-validated *what that session is allowed to see or do* on each
request — a textbook Broken Access Control / Insecure Design flaw.

## Mitigation Recommendations
- Enforce role-based access control (RBAC) checks server-side on every
  sensitive endpoint, not just at login.
- Never trust client-supplied object IDs (e.g. basket ID) without verifying
  the requesting user actually owns that object (a.k.a. IDOR prevention).
- Apply the principle of least privilege by default, and deny access unless
  explicitly authorized.

## Skills Gained
Distinguishing vertical vs. horizontal privilege escalation, using Burp
Suite to manipulate object references, and connecting exploitation to the
underlying access-control design flaw rather than just the injection
technique used to get there.
