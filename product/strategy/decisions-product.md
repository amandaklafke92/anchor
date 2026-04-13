---
project: Anchor
doc_type: decision-log
domain: product
last_updated: 2026-04-13
status: active
purpose: >
  Records product and feature decisions for Anchor — what to build, what to defer,
  and what was ruled out and why. Written for AI collaborators. Read when a product
  scope or feature question arises. For system design decisions (file structure,
  metadata, workflow), see decisions-system.md.
read_when: product scope question arises, feature prioritisation, onboarding with no prior context
---

# Anchor — Product Decision Log

Status options: `decided` · `deferred` · `open`

---

## Interface Strategy

**Status: decided — 2026-04**

Do not build a custom interface yet. Do not piggyback on an existing app. Complete the automation layer (formatting, tagging, synthesis) first. Revisit interface when usage patterns are stable.

Context: target user is non-technical and has never heard of frontmatter. Anchor must feel like zero setup.

Core value stack (what Anchor must deliver):
1. Frictionless capture
2. Consistent formatting + tagging
3. Scheduled synthesis (monthly/yearly)
4. Searchable retrieval
5. User-owned data

Options evaluated:

**Apple Notes** — familiar, syncs across devices, supports data ownership. But contributes nothing to items 2–4; still requires building everything else. Not a real simplification.

**Obsidian** — structured markdown, plugin ecosystem, data ownership. But target user is not the Obsidian user. Wrong audience fit.

**WhatsApp** — universal install, zero friction, supports voice/photo/text. But WhatsApp Business API requires verified business account + dedicated number + paid provider (e.g. Twilio); messages pass through Meta servers, violating data ownership principle.

Key insight: capture is already solved (talking to Claude). The bottleneck has never been capture UI — it is the automation pipeline. No existing app addresses that. Interface is a distraction until the backend works.

> Principle: solve formatting, tagging, and synthesis automation first. Then design the front door.

---

## Tagging (MVP)

**Status: decided — 2026-04-07**

Tags are AI-generated post-processing, not manually selected upfront. If AI tagging cannot ship in MVP, tags do not appear at all — manual pre-selection is the wrong UX and creates a dumping ground problem.

Reasoning: tags get unmanageable quickly without structure. AI-chosen tags over a controlled vocabulary is the right model. Vector search may eventually reduce the need for tags entirely.

Excluded from MVP:
- Manual tag selection
- Vector search (unresolved complexity)

---

## Storage Architecture

**Status: deferred**

Where journal entries live and who owns the storage layer.

Options considered:
- **Local device storage** — honours data ownership principle but doesn't support cross-device access; phones are cloud-first, users don't manage local files
- **Anchor-hosted cloud** — simplest to implement, but requires users to trust Anchor with personal writing; different product commitment
- **User's own cloud (iCloud, Google Drive, Dropbox)** — satisfies cross-device access AND the vision's data ownership principle; user's data stays in their account, in an open format

Leaning toward: sync to user's own cloud storage. Decision pending implementation research.

VISION.md reference: "data lives on your own device or cloud account, as a plain markdown file."

---

## Audio Preservation

**Status: deferred**

Whether to store the original audio file after transcription.

Options considered:
- Storing audio allows cross-checking transcript quality
- Not storing reduces storage cost and complexity
- Modern transcription quality is likely sufficient to not need the source file
- "Upload" as a button label implies storage — if audio is not kept, label needs to change (e.g. "Import")

Leaning toward: do not store audio by default. Decision blocked on storage architecture (above).

---

## Monthly File Attribution

**Status: open**

Which weekly files feed into a monthly summary? (Note: weekly files have since been dropped — this question now applies to which *entry files* are included in a monthly synthesis.)

Weekly files were defined by their Monday start date, but a week spans two calendar months at boundaries. A monthly synthesis for March might need to include entries from a week that started in March but ends in April.

Options:
- All entries whose `date:` field falls within the calendar month (cleanest; consistent with how entry YFM works)
- All entries from weeks whose Monday falls in that month (risks excluding late-month entries)
- All entries from weeks where the majority of days fall in that month

Current approach in the monthly skill: read all entries whose `date:` field falls within the target calendar month. Needs explicit confirmation before treating as settled.
