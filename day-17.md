# Day 17 - 2026-10-26

## DNS in Detail (TryHackMe)
Room completed: 100% (all 5 tasks)

## What I learned

### What is DNS?
DNS (Domain Name System) turns names that humans remember, like
example.com, into IP addresses that computers use. It is the phone book
of the internet.
- Example: I save a friend's name in my phone, and the phone looks up
  the number when I call. I do the same with a website name.
- Without DNS, I would have to remember the IP address of every site.

### Domain Hierarchy
A domain name is read from right to left, from the most general part
to the most specific.
- **TLD (top-level domain):** the last part, like `.com`, `.org`, `.hu`
- **Second-level domain:** the main name, like `example` in example.com
- **Subdomain:** the part at the front, like `www` or `shop`
- Example: in `shop.example.com`, `.com` is the TLD, `example` is the
  domain, and `shop` is the subdomain.
- Length limits exist (a name has a maximum size, and each part too).

### Record Types
DNS stores different kinds of information in records:
| Record | What it does |
|--------|--------------|
| **A** | Maps a name to an IPv4 address |
| **AAAA** | Maps a name to an IPv6 address |
| **CNAME** | An alias that points one name to another name |
| **MX** | Says which mail server handles email for the domain. It has a priority number, and a lower number is tried first |
| **TXT** | Stores text information, often used to prove ownership or for email security |

### Making A Request
When I type a website name, the lookup follows these steps:
1. My computer checks its **local cache** first.
2. If not found, it asks the **recursive DNS server** (usually my ISP's
   or a public one).
3. That server asks a **root server**, which points to the right
   **TLD server**.
4. The TLD server points to the domain's **authoritative server**,
   which holds the real answer.
5. The answer returns to me and gets **cached** for a time (the **TTL**,
   Time To Live), so the next lookup is faster.

### Practical
I used the room's website to build DNS queries and see the results. The
site also showed the command I would run on my own computer, which is
`nslookup` or `dig`. I looked up different record types for a practice
domain and read the answers. 

## Connection to earlier days
- Day 6: `nslookup` resolves a domain to an IP address. Now I know the
  steps behind it.
- Day 10: `ipconfig /all` showed my DNS servers, which are the ones I ask.
- Day 14: `nslookup` is one of the Windows command line tools.
- Day 15: DNS is an Application layer protocol and usually uses UDP.
- Day 16: DNS records are public, so they are also an OSINT source.

## Why this matters for security
- **DNS spoofing/poisoning:** if an attacker puts a fake answer in a
  cache, users get sent to a fake site even though they typed the
  right name.
- **Phishing domains:** attackers register lookalike names, so checking
  the domain really matters.
- **TXT records** are used for email security (like SPF), which helps
  stop fake emails, so defenders read them.
- **Subdomains and records** can reveal what a company runs, which
  attackers and defenders both check (OSINT).
- DNS logs help a SOC analyst spot suspicious activity, like a computer
  asking for strange domains.
- I only query domains in labs or ones I am allowed to test.

## Time and completion
- Time spent: 30 minutes
- Room completed: 100%
