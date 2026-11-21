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
