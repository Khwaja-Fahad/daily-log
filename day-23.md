# Day 23 - 2026-11-04

## Rooms completed
1. The CIA Triad (TryHackMe): 100%, 4 tasks
2. Data Encoding (TryHackMe): 100%, 4 tasks

## Room 1: The CIA Triad

CIA = **Confidentiality, Integrity, Availability**. It is the basic
model for deciding what "secure" means. (It has nothing to do with the
Central Intelligence Agency.)

### Understanding the CIA Triad
| Part | Meaning | Example | How it is attacked | How it is protected |
|------|---------|---------|--------------------|---------------------|
| **Confidentiality** | Only authorised people can see the data | Medical records | Data theft, password guessing, sniffing Telnet or HTTP (Day 15, 18) | Encryption, HTTPS, strong passwords, permissions |
| **Integrity** | Data is correct and has not been changed without permission | A bank balance | Altering files, ARP spoofing (Day 12), tampering with `/etc/sudoers` (Day 22) | Hashes and checksums (`debsums`), file integrity monitoring, permissions |
| **Availability** | Systems and data are there when needed | A bank website | Ransomware, DoS (Denial of Service) | Backups (3-2-1 rule, Day 13), redundancy, updates |

- Example for all three: an online bank. Only I can see my account
  (confidentiality), the balance is accurate (integrity), and the site
  works when I log in (availability).
- Improving one can weaken another. Example: very strict access
  controls protect confidentiality, but can make data harder to reach,
  which hurts availability. Security is about balance.

### The Security Mindset
- Ask "what could go wrong?" and "how could this be abused?", not only
  "does it work?". This is how attackers think, and defenders need to
  think like them (Day 1 and 2: offensive vs defensive).
- **Least privilege:** give people only the access they need
  (Day 20: `$` vs `#`, Day 7: users and groups).
- **Defence in depth:** several layers, so if one fails another
  stops the attack (UAC, antivirus, firewall, backups).
- Assume systems will be attacked, so plan to **detect and recover**,
  not only to prevent (Day 2: detect, contain, report).

### Why it matters
When I read a security problem, I can ask which part of CIA it hits.
Example: ransomware that encrypts files hits **availability**, and if
it also steals the files, **confidentiality** too.

## Room 2: Data Encoding

**Encoding** means converting data into a format that computers can
store and send. Everything is bytes underneath (Day 19), and an
encoding says which numbers stand for which characters.

### ASCII
- ASCII = **American Standard Code for Information Interchange**.
- Uses 7 bits, so 128 characters: English letters, digits,
  punctuation, and control codes. Extended versions use 8 bits (256).
- Examples: `A` = 65, `a` = 97, `0` = 48. Capital and small letters
  differ by 32.
- Limit: no accents or non-English alphabets, and no emoji.

### Unicode
- Unicode gives every character in every language a unique number,
  called a **code point**, written like `U+0041` (that is `A`).
- Covers more than a hundred thousand characters: other alphabets,
  symbols, emoji.
- **UTF** = **Unicode Transformation Format**, the ways of storing
  code points as bytes:
  - **UTF-8:** 1 to 4 bytes per character. The first 128 characters
    are identical to ASCII, so old ASCII text still works. The most
    common on the web.
  - **UTF-16:** 2 or 4 bytes per character.
  - **UTF-32:** always 4 bytes, simple but uses more space.
- If the wrong encoding is used to read text, it shows as garbled
  characters.

### Connection to earlier days
- Day 19: binary and hex. ASCII `A` = 65 = hex `41` = binary `01000001`.
- Day 5: the `file` command can tell what a file really contains.
- Day 6: `exiftool` reads metadata encoded in the file's bytes.
- Day 16: a **hash** is shown as hex characters.
- Day 17: lookalike domain names in phishing.

### Why it matters for security
- **Encoding is not encryption.** Anyone can reverse it, because it
  needs no key. Example: Base64 or hex makes data look strange, but
  gives no protection (Day 19).
- Attackers use encoding to hide malicious input from simple filters,
  so analysts need to recognise common encodings in logs and URLs.
- **Homograph attacks:** Unicode contains letters that look identical
  to others (for example from a different alphabet), so a fake domain
  can look like a real one. Defenders and users should check the real
  address.
- Mixed encodings can cause bugs that become vulnerabilities, such as
  filters that check text before it is converted.

## Full forms from today
- **CIA:** Confidentiality, Integrity, Availability
- **DoS:** Denial of Service
- **ASCII:** American Standard Code for Information Interchange
- **UTF:** Unicode Transformation Format
- **FIM:** File Integrity Monitoring

## Time and completion
- Time spent: 90 minutes
- Both rooms: 100%
