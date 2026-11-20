# Troubleshooting

Most problems announce themselves in the console. Here is where to look and what it means.

## Browser still says "Not secure" after installing the certificate

- **Chain contains an old certificate.** If the server's store holds several self-signed certificates with the same name (re-created over time), Windows attaches a stale one to the TLS chain and the browser judges that one. Run `DicomServer.Setup cert prune` on the server, restart the service, then re-run *Trust-TekVaultPACS.cmd* on the PC. It also removes stale copies from the PC's store.
- **Name mismatch.** The address bar must use a name the certificate covers. The login page flags it and lists the valid names. Browsing by IP needs a certificate that includes it: `DicomServer.Setup cert new SERVER,192.168.1.10`. New self-signed certificates include the server's IPv4 addresses automatically.
- **Wrong store.** It must be under *Trusted Root Certification Authorities*, not *Personal*. Choose *Local Machine* so every user benefits.
- **Browser not fully restarted.** Edge and Chrome keep running in the background. Close them from the tray or sign out and in.
- **Firefox** ignores the Windows store unless `security.enterprise_roots.enabled` is true in `about:config`.

## Senders report "out of resources" / the dashboard says images are refused

1.  Free space on the primary storage dropped below *Minimum free space* (Settings, Storage. Default 1 GB) and no additional location has room.
2.  The server answers every C-STORE with *Storage full*; TekVault senders show that under the progress bar and keep retrying. The Audit Log lists each rejected image.
3.  Free space, add a storage location, or lower the minimum.
4.  The *Low-disk warning* (default 10 GB) is only a warning.

## A send shows "waiting" with retries

1.  The destination answered busy / out of storage, rejected the association for congestion, or dropped the connection.
2.  The reason is shown under the bar (the destination's own words when it gives any).
3.  Retries back off up to the limits in *Under Settings, go to Bandwidth & Sending*. When they run out the job fails with the last error, and *Retry* re-sends only the undelivered images.

## Backup shows "connection lost – retrying"

1.  Normal during an internet or share outage, or while a workstation with the backup drive is asleep: the run pauses and retries with growing delays for up to *Keep trying for* minutes (Settings, Backups, default 120).
2.  If it still fails, the automatic job retry re-runs it later from where it stopped.

## The agent will not pair or shows offline

- Agent version must match the server's major features: backups to a USB drive on a workstation need agent 1.2 or newer (*Test* on the target says so).
- The agent connects *outbound* over HTTPS to the server. Nothing is opened on the workstation. If the server certificate was replaced, the agent pins the new one on the next pairing. Use *Forget this server* and pair again.
- Right-click the tray icon, then *Show activity…* to see live transfers, or *Open log folder*.

## Service will not start / console unreachable

1.  Start Menu, then *PACS - Service status* shows each port (DICOM, TLS, HTTP, HTTPS), who holds it, and the firewall rules.
2.  HTTPS "connection reset" means the service account cannot read the certificate's private key: `DicomServer.Setup grant`.
3.  Log files are in the data folder's `Logs` subfolder. Warnings also go to the Windows Event Log (source *DicomServer*).

## Duplicate studies in the list

1.  Two studies with the same accession number for one patient are flagged with an amber *×2* badge. Clicking it highlights the set.
2.  This happens when a modality re-sends a study under new UIDs.
3.  TekVault stores by UID (so nothing is lost) and flags at the list level, as most PACS do.

## A patient's name, ID or birth date is wrong

1.  Modalities occasionally send a misspelt name, a wrong ID or a swapped birth date.
2.  Administrators fix it from the Studies page: the ⋯ menu on the patient row, then **Edit patient details**.
3.  Enter the family, given and middle names, the patient ID, birth date and sex, press Apply and confirm.
4.  TekVault PACS rewrites the index and every stored image of that patient (the original values are kept inside each file in the DICOM Original Attributes Sequence) and records who changed what in the Audit Log.
5.  Exports, sends and backups from then on carry the corrected data.
6.  If the corrected ID belongs to a patient already in the archive, the two are merged.
7.  Two patients that are really the same person under different IDs are merged the same way: give one of them the other's ID.
