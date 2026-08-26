# Linux Fundamentals — Condensed Notes

## Filesystem layout

Everything hangs off a single root `/` — no drive letters.

| Path | What lives there |
|---|---|
| `/etc` | System-wide config files (e.g. `/etc/passwd`, `/etc/ssh/sshd_config`) |
| `/var/log` | Log files — your first stop for forensics/incident response |
| `/home` | Per-user home directories (`/home/alice`) |
| `/bin`, `/usr/bin` | Executable binaries |
| `/tmp` | Scratch space, world-writable, often cleared on reboot |
| `/proc` | A virtual filesystem exposing running process/kernel info |

## Navigation

```bash
pwd          # print working directory
ls -la       # list files, including hidden (-a) with detail (-l)
cd /var/log  # change directory
cd ..        # up one level
cd ~         # back to home
```

## Reading and editing files

```bash
cat file.txt        # dump whole file to stdout
less file.txt        # page through it (q to quit, / to search)
nano file.txt         # simple editor
vim file.txt          # modal editor — steeper curve, worth learning i/Esc/:wq
tail -f /var/log/syslog   # follow a log file live — used constantly
```

## Permissions

```bash
chmod 755 script.sh     # rwx owner, r-x group, r-x other (see self-check)
chmod u+x script.sh      # add execute for owner only
chown alice:staff file  # change owner:group
```

Read the permission string from `ls -l`: `-rwxr-xr--` breaks into
owner/group/other triplets after the leading file-type character
(`-` regular file, `d` directory, `l` symlink).

## Processes

```bash
ps aux            # list all running processes
ps aux | grep nginx   # find a specific one
kill <PID>        # ask a process to terminate (SIGTERM)
kill -9 <PID>     # force-kill (SIGKILL) — last resort
top / htop        # live, interactive process viewer
```

## Basic networking from the shell

```bash
ping example.com        # basic reachability check
curl -v https://example.com   # make an HTTP(S) request, see headers/handshake
ss -tulpn                # what's listening on what port (see self-check Q2)
```

## Pipes and redirection

```bash
cmd1 | cmd2       # pipe: stdout of cmd1 becomes stdin of cmd2
cmd > file.txt     # redirect stdout, OVERWRITE file
cmd >> file.txt    # redirect stdout, APPEND to file
cmd 2> err.txt      # redirect stderr specifically
grep "ERROR" /var/log/syslog | wc -l   # count matching lines — very common pattern
```

## Do this, don't just read it

Work through the Cybrary Linux CLI Basics lab (see README) — actually type
every command instead of reading past it. If you have any Linux access
(WSL, a VM, a cheap cloud box), spend 30 minutes just poking around
`/etc` and `/var/log` with `ls`, `cat`, and `less`.
