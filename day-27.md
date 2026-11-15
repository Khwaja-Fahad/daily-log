# Day 27 - 2026-11-15

## Junior Security Analyst Intro (TryHackMe)
Room completed: 100% (all 3 tasks)

## What I learned

### Junior Security Analyst Journey
- A **junior security analyst** (also called Tier 1 analyst or triage specialist) is the first person to look at security alerts. The job is to decide quickly what is real and what is not.
- Main duties:
  - Monitor alerts and logs
  - Triage (sort by seriousness and decide if it is a threat)
  - Investigate suspicious activity
  - Escalate real incidents to senior analysts
  - Document everything clearly
- Useful skills: networking basics, Linux and Windows basics, log reading, curiosity, clear writing, and staying calm under pressure.
- Career path: Tier 1 analyst, then Tier 2 (deeper investigation and response), then Tier 3 (threat hunting and advanced analysis), and later roles like incident responder or security engineer.

### Security Operations Center (SOC)
- **SOC** (Security Operations Centre) is the team and place that watches an organisation's systems 24 hours a day, 7 days a week, so attacks are found and stopped quickly.
- It rests on three pillars: **people** (analysts, engineers, managers), **process** (playbooks, escalation steps, incident response), and **technology** (the tools).
- Tools a SOC uses:
  - **SIEM** (Security Information and Event Management): collects logs from many systems and raises alerts
  - **EDR** (Endpoint Detection and Response): watches laptops and servers for suspicious behaviour
  - **Firewall** and **IDS/IPS** (Intrusion Detection/Prevention System): filter traffic and spot attacks
  - **Ticketing system**: tracks each alert from start to finish
  - **Threat intelligence**: information about known attackers and bad IPs or domains
- Because the SOC works in shifts, a good **handover** (telling the next shift what is open) matters.

### A Day in the Life of a Security Analyst
- The day is a loop: an alert arrives, I check it, decide what it is, act, and write it up.
- Alert outcomes:
  - **True positive:** a real threat, so contain it and escalate
  - **False positive:** a harmless event flagged by mistake, so close it with a note
  - Missing a real attack (a **false negative**) is the most dangerous outcome
- Triage questions I ask: What happened? When? Which user, device and IP? Is it normal for them? How serious is it?
- Evidence comes from several sources (logs, network data, endpoint data), because one source can mislead.
- Every case needs clear notes: what I saw, what I did, and why.

## Connection to what I already know
- The incident flow I practised (detect, contain, investigate, report) is exactly the analyst's routine.
- Log reading, such as failed logins and unusual accounts, is the daily core of the work.
- Network knowledge (DNS, HTTP, IP, ports) helps me understand what an alert means.
- The CIA Triad helps me judge how serious an alert is: does it threaten confidentiality, integrity or availability?
- Writing clear reports is as important as technical skill.

## Why this matters
- This is the role I am aiming for, so I now know what employers expect on day one.
- Gaps to fill: a SIEM tool, Windows event logs, Active Directory basics, and scripting for automation.
- Real analysts follow written playbooks and ask for help early, so asking is not a weakness.
- Only work on systems and data I am authorised to access.

## Full forms
- **SOC:** Security Operations Centre
- **SIEM:** Security Information and Event Management
- **EDR:** Endpoint Detection and Response
- **IDS / IPS:** Intrusion Detection System / Intrusion Prevention System
- **TP / FP / FN:** true positive, false positive, false negative

## Time and completion
- Time spent: 15 minutes
- Room completed: 100%
