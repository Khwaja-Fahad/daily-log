# Day 9 - 2026-10-17

## Windows Fundamentals 2 (TryHackMe)
Room completed: 100% (all 9 tasks)

## What I learned

### System Configuration and Advanced System Settings
Tools for controlling how Windows starts and behaves. System Configuration
(msconfig) lets me see and change things like startup options and
services. Advanced System Settings covers performance, user profiles and
environment settings.

### Change UAC Settings
Last time I learned that UAC (User Account Control) asks permission before
big changes. This time I saw that its level can be adjusted, from always
notify to never notify. Lower levels are less annoying but less safe, so
turning UAC off is a bad idea.

### Computer Management
A single place to manage a machine: users and groups, services, disks,
event logs and more. Useful for defenders because it shows what is
running and who has access.

### System Information
Shows details about the machine: Windows version, hardware, and system
settings. Useful when I need to know exactly what I am looking at.

### Resource Monitor
Shows live CPU, memory, disk and network usage in more detail than Task
Manager. For a defender, it can show which program is using the network,
which may reveal suspicious activity.

### Command Prompt
The Windows command line. I can do things by typing commands instead of
clicking.
### Registry Editor
The registry is a large database where Windows stores its settings and
configuration. Programs and Windows read from it all the time.
Important: wrong changes can break the system, so look but do not edit
unless I know exactly what I am doing.

## Why this matters for security
- Attackers often use the registry and startup settings to make malware
  run every time the computer starts (called persistence), so defenders
  need to know where to look.
- Resource Monitor and Computer Management help spot unusual programs,
  connections and accounts.
- UAC settings are a first layer of defence, so weakening them helps
  attackers.
- Knowing normal Windows tools helps me notice what is abnormal.

## Connection to earlier days
- Day 5/6: Linux and Windows commands both give me a way to inspect a
  system from the command line.
- Day 7: Windows Fundamentals 1 covered accounts, UAC, and Task Manager.
  Today added deeper tools for the same ideas.
