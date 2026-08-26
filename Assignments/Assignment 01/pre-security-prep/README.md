# pre-security-prep

Prep repo for the "3 areas of assumed fluency" before Week 1: **Networking**,
**Linux**, and **Windows/Active Directory**. Budget ~10 hours total, spread
over 1–2 weeks — not crammed the night before.

## Structure

```
pre-security-prep/
├── README.md                  <- you are here
├── self-check-answers.md      <- the 5 gate questions, answered + explained
├── networking/notes.md        <- IP/ports, DNS, HTTP/HTTPS, LAN/NAT/routing
├── linux/notes.md             <- filesystem, files, perms, processes, pipes
└── windows-ad/notes.md        <- users/groups/NTFS, registry, services, PowerShell
```

## How to use this

1. Read `self-check-answers.md` FIRST, cold, without looking at your notes.
   Time yourself — 30 seconds per question. Whatever you miss tells you
   which folder to actually spend time in.
2. For each weak area, go to that folder's `notes.md`. Each file is a
   condensed reference, not a replacement for the hands-on labs below —
   it's there so you have something to check your work against while
   you're in the labs.
3. Do the labs. Reading is not doing. The muscle memory is the point.

## Required labs (free)

| Topic | Link |
|---|---|
| Linux CLI basics | https://app.cybrary.it/browse/virtual-lab/linux-cli-basics |
| HTTP in Detail | https://tryhackme.com/room/httpindetail |
| Web Application Basics | https://tryhackme.com/room/webapplicationbasics |
| DNS in Detail | https://tryhackme.com/room/dnsindetail |
| Intro to LAN | https://tryhackme.com/room/introtolan |
| Networking Basics (YouTube) | https://www.youtube.com/watch?v=3QhU9jd03a0 |

**If a TryHackMe room is gated behind premium when you get to it:** report it
to the instructional team, then fall back to Microsoft Learn (Windows),
Linux Foundation free intro courses (Linux), or Cloudflare Learning Center
(web/networking) for that topic.

## Common mistakes to avoid

- **Watching instead of doing.** Skimming the reading and skipping lab
  tasks means the muscle memory won't be there in Week 4 (web app security)
  or Week 6 (endpoint forensics).
- **"I'm a developer, I've got this."** Devs are often weaker on the OS/
  networking side than they think. Actually run the self-check — don't
  assume.
- **Cramming the night before.** These topics compound on each other.
  Spread it out.

## Suggested time split (~10 hours)

- Networking: ~4 hrs (DNS, HTTP, LAN room + video)
- Linux: ~3 hrs (Cybrary lab + practicing on any Linux box/VM/WSL you have)
- Windows/AD: ~3 hrs (Microsoft Learn reading + poking around a VM's
  Task Scheduler, Services, Registry, and PowerShell `Get-*` cmdlets)
