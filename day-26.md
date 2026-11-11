# Day 26 - 2026-11-11

## Cryptography Basics (TryHackMe)
Room completed: 100% (all 7 tasks)

## What I learned

### Importance of Cryptography
Cryptography is the practice of protecting information so that only the
right people can read it or trust it. It supports the CIA Triad (Day 23):
- **Confidentiality:** only authorised people can read the data
- **Integrity:** the data was not changed on the way
- **Authentication:** I can check who sent it
- **Non-repudiation:** the sender cannot deny sending it
Example: HTTPS protects my bank login, and SSH protects a remote
login.

### Plaintext to Ciphertext
| Term | Meaning |
|------|---------|
| **Plaintext** | The original readable message |
| **Ciphertext** | The scrambled, unreadable result |
| **Cipher / algorithm** | The method used to scramble |
| **Key** | The secret value the method needs |
| **Encryption** | Plaintext to ciphertext |
| **Decryption** | Ciphertext back to plaintext |
- Example: a padlock. The padlock design is the algorithm, and the key is
  what opens it. Everyone can know how the padlock works, but only the key
  holder opens it.
- Modern security rule (Kerckhoffs's principle): the algorithm can be
  public, and **only the key needs to be secret**.

### Historical Ciphers
- **Caesar cipher:** shift every letter by a fixed number. With a shift of
  3, `HELLO` becomes `KHOOR`. The shift is the key.
- Historical ciphers are weak today. With only 25 possible shifts, a
  computer tries them all in a moment (a **brute-force** attack). Letter
  patterns can also give them away (**frequency analysis**: in English, `E`
  is the most common letter).
- Lesson: hiding the method is not security. A good cipher survives even
  when the attacker knows how it works.

### Types of Encryption
| Type | Keys | Speed | Examples |
|------|------|-------|----------|
| **Symmetric** | One shared key encrypts and decrypts | Fast | **AES** (Advanced Encryption Standard), **DES** (Data Encryption Standard, old and weak) |
| **Asymmetric** | A pair: **public key** encrypts, **private key** decrypts | Slower | **RSA** (Rivest-Shamir-Adleman) |
- **Symmetric problem:** how do both sides share the key safely? If an
  attacker gets it, they can read everything.
- **Asymmetric** solves the sharing problem. The public key can be given to
  anyone, and the private key stays secret. This is the idea behind SSH
  key login (Day 20), where the private key must be protected (`chmod 600`).
- In practice they work together: HTTPS (TLS, Transport Layer Security)
  uses asymmetric encryption to agree on a key, then fast symmetric
  encryption for the data.

### Basic Math
- **XOR** (exclusive OR): compares two bits. Same gives `0`, different
  gives `1`. Example: `1 XOR 1 = 0` and `1 XOR 0 = 1`. XOR-ing with a key
  twice returns the original, so it is used inside many ciphers.
- **Modulo** (`mod`): the remainder after division. `7 mod 3 = 1`.
  Caesar uses `mod 26`, so after `Z` it wraps back to `A`.
- This links to Day 19: XOR and modulo work on binary and hex values.

## Connection to earlier days
- HTTPS uses TLS, which is encryption in motion. Plain HTTP and
  Telnet send data readable.
- **encoding is not encryption.** Base64 or hex needs no
  key, while encryption needs a key.
- SSH encrypts the connection, and key login uses a public and
  private key pair.
- MD5 (Message Digest 5) checksums in `debsums`. A **hash** is
  different from encryption: it is one-way and cannot be reversed to get
  the original.
- BIOS, boot and keys: attackers target every layer, including
  encryption keys.

## Encryption, encoding and hashing
| | Encoding | Encryption | Hashing |
|---|---|---|---|
| Purpose | Format data | Keep data secret | Check integrity |
| Needs a key | No | Yes | No |
| Reversible | Yes | Yes, with the key | No |
| Example | Base64, UTF-8 | AES, RSA | MD5, SHA-256 |

## Why this matters for security
- Encryption protects data **in transit** (HTTPS, SSH, Wi-Fi WPA3) and
  **at rest** (encrypted disks and backups).
- Most real failures are about **keys**: weak or reused passwords, stolen
  private keys, keys uploaded to GitHub, or an old algorithm like DES.
- Defenders check that old, broken methods are not in use (WEP vs WPA3).
- Never invent my own encryption. Use well-tested standards.
- Encryption protects confidentiality only. It does not stop deleting or
  tampering, so integrity and availability still need hashes and backups.
- I only practise breaking ciphers in labs and challenges.

## Time and completion
- Time spent: 45 minutes
- Room completed: 100%
