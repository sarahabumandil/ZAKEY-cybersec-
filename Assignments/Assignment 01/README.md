## (optional) Prerequisites 

This course assumes you walk in with working fluency in three areas. If you don't have all three, spend ~10 hours preparing using the resources below before Week 1. We will not re-teach these topics in lecture.What you need to know
Networking fundamentals. How traffic moves between machines.

• IP addresses and ports — how machines identify themselves and listen for connections
• DNS — how domain names become IPs (A records, CNAME, resolvers)
• HTTP/HTTPS — request structure (methods, headers, status codes), and what TLS adds on top
• LAN vs. public internet, NAT, and basic routing concepts
• How web applications work

Linux fundamentals. Comfort at the command line.

• Filesystem layout (/etc, /var/log, /home), navigation (cd, ls, pwd)
• Reading and editing files (cat, less, nano or vim)
• Permissions (chmod, chown), processes (ps, kill), basic networking (ping, curl, ss)
• Pipes and redirection (|, >, >>)

Windows and Active Directory fundamentals. Working knowledge of the OS most enterprises run.

• Users, groups, and NTFS permissions
• The Registry and where common settings live
• Services, scheduled tasks, and Task Manager
• PowerShell basics (Get-* cmdlets, the pipeline) — read-only competence is fine

Self-check
If you can answer each of these in under 30 seconds without looking anything up, you're ready:


• What's the difference between TCP port 80 and 443, and what protocol speaks on each?
• In Linux, how do you find which process is listening on a given port?
• In Windows, how do you list scheduled tasks from PowerShell?
• What does a DNS resolver return for an A-record query, and how is that different from a CNAME?
• What does chmod 755 mean in plain English?



If two or more give you trouble, prep before Week 1.

How to prepare (free)
The TryHackMe, Cybrary, and YouTube covers everything you need. We will keep this browser-based, hands-on, and structured.
Required for this course:

• https://app.cybrary.it/browse/virtual-lab/linux-cli-basics
• https://tryhackme.com/room/httpindetail
• https://tryhackme.com/room/webapplicationbasics
• https://tryhackme.com/room/dnsindetail
• https://tryhackme.com/room/introtolan
• https://www.youtube.com/watch?v=3QhU9jd03a0 (Networking basics)

Heads-up on premium TryHackMe rooms
TryHackMe periodically moves previously-free rooms behind a paid subscription. We will need to keep an eye on this. Please report to instructional team if a room becomes premium/paid only.
If any other room is gated when you reach it, the topic is well covered by free Microsoft Learn docs (Windows), the Linux Foundation's free intro courses (Linux), and Cloudflare's learning center (web/networking).
Common mistakes

• Watching, not doing. Pre-Security is hands-on for a reason. If you skim the reading and skip the lab tasks, the muscle memory won't transfer to Week 4 (web app security) or Week 6 (endpoint forensics).
• Assuming "I'm a developer" covers it. Developers often have weaker fundamentals on the OS and networking side than they think. Run the self-check.
• Cramming the night before. These topics compound. Spread the prep over 1–2 weeks.
