# Assignment 03 — Device Features and Upload — Samples

**v0.1 DRAFT — 2026-11-23** · Look-and-feel references only. They are **not** solutions.

One wireframe per screen in [product-brief.md](../product-brief.md) section 6. A second file appears only where a non-default state is central to the assignment.

| File | Screen | Shows |
|---|---|---|
| [S-01-reports-list.svg](screens/S-01-reports-list.svg) | S-01 Reports list | Rows with Uploading / Failed / Queued / Uploaded, progress, Cancel, Retry, New report |
| [S-02-new-report-form.svg](screens/S-02-new-report-form.svg) | S-02 New report form | Title, note, photo slot, Add photo, location field, Save |
| [S-03-photo-source-choice.svg](screens/S-03-photo-source-choice.svg) | S-03 Photo source choice | Bottom sheet: Take photo (unavailable, denied), Choose from gallery |
| [S-04-permission-rationale.svg](screens/S-04-permission-rationale.svg) | S-04 Permission rationale (in-app) | Reason for camera access, Continue, Not now |
| [S-05-os-permission-dialog.svg](screens/S-05-os-permission-dialog.svg) | S-05 OS permission dialog (system) | Generic system sheet: precise / approximate, allow options, Don't allow |
| [S-06-permission-denied-notice.svg](screens/S-06-permission-denied-notice.svg) | S-06 Permission denied notice | Permanently denied effect, gallery alternative, Open settings |
| [S-07-camera.svg](screens/S-07-camera.svg) | S-07 Camera | Captured preview, Retake, Use photo |
| [S-08-gallery-picker.svg](screens/S-08-gallery-picker.svg) | S-08 Gallery picker (system) | Generic system picker, limited access note, one photo selected |
| [S-09-location-status.svg](screens/S-09-location-status.svg) | S-09 Location status | Timeout reason, Try again, Enter place by hand, Save without |
| [S-10-report-detail.svg](screens/S-10-report-detail.svg) | S-10 Report detail | Photo, title, note, location, Uploading progress, Cancel |
| [S-10-report-detail-too-large.svg](screens/S-10-report-detail-too-large.svg) | S-10 Report detail (too large, 413) | Failed state with reason, Replace photo, Retry |
| [S-11-tester-debug.svg](screens/S-11-tester-debug.svg) | S-11 Tester / debug screen | Latency, mid-upload drop, force 5xx, force 413, upload queue |

**Limits (by design)**
- Static SVG wireframes. Names, text and numbers are placeholders.
- System dialogs and pickers are generic sketches; real wording and options come from the OS.
- Your layout, wording and styling may differ. Every status must carry a text label or icon, not colour alone.
