# Anchor — Plugin Context Block

*Operational reference for all Anchor skills. Read this block in full before executing any task.*

---

## Core design principle

Text records serve as a memory prosthetic — entries must reconstruct lived experience, not summarise it. This is the most important design principle in the system. Every formatting and synthesis decision should serve this goal.

---

## File naming convention

```
YYYY-MM_mmm_[type]-[DD].md
```

| Segment | Example | Notes |
|---------|---------|-------|
| `YYYY-MM` | `2026-01` | Zero-padded month — ensures chronological sorting |
| `mmm` | `jan` | Three-letter month abbreviation |
| `type` | `monthly` or `week` | File type |
| `DD` | `20` | Day the week starts (weekly files only) |

Examples:
- `2026-01_jan_monthly.md`
- `2026-01_jan_week-20.md`
- `2026-02_feb_week-03.md`

Weeks spanning two months are assigned to whichever month contains more days of that week.

---

## File structures

### Daily entry (stored inside the relevant weekly file)

```
## [Day, DD Month]

`source: [source name if imported — omit if captured directly]`
`tags: #tag1 #tag2 #tag3`
`keywords: [people, places, themes specific to this entry]`

[Entry content — preserve the user's exact voice and wording]

---
```

### Weekly file

```
# Week of [Month DD–DD], [Year]

people: [names appearing this week]
places: [locations appearing this week]
themes: [2–4 thematic words or short phrases]
highlights: [one-line summary of 2–3 standout moments]

---

[daily entries]

---

## Weekly Summary

**What happened:** [2–3 sentence overview]

**Themes this week:** #tag1, #tag2, #tag3

---
```

### Monthly file

```
# [Month] [Year] — Monthly Summary

*Synthesised from: [list of weekly files]*

---

## Moments worth remembering

- [anchor]
- [anchor]

---

## Threads to carry forward

- **[Theme]:** [what's unresolved, worth returning to, or has narrative potential]

---

## Dominant tags

`#tag1` `#tag2` `#tag3`

---
```

---

## Anchor format rules

The "Moments worth remembering" section is the most important part of every monthly file. These are not summaries or themes — they are concrete anchors specific enough to reconstruct the moment without opening the weekly file.

Each anchor must include: who, what, and the telling detail. Length should match what's needed — some moments need one sentence, some need three. There is no fixed format.

**Bad anchor:** *"The run"*
**Good anchor:** *"First 5km without stopping — legs burning past the 3km mark, didn't walk, finished in 31:42 on a grey Tuesday morning in the park near the office"*

**Bad anchor:** *"Difficult conversation with a colleague"*
**Good anchor:** *"After the presentation, pulling them aside to say the feedback had landed badly — they went quiet, then: 'I didn't realise I was doing that.' The pause before they spoke felt long."*

Test: could the user read this anchor cold in two years and know what happened, without opening the weekly file? If no, it needs more specificity.

---

## Tag system

Tags are categorical and thematic — not hyper-specific. Each entry should have 5–10 tags. Do not create new tags without flagging them to the user.

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

## Core operating rules

- **Preserve the user's voice.** Do not paraphrase, smooth out, or tidy up entry content. The rawness is the point.
- **Daily entries:** minimal processing — format and park. Do not synthesise or over-tag. The weekly is where synthesis begins.
- **Weekly summaries:** synthesise across the week's entries. Suggest tags generously — user will trim.
- **Monthly summaries:** written in second person ("you") to feel like a letter back to the user. Anchors must be concrete and specific — see anchor format rules above.
- **Source field:** use `source:` metadata for any entry imported from an external document, voice note, or non-session input. Omit if captured directly in session.
- **Date uncertainty:** if a date is uncertain, note it explicitly in the file (e.g. *[Date approximate]*). Never guess silently.
- **New tags:** suggest but do not create without flagging to the user.
- **Do not rely on memory between sessions.** All context lives in the files.

---
