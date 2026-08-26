# Self-Check — Answers & Explanations

Rule: if you can't answer in ~30 seconds without looking anything up, that's
a signal, not a failure. Go spend real time in the matching notes file +
labs before Week 1.

---

### 1. What's the difference between TCP port 80 and 443, and what protocol speaks on each?

- **Port 80** — plaintext **HTTP**. Anyone on the network path (ISP, coffee
  shop wifi, a compromised router) can read the request/response in transit.
- **Port 443** — **HTTPS**, which is HTTP wrapped in **TLS**. TLS adds
  encryption (confidentiality), integrity checking, and server authentication
  (via certificates) on top of the same underlying HTTP semantics.
- Both are just *conventions* — a server can technically listen on any port
  for any protocol — but 80/443 are the registered defaults browsers assume
  when you don't specify a port.

### 2. In Linux, how do you find which process is listening on a given port?

```bash
ss -tulpn | grep :443
# or, if not available / older systems:
sudo lsof -i :443
sudo netstat -tulpn | grep :443
```

`ss` is the modern replacement for `netstat`. `-t` = TCP, `-u` = UDP,
`-l` = listening sockets only, `-p` = show the owning process, `-n` = don't
resolve names (faster, avoids DNS lookups).

### 3. In Windows, how do you list scheduled tasks from PowerShell?

```powershell
Get-ScheduledTask
```

For more detail per task (last run time, actions, triggers):

```powershell
Get-ScheduledTask | Get-ScheduledTaskInfo
```

This matters for security work specifically because scheduled tasks are a
common **persistence mechanism** for malware — attackers create a task that
re-launches their payload on login/reboot.

### 4. What does a DNS resolver return for an A-record query, and how is that different from a CNAME?

- **A record** → an **IPv4 address** directly (e.g. `93.184.216.34`).
  (AAAA is the IPv6 equivalent.)
- **CNAME** → not an IP at all — it's an **alias pointing to another
  hostname**. The resolver then has to do a *second* lookup on that
  hostname (which eventually resolves to an A/AAAA record). CNAMEs can't
  coexist with other records on the same name, and you can't put a CNAME
  at a zone's root (apex) per the DNS spec.

### 5. What does `chmod 755` mean in plain English?

Three permission groups — **owner / group / other** — each represented by
one digit, where the digit is a bitmask of **read(4) + write(2) + execute(1)**:

| | Owner | Group | Other |
|---|---|---|---|
| Digit | 7 | 5 | 5 |
| Meaning | rwx (read, write, execute) | r-x (read, execute) | r-x (read, execute) |

So `755` = **owner can read/write/execute; everyone else can read and
execute but not modify.** This is the typical permission set for a script
or binary you want to be runnable by anyone but only editable by you.

---

## Scoring yourself

- **0–1 wrong:** you're ready. Skim the notes folders as a refresher.
- **2+ wrong:** don't skip the labs. Spend the full ~10 hours, weighted
  toward whichever folder(s) you struggled with.
