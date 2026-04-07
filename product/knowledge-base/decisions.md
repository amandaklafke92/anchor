# Anchor — Decision Log

Each entry: the decision, what was considered, why we landed here, and status.

Status options: `decided` · `deferred` · `open`

---

## Monthly file attribution

**Status: open**

Which weekly files feed into a monthly summary?

Weekly files are defined by their Monday start date, but a week can span two months. A monthly summary for March might need to include a week that started in March but ends in April — or exclude a week where most days were in March if its Monday fell in February.

Options to decide between:
- All weeks whose Monday falls in that month (consistent with how weeks are named, but could exclude entries from late in a month)
- All weeks that contain at least one day in that month (risks a week appearing in two monthlies)
- All weeks where the majority of days fall in that month

This affects edge cases in the monthly skill, particularly at month boundaries. Needs a decision before the skill can handle these reliably.

---

## Audio preservation

**Status: deferred**

Whether to store the original audio file after transcription.

Considered:
- Storing audio allows cross-checking transcript quality
- Not storing reduces storage cost and complexity
- Modern transcription quality is likely sufficient to not need the source file
- "Upload" as a button label implies storage — if audio is not kept, label needs to change (e.g. "Import")

Leaning toward: do not store audio by default. Decision blocked on storage architecture.

---

## Storage architecture

**Status: deferred**

Where journal entries live and who owns the storage layer.

Considered:
- Local device storage: honours data ownership principle but doesn't support cross-device access; phones are cloud-first, users don't manage local files
- Anchor-hosted cloud: simplest to implement, but requires users to trust Anchor with personal writing; different product commitment
- User's own cloud (iCloud, Google Drive, Dropbox): satisfies cross-device access AND the vision's data ownership principle — user's data stays in their account, in an open format

Leaning toward: sync to user's own cloud storage. Decision pending implementation research.

VISION.md reference: "data lives on your own device or cloud account, as a plain markdown file."

---

## Tagging (MVP)

**Status: decided — 2026-04-07**

Tags are AI-generated post-processing, not manually selected upfront. If AI tagging cannot ship in MVP, tags do not appear at all — manual pre-selection is the wrong UX and creates a dumping ground problem.

Reasoning: tags get unmanageable quickly without structure. AI-chosen tags over a controlled vocabulary is the right model. Vector search may eventually reduce the need for tags entirely.

Excluded from MVP:
- Manual tag selection
- Vector search (unresolved complexity)
