# pstack knowledge index

Skills read this file first. Only pull full framework files when the `Use when` column indicates relevance to your current task. Do not load all framework files at once.

---

## Frameworks

| File | TL;DR | Use when |
|---|---|---|
| `frameworks/jtbd.md` | People hire products for a job; design for the job (functional + emotional + social), not the persona | Vision (target user section), design brief (primary flow) |
| `frameworks/north-star-metric.md` | One metric captures core customer value; teams work on input metrics that drive it—not the star itself | Vision (success picture / North Star section), PRD (success metrics) |
| `frameworks/cagan-discovery.md` | Four risks to de-risk before building: value, usability, feasibility, viability | PRD (risks & assumptions), /cagan-review |
| `frameworks/shreyas-product-sense.md` | LNO prioritization (Leverage/Neutral/Overhead); high agency; most execution problems are strategy problems | /shreyas-review, challenge (priorities lens) |
| `frameworks/lenny-growth-loops.md` | Growth = compounding loops, not linear funnels; retention is the engine, acquisition amplifies it | /lenny-review, challenge (revenue lens) |
| `frameworks/hustle-badger-indie.md` | Solo builders win via niches, leverage, and constraints-as-clarity; ship fast to learn fast | Challenge (strategy lens), /bhaskar-review |
| `frameworks/ikigai-purpose-lens.md` | Purpose = intersection of love, skill, world-need, livelihood; ikigai-aligned founders sustain longer | /bhaskar-review, challenge (reflection lens) |

---

## Rubrics

Rubric YAML files are loaded by `/critique` and all persona reviews to anchor numeric scoring. Each dimension has a weight and a 1/3/5 scale definition.

| File | Artifact type | Dimensions scored |
|---|---|---|
| `rubrics/vision.yaml` | vision | Hypothesis clarity, JTBD sharpness, North Star quality, Why now, Non-goals |
| `rubrics/prd.yaml` | prd | Hypothesis, Success metrics, Scope discipline, Risk identification, AC quality |
| `rubrics/design-brief.yaml` | design-brief | Flow clarity, Screen inventory, Constraint specificity, JTBD-to-UX translation, Accessibility |

---

## Calibration sets

Reference artifacts at known score levels. Load the calibration set for the relevant artifact type before scoring — it anchors numeric judgment and prevents score drift across sessions.

| File | Artifact | Score | Key weakness / strength |
|---|---|---|---|
| `calibration/vision-score-2.md` | vision | 2.0 | Vague JTBD, no North Star, no Why Now |
| `calibration/vision-score-3.5.md` | vision | 3.5 | Clear problem, weak North Star, thin Why Now |
| `calibration/vision-score-5.md` | vision | 5.0 | All sections sharp; JTBD + NSM + Why Now complete |
| `calibration/prd-score-2.md` | prd | 2.0 | Weak hypothesis, vanity metrics, no risks |
| `calibration/prd-score-3.5.md` | prd | 3.5 | Decent scope, but success metrics under-specified |
| `calibration/prd-score-5.md` | prd | 5.0 | Crisp hypothesis, measurable metrics, all four risks tagged |
| `calibration/design-brief-score-2.md` | design-brief | 2.0 | No primary flow, vague constraints, no JTBD link |
| `calibration/design-brief-score-3.5.md` | design-brief | 3.5 | Flow present but incomplete, constraints generic |
| `calibration/design-brief-score-5.md` | design-brief | 5.0 | Full flow, specific constraints, tight JTBD-to-UX translation |

---

## Schemas (autonomy infrastructure)

These files define write patterns and entry structures used by all generator skills. Read the relevant schema before writing to any shared state file.

| File | What it governs | Read when |
|---|---|---|
| `schemas/last-session.schema.md` | Template + rules for writing `~/.config/pstack/last-session.md` | End of every skill run (step 10 in the skill contract) |
| `schemas/quality-log.schema.yaml` | Entry structure for `~/.config/pstack/quality-log.yaml` | End of every generator run (step 11) |
| `schemas/feedback-log.schema.yaml` | Entry structure for `feedback/<skill>-log.yaml` | End of every generator run (step 12) |
| `schemas/artifact-meta.schema.json` | `.pstack-meta.json` structure (state machine + artifact list) | When reading or writing project state |
| `schemas/persona.schema.yaml` | `persona.yaml` structure for all reviewer skills | When building or running persona reviews |
| `schemas/rubric.schema.yaml` | `rubric.yaml` structure (dimensions, weights, scale) | When building rubric YAML files in Phases 1–3 |
| `schemas/user-profile.schema.yaml` | `~/.config/pstack/user-profile.yaml` structure | /onboard, /challenge, persona reviews |
| `schemas/challenge.schema.yaml` | Challenge seed entry structure | /challenge skill |

---

## Lazy-loading rules

1. Read this INDEX first.
2. Check `Use when` to identify which framework files are relevant to the current task.
3. Read only those files — do not load all of `frameworks/` into context.
4. For scoring tasks, always load the matching calibration set before producing a score.
5. The TL;DR frontmatter in each framework file is a fast-path: if it fully answers the question, you do not need to read the full file.
