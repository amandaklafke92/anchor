---
name: anchor-daily
description: >
  This skill should be used when the user says "add entry", "daily capture",
  "log this", "new entry", "add a daily entry", or provides a block of text,
  voice transcript, or notes to be recorded as a journal entry. Use when the
  user wants to capture something that happened and park it in the correct
  weekly file.
version: 0.2.0
---

# Anchor — Daily Capture Skill

## Job

Take raw input (pasted voice transcript, typed dump, or imported text) and format it as a daily entry, then append it to the correct weekly file. Do not synthesise. Do not over-tag. Just format and park.

---

## Input

The user will provide one of the following:
- A pasted voice transcript
- A typed text dump
- Imported text with a source noted

The user may or may not specify the date. If no date is given, ask for it before proceeding. Do not guess silently.

---

## File naming convention

Weekly files follow this pattern:

```
YYYY-MM_mmm_week-DD.md
```

| Segment | Example | Notes |
|---------|---------|-------|
| `YYYY-MM` | `2026-01` | Zero-padded month — ensures chronological sort |
| `mmm` | `jan` | Three-letter month abbreviation |
| `week-DD` | `week-20` | Day the week starts |

Examples: `2026-01_jan_week-20.md`, `2026-02_feb_week-03.md`

Weeks spanning two months are assigned to whichever month contains more days of that week.

---

## Daily entry structure

Each entry is appended inside the relevant weekly file using this exact format:

```
## [Weekday, DD Month]

`source: [source name if imported — omit line entirely if captured directly in session]`
`tags: #tag1 #tag2 #tag3`
`keywords: [people, places, themes specific to this entry]`

[Entry content — preserve the user's exact voice and wording verbatim]

---
```

---

## Tag system

Tags are categorical and thematic — not hyper-specific. Each entry should have 5–10 tags. Do not create new tags without flagging them to the user first.

### Entry type
- `#scene` — a moment captured vividly (dialogue, interaction, setting, sensory detail)
- `#reflection` — thinking through something, processing, introspection
- `#fact` — what happened (neutral capture, events, logistics)
- `#dialogue` — interesting conversation or exchange worth remembering
- `#turning-point` — felt significant, might matter later
- `#character` — interesting person or interaction worth remembering

### Life domains
- `#work` — career, projects, job stuff
- `#travel` — movement, places, geography
- `#relationship` — people, conversations, connections
- `#health` — body, sleep, exercise, energy
- `#mental-health` — therapy sessions, mood patterns, psychological self-reflection
- `#learning` — new ideas, skills, insights
- `#rest` — downtime, leisure, recharge
- `#social` — friends, gatherings, community

### Emotional / thematic
- `#beauty` — moments of aesthetic or emotional beauty
- `#struggle` — hard things, frustration, confusion, difficulty
- `#joy` — happiness, lightness, fun, laughter
- `#grief` — loss, sadness, mourning
- `#wonder` — curiosity, amazement, discovery
- `#creative` — making something, artistic moments

### Meta
- `#planning` — thinking ahead, setting intentions
- `#review` — looking back, assessing
- `#note-to-self` — reminders, lessons, things to remember

---

## Process

1. Identify or confirm the date of the entry
2. Format the content as a daily entry block using the structure above
3. Preserve the user's exact voice and wording — do not paraphrase or tidy up
4. Suggest 5–10 tags from the tag system above — user will approve or trim
5. Populate the `keywords:` field with people, places, and themes that appear in the entry
6. If the content came from an external source (e.g. "this is from Voice Memos", "imported from Google Docs"), populate the `source:` field. If no source has been mentioned, ask: *"Would you like to note a source for this entry?"*
7. Determine the correct weekly file using the naming convention above
8. Append the formatted entry block to that weekly file. If the file does not exist yet, create it using the weekly file structure (see weekly skill) then add the entry.
9. Output the formatted entry block to confirm what was saved.

---

## Rules

- Do not synthesise or analyse — this is capture, not review
- Do not create new tags without flagging to the user
- If the date is uncertain, note it explicitly: *[Date approximate]*
- If the input covers multiple distinct moments or topics, split into separate dated entry blocks and flag this to the user
- If capturing directly in session (not imported), omit the `source:` line entirely — do not write `source: session` or leave it blank
