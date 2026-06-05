# pstack eval harness

This directory contains fixtures and golden snapshots for structural eval of pstack generator skills.

## What these evals test

These are **structural smoke tests**, not LLM quality evals. They verify:
- Required sections are present in generator output
- Minimum word count is met
- The skill references the correct framework files
- The internal rubric score meets the passing floor

They do NOT verify the quality of the prose. That requires human judgment and `/critique`.

## Running evals

Evals run from inside Claude Code. Open a Claude Code session in your project directory and follow the procedure in [run-evals.md](run-evals.md).

## Directory structure

```
tests/
├── fixtures/
│   ├── focus-timer/
│   │   ├── seed-idea.md          # Minimal one-paragraph idea to feed /vision
│   │   └── seed-vision.md        # A known-good vision to feed /prd
│   └── gapped-prd.md             # Deliberately flawed PRD for /critique testing
└── golden/
    ├── vision.expected.yaml      # Shape contract for /vision output
    ├── strategy.expected.yaml    # Shape contract for /strategy output
    ├── opportunity.expected.yaml # Shape contract for /opportunity output (optional, per-bet)
    ├── prd.expected.yaml         # Shape contract for /prd output
    └── design-brief.expected.yaml
```

## Adding a new fixture

1. Create `tests/fixtures/<project>/seed-idea.md`
2. Run the generator skill on it
3. If output is high quality, promote to `tests/fixtures/<project>/seed-<artifact>.md`
4. Update the corresponding `tests/golden/<artifact>.expected.yaml` if the contract should change
