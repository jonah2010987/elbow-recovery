# Single self-contained HTML file, hosted on public GitHub Pages, phone as canonical device

The tracker is one HTML file with inline CSS/JS and localStorage persistence — no backend, no build step, no sync. It is hosted on public GitHub Pages rather than copied to the phone as a file, because Chrome on Android opens downloaded HTML via `content://` URIs whose localStorage is ephemeral; a stable hosted origin is the only reliable way to persist data on Android without a backend. Logged data never leaves the device; only the protocol content is public.

## Consequences

- Laptop and phone have independent localStorage histories. The phone is the canonical logging device; the laptop is for viewing/analysis via JSON export/import.
- Updating the app (e.g. after a clinic visit) is a git push; the phone picks it up on next load.
- JSON import replaces state wholesale rather than merging. Merge logic was rejected: phone-as-canonical means the laptop never accumulates history worth merging, and the import confirmation shows record counts in both directions before overwriting.
