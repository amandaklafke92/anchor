---
name: anchor-weekly
description: >
  This skill should be used when the user says "do my weekly", "weekly synthesis",
  "wrap up the week", "weekly review", or asks to compile and summarise the week's
  entries. Use when the user wants to synthesise daily entries into a complete weekly
  file with a summary, themes, and highlights.
version: 0.1.0
---

# Anchor — Weekly Synthesis Skill

*Part of the Anchor plugin. Read ${CLAUDE_PLUGIN_ROOT}/references/anchor-context.md before executing.*

---

## Job

Take the week's daily entries and synthesise them into a complete weekly file — header block, formatted entries, and weekly summary.

---

## Input

The user will provide one or more of the following:
- Daily entry blocks formatted by the daily capture skill
- Raw entries not yet formatted (process these as per the daily capture skill first)
- A date range for the week

---

## Process

1. Read `${CLAUDE_PLUGIN_ROOT}/references/anchor-context.md` for file naming conventions, weekly file structure, and tag system
2. Confirm the week's date range if not already clear
3. Determine the correct filename using the naming convention (e.g. `2026-03_mar_week-16.md`)
4. Populate the file header block:
   - `people:` — all named people appearing across the week's entries
   - `places:` — all locations appearing across the week's entries
   - `themes:` — 2–4 thematic words or short phrases that characterise the week
   - `highlights:` — one line naming 2–3 standout moments from the week
5. Compile all daily entry blocks in chronological order
6. Write the weekly summary:
   - `**What happened:**` — 2–3 sentences covering the week as a whole
   - `**Themes this week:**` — dominant tags across the week
7. Output the complete weekly file, ready to save

---

## Scheduling & safeguards

This skill is designed to run on a schedule configured in Cowork.
Before executing, run the following check:

1. Are there daily entries in the current weekly file that have not yet been synthesised into a weekly summary?
   - If **no** — stop. Do not proceed. Do not consume tokens.
   - If **yes** — proceed with synthesis.

2. On completion, notify the user with a brief confirmation:
   which file was updated, how many entries were synthesised,
   and any flags or uncertainties carried forward from the daily entries.

3. After completing synthesis, check whether a monthly summary file
   exists for the current month (e.g. `2026-03_mar_monthly.md`).
   If it does not exist and the current date is within the last
   7 days of the month, notify the user:
   *"It's nearly the end of [month] — would you like to run the
   monthly reflection?"*

---

## Rules

- Preserve the user's exact voice in all entry content — do not paraphrase or tidy up
- Suggest tags generously — user will trim
- Do not create new tags without flagging to the user
- The weekly summary should be factual and grounded — not analytical or thematic. Save interpretation for the monthly.
- If entries span two months, assign the file to whichever month contains more days of that week
- If any dates are uncertain, carry the uncertainty flag (*[Date approximate]*) forward from the daily entries

---
