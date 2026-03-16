---
name: anchor-daily
description: >
  This skill should be used when the user says "add entry", "daily capture",
  "log this", "new entry", "add a daily entry", or provides a block of text,
  voice transcript, or notes to be recorded as a journal entry. Use when the
  user wants to capture something that happened and park it in the correct
  weekly file.
version: 0.1.0
---

# Anchor — Daily Capture Skill

*Part of the Anchor plugin. Read ${CLAUDE_PLUGIN_ROOT}/references/anchor-context.md before executing.*

---

## Job

Take raw input (pasted voice transcript, typed dump, or imported text) and format it as a daily entry, ready to be added to the relevant weekly file. Do not synthesise. Do not over-tag. Just format and park.

---

## Input

The user will provide one of the following:
- A pasted voice transcript
- A typed text dump
- Imported text with a source noted

The user may or may not specify the date. If no date is given, ask for it before proceeding. Do not guess silently.

---

## Process

1. Read `${CLAUDE_PLUGIN_ROOT}/references/anchor-context.md` for file naming conventions, entry structure, and tag system
2. Identify or confirm the date of the entry
3. Format the content as a daily entry block using the structure in the context block
4. Preserve the user's exact voice and wording — do not paraphrase or tidy up
5. Suggest 5–10 tags from the tag system — user will approve or trim
6. Populate the `keywords:` field with people, places, and themes that appear in the entry
7. If the user has indicated the content came from an external source (e.g. "this is from Voice Memos", "imported from Google Docs"), populate the `source:` field accordingly. If no source has been mentioned, ask the user: *"Would you like to note a source for this entry?"*
8. Output the formatted entry block, ready to paste into the relevant weekly file
9. Append the formatted entry block to the correct weekly file. If the weekly file does not exist yet, create it using the naming convention and weekly file structure from the context block, then add the entry.

---

## Rules

- Do not synthesise or analyse — this is capture, not review
- Do not create new tags without flagging to the user
- If the date is uncertain, note it explicitly with *[Date approximate]*
- If the input is very long (multiple distinct moments or topics), split into separate dated entry blocks and flag this to the user
- Keep processing light — the weekly skill is where synthesis begins

---
