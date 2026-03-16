---
name: anchor-monthly
description: >
  This skill should be used when the user says "monthly review", "monthly synthesis",
  "end of month", "monthly reflection", or asks to summarise the month. Use when the
  user wants to synthesise all weekly files for a given month into a monthly summary
  with concrete memory anchors, threads to carry forward, and dominant tags.
version: 0.1.0
---

# Anchor — Monthly Synthesis Skill

*Part of the Anchor plugin. Read ${CLAUDE_PLUGIN_ROOT}/references/anchor-context.md before executing.*

---

## Job

Synthesise the month's weekly files into a monthly summary — concrete memory anchors, threads to carry forward, and dominant tags.

---

## Input

User-triggered. On trigger, read all weekly files for the current month from the project folder automatically. The user may optionally provide additional context or notes to inform the synthesis before proceeding.

---

## Process

1. Read `${CLAUDE_PLUGIN_ROOT}/references/anchor-context.md` in full — particularly the anchor format rules and monthly file structure
2. Read all weekly files for the month
3. Identify 4–8 moments worth anchoring — moments that are vivid, significant, or have narrative potential. Prioritise specificity over coverage.
4. Write each anchor using the format rules in the context block:
   - Include who, what, and the telling detail
   - Length should match what's needed to reconstruct the moment — not a fixed format
   - Test: could the user read this cold in two years and know what happened without opening the weekly file?
5. Identify 3–5 threads to carry forward — things unresolved, worth returning to, or with memoir/essay potential
6. Identify dominant tags across the month
7. Output the complete monthly file, written in second person ("you"), ready to save

---

## Rules

- Monthly summaries are written in **second person** ("you did this, you felt that") — they should feel like a letter back to the user, not a report
- Anchors must be concrete and specific — see anchor format rules in context block. Do not write abstract thematic summaries and call them moments.
- Do not create new tags without flagging to the user
- If the month is incomplete (not all weeks are in), note this in the synthesised from line (e.g. *partial — through [date]*)
- Threads should be named specifically enough to be actionable — not just "the relationship question" but what specifically is unresolved or worth examining

---
