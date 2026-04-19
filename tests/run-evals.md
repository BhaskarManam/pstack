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

### Step 2 — PRD eval

```
/prd
```

Use inputs from `tests/fixtures/focus-timer/seed-vision.md` when prompted.
Verify `02-prd.md` against `tests/golden/prd.expected.yaml`.

### Step 3 — Design brief eval

```
/design-brief
```

Verify `03-design-brief.md` against `tests/golden/design-brief.expected.yaml`.

### Step 4 — Critique gap detection

Copy `tests/fixtures/gapped-prd.md` to `pstack-workspace/focus-timer/02-prd.md`, then:

```
/critique pstack-workspace/focus-timer/02-prd.md
```

Expected: critique surfaces the missing success metric section. If it doesn't flag this, the rubric or critique skill needs attention.

### Step 5 — Persona differentiation check

Run on the same PRD:

```
/cagan-review pstack-workspace/focus-timer/02-prd.md
/lenny-review pstack-workspace/focus-timer/02-prd.md
```

Manually verify the two review files in `reviews/` are substantively different (>60% unique content).

## Regression baseline

After a clean run, save the output hashes:

```sh
md5 pstack-workspace/focus-timer/00-vision.md
md5 pstack-workspace/focus-timer/02-prd.md
md5 pstack-workspace/focus-timer/03-design-brief.md
```

If hashes change significantly on re-run without intent, investigate prompt drift in the relevant skill.
