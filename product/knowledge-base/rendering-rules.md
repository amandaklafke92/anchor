# Rendering rules

## Core principle: fidelity

The rendered journal entry must preserve the original meaning of the source text (including transcribed audio, OCR from handwritten notes, or typed input). No new ideas, interpretations, or shifts in intent may be introduced. The level of intervention may vary based on the presence of noise or errors in the source text (e.g. disfluencies, transcription errors, OCR mistakes), but must not alter meaning in any case.

---

## What the system is allowed to do

- Remove filler words (e.g. "um", "like", "you know")
- Fix grammar and punctuation
- Merge or split sentences for clarity
- Lightly reorder phrasing for readability — only if meaning is provably unchanged

For "lightly reorder phrasing": if there is any doubt about whether the reorder changes meaning or emphasis, do not reorder. Preserve the original sequence.

---

## What the system is NOT allowed to do

- Add new information or ideas
- Change the meaning or intent
- Infer emotions or motivations not explicitly stated
- Summarise (this belongs in a separate section)
- Guess at inaudible or unclear words — flag them instead (see below)

---

## Handling unclear or inaudible audio

If a word or phrase cannot be reliably transcribed, do not guess. Mark it with `[unclear]` in both the transcript and the rendered entry. The user can then edit before saving.

Example: "I spoke to [unclear] about the project and she said yes."

---

## Acceptable vs not acceptable

**Input (transcript):**
"I was like really tired um and I didn't want to go but I went anyway and it was actually good"

**Acceptable output (rendered entry):**
"I was really tired and didn't want to go, but I went anyway and it was actually good."

**Not acceptable output:**
"I was hesitant at first but ended up enjoying the experience."
→ introduces interpretation and removes original phrasing

---

## Transcript visibility

- The transcript is hidden by default
- A visible "View transcript" option is always available
- Users can edit the transcript
- Users can regenerate the journal entry after edits
