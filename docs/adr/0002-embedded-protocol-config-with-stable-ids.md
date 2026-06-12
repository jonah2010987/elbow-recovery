# Protocol embedded as a config object with stable IDs; UI overrides for small edits

The protocol markdown is written for humans and has no machine-readable structure, so the app does not parse it at runtime. Instead, the HTML file embeds a `PROTOCOL` config object (phases, exercises, dosing, entry criteria) that Claude Code regenerates from the markdown when the protocol changes — the translation is interpretive work, done at authoring time.

Every phase, exercise, and entry criterion carries a permanent ID. All localStorage history is keyed against these IDs, so regenerations MUST preserve existing IDs or history orphans. Stored data carries a schema version number so future shape changes can migrate rather than wipe.

Small clinic-driven edits (brace block schedule, criterion wording, phase date ranges) are made in the app UI and stored in localStorage as overrides layered on top of the embedded defaults. Structural changes (new exercises, reordered phases) go through the markdown → regeneration path.
