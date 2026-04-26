# Anchor

Anchor is a personal journaling and life-archive system. It turns scattered notes, voice transcripts, and handwritten captures into structured Markdown records you can actually return to.

It is built on one idea: a life worth living is worth recording, and records are only useful if you can get back inside them.

## What Anchor Does

Anchor is designed around three jobs:

- **Capture:** put the memory in however it arrives: typed text, voice transcript, uploaded audio, or a photo of handwritten notes.
- **Storage:** keep every entry as plain Markdown in a folder the user controls.
- **Review:** turn structured entries into monthly reflections with concrete moments, emotional arc, and threads worth carrying forward.

For the longer product vision, read [VISION.md](VISION.md).

## Current State

Anchor currently exists as a small plugin/skills system, not a standalone app. The public repo contains the plugin, product direction, public docs, and fictional examples.

Available skills:

| Skill | What it does | Trigger phrases |
| --- | --- | --- |
| Daily capture | Formats and files a journal entry | "add entry", "log this", "daily capture", "new entry" |
| Monthly reflection | Synthesises all entries in a calendar month | "monthly review", "monthly synthesis", "end of month" |

See [plugin/README.md](plugin/README.md) for usage notes.

## Data Privacy

Do not store real journal entries in this public repo.

Real entries, monthlies, exports, and private archive material should live in a separate private folder or repository, such as `anchor-data/`. This repo intentionally includes only fictional examples under `examples/`.

The default Anchor data shape is:

```text
entries/
├── 2026-04-13.md
└── ...

monthlies/
├── 2026-04_monthly.md
└── ...
```

See [docs/data-format.md](docs/data-format.md) for the entry and monthly formats.

## Roadmap

The current product direction is a simple Now / Next / Later sequence:

- **Now:** prove the capture -> review -> save workflow.
- **Next:** add voice, audio upload, handwritten-note photo input, source preservation, and automatic storage handling.
- **Later:** add search, monthly reviews, yearly summaries, and printed life records.

See [docs/roadmap.md](docs/roadmap.md) for the public roadmap.

## Repo Structure

```text
anchor/
├── plugin/                  # Installable plugin and skills
├── docs/                    # Public product/system docs
├── examples/                # Fictional sample entries and monthlies
├── product/                 # Product strategy and design working material
├── decisions-system.md      # System design decision log
├── VISION.md                # Product vision
└── README.md
```

## Contributing

Anchor is early. Small, concrete improvements are more useful than large abstractions. Start with [CONTRIBUTING.md](CONTRIBUTING.md).
