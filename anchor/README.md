# Anchor

A personal memory system for capturing and synthesising lived experience. Built around the principle that text records serve as a memory prosthetic — entries must reconstruct lived experience, not summarise it.

---

## Skills

| Skill | Trigger phrases | What it does |
|-------|----------------|--------------|
| `anchor-daily` | "add entry", "daily capture", "log this", "new entry" | Formats raw input (voice transcript, typed dump, imported text) as a daily entry and appends it to the correct weekly file |
| `anchor-weekly` | "do my weekly", "weekly synthesis", "wrap up the week" | Synthesises the week's daily entries into a complete weekly file with header metadata and a weekly summary |
| `anchor-monthly` | "monthly review", "monthly synthesis", "end of month" | Synthesises all weekly files for a month into a monthly summary with concrete memory anchors and threads to carry forward |

---

## Setup

No external services or environment variables required. The plugin works entirely with local files in your connected folder.

Point Cowork at the folder where you want your journal files to live before running any skill.

---

## Usage

**Daily capture:** Say "add entry" or "log this" and paste in your text — a voice memo transcript, something you typed out, notes from the day. The skill will format it, suggest tags, and file it in the right weekly file. If the weekly file doesn't exist yet, it will be created.

**Weekly synthesis:** Say "do my weekly" at the end of the week. The skill reads your daily entries and compiles a complete weekly file — people, places, themes, highlights, and a brief written summary. Can also be run on a schedule.

**Monthly reflection:** Say "monthly review" or "end of month". The skill reads all your weekly files and writes a monthly summary in second person — concrete memory anchors (specific enough to reconstruct the moment in two years), threads to carry forward, and dominant tags.

---

## File naming convention

All files follow the pattern `YYYY-MM_mmm_[type]-[DD].md`. Full details are in `references/anchor-context.md`.

---
