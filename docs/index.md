# TekVault PACS documentation

Step-by-step guides with screenshots for everyone who uses or runs TekVault PACS, from sending a study to a USB stick to rebuilding a server from its backup. The same guides are built into the console under *Help & support*.

**Start here:** [Getting started: install and first images](getting-started.md) · [Troubleshooting](troubleshooting.md) · [What's new](whats-new.md)

## Everyday use

- **[Viewing images in the browser](viewer.md)**: Open a study in the built-in viewer: window/level, zoom, pan, scroll through series, measure. (5 steps)
- **[Finding and exporting studies](export.md)**: Search the archive, select studies and download a ZIP or write them to a USB drive. (7 steps)
- **[Query Remote](query.md)**: Search another PACS or modality and pull its studies into TekVault PACS. (5 steps)
- **[Sending studies to another node](send.md)**: Forward selected studies to a remote PACS or workstation with C-STORE. (5 steps)
- **[Importing files without the network](import.md)**: Bring DICOM files in from a folder on the server, from your own PC via the agent, or through the inbox folder. (4 steps)
- **[Installing and pairing the TekVault Agent](agent.md)**: Let users export to and import from USB drives and discs on their own PC. (6 steps)

## Setting up

- **[Receiving images from a modality or PACS](receiving.md)**: Register the sender, point it at this server and verify the first transfer. (6 steps)
- **[Automatic routing (forwarding) of studies](routing.md)**: Send received studies on to other nodes by modality, sending AE title, IP address, station or institution. (5 steps)
- **[Signing in and permissions](signin.md)**: Choose how users sign in and who gets administrator rights. (6 steps)
- **[Stopping certificate warnings](certificate.md)**: Trust the server's certificate on client PCs, or install one from your own CA. (5 steps)
- **[Storage locations and quotas](storage.md)**: Add drives, control where new images go, and set limits. (4 steps)

## Keeping it healthy

- **[Backups and restore](backup.md)**: Set up a backup target, watch it run, and bring studies back when needed. (5 steps)
- **[Working with jobs](jobs.md)**: Understand the Jobs table, retries and the details popup. (5 steps)
- **[Keeping the server healthy](health.md)**: Maintenance checks, logs and resource tuning. (4 steps)
- **[Emergency administrator (command line)](emergency.md)**: Get back in when nobody can sign in as an administrator: add-admin, test-login, set and restart from the server. (5 steps)

## Access

What each kind of account can open in the console. Administrators are the members of the administrator groups on the Web & login page under Settings.

### All users

1.  **Studies**: search the archive and open studies in the [viewer](viewer.md).
2.  **Send To Node**: [forward studies](send.md) to another PACS or workstation.
3.  **Export / Download**: [ZIP download, USB drive, folder, or a CD / DVD](export.md) on your own PC.
4.  **My agents**: [pair and manage](agent.md) your own computers.
5.  **Help & support**.

### Administrators

1.  Everything above.
2.  **Dashboard**: live transfers, health and storage at a glance.
3.  **Query Remote**: [search another PACS](query.md) and retrieve its studies.
4.  **Import / Upload**: [bring files in](import.md) from a folder or the inbox.
5.  **Jobs**: [every background task](jobs.md), with cancel and retry.
6.  **Audit Log**: connections, transfers, sign-ins and changes.
7.  **Settings**: DICOM & TLS, [Remote nodes](receiving.md), [Routing](routing.md), [Storage](storage.md), [Backups](backup.md), Restore, Export, Agents, Bandwidth, Memory, Security, [Web & login](signin.md), [Maintenance](health.md).
8.  Delete studies and edit patient details on the Studies page.

## Reference

- **[Getting started](getting-started.md)**: Install the server, trust the certificate, register the first modality, pair a workstation agent.
- **[Troubleshooting](troubleshooting.md)**: Most problems announce themselves in the console. Here is where to look and what it means.
- **[Disaster recovery](disaster-recovery.md)**: Rebuild a lost server from a backup drive or bucket: installers, snapshot restore, missing-file restore.
- **[What's new](whats-new.md)**: Release notes for every version.
