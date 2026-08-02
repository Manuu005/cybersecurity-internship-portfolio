# Social Engineering — Phishing Attack Simulation

## Objective
Understand how credential-harvesting phishing pages are built and deployed,
from the attacker's perspective, in order to better recognize and defend
against them — using only dummy accounts and disposable infrastructure, no
real user data.

## Tools Used
- **Zphisher** (open-source phishing simulation framework)
- A disposable/temporary email service to create a throwaway test account

## Methodology
1. **Ethical setup:** created a throwaway test social-media account using a
   temporary/disposable email address specifically so no real account or
   real user data was ever involved in the exercise.
2. **Tool setup:** installed Zphisher in an isolated Kali Linux VM and
   generated a cloned login page template.
3. **Simulation:** walked through the flow a victim would experience —
   landing on a page that visually mirrors a real login screen — to study
   how convincingly credential-harvesting pages can imitate legitimate
   sites.
4. **Analysis:** examined what a real attacker would additionally need
   (link delivery via email/SMS, believable pretext, a properly disguised
   URL) to make this effective, and what defensive signals would give it
   away.

## Key Learnings
- Cloned login pages can be visually indistinguishable from the real thing
  — the meaningful defense is checking the **URL/domain**, not the page's
  appearance.
- Phishing succeeds by exploiting trust and urgency, not technical flaws —
  making user awareness a critical control alongside technical defenses.

## Mitigation Recommendations
- Enable multi-factor authentication everywhere, so a phished password
  alone isn't enough to compromise an account.
- Train users to verify sender domains and hover/inspect links before
  clicking, and to navigate to sensitive sites directly rather than via
  emailed links.
- Deploy email security controls (SPF/DKIM/DMARC, link-rewriting/sandboxing)
  to catch phishing attempts before they reach the inbox.

## Skills Gained
Hands-on understanding of the phishing kill chain, and how to translate
that offensive knowledge into concrete, actionable user-awareness and
email-security recommendations.

> Note: performed entirely with dummy/throwaway accounts on isolated lab
> infrastructure — no real users or real credentials were targeted at any
> point.
