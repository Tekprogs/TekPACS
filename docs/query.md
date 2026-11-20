# Query Remote: pulling studies from another system

Search another PACS, modality or archive and retrieve its studies into TekVault PACS (C-FIND + C-MOVE / C-GET).

### 1. Prepare the node

1.  The remote system must be listed on the Remote nodes page under Settings with *Query* ticked and must answer C-ECHO (green dot).
2.  In the node's Queue options choose how studies are pulled: **C-MOVE** (the default.
3.  The remote sends the study to TekVault PACS, so it must have this server registered as a destination with the AE title, IP and DICOM port shown on the Dashboard) or **C-GET** (the images come back on the same connection.
4.  Nothing to set up on the remote side, but not every system supports it).

In the console: `/settings/nodes`

### 2. Search

1.  Open **Query Remote** in the left menu, pick the server / node in the first drop-down and search exactly as on the Studies page: patient name (with \* wildcards), ID, accession, modality, date range, and under *More fields* description, study ID, referring physician and institution.
2.  Most systems refuse an unrestricted query, so give at least a name, ID, accession, modality or date range.
3.  The last seven days are pre-filled.

In the console: `/query`

### 3. Look at the results

1.  The table lists what the remote system reported: patient, ID, birth date, study date, modalities, description, accession, series and image counts (when the system supplies them).
2.  Studies that TekVault PACS already holds are marked *In archive* with a link to them.
3.  The arrow button on a row asks the remote system for the series of that study.
4.  The first 500 matches are shown. Narrow the search when you hit that limit.

### 4. Retrieve

1.  Press **Retrieve** on a study, or tick several (or *Select all not in archive*) and press **Retrieve selected**.
2.  Each study becomes a job under Retrieve jobs (and on the Jobs page) that shows images received and remaining.
3.  The row shows progress and turns into a *Retrieved* link when done.
4.  Retrieved images are stored, indexed and routed like any received study.
5.  The Audit Log records the query and the retrieve.

### 5. C-MOVE or C-GET?

1.  With C-MOVE the remote system opens its own connection to TekVault PACS to deliver the images.
2.  If a retrieve finishes with "accepted the request but reported no images", the remote system does not know this server as a destination: add it there (AE title, IP, port) or switch the node to C-GET.
3.  C-GET needs no configuration on the remote system but is not offered by every PACS or modality.
4.  If the node rejects it, use C-MOVE.

[Sending studies to another node](send.md) · [Importing files](import.md)
