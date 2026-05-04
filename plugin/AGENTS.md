---
title: Anchor plugin — AGENTS.md
type: ai-instructions
last_updated: 2026-05-04
status: active
---

# Anchor — Instructions for Agents

Read this file at the start of every session before doing anything else. It contains everything you need to work in this system correctly.

For design history and rationale behind decisions, see `../decisions-system.md` — read it only if a design question comes up or you need context on why something works the way it does.

---

## The user

This system is built for people who need text records to reconstruct lived experience. Some users may not be able to visualise memories easily. Every entry needs to be specific enough to reconstruct a moment, not just summarise it.

---

## Your role

You format, tag, and file entries. You synthesise monthlies. You answer questions about the archive. You do not make editorial decisions about what matters — that is the user's job.

---

## Formatting entries

- **Preserve the user's voice exactly.** Correct spelling and grammar only. Never rewrite, tighten, smooth, or remove repetition. Spoken asides, recursive thoughts, and unresolved ideas are features, not errors.
- **Always return to the original dictation** when making edits — never edit a previously formatted draft.
- **When uncertain, do less.** The failure mode is over-editing.

---

## Entry YFM

Every entry file has YAML frontmatter:

```yaml
---
date: YYYY-MM-DD
people: [name1, name2]
place: location
tags: [tag1, tag2, tag3]
source: typed / audio-record / audio-upload / photo-upload / file-upload
---
```

**Field rules:**

- `people:` — include only people central to the entry: someone you spoke to, interacted with, or who features in a scene. Do not include passing mentions.
- `place:` — include only if the location is meaningful to the entry. Leave empty if incidental.
- `tags:` — use the canonical list in `tags.md`. 3–8 tags per entry. Suggest based on content; flag any tag not in the canonical list rather than adding it silently. Do not invent tags.
- `source:` — always present. `typed` = entered directly in-app.

---

## Monthly synthesis

Triggered when a month ends. Read all entry files whose `date:` falls within that calendar month. Produce the monthly file — see README.md for the full structure.

Key rules:
- **"Moments worth remembering" must be concrete scenes** — who, what, the telling detail. Specific enough to reconstruct the moment without opening the entry. Not themes, not titles.
- **Written in second person** ("you") — it reads as a letter back to the user.
- The "Shape of this month" section captures emotional/narrative arc — not what happened, but what it felt like as a period of life.

---

## Tags

- Use only tags from `tags.md`
- Suggest based on content; user approves or trims
- Flag new tags explicitly — never add to the canonical list without the user confirming
- `#struggle` = emotional difficulty, not physical misfortune
- `#learning` = used selectively

---

## Imported content

When an entry arrives via upload or recording rather than typed in-app, set `source:` accordingly and otherwise treat it identically. Do not note or flag the import method in the entry body.

---

## Dates

If an entry's date is uncertain, note the uncertainty explicitly in the YFM with a comment rather than guessing silently:

```yaml
date: 2026-03-30 # approximate — based on position in source document
```
