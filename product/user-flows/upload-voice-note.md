# User flow: Upload voice note

## 1. Core outcome

When a user uploads a voice note, the minimum successful outcome is that it becomes an editable transcript, which then gets rendered as a journal entry.

The journal entry must closely approximate the transcript, preserving the user's voice and wording. A transcript is also stored alongside the journal entry as the source of truth.

For cleanup and fidelity rules, see: [`../knowledge-base/rendering-rules.md`](../knowledge-base/rendering-rules.md)

---

## 2. Must the user review before saving?

The user may optionally review and edit the journal entry and/or transcript before saving.

---

## 3. Preservation priority

The decision on whether to preserve audio depends on transcription quality.

- If transcription is reliable → audio may not need to be stored
- If not → audio likely needs to be preserved
- Concern: storage cost + user expectation (upload implies storage)
- If audio is not stored, this must be made explicit to users

> **Status: deferred.** Storage and audio preservation decisions are linked to the broader storage architecture question. See decision log when created.

---

## 4. Post-save behaviour

After saving, the user is returned to the home (capture) screen.

Flow:
1. User reviews journal entry
2. Reviews AI-suggested tags
3. Clicks save
4. Sees confirmation message
5. Redirected to home

---

## 5. Tags (MVP)

After processing, the system suggests tags using AI. Tags are not pre-shown for manual selection — they are AI-generated post-processing and presented for the user to confirm or deselect.

Open question: whether AI tagging ships in the MVP or is deferred. If deferred, tags do not appear at all in the MVP.

---

## 6. Search (MVP)

In the MVP, users must be able to retrieve entries by:

- Date
- Input type
- Possibly tags

Not prioritised for MVP:
- Keyword search (unclear implementation complexity)

---

## 7. Storage philosophy

> **Status: deferred.** Cloud vs local storage, and whose cloud, is an open architectural decision. User experience and cross-device access are priorities. Data ownership principle from VISION.md still applies.

---

## 8. Reviews (MVP)

The product includes a basic monthly review in the MVP.

Reason:
- Forces better system design early
- Introduces aggregation layer (daily → monthly)
- Sets foundation for future yearly reviews

---

## 9. Core value of the MVP

- Capturing across formats
- Converting messy input into clean, usable text
- Storing everything in one place

Future:
- Deeper insight through review layers (monthly → yearly)

---

## 10. Explicit exclusions (MVP)

Excluded:
- Yearly review
- Photo integration
- Shorthand dictionary

Unresolved / needs decision:
- AI tagging
- Vector search
- Cloud sync
- Audio preservation
