# Week 1 Review (2026-10-07 to 2026-10-15)

My first week learning cyber security: key ideas, commands, and habits to remember.

---

## 1. The big picture
- **Cyber security** = protecting computers, networks and data from attacks.
- **Offensive security** = thinking like an attacker to find weaknesses
  (example: scanning a site for hidden pages).offensive people actively test systems (with permission) to find weaknesses before attackers do, while a SOC analyst watches for real attacks and responds.
- **Defensive security** = detecting, blocking and investigating attacks
  (example: a SOC analyst).
- **Incident flow I practised:** detect -> contain (block) -> report.
- A good incident report answers: who, what, when, where, which account.

## 2. Careers I know about
- **SOC Analyst:** watches alerts and logs, decides what is a real threat
- **Penetration Tester:** legally attacks systems to find weaknesses
- **Digital Forensics Analyst:** investigates what happened after an incident
- **Security Engineer:** builds and maintains security tools
- **GRC Analyst:** risk, rules and compliance

## 3. How a computer works
| Part | What it does |
|------|--------------|
| Motherboard | Connects all components |
| CPU | The brain, runs instructions |
| RAM | Short-term memory (cleared when power is off) |
| Storage (SSD/HDD) | Long-term memory for files and the OS |
| GPU | Graphics |
| PSU | Power supply |
| BIOS/UEFI | Firmware that starts the computer |

**Boot steps:** power on -> BIOS/UEFI checks hardware (POST) -> finds the
OS on storage -> bootloader loads the kernel -> login screen.

## 4. Operating systems
- The OS is the **middleman between users, apps and hardware**
  (airport air traffic control analogy).
- It manages hardware, memory, files, and users/permissions.
- **Kernel space:** unrestricted hardware access, trusted core code.
- **User space:** normal apps, restricted, must ask the kernel.
- Attackers aim for the kernel because it controls everything.
- **Windows:** most common on desktops, most targeted.
- **Linux:** open source, runs most servers, many security tools.
- **macOS:** Apple's system, Unix-based.
- **File system:** how the OS stores and finds files (NTFS on Windows,
  ext4 on Linux). Think of a library: books, shelves, catalogue.

## 5. Commands cheat sheet

### Linux
| Command | What it does | Example |
|---------|--------------|---------|
| `ls` | List files and folders | `ls` |
| `cd` | Change directory | `cd folder1`, `cd ..` |
| `cat` | Print a file's contents | `cat notes.txt` |
| `file` | Show a file's real type | `file notes.txt` |
| `find` | Search for files | `find . -name filename` |

Remember:
- A space is needed between a command and its argument (`cd ..`, not `cd..`)
- `cat` with no filename waits for input and looks stuck. Press `Ctrl+C`.
- `Ctrl+C` stops almost any command that seems frozen.

### Security tools
| Command | What it does |
|---------|--------------|
| `dirb http://site` | Finds hidden pages by guessing common names |
| `nmap -sn IP` | Finds live hosts without scanning ports |
| `nslookup domain` | Turns a domain name into an IP address |
| `exiftool file.jpg` | Reads metadata (date, device, sometimes GPS) |

Status codes: **200** = page works, **301** = redirect.

## 6. Windows Fundamentals
- **Editions:** versions of Windows for different users
- **GUI:** desktop, Start menu, taskbar
- **NTFS:** Windows file system, supports permissions
- **System32:** critical system files, do not delete or edit
- **Users and groups:** users inherit permissions from their groups
  (`lusrmgr` shows them)
- **UAC (User Account Control):** asks permission before big changes,
  helps stop silent malware
- **Settings / Control Panel:** manage system settings
- **Task Manager:** shows running processes and resource use, useful
  for spotting suspicious programs
- **Windows Security:** built-in antivirus. In the lab it caught a real
  malicious file. Not perfect, but a solid first layer. Keep it on.

## 7. Networking (Cisco Module 1)
- Local and global networks connect daily life, business and the internet.
- The internet is the biggest network, made of millions of smaller ones.

## 8. Safety and ethics rules
- Only test systems I own or have **written permission** to test
  (TryHackMe, my own VMs).
- Never share flags, answers or full walkthroughs for rooms.
- Never commit passwords, keys or personal data to GitHub.
- Photos can leak location through metadata.
- Skills are not enough, trust and ethics matter just as much.

## 9. Mistakes that taught me something
- Typed `drib` instead of `dirb` -> "Unknown command"
- Forgot `//` in `http://`
- Typed `cd..` and `.cd`
- Ran `cat` alone and thought the machine was frozen
- Account name was cut off with "..." -> widen the column
