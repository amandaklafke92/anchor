---
name: anchor-weekly
description: >
  This skill should be used when the user says "do my weekly", "weekly synthesis",
  "wrap up the week", "weekly review", or asks to compile and summarise the week's
  entries. Use when the user wants to synthesise daily entries into a complete weekly
  file with a summary, themes, and highlights.
version: 0.3.0 
---

# Anchor — Weekly Synthesis Skill

## Job

Read the week's daily entries and synthesise them into a complete weekly file — weekly summary at the top, followed by daily entries, then the populated header block.

---

## File naming convention

```
YYYY-MM_mmm_week-DD.md
```

| Segment | Example | Notes |
|---------|---------|-------|
| `YYYY-MM` | `2026-01` | Zero-padded month |
| `mmm` | `jan` | Three-letter month abbreviation |
| `week-DD` | `week-20` | Day the week starts |

Examples: `2026-01_jan_week-20.md`, `2026-03_mar_week-17.md`

Weeks spanning two months are assigned to the month the first entry of that week falls in. If the first entry is dated 30 March, the file belongs to March — regardless of how many days fall in April.

---

## Weekly file structure

The complete weekly file looks like this:

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

## [Next entry...]

---
```

---

## Process

1. Ask the user which week they are wrapping up:
   > "Which week would you like to wrap up?"
   > - This week ([Mon DD Mon] – today)
   > - Last week ([Mon DD Mon] – [Sun DD Mon])

2. Determine the correct filename using the naming convention above, based on their answer

3. Read all daily entries in the weekly file

4. Check: does the file already have a Weekly Summary section?
   - If **yes** — stop. Notify the user that this week already has a summary.
   - If **no** — proceed.

5. Write the Weekly Summary section at the **top** of the file, directly under the title:
   - `**What happened:**` — 2–3 factual sentences covering the week as a whole
   - `**Themes this week:**` — dominant tags across the week

6. Populate the header block beneath the summary:
   - `people:` — key figures who appear across the week's entries. Exclude anyone mentioned only in passing (a stranger, a name dropped once without context).
   - `places:` — meaningful or orienting locations (a city, a venue, a significant setting). Exclude incidental details like "at my desk" or "in bed".
   - `themes:` — 2–4 thematic words or short phrases that characterise the week
   - `highlights:` — one line naming 2–3 standout moments

7. Save the updated file

8. Confirm to the user: which file was updated, how many entries were synthesised, and any flags or uncertainties carried forward from the entries

9. Check whether a monthly summary file exists for the current month (e.g. `2026-03_mar_monthly.md`). If it does not exist and the current date is within the last 7 days of the month, notify the user: *"It's nearly the end of [month] — would you like to run the monthly reflection?"*

---

## Rules

- Preserve the user's exact voice in all entry content — do not paraphrase or edit entries
- The weekly summary should be **factual and grounded** — not analytical. Save interpretation for the monthly.
- Suggest the most specific and accurate tags that fit the entry — user will confirm before they're finalised
- Do not create new tags without flagging to the user
- If any dates are uncertain, carry the *[Date approximate]* flag forward from the daily entries
