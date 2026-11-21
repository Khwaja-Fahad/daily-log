# Day 31 - 2026-11-21

## Windows CLI Basics (TryHackMe)
Room completed: 100% (all 4 tasks)

## The scenario
Day 2 of a simulated internship: find a hidden-away file using only the Windows Command Prompt, read it, and then collect basic information about the machine.

## What the Windows command line is
- The **Command Prompt (CMD)** is a text-based interface where I type commands instead of clicking folders and menus.
- It is faster, more precise and easier to automate, and many tools only run in the terminal.
- Windows is the most common desktop system in workplaces, so many real investigations and attacks involve Windows machines.

## Commands I used

### Navigating and finding files
| Command | What it does |
|---------|--------------|
| `cd` (alone) | Shows the full path of the folder I am in |
| `cd folder` | Moves into a folder |
| `cd ..` | Moves back up one level |
| `dir` | Lists the visible files and folders |
| `dir /a` | Also shows **hidden** files and folders |
| `dir /s filename` | Searches all subfolders from here and prints the full path if the file exists |
| `type file.txt` | Prints a file's contents |

### Gathering system information
| Command | What it tells me |
|---------|------------------|
| `whoami` | Which user account I am logged in as |
| `hostname` | The computer's name |
| `systeminfo` | OS name, OS version and system type (32-bit or 64-bit), plus much more |
| `ipconfig` | Network settings: IPv4 address and default gateway |

## Things I learned
- **Hidden does not mean secret.** Windows hides some files by default, and `dir /a` reveals them. Real data is often buried in hidden or deeply nested folders.
- **Search instead of guessing.** `dir /s` finds a file when I only know its name, like `find` on Linux.
- `cd` does two jobs: with no folder it shows where I am, and with a folder it moves me there.
- `systeminfo` prints a lot. I only need to focus on the OS name, version and system type, and I do not need to understand every line at first.
- The default gateway from `ipconfig` is the router's address, which matters for network checks.

## Windows vs Linux commands
| Job | Windows | Linux |
|-----|---------|-------|
| Where am I | `cd` | `pwd` |
| List files | `dir` | `ls` |
| Show hidden files | `dir /a` | `ls -a` |
| Find a file | `dir /s name` | `find . -name name` |
| Read a file | `type` | `cat` |
| Current user | `whoami` | `whoami` |
| Computer name | `hostname` | `hostname` |
| System details | `systeminfo` | `uname -a` |
| Network settings | `ipconfig` | `ip a` |

## Why this matters for security
- These are the first commands an analyst runs on a machine: who am I, what machine is this, which version, how is it connected.
- The **user account** matters because different accounts have different permissions.
- The **Windows version** matters because known vulnerabilities depend on it, and old unpatched versions are riskier.
- The **IP address and gateway** help trace where a machine sits on the network and who it talks to.
- Attackers hide files and tools, so knowing how to reveal hidden items and search the disk is part of an investigation.
- Typing commands leaves a smaller footprint than clicking through a GUI, and commands can be automated into scripts.
- Only run these on my own machines, lab machines, or systems I am authorised to examine.

## Full forms
- **CMD:** Command Prompt
- **CLI:** Command Line Interface
- **OS:** Operating System
- **IP / IPv4:** Internet Protocol / Internet Protocol version 4

## Time and completion
- Time spent: 30 minutes
- Room completed: 100%

## Operating System Security (TryHackMe)
Room completed: 100% (all 3 tasks)

## What I learned

### Introduction to Operating System Security
- **Hardware** is everything I can touch: screen, keyboard, motherboard, CPU, RAM and storage.
- The **operating system (OS)** is the layer between the hardware and my applications. Programs cannot run directly on the hardware, so the OS lets them use it according to rules.
- OS types:
  - Desktop and laptop: Windows, macOS, Linux
  - Phone: Android, iOS
  - Server: Windows Server, IBM AIX, Oracle Solaris, Linux
- Linux is used on both personal computers and servers. Applications such as email programs and browsers are **not** operating systems.
- Computers hold private data: messages, photos, ID copies, work files, saved passwords and banking apps. So the OS must be secured to protect all three parts of the **CIA Triad**:
  - **Confidentiality:** only the right people can see the data
  - **Integrity:** nobody can tamper with it
  - **Availability:** the device works when I need it

### Common examples of OS security problems

**1. Authentication and weak passwords**
- **Authentication** means proving who I am. Three kinds of proof:
  - Something I **know** (password, PIN)
  - Something I **are** (fingerprint)
  - Something I **have** (phone for an SMS code)
- Passwords are the most common method, so they are the most attacked.
- Typical mistakes: easy-to-guess passwords, the same password on many sites, and personal details such as a birthday or pet's name.
- Public lists of the most common passwords show attackers' favourites: number sequences (`123456`), dictionary words, and **keyboard patterns** (`qwerty`). A pattern that looks complex is still very predictable.
- **Swapping letters for numbers** (like `o` to `0`) does not make a weak word strong, because attackers try those swaps first.
- Good practice: long, unique passphrases (several unrelated words), a **password manager**, a different password for every account, and **multi-factor authentication**.

**2. Weak file permissions**
- **Least privilege:** each person gets only the access needed for their work, which answers "who can access what?"
- Weak permissions hurt **confidentiality** (people read files they should not) and **integrity** (people change files they should not).

**3. Malicious programs**
- A **Trojan** looks harmless but gives the attacker access, so they can read or change files.
- **Ransomware** encrypts the user's files and demands payment for the key. It attacks **availability**.

### Practical: attacking a weak account in a lab
Scenario: a security check for a client. The lab machine had accounts with careless users.
- **Commands used:**
  | Command | What it does |
  |---------|--------------|
  | `ssh user@IP` | Connects to a remote Linux machine securely |
  | `whoami` | Shows which user I am logged in as |
  | `ls` | Lists the files in the current folder |
  | `cat file` | Prints a file's contents |
  | `history` | Shows the commands this user has typed |
  | `su - user` | Switches to another user account |
- On the **first SSH connection**, a warning says the server's authenticity cannot be verified, and I answer yes to trust it.
- When typing an SSH password **nothing appears on screen** (no dots or stars). That is normal.
- **Guessing passwords:** I tried the most common passwords against a known username. A weak password gave me access, which shows why common passwords are dangerous.
- **Privilege escalation:** the goal is to reach the administrator account. It is called **root** on Linux, Android and Apple systems, and **Administrator** on Windows. Both have unrestricted access to the system.
- **Shell history lesson:** `history` can reveal what a user typed, including a password typed by mistake at the command prompt. Never type a password where a command goes, because it is saved in plain text.
- I only did this inside the lab machines provided.

## Connection to what I already know
- This is the CIA Triad applied: weak passwords attack confidentiality, weak permissions attack confidentiality and integrity, and ransomware attacks availability.
- The SSH host key warning on first connection is the same trust check explained in the Linux administration course.
- The command history is a file in the user's home folder, which is one of the first places an investigator looks.
- Password guessing leaves traces: many failed logins in the authentication logs, which a SOC analyst watches for.
- Least privilege links to Linux file permissions, groups and the `sudo` model.

## The defender's view (what stops this attack)
- **Strong, unique passwords** and a password manager
- **Multi-factor authentication**, so one stolen password is not enough
- **Account lockout** or rate limiting after failed attempts
- **SSH keys** instead of passwords, and no direct root login over SSH
- Use `sudo` for admin tasks instead of sharing the root password
- Monitor failed logins and alert on many attempts from one source
- Regular permission reviews and **backups** against ransomware
- Train users not to type passwords into the command line

## Why this matters for security
- Most real attacks start with a **stolen or guessed credential**, not with advanced hacking.
- One weak account plus one careless habit (a password in the history) can lead to full system control.
- Knowing how the attack works helps me recognise it in logs and recommend fixes in an incident report.
- Only attempt this on lab machines or systems I am authorised to test. Guessing passwords on real systems is illegal.

## Full forms
- **OS:** Operating System
- **CIA:** Confidentiality, Integrity, Availability
- **SSH:** Secure Shell
- **MFA:** Multi-Factor Authentication
- **PIN:** Personal Identification Number
- **SMS:** Short Message Service
- **NCSC:** National Cyber Security Centre (UK)
- **CPU:** Central Processing Unit
- **RAM:** Random Access Memory
- **HDD / SSD:** Hard Disk Drive / Solid State Drive

## Time and completion
- Time spent: 60 minutes
- Room completed: 100%
