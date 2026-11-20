## TekVault PACS 1.6.4

Server and agent are released together; update both. The console offers the agent download to every user whose agent is older.

### Changes
- Patients who share a Patient ID are kept apart and listed under Jobs, Mitigation for a decision; Settings, Data matching sets what must agree (ID, name, birth date and source system by default); Maintenance, Data validation checks the archive against the images.
- Disc writing asks for a blank disc of the right kind and ejects a used one; drives show whether they write dual layer.
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
| TekVaultPACS-Setup-1.6.4.exe | (from publish\github-release\v1.6.4\SHA256SUMS.txt after the build) |
| DicomAgent-Setup-1.6.4.exe | (from publish\github-release\v1.6.4\SHA256SUMS.txt after the build) |

Runs on Windows Server 2016 or newer, or Windows 10 / 11 (64-bit). Windows SmartScreen may warn about a newly downloaded installer; choose *More info*, then *Run anyway*.

Download the installer files above. The "Source code" links that GitHub adds to every release contain documentation only; TekVault PACS is not an open-source project.
