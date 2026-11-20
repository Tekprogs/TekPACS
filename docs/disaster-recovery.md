# Disaster recovery

Rebuilding a lost server from nothing but its backup.

Every backup target (folder, share, S3, Azure, USB drive on a workstation) holds three things.

1.  `files/`: every image as received.
2.  `snapshots/`: daily copies of the index database and `config.json`.
3.  `installer/`: the server and agent installers plus a `HOW-TO-RESTORE.txt` written for that server.

That is enough to come back from a dead machine.

1.  **Install.** On the new Windows server run `installer\TekVaultPACS-Setup-<version>.exe` from the backup. Accept the defaults. The AE title, ports and settings come back in the next step.

2.  **Reach the backup.** Plug in the drive, map the share or have the cloud credentials ready. If the backup lives on a workstation's USB drive, install the agent there and pair it.

3.  **Restore the snapshot.** In an administrator prompt in the install folder's `Setup\` directory:

        DicomServer.Setup restore-snapshot "<target name>"

    This puts `config.json` and `index.db` back from the newest snapshot and restarts the service. (If the target was not part of the restored configuration, add it first on the Backups page under Settings.)

4.  **Bring the images back.** Sign in, open *Under Settings, go to Restore*, choose the target and press **Restore missing files** (or *Restore entire archive*). Images stream from `files/` into the storage folder. Progress is on the Restore page and the dashboard.

5.  **Re-point modalities** only if the server's IP or name changed. The AE title and ports came back with the configuration.

6.  **Workstations**: re-run `installer\DicomAgent-Setup-<version>.exe` if needed and pair again from the Export page.

Partial restores (a few studies) never need any of this: *Under Settings, go to Restore*, then search, then tick, then Restore. The [backup guide](backup.md) covers it.
