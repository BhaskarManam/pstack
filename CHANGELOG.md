# pstack changelog

All notable changes to pstack are documented here.
Format: [Semantic Versioning](https://semver.org/).

---

## v0.2.1 — 2026-06-05

### Added
- **`/ravi-review`** — Ravi Mehta's lens: 12 product competencies (execution, customer insight, strategy, influence), outcome accountability over output, product strategy stack coherence, NCT goal clarity. WebSearch-grounded from ravi-mehta.com and Reforge Blog.
- **`/julie-review`** — Julie Zhuo's lens: problem-first thinking (the three questions), intentionality as the hallmark of quality, simplicity as discipline, user outcomes before feature specs. WebSearch-grounded from The Making of a Manager and The Year of the Looking Glass.
- **`/north-star`** — Optional, per-product metric design session. Produces a full metric tree: one North Star Metric + 3–5 inputs with causal story + guardrail metrics + operationalization table. Does not advance project state (like `/opportunity`).
- `knowledge/frameworks/ravi-mehta-product-excellence.md` (WebSearch-grounded)
- `knowledge/frameworks/julie-zhuo-design-leadership.md` (WebSearch-grounded)
- `knowledge/rubrics/north-star.yaml` (5 dimensions: NSM quality, inputs, tree coherence, guardrails, operationalization)
- Two north-star calibration artifacts (score-2, score-5)
- Golden shape contract `tests/golden/north-star.expected.yaml`
- 19 skills total (was 16). `setup` symlinks all three new skill dirs.

---

## v0.2.0 — 2026-06-04

### Added
- **`/strategy`** — the gated "missing middle" between vision and PRD (slot `01-strategy.md`). Produces a focused bet (with an explicit won't-do list), segment & sequencing, the insight, and the success definition (North Star + inputs + guardrail). Grounded in Cagan's product strategy (focus / insights / actions / management).
- **`/opportunity`** — optional, per-bet discovery assessment (`opportunity-<bet>.md`). Pressure-tests one strategic bet against the four risks, names the riskiest assumption + smallest viable test + kill criteria. Gates nothing; does not change project state.
- `knowledge/frameworks/cagan-product-strategy.md` (WebSearch-grounded from SVPG)
- `knowledge/rubrics/strategy.yaml` + `knowledge/rubrics/opportunity.yaml`
- Six calibration artifacts (strategy + opportunity × score-2 / 3.5 / 5)
- Golden shape contracts `tests/golden/strategy.expected.yaml` + `opportunity.expected.yaml`

### Changed
- **`/prd` now gates on strategy ≥ 2.5** (was vision ≥ 2.5). The PRD specs a bet the strategy has already chosen, and its success metrics inherit from the strategy's success definition.
- `/vision` now suggests `/strategy` as the natural next step.
- State machine adds `DRAFT_STRATEGY` / `STRATEGY_DONE` between `VISION_DONE` and `DRAFT_PRD` (`artifact-meta.schema.json`, `last-session.schema.md`).
- `/critique`, `/challenge`, `/pstack-status`, `/pstack-help` updated to recognize the new artifacts and states.
- 16 skills total (was 14). `setup` symlinks both new skill dirs.

---

## v0.1.0 — 2026-04-22

### Added
- Dual distribution: gstack-style install (`./setup` + symlinks) and `.claude-plugin` format
- 14 skills: vision, prd, design-brief, critique, cagan-review, shreyas-review, lenny-review, bhaskar-review, challenge, onboard, pstack-status, pstack-upgrade, pstack-help, pstack-learn
- Two-tier CLAUDE.md memory (user-level identity + project-level pstack commands)
- Five architecture pillars: context persistence, knowledge quality, skill design patterns, autonomy, performance
- Internal draft→critique→revise quality loop in every generator skill
- Structured YAML schemas for personas, rubrics, challenges, user-profile, artifact-meta
- Knowledge calibration sets (score-2 / score-3.5 / score-5) per artifact type
- `knowledge/INDEX.md` for lazy-loading framework files
- `~/.config/pstack/` global state (user-profile.yaml, last-session.md, quality-log.yaml)
- `CONVERSATIONS.md` + `./publish-docs` privacy pipeline
- `CHALLENGES.md` per-project (gitignored by default)
- `ROADMAP.md` and `CONVERSATIONS.md` as living memory docs
- Eval harness skeleton in `tests/`
