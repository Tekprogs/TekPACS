## TekVault PACS 1.7.0

Server and agent are released together; update both. The console offers the agent download to every user whose agent is older. The database is unchanged from 1.6.4.

### Changes
- One viewer for the console and for every disc and USB export. Discs carry the stored pixel values instead of pictures, so window/level, presets and Hounsfield values are real on the disc too.
- Layouts from 1 × 1 to 2 × 3 with linked scrolling by slice position, linked window and zoom, cross-reference lines and R L A P H F orientation markers.
- Window presets (soft tissue, lung, bone, brain, liver, abdomen, mediastinum, stroke), typed window values, Auto, and W/L from ROI.
- Length, angle and Cobb angle with calibration; rectangle, ellipse and freehand ROI with mean, deviation, minimum, maximum and area; pixel probe; text and arrow labels; drawings can be selected, moved, deleted and exported as CSV.
- MPR: axial, coronal and sagittal planes with a crosshair, slab MIP / MinIP / average, and a rotating 3D projection with a threshold. Fuse overlays another series in colour (PET on CT); Highlight colours a value range.
- Tag inspector with filter, export of the view as PNG or JPEG, print, and download of the original DICOM file. Cine uses the frame rate stored in the file. Every toolbar button has an icon.
- Full notes: https://tekprogs.com/docs/whats-new.html

### Files
| File | SHA-256 |
|---|---|
| TekVaultPACS-Setup-1.7.0.exe | (from publish\github-release\v1.7.0\SHA256SUMS.txt after the build) |
| DicomAgent-Setup-1.7.0.exe | (from publish\github-release\v1.7.0\SHA256SUMS.txt after the build) |

Runs on Windows Server 2016 or newer, or Windows 10 / 11 (64-bit). Windows SmartScreen may warn about a newly downloaded installer; choose *More info*, then *Run anyway*.
