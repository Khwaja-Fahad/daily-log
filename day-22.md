# Day 22 - 2026-11-03

## Linux File System Analysis (TryHackMe)
Room completed: 100% (all 8 tasks)
Time spent: 2 hours

## What I did
Real-time analysis of a compromised Linux system to find the attacker's
artefacts (the traces they leave behind). I used the defender workflow
from Day 2: detect, contain, report.

## Commands I used

| Command | What it does |
|---------|--------------|
| `ls -al /home/user/.ssh/authorized_keys` | Shows permissions, owner, size and date of a user's SSH keys file |
| `ls -la /home/user` | Lists all files in a home directory, including hidden dotfiles |
| `ls -l /home` | Lists all user home directories |
| `cat /home/user/.bash_history` | Tries to read a user's command history |
| `sudo cat /home/user/.bash_history` | Runs `cat` as root to read a file I was denied as a normal user |
| `sudo ls /home/user` | Lists another user's directory with root rights |
| `stat file` | Shows exact Access, Modify and Change timestamps |
| `sudo chkrootkit` | Scans for known rootkit signatures and suspicious files |
| `sudo find / -name "*.sh" 2>/dev/null` | Finds all shell scripts, and hides "Permission denied" errors |
| `sudo debsums -e -s` | Checks config files against original package checksums (`-e` = config files only, `-s` = silent, shows only errors) |

## What I looked for
1. **Backdoor user accounts:** checked `/etc/passwd` for new accounts and
   for an extra account with UID 0.
2. **SSH backdoors:** checked `authorized_keys` for unauthorised keys and
   its permissions with `ls -al`.
3. **Altered config files:** `debsums` showed that the sudo configuration
   had been changed.
4. **Rootkits and persistence scripts:** `chkrootkit` flagged a suspicious
   script in a temporary directory.

## Terms I didn't understand
- **`.bash_history`:** a hidden file in a user's home folder that records
  the commands typed in their terminal. In forensics, it is often the
  first place analysts check to see what an attacker or user did.
  Caution: an attacker can delete or edit it, so an empty history is
  itself suspicious.
- **`authorized_keys`:** a file in `~/.ssh/` containing the public SSH
  keys allowed to log in to that account without a password. If an
  attacker adds their key here, they can SSH in whenever they want.
- **World-writable file (`rw-rw-rw-` or 0666):** a permission setting
  that lets any user on the system, even unprivileged ones, modify or
  overwrite the file.
- **UID (User ID) / UID 0:** Linux gives every account a numeric ID.
  UID 0 is root, the superadministrator. If another account also has
  UID 0, it has full root control.
- **Rootkit:** malicious software or scripts designed to hide an
  attacker's presence and keep privileged access to a system.
- **`chkrootkit`:** a command-line tool that scans Linux systems for
  signs of rootkits, backdoors and malicious scripts. It checks known
  signatures, so it cannot prove a system is clean.
- **`debsums`:** a tool on Debian and Ubuntu that checks the integrity
  of installed packages by comparing local files with the original
  MD5 (Message Digest 5) checksums.

## Mistakes and lessons
Mistakes made on the system, and how to fix each:

1. **Insecure SSH permissions:** `authorized_keys` was world-writable
   (`rw-rw-rw-`), so an unprivileged user could easily add an SSH public
   key and gain SSH access to another user's account.
   Fix: `chmod 600` on the file, and regular permission audits.
2. **Unmonitored local user creation:** a backdoor account with UID 0
   was created without triggering any alert or account audit.
   Fix: audit accounts, and alert on any non-root UID 0.
3. **No file integrity monitoring:** critical config files such as
   `/etc/sudoers` were modified without any File Integrity Monitoring
   (FIM) alerting the administrators.
   Fix: use a FIM tool and run `debsums` checks.
4. **Leftover persistence scripts:** malicious scripts were placed in a
   world-writable temporary directory (`/var/tmp/`) and left unmonitored.
   Fix: monitor temporary folders, and remove unknown scripts.

## Connection to earlier days
- Day 5: `ls`, `cat`, `find`, now used for investigation.
- Day 20: SSH keys, `chmod 600`, root vs normal user.
- Day 21: chmod numbers and permissions.
- Day 7 and 9: persistence on Windows (registry). This is the Linux version.

## Safety
Only investigate machines I own, lab machines, or systems I have written
permission to examine. I did not record the room's account names, file
paths for flags, or answers here.
