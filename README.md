# TekVault PACS

A self-hosted DICOM server and archive for Windows. Receives from any modality, stores securely, backs itself up, and lets staff search, view, export and send studies from a browser. One installer, one Windows service, one browser console. Nothing to license per modality or per seat.

**[Download the latest release](../../releases/latest)** (also available from [tekprogs.com/downloads](https://tekprogs.com/downloads.html)) · [Documentation](docs/index.md) · [Website](https://tekprogs.com) · [Support](https://tekprogs.com/support.html)

> This repository holds the installers and the documentation. The source code is not published here.

## Downloads

| Package | What it is | Runs on |
|---|---|---|
| `TekVaultPACS-Setup-x.y.z.exe` | The server: Windows service, web console, setup wizard. Run as administrator. The .NET 10 runtimes are inside the installer. | Windows Server 2016, 2019, 2022, 2025, or Windows 10 / 11 (64-bit) |
| `DicomAgent-Setup-x.y.z.exe` | TekVault Agent: tray application for exporting to USB drives and discs and importing from CD/USB on a user's own PC. Per-user install, no admin rights. | Windows 10 / 11 (64-bit); also works on Windows Server 2016 or newer |
| `DicomTestKit.zip` | Test-data generator and C-STORE/C-FIND/C-MOVE load tool with GUI and PowerShell support. For testing and demos. | Windows 10 / 11 or Windows Server 2016 or newer (64-bit) |

All files are on the **[Releases](../../releases)** page. Each release lists the SHA-256 of every file.

Windows SmartScreen may warn about a newly downloaded installer; choose *More info*, then *Run anyway*.

## Installing

1. Run `TekVaultPACS-Setup-x.y.z.exe` on the server as administrator.
2. The wizard asks for everything on its pages: AE title, DICOM / HTTP / HTTPS ports (busy ports are detected), data and image folders, and sign-in (a local admin account or your domain groups).
3. It registers the service, creates a self-signed certificate, opens the firewall and starts the service, then checks the ports and TLS handshake and reports the result.
4. Open the console from the desktop shortcut and sign in. On each PC run `Trust-TekVaultPACS.cmd` from the login page to stop the certificate warning. Add your modalities under Settings, Remote nodes.
5. Later releases: run the newer installer over the top. It offers to keep your configuration and to let running transfers finish first; the archive is untouched. Update the TekVault Agent on workstations at the same time.

Full walkthrough: [Getting started](docs/getting-started.md).

## What it does

**Receiving**
- C-STORE from any modality or PACS, with TLS. Every storage class, every transfer syntax, lossless or lossy.
- Accept only known AE titles, allow and deny IP ranges.
- Automatic routing to other nodes by modality, sender, station or institution.
- Inbox folder: drop files in and they are imported.

**Query and retrieve**
- C-FIND and C-MOVE for other systems querying this server.
- Query Remote: search another PACS and pull studies in with C-MOVE or C-GET, queued and paced so the server stays responsive.

**Finding and viewing**
- Search by patient, ID, accession, modality, date and every other study field. Sort by any column.
- Built-in browser viewer: window and level, zoom, pan, scroll, cine, measure, presets.
- Edit patient details with a full change record in the images.

**Export and send**
- Send to any node with retries, send windows and bandwidth limits.
- Export as ZIP, to a folder, to a USB drive, or burn a CD or DVD. Every disc and USB carries a viewer that opens in any browser.

**Storage, backup and operations**
- Several storage locations, folder layouts, quotas and minimum free space.
- Scheduled backups to local and UNC paths, S3-compatible storage, Azure Blob, or a paired PC's USB drive. Restore a study, a patient or everything.
- Dashboard, Jobs page, bandwidth and memory limits, full audit trail. Runs with no internet access.

**Security**
- Sign in with Windows domain, LDAP, local accounts or Microsoft Entra ID. Administrator and User roles.
- HTTPS with your own or a self-signed certificate, TLS for DICOM. Blocked and allowed address lists.

## Documentation

The guides in [`docs/`](docs/index.md) are the same ones built into the console under *Help & support*: everyday use (viewing, exporting, Query Remote, sending, importing, the agent), setting up (receiving, routing, sign-in, certificates, storage), keeping it healthy (backups, jobs, health, emergency administrator), troubleshooting and disaster recovery.

## Support and security

- Questions, installation help or a feature you need: [tekprogs.com/support](https://tekprogs.com/support.html), or open an issue here.
- Security issues: please do **not** open a public issue. Send them through the support page and they will be handled privately.

## Licence

TekVault PACS is proprietary software, free to download and use under the terms in [LICENSE.md](LICENSE.md). The source code is not open.
