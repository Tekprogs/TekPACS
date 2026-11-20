# Getting started

From a blank Windows Server to the first study on screen, in about twenty minutes.

## 1. Install the server

1.  **Download** `TekVaultPACS-Setup-1.6.2.exe` from the [Downloads](../../releases/latest) page onto the server (Windows Server 2016 or newer, or Windows 10/11 for a small site).
2.  **Run it as administrator.** A local administrator of the server is enough. Domain admin rights are not needed (only the optional Group Policy certificate push needs them).
3.  The wizard asks for everything on its pages: AE title, DICOM / HTTP / HTTPS ports (it checks they are free), the data and image folders, and how people sign in (a local admin account or your domain groups).
4.  It registers the *TekVault PACS* Windows service, creates a self-signed certificate, opens the firewall ports, starts the service and checks the ports and the TLS handshake. The status line shows each step as it happens. The final dialog lists what was done.
5.  Re-running a newer installer later **upgrades in place** and offers to keep the existing configuration.

Start Menu, then *Tekprogs* holds the shortcuts: *TekVault PACS Console*, *PACS - Start / Stop / Restart service*, *PACS - Service status*, *PACS - Log folder* and the setup utility.

## 2. Sign in and stop the certificate warning

1.  Open `https://<server>/`.
2.  The browser will warn about the self-signed certificate. On each PC either run **Trust-TekVaultPACS.cmd** from the login page (it installs the certificate for the whole machine and offers to restart the browser) or follow the [certificate guide](certificate.md).
3.  On a domain, push the certificate once by Group Policy or use a certificate from your own CA.

## 3. Register the first modality

1.  [Receiving images](receiving.md) walks through it: add the sender under *Under Settings, go to Remote nodes* (name, AE title, IP, port), configure the server's AE title / IP / port on the modality, press *Check*, send a test study.
2.  Rejections and their reasons appear in the Audit Log.

## 4. Set up a backup

1.  Under *Under Settings, go to Backups* add at least one target: a folder or share, S3-compatible storage, Azure Blob, or a USB drive on a paired workstation, and press *Test*, then *Run now*.
2.  Every target also receives a copy of the installers and a `HOW-TO-RESTORE.txt`, so the backup alone can rebuild a lost server.
3.  See the [backup guide](backup.md) and [disaster recovery](disaster-recovery.md).

## 5. Give users the workstation agent

1.  The **TekVault Agent** lets a user export straight to a USB stick in their own PC and import from CDs or folders there.
2.  Install `DicomAgent-Setup.exe` (no admin rights), then on the Export page press **Pair this computer**.
3.  The agent pairs itself. Details in the [agent guide](agent.md).
