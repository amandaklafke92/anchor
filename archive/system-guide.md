# Anchor — System Guide

How the Anchor journaling system works. This is the reference document for the plugin — covering file naming, entry structures, the tag system, and the principles that govern how entries are written and synthesised.

---

## Core design principle

Text records serve as a memory prosthetic. Entries must reconstruct lived experience, not summarise it. This is the most important principle in the system — every formatting and synthesis decision serves this goal.

An entry isn't useful if it just captures what happened. It has to reconstruct the moment: who was there, what was said, the specific detail that makes it real.

---

## File naming convention

All Anchor files follow this pattern:

```
YYYY-MM_mmm_[type]-[DD].md
```

| Segment | Example | Notes |
|---------|---------|-------|
| `YYYY-MM` | `2026-03` | Zero-padded month — ensures chronological sort |
| `mmm` | `mar` | Three-letter month abbreviation, lowercase |
| `type` | `week` or `monthly` | File type |
| `DD` | `16` | Day number — weekly files only; always the Monday that starts the week |

Examples:
- `2026-03_mar_week-16.md` — week starting Monday 16 March 2026
- `2026-03_mar_monthly.md` — monthly summary for March 2026

**Week attribution:** weeks are always assigned to the month their Monday falls in, regardless of how many days fall in the following month. If Monday 30 March starts the week, the file belongs to March.

This naming convention keeps files sorted chronologically and grouped by month in any file browser.

---

## Date handling

**Daily entries:**
- If the user provides a date, use it.
- If no date is given, use the date of the current session and add a small flag directly below the entry heading: *[date autoselected — correct if needed]*

---

## File structures

### Daily entry

Daily entries are stored inside the relevant weekly file, not in separate files.

```
## [Weekday, DD Month]

`source: [source name if imported — omit line entirely if captured directly in session]`
`tags: #tag1 #tag2 #tag3`
`keywords: [people, places, themes specific to this entry]`

[Entry content — preserve the user's exact voice and wording]

---
```

The `source:` line is only included when the entry was imported from an external source (voice memo, Google Doc, etc.). If captured directly in the Cowork session, omit the line entirely — do not write `source: session` or leave it blank.

---

### Weekly file

```
# Week of [Month DD–DD], [Year]

## Weekly Summary

**What happened:** [2–3 sentence factual overview of the week]

**Themes this week:** #tag1, #tag2, #tag3

---

people: [key figures who appear this week — not passing mentions]
places: [meaningful or orienting locations — not incidental settings like "in bed"]
themes: [2–4 thematic words or short phrases]
highlights: [one-line summary of 2–3 standout moments]

---

## [Weekday, DD Month]

`tags: #tag1 #tag2 #tag3`
`keywords: [people, places, themes]`

[Entry content]

---

[further daily entries...]
```

The Weekly Summary goes at the top so the week can be understood without reading every entry.

---

### Monthly file

```
# [Month] [Year] — Monthly Summary

*Synthesised from: [list of weekly files used]*

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

**"Moments worth remembering" is the most important section of every monthly file.** These are not summaries or themes — they are concrete anchors specific enough to reconstruct the moment without opening the weekly file.

Each anchor must include: **who, what, and the telling detail.** Length should match what's needed — some moments need one sentence, some need three.

**Not good enough:**
- *"The run"*
- *"Difficult conversation with a colleague"*

**Good:**
- *"First 5km without stopping — legs burning past the 3km mark, didn't walk, finished in 31:42 on a grey Tuesday morning in the park near the office"*
- *"After the presentation, pulling them aside to say the feedback had landed badly — they went quiet, then: 'I didn't realise I was doing that.' The pause before they spoke felt long."*

**Test:** could the user read this anchor cold in two years and know what happened, without opening the weekly file? If no, it needs more specificity. Titles and themes fail this test. Scenes pass it.

Aim for 4–8 anchors per month. Prioritise moments that are vivid, significant, or have narrative potential — not coverage of every week.

---

## Editing and fidelity

When formatting a voice note, transcript, or raw entry, preserve the user's voice. The goal is light cleanup, not rewriting.

**Acceptable:**
- Removing filler words ("um", "like", "you know")
- Fixing grammar and punctuation
- Fixing clear transcription errors (e.g. "Down Hall" → "Town Hall")
- Splitting a long run-on into two sentences where it aids readability — without changing any words
- Reordering sentences within a paragraph only when the original order was clearly scrambled — flag this to the user rather than doing it silently

**Not acceptable:**
- Rewriting sentences, even if the result is "better" writing
- Replacing the user's phrasing with cleaner or more polished alternatives
- Condensing or cutting content
- Smoothing out rawness, informality, or repetition — these are intentional
- Completing a sentence that trails off — leave it trailing
- Inferring emotions or motivations not explicitly stated

**Unclear audio:** if a word or phrase cannot be reliably transcribed, mark it `[unclear]` rather than guessing. The user can correct it before saving.

**Example — not acceptable:**

Original: *"I was feeling nervous because in the past I haven't had the best experiences at networking events. Always being dragged there by my ex-boss to talk about recruitment, which I really couldn't care less about."*

Over-edited: *"I'd been nervous about going. In the past, networking events had always been a drag — recruited by my ex-boss to talk about recruitment (which I couldn't care less about)."*

The second version is tighter, but it's no longer her voice.

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

## Core operating principles

- **Preserve the user's voice.** Do not paraphrase, smooth out, or tidy up entry content. The rawness is the point.
- **Daily is capture, not synthesis.** Format and park. Do not analyse or summarise.
- **Weekly summary is factual.** What happened — not interpretation. Save analysis for the monthly.
- **Monthly is written in second person.** "You did this, you felt that" — it should feel like a letter back to the user, not a report.
- **Date uncertainty must be noted explicitly.** Never guess silently — use *[Date approximate]* or *[date autoselected — correct if needed]*.
- **New tags are flagged before creating.** Suggest but do not create without the user's approval.
- **Do not rely on memory between sessions.** All context lives in the files.
