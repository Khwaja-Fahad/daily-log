# Day 25 - 2026-11-10 (Exam day)

## Self-assessment exams
I took multiple-choice exams written from my own study notes (Days 1 to 24),
to test recall and how I apply what I learned.

| Exam | Focus | Score |
|------|-------|-------|
| Exam 1 | Foundations (computers, Linux, Windows, networking, OSI, DNS, HTTP, encoding, CIA, wireless) | 43/50 (86%) |
| Exam 2 | SOC scenarios (logs, suspicious accounts, network problems, web security, ethics) | 49/50 (98%) |

## What the exams showed
- **Strong areas:** networking basics, Linux investigation, CIA
  Triad, incident response order: contain, investigate, report
- **Scenario questions went better than definitions:** I scored higher
  when I had to decide what to do in a situation (Exam 2) than when I had
  to recall facts (Exam 1).
- **Honest limit:** the exams were written from my own notes, so a high
  score shows my notes are solid. It does not prove job readiness, and real
  exams and interviews will be less predictable.

## Red Hat note
I decided that RH124 background items (open source license types, Fedora to
CentOS Stream to RHEL flow, subscriptions, `lab` commands, tty consoles) are
only needed for the Red Hat course, not for my security path. I keep the
security-relevant parts: command, option and argument, `$` vs `#`, SSH keys
and `chmod 600`, and a changed SSH host key as a warning sign.

## Lessons for working as an analyst
- Order of response: **contain, investigate, report**.
- Use several evidence sources (logs, file checks, network tools) instead
  of trusting one.
- Only test systems I own or have written permission to test.
- If I find a flaw on a real site, stop and report it responsibly.
