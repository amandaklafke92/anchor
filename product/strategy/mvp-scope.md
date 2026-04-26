# Anchor — MVP Scope

What is in, what is explicitly out, and what is still being decided.

---

## In scope (MVP)

**Capture methods**
- Record voice (live recording)
- Upload voice note (import audio file → transcription)
- Type it out
- Upload a note (handwriting or digital — OCR → transcription)

**Processing**
- Audio transcription
- OCR for handwritten/uploaded notes
- Rendering: transcript → clean journal entry (see rendering-rules.md for fidelity rules)
- User can review and edit transcript and/or journal entry before saving

**Storage**
- One place for all entries regardless of input type
- Transcript stored as source of truth alongside journal entry
- Plain markdown format
- TBD: cloud storage provider (see decisions.md)

**Review**
- Monthly review (basic)
- Reason: forces good system design early; introduces the aggregation layer; foundation for yearly

**Search / retrieval**
- By date
- By input type
- Possibly by tag (if AI tagging ships)

---

## Explicitly out of MVP

- Yearly review
- Photo integration
- Shorthand dictionary
- Keyword / full-text search
- Vector search
- Manual tag selection upfront

---

## Unresolved (needs decision before build)

- AI tagging: ships in MVP or deferred entirely? (see decisions.md)
- Storage architecture: user's cloud vs Anchor-hosted (see decisions.md)
- Audio preservation: store or discard after transcription? (see decisions.md)
- Cloud sync implementation approach

---

## Core value of MVP

Capture across formats. Convert messy input into clean, usable text. Store everything in one place.

---

## Shipping

"Released" means: a working app with the MVP feature set above, stable enough to give to real users.

When you're ready to ship, the process on GitHub is:
1. Tag a commit with a version number (e.g. `v1.0`) — this is called a Release
2. GitHub's Releases feature (right-hand sidebar of the repo) lets you write release notes and attach the installable file
3. Users can browse all past releases and download any version

You don't need individual version files or a separate changelog. GitHub handles the version history. Write the release notes in plain language — what's new, what's fixed — aimed at users, not developers.
