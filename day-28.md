# Day 28 - 2026-11-16

## SOC Fundamentals (TryHackMe)
Room completed: 100% (all 7 tasks)

## What I learned

### Introduction to SOC and Purpose and Components
- **SOC** (Security Operations Centre) is the team, process and set of tools that continuously monitor an organisation, so threats are detected and handled quickly.
- What a SOC watches for:
  - Vulnerabilities (weak spots that could be used)
  - Policy violations (rules being broken)
  - Unauthorised activity (accounts or devices doing things they should not)
  - Intrusions (an attacker getting into the network)
- Core purpose: **detect, respond, and improve**. The aim is to find an attack early, before it does damage.
- The three pillars: **People, Process, Technology**. A SOC needs all three to work well.

### People
| Role | What they do |
|------|--------------|
| **SOC Analyst, Tier 1 (Level 1)** | First line: watches alerts, triages, escalates real threats |
| **SOC Analyst, Tier 2 (Level 2)** | Deeper investigation and response |
| **SOC Analyst, Tier 3 / Threat Hunter** | Advanced analysis, proactively hunts for hidden attackers |
| **Incident Responder / Forensic Analyst** | Contains attacks and studies what happened |
| **Detection Engineer** | Builds and tunes the rules that create alerts |
| **SOC Lead / Manager** | Runs the team, shifts, reporting and priorities |
- Good analysts need curiosity, clear writing, teamwork and calm under pressure.

### Process
- **Alert triage:** an alert arrives, and I decide if it is a **true positive** (real) or a **false positive** (harmless).
- Questions to ask: What happened? When? Where (which system)? Who (which user or IP)? Why or how?
- **Prioritisation:** handle the most serious and most widespread alerts first.
- **Escalation:** pass real incidents to a higher tier, with clear notes.
- **Reporting and documentation:** write what I saw, what I did and why, so another analyst can continue without asking me.
- Other processes: **incident response**, **digital forensics**, **vulnerability management** (finding, ranking and fixing weak spots), and **handover** between shifts.

### Technology
| Tool | Full form | Job |
|------|-----------|-----|
| **SIEM** | Security Information and Event Management | Collects logs from many sources, correlates them and raises alerts |
| **EDR** | Endpoint Detection and Response | Watches laptops and servers for suspicious behaviour |
| **Firewall** | | Filters network traffic by rules |
| **IDS / IPS** | Intrusion Detection / Prevention System | Detects (IDS) or blocks (IPS) attacks in traffic |
| **SOAR** | Security Orchestration, Automation and Response | Automates routine response steps |
| **Threat intelligence** | | Data on known bad IPs, domains and attacker methods |
- Logs come from many places: firewalls, servers, endpoints, DNS, web servers and user logins.
- A SIEM is only as good as the logs it receives and the rules that are tuned.

### Practical Exercise of SOC
- I worked on a realistic alert as a Level 1 analyst.

## Connection to what I already know
- The incident flow I practised (detect, contain, investigate, report) is the same cycle a SOC follows.
- Log reading (failed logins, unusual accounts, odd processes) is the daily core of the work.
- Networking knowledge (IP, DNS, HTTP, ports) explains what many alerts mean.
- Linux and Windows investigation skills help when checking a suspicious machine.
- The CIA Triad helps me judge how serious an alert is.
- Writing a clear incident report is as important as the technical work.

## What a SOC gives an organisation
- Round-the-clock monitoring, usually in shifts, so attacks outside office hours are still noticed.
- Faster detection and response, which lowers damage and cost.
- A record of incidents, so lessons are learned and defences improve.

## Skills to build next
- Use a real **SIEM** (for example Splunk or Elastic) and write simple searches.
- Read **Windows event logs** and basics of **Active Directory**.
- Learn **phishing analysis** and basic **threat intelligence** lookups.
- Practise scripting with PowerShell or Python to automate log analysis.

## Full forms
- **SOC:** Security Operations Centre
- **SIEM:** Security Information and Event Management
- **EDR:** Endpoint Detection and Response
- **IDS / IPS:** Intrusion Detection System / Intrusion Prevention System
- **SOAR:** Security Orchestration, Automation and Response
- **TP / FP:** true positive / false positive

- Time spent: 45 minutes
- Room completed: 100%
