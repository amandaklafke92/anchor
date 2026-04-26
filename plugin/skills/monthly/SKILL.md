---
name: anchor-monthly
description: >
  This skill should be used when the user says "monthly review", "monthly synthesis",
  "end of month", "monthly reflection", or asks to summarise the month. Use when the
  user wants to synthesise all entries in a calendar month into a monthly summary
  with concrete memory anchors, threads to carry forward, and dominant tags.
version: 0.3.0
---

# Anchor — Monthly Synthesis Skill

## Job

Read all entry files for the target month and synthesise them into a monthly summary — concrete memory anchors, the shape of the month, threads to carry forward, and dominant tags. Written in second person, like a letter back to the user.

---

## File naming

```
monthlies/YYYY-MM_monthly.md
```

Examples: `monthlies/2026-01_monthly.md`, `monthlies/2026-03_monthly.md`

---

## Monthly file structure

```
# [Month YYYY] — Monthly Summary

*Synthesised from: [number] entries, [date range]*

---

## Moments worth remembering

- [anchor]
- [anchor]
- [anchor]

---

## The shape of this month

[2–3 sentences on the emotional or narrative arc of the month — not what happened, but how it felt to live through it. This feeds the yearly synthesis.]

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

**"Moments worth remembering" is the most important section of every monthly file.** These are not summaries or themes — they are concrete anchors specific enough to reconstruct the moment without opening the entry file.

Each anchor must include: **who, what, and the telling detail.** Length should match what's needed — some moments need one sentence, some need three.

**Bad:** *"The shoulder press stranger"*
**Good:** *"After two nights of bad sleep, dragging herself to the gym — a stranger complimented her shoulder press and form unprompted (17.5 kg, 8 reps)"*

**Bad:** *"Conversation with Sam"*
**Good:** *"Sitting on Sam's kitchen floor after dinner, Sam asked 'do you actually want this job?' and the answer came out faster than expected: 'I want the work, not the version of myself I become there.'"*

**Test:** Could the user read this anchor cold in two years and know what happened, without opening the entry file? If no, it needs more specificity. Titles and themes fail this test. Scenes pass it.

Aim for 4–8 anchors per month. Prioritise moments that are vivid, significant, or have narrative potential — not coverage of every entry.

---

## Process

1. Confirm the month and year with the user
2. Read all files in `entries/` whose `date:` YFM field falls within that calendar month
3. Check: does `monthlies/YYYY-MM_monthly.md` already exist?
   - If **yes** — stop. Notify the user that this month already has a summary.
   - If **no** — proceed.
4. Identify 4–8 moments worth anchoring — vivid, significant, or with narrative potential
5. Write each anchor using the format rules above. Test each one: could the user read it cold in two years and know what happened?
6. Write "The shape of this month" — 2–3 sentences on the emotional or narrative arc. Not a summary of events — how it felt to live through.
7. Identify 3–5 threads to carry forward — things unresolved, worth returning to, or with narrative potential. Name them specifically enough to be actionable.
8. Identify dominant tags across the month's entries
9. Write the complete monthly file using the structure above, in **second person ("you")** throughout
10. Save to `monthlies/YYYY-MM_monthly.md`
11. If the month is incomplete, note it in the synthesised from line: *partial — through [date]*

---

## Rules

- Write in **second person** throughout — every sentence. It should feel like a letter back to the user, not a report.
- Anchors must be concrete and specific. Do not write abstract thematic summaries and call them moments.
- Do not create new tags without flagging to the user
- Threads should be named specifically — not "the relationship question" but what specifically is unresolved
- Do not rely on memory between sessions — all context comes from the entry files you read
