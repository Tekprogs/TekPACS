## TekVault PACS 1.6.4

Server and agent are released together; update both. The console offers the agent download to every user whose agent is older.

### Changes
- Patients who share a Patient ID are kept apart and listed under Jobs, Mitigation for a decision (same person, different people, or a new ID for one of them). Settings, Data matching sets what must agree: ID, name, birth date and source system by default. Settings, Maintenance, Data validation checks the archive against the images.
- Disc writing asks for a blank disc of the right kind and ejects a used one; the Export page shows whether each drive writes dual layer.
- Query Remote: View opens the local copy even when it is filed under another patient name here, and says which one.
- Studies: series toggle in the Actions column, a clear gap between patients, selection and delete buttons on their own line.
- Full notes: https://tekprogs.com/docs/whats-new.html

### Files
| File | SHA-256 |
|---|---|
| TekVaultPACS-Setup-1.6.4.exe | (from publish\github-release\v1.6.4\SHA256SUMS.txt after the build) |
| DicomAgent-Setup-1.6.4.exe | (from publish\github-release\v1.6.4\SHA256SUMS.txt after the build) |

Runs on Windows Server 2016 or newer, or Windows 10 / 11 (64-bit). Windows SmartScreen may warn about a newly downloaded installer; choose *More info*, then *Run anyway*.

Download the installer files above. The "Source code" links that GitHub adds to every release contain documentation only; TekVault PACS is not an open-source project.
