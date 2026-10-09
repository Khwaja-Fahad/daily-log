# Day 3 - 2026-10-09

## Careers in Cyber
I learned that cyber security has many different career paths, not just
"hacker". Some examples:
- **SOC Analyst:** monitors alerts and investigates suspicious activity
- **Penetration Tester:** legally attacks systems to find weaknesses
- **Digital Forensics Analyst:** investigates what happened after an incident
- **Security Engineer:** builds and maintains security tools and systems
- **GRC Analyst:** handles risk, rules and compliance

The role that interests me most now: [YOUR CHOICE and why, one sentence].

## Computer Fundamentals: inside a computer
I learned what the main parts of a computer are and how they work together.
- **Motherboard:** the main circuit board that connects every component
- **CPU:** the "brain" that executes instructions
- **RAM:** short-term memory for programs that are running (cleared when
  power is off)
- **Storage (SSD/HDD):** long-term memory where files and the OS are kept
- **GPU:** handles graphics and visual processing
- **PSU:** supplies power to all the components
- **BIOS/UEFI:** firmware on the motherboard that starts the computer

## What happens when I press the power button
1. Power flows from the PSU to the motherboard
2. BIOS/UEFI starts and runs a check on the hardware (POST)
3. The computer finds the storage device that holds the operating system
4. A bootloader loads the OS kernel into RAM
5. The OS finishes starting and shows the login screen/desktop

Why this matters for security: attackers can target every layer, from
firmware to the OS, so defenders need to understand how a normal startup
looks.

## Operating Systems: Introduction
An operating system (OS) is the software that manages the hardware and
lets programs and users work with the computer. It handles:
- Running programs (processes)
- Memory
- Files and storage
- Users and permissions

Common examples: Windows, Linux, macOS. [Add anything else the room
taught you, e.g. the kernel or how Linux differs from Windows.]

## Terminal practice (Linux)
- `ls` lists files in the current folder
- `cd foldername` moves into a folder; `cd ..` goes up one level
  (the space before `..` is required)
- `cat filename` prints a file's contents
- Running `cat` with no filename makes it wait for input, so it looks
  stuck. `Ctrl+C` stops it.

### Mistakes and lessons
- I typed `cd..` and `.cd`, which gave "command not found"
- I ran `cat` without a filename and thought the machine was frozen
- Lesson: commands and arguments are separated by spaces, and `Ctrl+C`
  is my escape button


