# Anchor Plugin

This plugin contains the current working version of Anchor: two skills that help capture and review journal entries.

## Skills

| Skill | Purpose |
| --- | --- |
| `anchor-daily` | Format a raw journal entry and save it as a dated Markdown file. |
| `anchor-monthly` | Read a month of entries and create a monthly synthesis. |

## Expected Data Folder

Point the plugin at a private journal folder, not this public repo.

Recommended private structure:

```text
anchor-data/
├── entries/
│   └── 2026-04-13.md
└── monthlies/
    └── 2026-04_monthly.md
```

Real entries should never be committed to this public repository.

## Current Limits

- Typed entries and pasted transcripts are the most mature path.
- Upload/photo/audio flows are product goals, but not all are implemented in the plugin yet.
- The plugin stores Markdown files; it is not yet a standalone app.

See [../docs/data-format.md](../docs/data-format.md) for the file format.
