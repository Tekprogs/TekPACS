# Viewing images in the browser

Open a study in the built-in viewer: window/level with presets, layouts, measurements, ROI statistics, MPR, fusion, tag inspector and export.

### 1. Open a study

1.  In Studies, press View on a study row (or 'View images…' in its ⋯ menu).
2.  The viewer opens in a new tab so the study list stays where it was.

In the console: `/studies`

### 2. Pick a series and a layout

1.  The left column lists the series with a thumbnail, modality and image count. Click one to show it in the active viewport; the left / right arrow keys also switch series.
2.  The layout list (1 × 1 up to 2 × 3) shows several series side by side. Click a viewport to make it the active one; Tab moves to the next.
3.  Link scroll keeps the other viewports on the same slice position, Link W/L and Link zoom share the window and the zoom.
4.  Ref lines draws where each viewport's image cuts the others, and Markers labels the edges of the image with R L A P H F.

### 3. Scroll, window, zoom

1.  Mouse wheel (or ↑ ↓, PgUp/PgDn) steps through the images; the slider at the right does the same, and the Stack tool scrolls by dragging.
2.  Left drag adjusts window/level (left-right = width, up-down = centre), right drag or Ctrl+wheel zooms, middle drag pans.
3.  CT presets (soft tissue, lung, bone, brain, liver, abdomen, mediastinum, stroke) are in the Window list. 'Window: as sent' restores the modality's values, Auto uses the full range of the image, W/L… takes typed values, and W/L from ROI sets the window from the values inside a drawn region.

### 4. Orientation and cine

1.  Rotate 90° left or right, 180°, flip H / V, Invert, Fit, 1:1 and Reset are on the toolbar.
2.  Cine plays a multi-frame image or a whole series; the fps box sets the speed (taken from the file when it says).

### 5. Measure

1.  Length, Angle (three clicks) and Cobb angle (two clicks per line) use the pixel spacing stored in the image.
2.  Calibrate: drag along a distance of known length and type it; every measurement on that series is scaled accordingly.
3.  Rect, Ellipse and Freehand draw a region and show mean, standard deviation, minimum, maximum and area; on CT the values are Hounsfield units. Probe shows the value under the pointer.
4.  Text and Arrow add labels. Click a drawing to select it, drag its handles to adjust it, press Delete to remove it; Clear removes all drawings on the image.
5.  Measurements are approximate and not for diagnostic use.

### 6. MPR, fusion and highlight

1.  MPR rebuilds a CT or MR stack into axial, coronal and sagittal planes with a crosshair, a slab (MIP, MinIP or average, thickness in mm) and a 3D projection that rotates when dragged. The 3D threshold keeps only values above it; 200 shows the bone on a CT.
2.  Fuse… overlays another series of the study in colour on the current one, for example PET on CT, matched by position.
3.  Highlight… colours every pixel inside a value range; the ROI statistics then also count the pixels in that range.

### 7. Tags, export, print

1.  Tags opens the DICOM header of the current image with a filter box.
2.  Export saves the current view as PNG or JPEG, prints it, saves all measurements as CSV, or downloads the original DICOM file.
3.  Press ? for the full key list.

### 8. What it can show

1.  Grey-scale and colour images of any modality, including compressed transfers (JPEG, JPEG-LS, JPEG 2000, RLE). They are decoded on the server.
2.  Reports, PDFs, presentation states and raw data are listed in Studies but skipped by the viewer.
3.  The viewer on exported discs and USB drives is the same viewer with the same tools; see the export guide.
4.  Every study opened is recorded in the Audit Log (Web, then View).

[All guides](index.md) · [Finding and exporting studies](export.md)
