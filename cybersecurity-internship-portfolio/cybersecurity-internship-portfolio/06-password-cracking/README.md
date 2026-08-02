# Password Security — John the Ripper

## Objective
Study how weak or default passwords protecting local files can be recovered,
and use that as a lens to understand password storage/verification across
Linux, Windows, and web applications.

## Tools Used
- **John the Ripper** — offline password-cracking tool
- Supporting hash-extraction utilities to convert a password-protected file
  into a crackable hash format

## Methodology (high level)
1. Extracted the password hash from a password-protected PDF using John the
   Ripper's companion hash-extraction utility.
2. Ran a dictionary attack against the extracted hash using John the Ripper
   with a standard wordlist.
3. Compared how long dictionary vs. brute-force approaches take against
   weak vs. strong passwords, to build intuition for password strength.

## Key Learnings
- The practical difference between hashing, salting, and encryption, and
  why weak or unsalted hashes are cracked far faster.
- How quickly a weak, dictionary-word password falls to an offline attack
  compared to a long, random passphrase.
- Why offline attacks (no rate-limiting, no lockouts) are far more dangerous
  than online login attempts.

## Mitigation Recommendations
- Use long, random, unique passwords/passphrases — ideally via a password
  manager.
- Enforce salted, slow hashing algorithms (e.g. bcrypt/Argon2) for any
  application storing credentials.
- Enable multi-factor authentication so a cracked password alone isn't
  enough to gain access.

## Skills Gained
Offline password auditing, hash extraction workflow, and translating a
technical cracking exercise into concrete password-hygiene and MFA
recommendations.

> Note: this exercise was performed on a personal/test file created for the
> internship, not on any real third-party or production credentials.
