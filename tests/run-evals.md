# Running pstack evals

## Prerequisites

- pstack installed (Path A or Path B)
- A scratch directory with no existing `pstack-workspace/`

## Eval procedure

Open Claude Code in a scratch directory and run each step:

### Step 1 — Vision eval

```
/vision
```

When prompted, use the inputs from `tests/fixtures/focus-timer/seed-idea.md`.

After completion, verify the output at `pstack-workspace/focus-timer/00-vision.md` against `tests/golden/vision.expected.yaml`:
- All `required_sections` present (grep for each heading)
- Word count ≥ `min_word_count`
- References at least one of `must_reference` framework files
- `rubric_score` in `.pstack-meta.json` ≥ `rubric_floor_score`

### Step 2 — Strategy eval

```
/strategy
```

Runs on the `00-vision.md` produced in Step 1 (gate: vision ≥ 2.5).
Verify `01-strategy.md` against `tests/golden/strategy.expected.yaml`:
- All `required_sections` present, including an explicit "won't-do" list under "The bet"
- `state_after` is `STRATEGY_DONE`

### Step 3 — Opportunity eval (optional path)

```
/opportunity
```

Runs on `01-strategy.md` (gate: strategy ≥ 2.5). Pick one bet when prompted.
Verify `opportunity-<bet>.md` against `tests/golden/opportunity.expected.yaml`:
- The project `state` is **unchanged** (still `STRATEGY_DONE`) — opportunity is a side artifact
- Confirm `/prd` still runs whether or not this step was performed (opportunity gates nothing)

### Step 4 — PRD eval

```
/prd
```

Runs on `01-strategy.md` (gate: **strategy** ≥ 2.5, not vision).
Verify `02-prd.md` against `tests/golden/prd.expected.yaml`. Confirm the PRD's success metrics descend from the strategy's success definition.

### Step 5 — Design brief eval

```
/design-brief
```

Verify `03-design-brief.md` against `tests/golden/design-brief.expected.yaml`.

### Step 6 — Critique gap detection

Copy `tests/fixtures/gapped-prd.md` to `pstack-workspace/focus-timer/02-prd.md`, then:

```
/critique pstack-workspace/focus-timer/02-prd.md
```

Expected: critique surfaces the missing success metric section. If it doesn't flag this, the rubric or critique skill needs attention.

### Step 7 — North Star eval (optional path)

```
/north-star
```

Runs on the `00-vision.md` or `01-strategy.md` context. Produces `north-star-<slug>.md`.
Verify against `tests/golden/north-star.expected.yaml`:
- All `required_sections` present
- State is **unchanged** (same as before running — `/north-star` is optional, like `/opportunity`)
- Guardrail metrics section is present with at least one threshold

### Step 8 — Persona differentiation check

Run on the same PRD:

```
/cagan-review pstack-workspace/focus-timer/02-prd.md
/ravi-review pstack-workspace/focus-timer/02-prd.md
/julie-review pstack-workspace/focus-timer/02-prd.md
/lenny-review pstack-workspace/focus-timer/02-prd.md
```

Manually verify the four review files in `reviews/` are substantively different (>50% unique content per pair). Ravi's review should feature a competency gap scan table. Julie's should open with the three product questions check. Cagan's should lead with four risks.

## Regression baseline

After a clean run, save the output hashes:

```sh
md5 pstack-workspace/focus-timer/00-vision.md
md5 pstack-workspace/focus-timer/01-strategy.md
md5 pstack-workspace/focus-timer/02-prd.md
md5 pstack-workspace/focus-timer/03-design-brief.md
```

If hashes change significantly on re-run without intent, investigate prompt drift in the relevant skill.
