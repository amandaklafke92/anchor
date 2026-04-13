# Anchor — Plugin Development Context

Anchor is a Cowork plugin that gives Claude two journaling skills: daily capture and monthly reflection. Entries are stored as plain markdown files in a user-specified folder.

**Core design principle:** text records should reconstruct lived experience, not summarise it.

---

## Repo structure

```
anchor/
├── plugin/              # The plugin bundle — what users install
│   ├── skills/
│   │   ├── daily/SKILL.md
│   │   └── monthly/SKILL.md
├── product/             # Product development work (not part of the plugin)
│   ├── strategy/        # Specs, decisions, and working principles
│   ├── user-flows/      # User flow documentation and prototype screenshots
│   └── designs/         # Figma exports and wireframes
├── logs/                # Session logs
├── archive/             # Archived files
├── decisions-system.md  # System design decision log — check here before README when a structural question arises
├── VISION.md
└── README.md
```

---

## Decision logs

- `decisions-system.md` — confirmed design decisions for file structure, metadata, and workflow. The most granular record.
- `product/strategy/decisions-product.md` — product and feature decisions: what to build, defer, or rule out.

At the end of any product or system work session, check whether decisions were made or surfaced and prompt Amanda to log them if not already captured.

---

## Skill development conventions

Each skill lives in its own folder with a single `SKILL.md` file. Skills are written as plain instructions Claude reads at the start of a task. Skills are self-contained — all rules, structures, and conventions live within the skill file itself.

When writing or modifying skills:
- Read `decisions-system.md` before making changes — it is the authoritative record of current system design
- Preserve the user's voice in all entry handling — do not paraphrase or smooth out content
