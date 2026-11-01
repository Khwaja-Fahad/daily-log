# Day 21 - 2026-11-01

## Checkpoint 1: review of the first weeks

A review day with no new topics. I wrote down what I know about each topic so far, so I can see what is solid and what needs more practice.

---

## Two questions

### 1. What is the difference between a switch and a router?
- A **switch** works at **Layer 2 (Data Link)**. It uses **MAC addresses** to deliver data inside one local network.
- A **router** works at **Layer 3 (Network)**. It uses **IP addresses** to move data between different networks.

### 2. `ping 8.8.8.8` works but `ping google.com` fails. What is broken?
**DNS.** The internet connection itself is fine, because the raw IP address is reachable. What fails is turning the name into an IP address.

Next steps:
1. Check the DNS servers in `ipconfig /all`
2. Test with `nslookup google.com`

---

## The eight topics

### 1. Boot and OS
- Power flows from the PSU to the motherboard.
- BIOS/UEFI starts and runs **POST** to check the hardware.
- It finds the storage device that holds the OS.
- The **bootloader** loads the **kernel** into RAM and gives it control.
- The login screen appears.
- The OS is the **middleman** between users, apps and hardware. It manages hardware, memory, files, and users and permissions.
- The kernel has full hardware access, while apps run in restricted **user space**.

### 2. Linux commands
| Command | What it does |
|---------|--------------|
| `ls` | Lists files and folders |
| `cd` | Changes directory |
| `cat` | Prints a file |
| `file` | Shows a file's real type |
| `find . -name x` | Searches for files |
| `chmod` | Changes permissions |

**Permission numbers:** read = 4, write = 2, execute = 1, added up for the **owner, group, others** in that order.
- `644` = `rw-r--r--`: the owner can read and write, everyone else can only read.
- `755` = `rwxr-xr-x`: the owner has full access, everyone else can read and run it.
- `600` = owner only (used for SSH private keys).

Note: the RH124 course so far only used `chmod 600`, so the numbers 644 and 755 are something I need more practice with.

### 3. Windows tools
- **Task Manager:** shows running processes and resource use.
- **`lusrmgr.msc`:** manages local users and groups. Users inherit permissions from their groups.
- **UAC:** asks for permission before big changes, which makes changes visible and harder for malware to do silently.
- **Registry:** the database of Windows settings. Look, but don't edit unless I know exactly what I am doing.

### 4. IP, MAC, subnet mask, DHCP, ARP
- **IP address:** a logical address that can change between networks.
- **MAC address:** the hardware ID of the network card, written in hex.
- **Subnet mask:** shows which part of an IP address is the network and which is the device.
- **DHCP:** automatically gives devices their settings (address, mask, gateway, DNS).
- **ARP:** asks "who has this IP?" so a device can learn the matching MAC address.

### 5. The OSI layers (top to bottom)
Application, Presentation, Session, Transport, Network, Data Link, Physical.

Memory trick: **All People Seem To Need Data Processing.**

### 6. DNS
A lookup goes like this:
1. Check the **local cache**
2. Ask the **recursive resolver**
3. It asks a **root server**
4. Then the **TLD server**
5. Then the **authoritative server**
6. The answer comes back and is **cached** for its TTL

- **A record:** maps a name to an IPv4 address.
- **MX record:** names the mail server for a domain. A lower priority number is tried first.

### 7. HTTP
- **Methods:** GET (ask), POST (send), PUT (update), DELETE (remove).
- **Status codes:** 1xx information, 2xx success, 3xx redirect, 4xx client error, 5xx server error.
- **Cookies** let a stateless protocol remember who I am.
- The **Secure** flag means HTTPS only. **HttpOnly** means JavaScript can't read the cookie.

### 8. SSH vs Telnet
- Both give a remote command line.
- **Telnet** sends everything, including passwords, in plain text.
- **SSH** encrypts the connection, supports key-based login, and uses host keys to warn about interception.
- Use SSH, never Telnet.

---

## Why this review matters for security
- A SOC analyst needs these basics every day. Reading logs means knowing which layer a problem sits at, what a status code means, and what normal looks like.
- The `ping` question is a real troubleshooting pattern: test the local network, then the internet by IP, then by name, to find which part is broken.
- Reviewing without notes shows what I actually remember, not just what I have read once.

## Next
- Keep practicing the weak spots with flashcards, and type commands instead of only reading them.
- Continue RH124 and the networking and web topics.
