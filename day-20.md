# Day 20 - 2026-10-29

## Red Hat Academy: RH124 (Red Hat System Administration I)
Progress: Preface A, Chapter 1, and Chapter 2 up to Section 2.4 (Guided Exercise)

## Course introduction
RH124 teaches Linux administration "survival skills" for people with no
previous Linux admin experience. The goal is to operate and maintain an
existing Red Hat Enterprise Linux (RHEL) system from the command line.
It leads on to RH134 (System Administration II).

### How the labs work
- **Guided exercise:** step-by-step practice after a lesson
- **Quiz:** checks knowledge
- **End-of-chapter lab:** graded, with fewer hints
- `lab start <name>` prepares the environment and `lab finish <name>`
  cleans up afterwards. Always run `finish`, so later exercises are not
  affected.
- The classroom has a **workstation** machine plus **servera, serverb
  and serverc**. Timers stop or delete the environment, so keep the
  auto-stop timer set while working, and note that DELETE erases all
  saved work.

## Chapter 1: Introduction to Red Hat Enterprise Linux

### Why Linux
Linux runs web servers, the cloud, most supercomputers, smart TVs and
IoT devices, and Linux skills are in high demand.

### Open source
Software whose source code anyone can use, study, modify and share.
- **Copyleft licenses** (like GPL): anyone who shares the code must keep
  it open too.
- **Permissive licenses** (like MIT, Apache): maximum reuse, even inside
  proprietary products.
- Benefits: control, training, security (code can be inspected), and
  stability.

### Linux distribution
A complete installable OS made from the **Linux kernel** (started by
Linus Torvalds in 1991) plus tools, programs and libraries, with a way
to install and update them.

### The Red Hat ecosystem
**Fedora** (new features, short life) -> **CentOS Stream** (upstream of
RHEL) -> **RHEL** (stable, commercially supported, about 10 years).
RHEL is free to use as open source, and the subscription pays for
support, updates and security patches.
- Also learned: EPEL, UBI, and the free Red Hat Developer Subscription.

## Chapter 2: Accessing the Command Line

### The shell
- The command line is provided by a program called the **shell**. The
  default in RHEL is **Bash**.
- Prompt ending in **`$`** = regular user. Prompt ending in **`#`** =
  **superuser (root)**, so be extra careful, because mistakes can affect
  the whole system.
- A command has three parts: **command**, **options** (like `-L`) and
  **arguments** (the target). Example: `usermod -L user01` locks the
  password of user01.
- Bash is similar to Windows `cmd.exe` but closer to PowerShell,
  because of its scripting language.

### Logging in
- Physical console with virtual consoles **tty1 to tty6** (switch with
  Ctrl+Alt+F1 to F6). The graphical login usually runs on tty1.
- Servers are often **headless** (no screen), reached remotely.
- **SSH** is the standard way to get a remote shell:
  `ssh user@host`. It **encrypts** the connection.
- **Key-based login:** a private key (kept secret) matches a public key
  on the server, so no password is needed. The private key file must be
  readable only by its owner (`chmod 600`), or SSH refuses to use it.
- **First connection:** SSH warns it cannot verify the host and asks
  whether to trust it. If a saved host key later **changes**, SSH
  closes the connection with a warning, because it may be an
  interceptor attack.
- Leave a session with `exit` or **Ctrl+D**.

### The GNOME desktop
- Top bar, Activities Overview (Super key), message tray, dash,
  workspace selector, and system menu.
- Workspaces group windows by task.
- Terminal in RHEL 10 is **Ptyxis**. Open it from Activities by typing
  "terminal".
- Lock the screen from the system menu (or Super+L), log out, and
  power off or restart from the Power icon.

### Guided exercise (what I practised)
Logged out and back in, used the terminal to change a user's password
with `passwd`, locked and unlocked the screen, and found the power-off
option without shutting down. Ran `lab start` first and `lab finish` at
the end. (No passwords or solutions recorded here.)

## Connection to my other learning
- Day 5: `ls`, `cd`, `cat`, `find` are the same commands I will use here.
- Day 15: **SSH is the secure replacement for Telnet**, which sends
  passwords in plain text. This chapter showed why: SSH encrypts
  everything.
- Day 4: the kernel, user space and permissions ideas explain what a
  distribution is made of.
- Day 14: Bash compared with Windows Command Prompt and PowerShell.
- Day 7: UAC on Windows is similar in spirit to the `$` vs `#` warning:
  both mark when you have higher privileges.

## Why this matters for security
- Most servers run Linux, and both defenders and attackers work in the
  Bash shell.
- **Least privilege:** use a normal `$` account for daily work and root
  (`#`) only when needed.
- **Key-based SSH** is stronger than passwords, and **private keys must
  be protected** (permissions 600, never uploaded to GitHub).
- A **changed SSH host key** is a warning sign of someone intercepting
  the connection. Never just click yes without thinking.
- Open source code can be inspected and fixed by anyone, which helps
  security, though it still needs people to actually review it.
