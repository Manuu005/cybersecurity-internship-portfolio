# Web Vulnerabilities — OWASP Juice Shop

## Objective
Explore a range of common web application weaknesses beyond access control
— information disclosure, security-through-obscurity failures, and
Cross-Site Scripting (XSS) — using OWASP Juice Shop.

## Tools Used
- **OWASP Juice Shop** (local instance)
- Browser developer tools

## Methodology & Findings

### 1. Sensitive File Disclosure via `robots.txt`
Checked `robots.txt`, which is meant to tell search-engine crawlers which
paths *not* to index. It listed a disallowed `/ftp` directory — but
"disallowed for crawlers" isn't the same as "access-controlled." Browsing
directly to that path exposed files that should have required proper
authorization.
**Takeaway:** `robots.txt` is a crawler courtesy notice, not a security
control — anything listed there should already be properly access-controlled
independently.

### 2. Hidden Page Discovery (Security Through Obscurity)
Guessed the URL of an unlinked internal "scoreboard" page based on common
web app URL conventions and reached it directly, with no authentication
required.
**Takeaway:** hiding a page's link doesn't protect it — the page itself
needs its own auth/authorization check.

### 3. Cross-Site Scripting (XSS)
Injected JavaScript into an input field that the application rendered
without sanitizing, demonstrating how an attacker could execute arbitrary
script in another user's browser session (used in the real world for
cookie/session theft, defacement, or redirect-based phishing).

## Mitigation Recommendations
- Treat `robots.txt` entries as a hint to *lock down* those paths, not rely
  on them for obscurity.
- Explicitly authenticate/authorize every sensitive route server-side,
  regardless of whether it's linked in the UI.
- Sanitize and encode all user-supplied output (context-aware output
  encoding) and use a strict Content-Security-Policy to blunt the impact of
  any XSS that slips through.

## Skills Gained
Recognizing that "hidden" is not "secure," identifying information
disclosure through misconfigured or misunderstood web standards, and
practical XSS injection and impact analysis.
