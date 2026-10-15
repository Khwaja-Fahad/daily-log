# Day 7 - 2026-10-15

## Windows Fundamentals 1 (TryHackMe)

## What I learned

### Windows Editions
Windows comes in different versions (editions) made for different users,
such as home users and businesses.

### The Desktop (GUI)
The GUI (graphical user interface) is what I see and click on: the
desktop, Start menu, taskbar and icons. It lets me use the computer
without typing commands.

### The File System
Windows uses the **NTFS** file system to store and organise files. It
supports permissions, so it can control who may read or change a file.
Example: a library, where NTFS is the catalogue plus the rules about who
may borrow each book.

### The Windows\System32 folder
This folder holds files that Windows needs to run. It is critical, so
normal users should not delete or change anything inside it.

### User Accounts, Profiles, and Permissions
- Windows has built-in accounts like Administrator and Guest, plus
  accounts that people create.
- Users are placed in **groups**, and a user inherits the permissions of
  the group. I used `lusrmgr` (Local Users and Groups) to see the
  accounts and groups on the machine.
- Lesson: the account name was cut off with "...", and I fixed it by
  widening the column.

### User Account Control (UAC)
UAC asks for permission before a program makes big changes to the system.
It helps stop malware from changing things silently.

### Settings and the Control Panel
Both are places to manage system settings (users, programs, network,
updates). Control Panel is the older style, Settings is the newer one.

### Task Manager
Shows running programs and processes and how much CPU and memory they
use. Defenders use it to spot suspicious programs running.

## Why this matters for security
- Permissions and groups decide who can do what, so wrong settings can
  give attackers too much access.
- UAC and user accounts are the first layers that protect a system.
- Knowing what is normal in System32 and Task Manager helps me notice
  what is abnormal.

## Week 1 review
- Day 1: Offensive Security Intro, used `dirb`
- Day 2: Defensive Security Intro, FakeBank incident report
- Day 3: Careers in Cyber, computer basics, OS intro
- Day 4: Windows, Linux, macOS and file systems, Cisco Module 1
- Day 5: Linux commands (`ls`, `cd`, `cat`, `file`, `find`)
- Day 6: Windows basics, `nmap -sn`, `nslookup`, `exiftool`
- Day 7: Windows Fundamentals 1
