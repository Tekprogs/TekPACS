## TekVault PACS 1.6.2

Server and agent are released together; update both. The console offers the agent download to every user whose agent is older.

### Changes
- Retrieve queue: large retrievals from a remote PACS run one study at a time (adjustable under Settings, Bandwidth) so the server stays responsive while they arrive.
- Query Remote: status and actions per study, retrieve only studies not yet in the archive or overwrite existing ones, result limit up to no limit, paged results, sortable columns; an empty search lists every patient.
- Jobs: queued state with striped progress, selection with Cancel selected, Cancel all and Clear failed.
- Dashboard: live transfers and associations stay listed 90 seconds after finishing, recent tables fall back to the audit log, CPU and memory graphs, remote nodes in a table.
- Pause before an update: the installer and the Maintenance page let running transfers finish before the service restarts.
- Agent: update prompt in the console when a newer agent is available; redesigned disc writing window that fits small and large screens.
- Console: collapsible sidebar, all Studies columns sortable, consistent fonts and button sizes, time zone notice when the server clock is UTC.
- Exports: files named after the accession number, discs included.
- Sign in with Microsoft: the setup wizard now completes the Admin role assignment on every tenant.

### Files
| File | SHA-256 |
|---|---|
| TekVaultPACS-Setup-1.6.2.exe | `8a17e7512f25e436a60cbcfff3524c41307cc80e55349ede96288047cc1628e8` |
| DicomAgent-Setup-1.6.2.exe | `29dc3b0f8f3f9ed9597f54dcaf8a52b59e6eb2987389dffc6a781933bd296dbe` |
| DicomTestKit.zip | optional test tool, unchanged |

Runs on Windows Server 2016 or newer, or Windows 10 / 11 (64-bit). Windows SmartScreen may warn about a newly downloaded installer; choose *More info*, then *Run anyway*.
