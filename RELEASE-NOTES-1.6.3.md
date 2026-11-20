## TekVault PACS 1.6.3

Server and agent are released together; update both. The console offers the agent download to every user whose agent is older.

### Changes
- Jobs: tick rows and use Cancel selected; the bulk buttons cannot be pressed twice while they work.
- Query Remote: finds studies that are in the archive with images missing and fetches only the missing images; the status column shows what the archive actually holds, before and after a retrieve. A retrieve only counts as successful when the study is really in the archive afterwards.
- Disc writing: live progress from the drive (MB written, time left, buffer), clear step names, readable error messages, no sleep during a write; a failed disc is started again with a new blank.
- Agent: "Keep this PC awake always" option in the tray menu.
- Security: the DICOM allow-list starts as every address and is restored if emptied, so the server cannot be locked out.
- Sign in with Microsoft: the wizard completes the role assignment on every tenant.
- Full notes: https://tekprogs.com/docs/whats-new.html

### Files
| File | SHA-256 |
|---|---|
| TekVaultPACS-Setup-1.6.3.exe | (from publish\github-release\v1.6.3\SHA256SUMS.txt after the build) |
| DicomAgent-Setup-1.6.3.exe | (from publish\github-release\v1.6.3\SHA256SUMS.txt after the build) |

Runs on Windows Server 2016 or newer, or Windows 10 / 11 (64-bit). Windows SmartScreen may warn about a newly downloaded installer; choose *More info*, then *Run anyway*.

Download the installer files above. The "Source code" links that GitHub adds to every release contain documentation only; TekVault PACS is not an open-source project.
