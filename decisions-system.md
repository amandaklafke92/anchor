---
project: Anchor
doc_type: decision-log
domain: system-design
date_created: 2026-04-13
last_updated: 2026-04-13
status: active
purpose: >
  Records confirmed design decisions for the Anchor journaling system's
  file structure, metadata, and automation workflow. Written for AI collaborators.
  Read on demand — not required at every session. Check here before README when
  a structural question arises; this log is more granular.
read_when: design question arises, onboarding with no prior context, active system iteration
---

# Anchor — System Design Decision Log

---

## Design Philosophy

**Add structure only when the need is proven.** Every structural decision in this system has been made by asking whether a layer is doing real work. If it isn't, it gets dropped. It is always easier to add structure later than to undo it. Apply this principle to any future decisions about the system.

---

## Workflow

### Weekly summary

**Status: decided**

Dropped entirely. The weekly file no longer exists. There is no synthesis step at the weekly level. The AI reads entries directly when generating the monthly — an intermediate summary layer adds no value and creates unnecessary overhead.

### Monthly synthesis

**Status: decided**

AI-automated. Reads all entry files whose `date:` field falls within the target calendar month. Context window is not a constraint — a full month of daily entries is well within limits for current models even at maximum journalling frequency.

### Yearly synthesis

**Status: decided**

AI-automated. Reads from monthly files only — never from raw entries. Monthlies are the compression layer for the yearly. End product is a curated printed book. Photo integration is deferred to v2.

### User automation

**Status: decided**

The user's only manual input is the raw journal entry. All formatting, metadata generation, and file creation is handled by the automation layer.

---

## File Structure

### Weekly files

**Status: decided**

Dropped entirely. Originally introduced as a context management solution — an intermediate container to reduce the volume Claude needed to read for monthly synthesis. This problem does not exist at realistic journalling volumes. The weekly layer was never load-bearing.

### Separate entry files

**Status: decided**

Each journal entry is its own `.md` file named by date. No weekly container. Entries compose directly to monthlies.

Rationale:
- Each entry is self-contained with its own metadata
- Retrieval is cleaner — Claude opens exactly the file it needs
- Separate files are trivially combinable; combined files are harder to split
- Simpler automation

### Flat folder structure

**Status: decided**

Entry files live flat in a single `entries/` folder. No nesting by year or month. Most users will not journal every day — at realistic volumes a flat folder is manageable. Nesting can be added later if the need is proven.

### File naming: entry files

**Status: decided**

```
YYYY-MM-DD.md
```

### File naming: monthly files

**Status: decided**

```
YYYY-MM_monthly.md
```

`mmm` abbreviation dropped — redundant when the month number is already present.

### Index file

**Status: decided**

Dropped. Retrieval is better served by Claude scanning entry YFM blocks on demand. A human-readable overview can be generated on request rather than maintained continuously. Maintaining it would duplicate metadata that already exists in structured form at source.

### Confirmed folder structure

```
anchor/
├── entries/
│   ├── 2026-03-30.md
│   ├── 2026-03-31.md
│   └── ...
├── monthlies/
│   ├── 2026-03_monthly.md
│   └── ...
├── CLAUDE.md
├── README.md
├── decisions-system.md
├── decisions-product.md
└── tags.md
```

---

## Entry Metadata (YFM)

### `keywords:` field

**Status: decided**

Dropped. Replaced by explicit `people:` and `place:` fields, which serve retrieval more precisely.

### `date:` field

**Status: decided**

Added explicitly at entry level for machine-clean retrieval. Previously only lived in a human-readable section header.

### `place:` field

**Status: decided**

Always present as a field even if empty. Location is important enough to warrant a dedicated field.

### `people:` and `place:` threshold rule

**Status: decided**

Include only people and places central to the entry — someone the user interacted with or who features in a scene; a location meaningful to the entry. Not passing mentions.

### `source:` field

**Status: decided**

```
typed / audio-record / audio-upload / photo-upload / file-upload
```

Always present. Reflects the capture method, not the content origin.

### `highlights:` field

**Status: decided**

Dropped. Was a mini-summary in disguise — removed along with the weekly summary.

### `description:` in YFM

**Status: decided**

Considered and rejected. Replicates the dropped weekly summary and is outperformed by structured fields for retrieval purposes.

### Weekly YFM aggregate block

**Status: decided**

Dropped. Previously proposed as a fast-scan navigation layer at the top of weekly files. Dropped along with weekly files.

### `themes:` field

**Status: open**

Should `themes:` be a field in entry YFM, or is it fully covered by `tags:`? Not yet decided.

---

## Monthly File

### "The shape of this month" section

**Status: decided**

Added. Captures the emotional or narrative arc of the month in 2–3 sentences. Distinct from "Moments worth remembering" (scenes) and "Threads to carry forward" (unresolved themes). This section feeds the yearly synthesis.

---

## System Files

### README.md vs CLAUDE.md

**Status: decided**

Previously one blended file. Now split:
- **CLAUDE.md** — operational instructions for AI collaborators; read at session start
- **README.md** — human-facing documentation; purpose, how it works, capture methods, data ownership

---

## Tags

### Tag suggestion approach

**Status: decided**

Do not invent tags silently. Flag any new tag candidates to the user. Only suggest tags from the canonical list in `tags.md`.

---

## Open Questions

### Yearly curation

**Status: open**

How much of the yearly synthesis curation step is human vs AI? Not yet designed.

### Reflection prompts and check-in notifications

**Status: deferred**

Flagged as a future feature, deferred from v1.

### Entry storage location

**Status: deferred**

Where entries are saved (local vs cloud vs both) — TBD product decision. See `decisions-product.md` → Storage Architecture.
