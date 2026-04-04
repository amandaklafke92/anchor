---
name: anchor-monthly
description: >
  This skill should be used when the user says "monthly review", "monthly synthesis",
  "end of month", "monthly reflection", or asks to summarise the month. Use when the
  user wants to synthesise all weekly files for a given month into a monthly summary
  with concrete memory anchors, threads to carry forward, and dominant tags.
version: 0.2.0
---

# Anchor — Monthly Synthesis Skill

## Job

Synthesise the month's weekly files into a monthly summary — concrete memory anchors, threads to carry forward, and dominant tags. Written in second person, like a letter back to the user.

---

## File naming convention

```
YYYY-MM_mmm_monthly.md
```

Examples: `2026-01_jan_monthly.md`, `2026-03_mar_monthly.md`

---

## Monthly file structure

```
# [Month] [Year] — Monthly Summary

*Synthesised from: [list of weekly files used]*

---

## Moments worth remembering

- [anchor]
- [anchor]
- [anchor]

---

## Threads to carry forward

- **[Theme]:** [what's unresolved, worth returning to, or has narrative potential]
- **[Theme]:** [...]

---

## Dominant tags

`#tag1` `#tag2` `#tag3`

---
```

---

## Anchor format rules

**"Moments worth remembering" is the most important section of every monthly file.** These are not summaries or themes — they are concrete anchors specific enough to reconstruct the moment without opening the weekly file.

Each anchor must include: **who, what, and the telling detail.** Length should match what's needed — some moments need one sentence, some need three. There is no fixed format.

**Bad:** *"The shoulder press stranger"*
**Good:** *"After two nights of bad sleep, dragging herself to the gym — a stranger complimented her shoulder press and form unprompted (17.5 kg, 8 reps)"*

**Bad:** *"Conversation with Luis"*
**Good:** *"Sitting on Luis's bed, him asking 'are you happy with me?' — the honest answer was 'I'm not unhappy with you' but she didn't say it out loud"*

**Test:** Could the user read this anchor cold in two years and know what happened, without opening the weekly file? If no, it needs more specificity. Titles and themes fail this test. Scenes pass it.

Aim for 4–8 anchors per month. Prioritise moments that are vivid, significant, or have narrative potential — not coverage of every week.

---

## Process

1. Confirm the month and year
2. Read all weekly files for that month
3. Identify 4–8 moments worth anchoring — vivid, significant, or with memoir/essay potential
4. Write each anchor using the format rules above:
   - Include who, what, and the telling detail
   - Length should match what's needed to reconstruct the moment — not a fixed format
   - Test each anchor: could the user read this cold in two years and know what happened without opening the weekly file?
5. Identify 3–5 threads to carry forward — things unresolved, worth returning to, or with narrative/memoir potential. Name them specifically enough to be actionable.
6. Identify dominant tags across the month
7. Output the complete monthly file using the structure above, written in **second person ("you")** throughout — it should feel like a letter back to the user, not a report
8. If the month is incomplete, note it in the synthesised from line: *partial — through [date]*

---

## Rules

- Write in **second person** ("you did this, you felt that") throughout — every sentence
- Anchors must be concrete and specific — see format rules above. Do not write abstract thematic summaries and call them moments.
- Do not create new tags without flagging to the user
- Threads should be named specifically — not "the relationship question" but what specifically is unresolved or worth examining
- Do not rely on memory between sessions — all context comes from the weekly files you read
