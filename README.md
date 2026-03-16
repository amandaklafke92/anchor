# Anchor

A personal memory system for Claude that helps you capture and synthesise lived experience — daily entries, weekly reviews, and monthly reflections.

Anchor is built around a single design principle: **text records should reconstruct lived experience, not summarise it.** Every formatting and synthesis decision in the plugin serves that goal.

---

## What it does

Anchor gives Claude three skills:

**Daily capture** — paste in a voice transcript, typed notes, or anything from the day. Claude formats it as a dated journal entry, suggests tags, and files it in the correct weekly file. If the weekly file doesn't exist yet, it creates it.

**Weekly synthesis** — at the end of the week, Claude reads all your daily entries and compiles a complete weekly file: people, places, themes, highlights, and a short written summary.

**Monthly reflection** — at the end of the month, Claude reads all your weekly files and writes a monthly summary with concrete memory anchors (specific enough to reconstruct a moment two years later), threads to carry forward, and dominant tags. Written in second person, so it reads like a letter back to you.

---

## Installation

1. Download `anchor.plugin` from this repo
2. Open Cowork and go to **Plugins**
3. Drag in the `.plugin` file or use the install option
4. Point Cowork at the folder where you want your journal files to live

No external services or API keys required. Everything runs locally on your files.

---

## Usage

Once installed, trigger each skill by saying:

| Skill | Trigger phrases |
|-------|----------------|
| Daily capture | "add entry", "log this", "daily capture", "new entry" |
| Weekly synthesis | "do my weekly", "weekly synthesis", "wrap up the week" |
| Monthly reflection | "monthly review", "monthly synthesis", "end of month" |

---

## File naming convention

All journal files follow the pattern `YYYY-MM_mmm_[type]-[DD].md`, e.g.:

- `2026-03_mar_week-16.md`
- `2026-03_mar_monthly.md`

This keeps files sorted chronologically and grouped by month in any file browser.

---

## Plugin contents

```
anchor/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   ├── daily/
│   │   └── SKILL.md
│   ├── weekly/
│   │   └── SKILL.md
│   └── monthly/
│       └── SKILL.md
├── references/
│   └── anchor-context.md
└── README.md
```

---

## How the weekly and monthly skills behave

The weekly synthesis skill is designed to run on a schedule. Before it does anything, it checks whether there are unsynthesised daily entries in the current weekly file — if there aren't, it stops without consuming any processing. This means you can schedule it to run automatically without worrying about it firing unnecessarily.

At the end of each month, the weekly skill also checks whether a monthly summary exists for the current month. If it doesn't, and you're within the last 7 days of the month, it will prompt you to run the monthly reflection — so nothing gets missed without being heavy-handed about it.

---

## Built with

[Claude Cowork](https://claude.ai) — a desktop tool for knowledge work automation built on Claude.
