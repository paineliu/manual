# Files & Data Formats

> **Status: Review draft; content pending verification.** Resolve all “To confirm” items before publishing as user instructions.

[Guide home](index.md) · [简体中文](../zh/data-formats.md)

A recording produces a related set of files called a session. Keep the complete session together when saving, copying, or uploading data.

## What the files are for

These categories come from the project's data specifications and explain their purpose. Final filenames, included files, and reading methods depend on the confirmed device version.

| Category | Purpose | Recommendation |
| --- | --- | --- |
| Camera videos | Store camera views | Check that all streams belong to the same task |
| Video timestamps | Map frames to capture times | Use alongside videos for synchronization or processing |
| IMU data | Store device motion measurements | Read with the associated timing information |
| Session metadata | Identify the device, session, and recording configuration | Keep the original; do not edit identity fields manually |
| Calibration data | Describe camera parameters and sensor relationships | Use calibration matching the device and version |
| File manifest | Describe session files and integrity information | Validate with the supplied tool; do not rewrite it |
| Audio, if included | Store sound and related timing information | Availability depends on the delivered configuration |

## When working with data

- Timestamps may use different time bases. Similar values alone do not establish synchronization.
- Do not treat video container playback time as confirmed hardware capture time.
- Use project-approved tools for protected or otherwise unreadable companion files, and preserve the originals.
- A date in a session name does not establish that the device clock was correct. Review validation results for time issues.

## Technical reading reference

> **To confirm:** Add an approved complete session example and verify actual filenames, format versions, fields, units, time bases, coordinate frames, calibration conventions, and reading tools. Internal development examples are not the formal data interface until verified.

If you only need to upload, follow [Export & Verify](export.md); you do not need to read the technical field reference first.
