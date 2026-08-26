# Windows & Active Directory Fundamentals — Condensed Notes

## Users, groups, and NTFS permissions

- Every user/group has a unique **SID** (Security Identifier) under the
  hood, not just a name — names can change, SIDs don't.
- Groups are the normal way permissions get assigned (assign to group,
  add users to group) rather than one-by-one per user.
- **NTFS permissions** (on files/folders) are separate from **share
  permissions** (on a network share) — when both apply, the *more
  restrictive* of the two wins.
- Common NTFS permission levels: Full Control, Modify, Read & Execute,
  Read, Write. View/edit via file Properties → Security tab, or
  `icacls` from the command line.

## The Registry

- A hierarchical database of settings, replacing what would be config
  files on Linux. Key root hives:
  - `HKEY_LOCAL_MACHINE` (`HKLM`) — machine-wide settings, requires admin
    to edit
  - `HKEY_CURRENT_USER` (`HKCU`) — settings for the logged-in user
  - `HKEY_USERS`, `HKEY_CLASSES_ROOT`, `HKEY_CURRENT_CONFIG` — less
    commonly touched day to day
- Security-relevant example: a lot of persistence malware lives in
  `HKLM\...\Run` or `HKCU\...\Run` — programs listed there launch
  automatically at login.
- Browse with `regedit` (GUI) or query from PowerShell:
  ```powershell
  Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run"
  ```

## Services, scheduled tasks, and Task Manager

- **Services** are background processes managed by the OS (start on
  boot, run without a logged-in user). View/manage via `services.msc`
  or PowerShell:
  ```powershell
  Get-Service | Where-Object {$_.Status -eq "Running"}
  ```
- **Scheduled Tasks** run programs on a trigger (time, logon, event).
  ```powershell
  Get-ScheduledTask
  Get-ScheduledTask | Get-ScheduledTaskInfo   # last run time, etc.
  ```
  Security relevance: alongside registry Run keys, this is one of the
  most common **persistence** mechanisms attackers use.
- **Task Manager** (`taskmgr` or Ctrl+Shift+Esc) — quick GUI view of
  running processes, resource usage, startup programs, and users.

## PowerShell basics

- Cmdlets follow a consistent **Verb-Noun** pattern: `Get-Process`,
  `Get-Service`, `Get-ScheduledTask`, `Get-EventLog` / `Get-WinEvent`.
- The **pipeline** passes structured *objects* (not just text, unlike
  Linux pipes) from one cmdlet to the next:
  ```powershell
  Get-Process | Where-Object {$_.CPU -gt 100} | Sort-Object CPU -Descending
  ```
- Read-only competence is the bar for this course — you should be
  comfortable running `Get-*` cmdlets and filtering/sorting output, not
  necessarily writing scripts from scratch yet.
- A few you'll see constantly in security contexts:
  ```powershell
  Get-Process
  Get-Service
  Get-LocalUser
  Get-LocalGroupMember Administrators
  Get-WinEvent -LogName Security -MaxEvents 20
  ```

## Do this, don't just read it

Spin up (or borrow) a Windows VM and actually run the `Get-*` commands
above. Open `services.msc` and Task Scheduler and click around. Open
`regedit` and navigate to the `Run` key just to see it's real. Microsoft
Learn's free docs cover all of this if TryHackMe rooms are gated.
