# Day 14 - 2026-10-23

## Windows Command Line (TryHackMe)
Room completed: [100%?]

## What I learned
The command line lets me control Windows by typing instead of clicking.
It is faster, can be automated, and defenders and attackers both use it.
Open it with Start, type `cmd`, press Enter.

### Basic commands
| Command | What it does |
|---------|--------------|
| `hostname` | Shows the computer's name |
| `whoami` | Shows which user I am logged in as |
| `dir` | Lists files and folders (like `ls` on Linux) |
| `cd folder` | Moves into a folder, and `cd ..` goes up |
| `type file.txt` | Prints a file's contents (like `cat` on Linux) |
| `cls` | Clears the screen |

### Network troubleshooting
| Command | What it does |
|---------|--------------|
| `ipconfig /all` | Shows IP, MAC, gateway, DNS and DHCP info |
| `ping address` | Checks if a device answers and how fast |
| `nslookup domain` | Turns a domain name into an IP address |
| `tracert address` | Shows each router a packet passes through |
| `netstat` | Shows active network connections |

### Task and process management
| Command | What it does |
|---------|--------------|
| `tasklist` | Lists running processes (command-line Task Manager) |
| `taskkill` | Stops a process |

Command I would use to check what is running: `tasklist`.

## Windows vs Linux commands I now know
| Job | Windows | Linux |
|-----|---------|-------|
| List files | `dir` | `ls` |
| Read a file | `type` | `cat` |
| Clear screen | `cls` | `clear` |
| Find my info | `whoami` | `whoami` |

## How I read output
1. Split the command into parts (command, option, target)
2. Read from the top down
3. Look for key words like Reply, Lost, Address, Error
4. Ask: what did it show, is it normal, what would be unusual?
If I don't know a command, I add `/?` (example: `ping /?`).

## Why this matters for security
- Defenders use `tasklist`, `netstat` and `ipconfig` to investigate a
  suspicious machine quickly.
- Attackers also use the command line, so knowing normal commands helps
  me notice abnormal ones.
- `taskkill` and similar commands can break a system, so I only use
  them in labs or on machines I own.

## Time and completion
- Time spent: 1 hour
