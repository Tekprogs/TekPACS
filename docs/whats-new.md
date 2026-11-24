# What's new in 1.6

Server and agent are released together; both must be updated for the agent-related features.

## TekVault PACS 1.6.4

Update the server and the agent together; the console offers the agent download to every user whose agent is older. The database upgrades itself on the first start.

### Viewer

- The console viewer and the viewer written to every disc and USB export are now **one and the same**: the disc carries the stored pixel values instead of pictures, so window/level, presets and Hounsfield values are real on the disc too.
- Layouts from 1 × 1 to 2 × 3 with linked scrolling by slice position, linked window and zoom, cross-reference lines between viewports and R L A P H F orientation markers.
- Window presets (soft tissue, lung, bone, brain, liver, abdomen, mediastinum, stroke), typed window values, Auto, and **W/L from ROI**.
- Length, angle and Cobb angle with calibration; rectangle, ellipse and freehand ROI with mean, deviation, minimum, maximum and area; pixel probe; text and arrow labels; drawings can be selected, moved and deleted, and exported as CSV.
- **MPR**: axial, coronal and sagittal planes with a crosshair, slab MIP / MinIP / average, and a rotating 3D projection with a threshold. **Fuse** overlays another series in colour (PET on CT), **Highlight** colours a value range.
- Tag inspector with filter, export of the view as PNG or JPEG, print, and download of the original DICOM file. Cine uses the frame rate stored in the file.

### Patients who share a Patient ID

- A Patient ID is only unique on the system that issued it. A study that arrives under an ID already used here by a different person is now filed as a **separate patient** with the same ID instead of being merged into the first one. Under Settings, go to **Data matching** to choose what must agree for two studies to belong to the same patient: by default the ID, the name, the birth date and the source system (the AE title the images came from).
- Every such clash is listed under Jobs, **Mitigation**, where an administrator decides: the same person (merge), different people (keep apart), or give one of them a new Patient ID (the images are rewritten with the change record).
- Under Settings, go to Maintenance, and look for **Data validation**: it reads the first image of every study and compares it with the index, lists studies filed under the wrong person for Mitigation, corrects study details that drifted, and counts missing files. Archives from earlier versions should run it once.
- Delete patient and Edit patient details act on one person only, never on somebody else who shares the ID.

### Disc writing

- Before writing, the agent checks the disc. A used, failed or wrong disc is ejected and a window asks for a blank of the right kind for the data ("a blank DVD-R or DVD+R (4.7 GB)"); Start becomes available when one is detected, Cancel ends the export without writing.
- The Export page shows for each drive whether it writes dual-layer or Blu-ray discs, and only suggests disc types that drive can write.

### Query Remote and Studies

- View opens the local copy of a study even when it is filed under another patient name here, and the Status column says under which name and ID it is filed when that differs from the remote system.
- Studies: the series toggle sits in the Actions column, patients are separated by a clear gap, and the selection and delete buttons have their own line.

## TekVault PACS 1.6.3

1.6.3 follows 1.6.2 closely. Update the server and the agent together; the console offers the agent download to every user whose agent is older.

### Query Remote

- The archive is compared image by image with what the remote system reports. A study that is here but short of images shows **Missing x of y** and gets a **Get missing** button that fetches only the missing images. Tick **only studies with missing images** to list them together with the studies not here at all, and use **Select all with missing images** to retrieve them in one go.
- The Status column shows what the archive holds, re-read from the index when a retrieve finishes, rather than the retrieve's own report. A retrieve only counts as successful when the study is really in the archive afterwards; a remote system that accepts the request and sends nothing is reported as a failure with the likely cause.

### Jobs

- Every jobs table has a checkbox column. The header box selects all rows shown in the current tab; **Cancel selected** stops the selected running or queued jobs and removes the selected finished ones. Cancel all and Clear failed remain for the one-click cases.
- While one of those actions runs, the buttons are disabled and read "Working" so it cannot be started twice; a short notice says what was done.

### Writing discs with the agent

- Progress comes from the drive itself: MB written of the total, percentage, time left, write speed and buffer fill, with each step named (checking the disc, calibrating, writing, closing the disc, verifying, finishing). Closing a dual-layer disc is announced because it takes minutes on its own.
- Buffer-underrun protection is switched on and the agent runs at higher priority while writing. A disc being written keeps the PC awake.
- Errors are explained in plain words (I/O error on the disc, buffer ran empty, drive not ready, and so on) with what to do. A failed disc is not retried: insert a new blank and start the export again.
- The progress window is narrower and wraps its text.

### Agent

- **Keep this PC awake always** in the tray menu holds off sleep the whole time the agent runs, for a PC that must stay reachable for exports and backups. The display can still turn off.

### Security and setup

- The DICOM allow-list starts with 0.0.0.0/0 and ::/0 (every address). Replace them with your networks to restrict access; if every entry is removed the allow-all entries are put back, so the server cannot be locked out by accident.
- The Sign in with Microsoft wizard completes the Admin role assignment on every tenant (one Microsoft Graph lookup was refused on some tenants and stopped the wizard at its last step).
- The sidebar menu text is slightly larger. The support card shows the company contact only.

## TekVault PACS 1.6.2

1.6.2 is a maintenance release on top of 1.6.1. Update the server and the agent together; the console offers the agent download to every user whose agent is older.

### Retrieving from a remote PACS

- Retrievals are queued and run one study at a time by default, so a retrieval of hundreds of studies no longer slows down receiving, sending and the console. Under Settings, go to Bandwidth, and look for **Retrieves at the same time** to allow more in parallel.
- Query Remote shows a **Status** and **Actions** column per study (View, Retrieve, Retry, Re-retrieve). Tick **Only studies not in the archive** to skip what you already have, or **Overwrite** to replace it.
- Choose how many results to fetch (500, 2,000, 10,000 or no limit). Results are shown 100 per page; Select all and Retrieve selected act on every result, not only the page shown.
- Every column can be sorted. Searching with nothing entered lists every patient (a wildcard is placed in the name box; type a name to replace it).

### Jobs and dashboard

- Jobs waiting for a slot show as **Queued** with a striped bar. **Cancel all** and **Clear failed** act on the whole list.
- Live transfers and Active associations stay on the dashboard for 90 seconds after they finish, with their outcome. When nothing is live the Recent tables show the last 8 from the audit log.
- Administrators see CPU and memory graphs. Remote nodes are laid out in a table that grows sideways.

### Updating without losing transfers

- The installer offers to **pause** the running server first: new incoming associations are told to retry later, running transfers and jobs finish, then the service is replaced. Under Settings, go to Maintenance, and look for **Before an update** to do the same by hand, resume, or restart the service.

### Console and agent

- The sidebar can be collapsed with the button at its top. All Studies columns sort. Fonts and button sizes are consistent across pages; the date picker matches the dark theme.
- When the server clock is UTC and no display time zone is chosen, the dashboard says so. Under Settings, go to Web, and look for Time zone.
- Users whose TekVault Agent is older than the server are offered the download in the console.
- The disc writing window of the agent has been redesigned, with a spinning disc, striped progress and sizes that suit small and large screens.
- Exports name each file after the accession number (`DICOM\ACC123\ACC123_<image>.dcm`), on discs as well as USB, folder and ZIP exports.

## TekVault PACS 1.6.1

1.6.1 is the first public release of the 1.6 line (1.6.0 was an internal build) and includes everything from the internal 1.5.0 build (.NET 10, security updates, time zone, the console refresh) plus the new features below. Both installers now carry the .NET 10 runtime installers inside them, so an offline Windows 10 / 11 PC or server needs no download.

### Fix patient details

- Studies, then patient row, then ⋯, then **Edit patient details**: correct the family / given / middle name, patient ID, birth date and sex of a patient that a modality got wrong.
- The correction is written into the index **and into every stored image** of the patient, so sends, exports, backups and C-FIND all return the corrected values. The original values are preserved inside each file (DICOM Original Attributes Sequence, reason CORRECT) and the change - who, when, old and new - goes to the Audit Log.
- Changing the ID to one that already exists merges the studies into that patient. With the by-patient storage layout the files move to the renamed folder.

### CD / DVD with a built-in viewer

- Export, then **CD / DVD**: the disc writer in *your* PC is listed (through the TekVault Agent 1.6), with the disc that is in it and its free space. The export is built on the server, sent to the PC and written there; the job on the Export page follows the burn and the agent shows a notification when the disc is done (ejected by default).
- Every disc - and, by default, every USB, folder and ZIP export - now carries the **built-in viewer**: open `OPEN_VIEWER.html` on the disc in any web browser (Windows, Mac, Linux, tablet) and browse patients, then studies, then series, scroll through images, zoom, pan, brightness/contrast, invert, rotate, cine and print. There is nothing to install, and the full DICOM files and the DICOMDIR are still on the disc for radiology viewers.
- CD-R/RW, DVD±R/RW, dual layer and Blu-ray are supported; a disc with data already on it gets a new session. Settings, Export: switch the built-in viewer off for USB/ZIP, choose whether to eject.

### Storage layouts

- Under Settings, go to Storage, and look for **Folder layout**: keep the default hashed layout (`{hh}\{StudyUID}\…`, best for very large archives) or store images **by patient name** (`LASTNAME, FIRSTNAME (12345)\20261111_{StudyUID}\…`), **by last name, then first name** (`LASTNAME\FIRSTNAME (12345)\20261111_{StudyUID}\…`) or **by date, then patient** (`2026\2026-11-11\LASTNAME, FIRSTNAME (12345)\{StudyUID}\…`) so the storage share is browsable in Explorer.
- The layout applies to new images; existing files stay where they are (each remembers its own path). **Under Settings, go to Maintenance, and look for Reorganise files** moves the archive into the chosen layout, with a dry run first. Backups and restores work with every layout.

### Query Remote

- New **Query Remote** page (left menu, above Studies): pick a remote PACS, modality or archive and search it with the same filters as the Studies page (C-FIND at study level, series on demand). Studies already in the archive are marked as such.
- **Retrieve** pulls a study into TekVault PACS - per node by C-MOVE (the remote sends to our AE title) or C-GET (images return on the query connection) - as a tracked job with progress; retrieved images are stored, indexed and routed like received ones and everything is audited.

### Sign in with Microsoft - set up from the console

- Under Settings, go to Web & login, and look for O365 / Azure AD Settings, then **Set up Sign in with Microsoft**: a Global Administrator enters a device code once and TekVault PACS creates its own Entra app registration (redirect URI, Admin / User app roles, groups claim, admin consent, 2-year secret), assigns the administrator the Admin role and fills in the settings. There is no portal work and nothing to copy by hand.
- The Dashboard's PACS server card shows the **Microsoft 365 sign-in** connection status (Microsoft reachable, tenant valid, client ID and secret accepted - checked every 5 minutes, "check now" link), and warns 30 days before the client secret expires. When the connection is down the login page marks the Microsoft button as unavailable and, if it is clicked or a Microsoft sign-in fails, shows a pop-up with the reason and the other ways to sign in.

### Installers

- TekVaultPACS-Setup and DicomAgent-Setup bundle the .NET 10 runtime installers (runtime, ASP.NET Core, Desktop). When a runtime is missing the setup asks and installs it from the bundle - no internet needed; the download path remains as a fallback. The build scripts fetch the Microsoft installers once into `installer\redist`.

### From the 1.5.0 build

- **Platform:** moved to .NET 10 (LTS). The installer checks for the .NET 10 and ASP.NET Core 10 runtimes.
- **Security:** patched vulnerabilities found in previous versions. Updating is recommended for every installation.
- **Blocked and allowed addresses:** Settings, Security now has Blocked and Allowed tabs. Addresses that keep failing are blocked automatically and an administrator can block, unblock or allow addresses by hand. The server's own networks and the paired agents' networks are allowed automatically.
- **Roles:** users (non-administrators) see Studies, Viewer, Send To Node, Export and their own agents only. Everything else is for administrators.
- **Help:** guides in the console and on this site are written as short numbered points instead of long paragraphs.
- **Console:** time zone setting (cloud servers run on UTC - pick the practice's zone and every time in the console, schedules and send windows follow it); settings cards split into tabs (Backups, Storage, Web & login); one size for every field and button, a colour per action (Save green, Edit/Browse orange, Delete red, Add blue, Refresh purple, Download teal), icons on every button and menu item, orange tabs; Studies with patient and image-stack icons, click a name to expand; the selected-studies list on Export / Send as a scrolling table; a "Back to Studies" button in the viewer; user / group Browse and Validate pickers for the permission lists.
- **Jobs:** "Completed w/ exceptions" state for jobs that skipped items (duplicates, non-DICOM files), with **Confirm OK** / **Mark failed** review buttons; the decision is recorded with the job.
- **Import:** accepts DICOM files without the 128-byte preamble (Agfa NX media exports); inbox options for subfolders; after handling, inbox files can be **moved to \_imported / \_skipped / \_failed** folders (the new default for fresh installs), deleted, or left in place.
- **Remote nodes:** enable / disable a node with one click (kept but ignored while disabled); send-only nodes; association diagnostics in the log on every reject or abort.
- **Routing:** modality tick boxes, destinations one per row, confirmed "Stop", required fields highlighted.
- **Agent:** update from the tray menu; desktop shortcut to the PACS console; Settings, Agents as four steps with a Download button.
- **Backups:** "Locations" tab, live last-run column, Run-now guard; dashboard "PACS server" card; Memory page graph.

## TekVault PACS 1.4.0

### Browser image viewer

- **View** on any study row opens the images in a new tab - no viewer software to install on the PC.
- Series column with thumbnails; mouse wheel, arrow keys or a slider step through the stack; left drag for window/level, right drag or Ctrl+wheel to zoom, middle drag to pan; double-click to fit.
- CT presets (lung, bone, soft tissue, brain, liver, abdomen), invert, rotate, flip, Fit and 1:1, cine playback for multi-frame images and series, and a distance measurement that uses the image's pixel spacing. Press <span class="kbd">?</span> in the viewer for the key list.
- Compressed transfers (JPEG lossless/baseline, JPEG-LS, JPEG 2000, RLE) are decoded on the server, so every modality's images display; grey-scale (signed/unsigned, MONOCHROME1/2) and colour (RGB, YBR) are supported. Reports, PDFs, presentation states and raw data are skipped with a note.
- Every study opened in the viewer is written to the Audit Log (Web, then View).

### Automatic routing

- New **Under Settings, go to Routing**: rules that forward received studies to other nodes by modality, sending AE title, sending IP (wildcards or CIDR), station name, institution, study description or SOP class. Conditions AND together; comma-separated alternatives OR; empty = any.
- A study is forwarded once it has settled (no new images for N minutes, default 2) so it arrives complete at the destination; later additions are forwarded without repeating what was already sent. Studies are never sent back to their sender.
- Routed sends use each destination's queue rules and show under Jobs as "routing: rule"; the Routing page lists studies waiting to settle (with Route now) and the recent decisions; the Audit Log records every forward.

### Remote nodes

- **Send-only** flag for modalities that push images but reject associations from a PACS (e.g. Agfa NX): the health check only tests that the port answers, so the node shows green when the device is up.
- The node check explains a TLS mismatch ("untick TLS for this node") and a dropped association (send-only modality, or our AE title not allowed) in plain words instead of the raw socket error.

## TekVault PACS 1.3.0

### Studies & search

- Every study now records **institution**, **station name** (location), **source AE / server**, the **importing user** and a **status** line that follows the study: Received, Imported, Sent to X, Partly sent, Exported to USB on Y, Downloaded (ZIP), Restored.
- Studies page: *More fields* searches Study ID, sex, birth date, referring physician, institution, station, source, status and importer (wildcards allowed); *all columns* shows them in the table.
- C-FIND matches Study ID, sex, birth date, referring physician and institution and returns Institution, Station Name, Instance Availability and Retrieve AE Title, so worklist-style viewers fill their columns.
- Under Settings, go to Maintenance, and look for *Refresh study metadata* back-fills studies indexed by earlier versions.

### Sending: jobs per study, queues per node

- Send To Node creates **one job per study**, each with its own progress, retry and status.
- Each remote node has **queue rules** (Remote nodes, then Queue): studies sent at the same time, *Hold the queue*, a daily *send window* (e.g. overnight to a reading site) and *keep pending while unreachable*.
- Queued jobs show why they are waiting; **Send now** overrides the rules for one job. Retries and restarts use the same queue; the dashboard shows how many jobs are waiting.

### Agent & backups

- Agent transfers are several times faster over WAN links: binary protocol and several 1 MB chunks in flight; the agent accepts chunks in any order.
- Backups to a workstation no longer stall after a connection drop (the agent abandons stale sessions; usage measurement is a cheap count instead of a file list).
- Agent: *Keep this PC awake during transfers* toggle; rolling speed and 1-minute average in the Activity window.
- Backup targets run independently; the console stays responsive during large imports (private SQLite cache, cached dashboard counters); action buttons cannot be double-clicked.

### Updates

- Opt-in daily check of tekprogs.com (installer option; Settings, Maintenance, Updates): a dashboard banner when a newer release exists, and an *update* badge on outdated workstation agents. Nothing is installed automatically.

## TekVault PACS 1.2.1

- **Update notices**: the server checks tekprogs.com once a day (installer option; Settings, Maintenance, Updates) and shows a dashboard banner when a newer release exists; outdated workstation agents are flagged on the Agents page under Settings. Nothing is installed automatically.
- Agent transfers are several times faster over WAN links (binary protocol, several chunks in flight); backups to a workstation no longer stall after a connection drop; keep-awake toggle on the agent; rolling speed in the Activity window.
- Backup targets run independently; the console stays responsive during large imports; action buttons cannot be double-clicked.

## TekVault PACS 1.2.0

### Backups

- New target type: **USB drive or folder on a paired computer**, written through the TekVault Agent with a minimum-free-space stop and start/complete notifications on the workstation.
- **Per-target schedules**: default, custom (time, days of the week, incremental interval) or manual only. Targets are managed in a table with Edit / Run now / Delete; the editor is a popup.
- **Resilient runs**: connection drops pause the run and retry with growing delays for up to *Keep trying for* minutes instead of failing.
- Backup jobs show real progress (files done / total); the installers and a `HOW-TO-RESTORE.txt` are placed on every target.

### Storage & sending

- *Low-disk warning* and the hard stop *Minimum free space* are separate settings. A server that refuses images shows a red banner on the dashboard; senders are told *Storage full* and show it under the progress bar.
- Multiple storage locations with fill order and per-location minimum free space; dashboard shows one row per location.
- Separate limits for incoming and outgoing associations; one-minute average speeds alongside current speed everywhere.

### Bandwidth & memory

- Daily limit window moved next to the limits, with time pickers and *Monday to Friday only*; per-workstation agent limits (default on the Bandwidth page, override per computer).
- *Reserved memory* (hard minimum working set) and *Process priority* on the Memory page under Settings.

### Certificates & installer

- **Trust-TekVaultPACS.cmd** on the login page installs the certificate for the whole PC and removes stale copies; `cert prune`; self-signed certificates include the server's IP addresses; the login page flags a name mismatch.
- The installer shows live status during the configure step and no longer walks the whole archive to set permissions on upgrades. Start Menu shortcuts are renamed with badge icons.

### Console

- Step-by-step guides with screenshots under Help & support (this documentation); display scale control; job numbers and detail popups; duplicate-accession flagging in Studies; in-app confirmation dialogs.

## TekVault Agent 1.2.0

- **One-click pairing**: press *Pair this computer* in the web console; the browser hands a `tekvault://` link to the agent, which pairs itself.
- **Activity window** (double-click the tray icon): transfers in progress with direction, folder, files, size and speed, plus recent history.
- Backup target support; new TekVault cube tray icon with status dot; Windows notifications titled *TekVault Agent*; Start Menu shortcuts renamed with badge icons; the installer closes a running agent before updating.
