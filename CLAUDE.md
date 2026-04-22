# pstack — Claude Code project context

This is the **pstack repository** — a Claude Code skill pack being actively built.

> You are working ON pstack (building it), not WITH pstack (using it to build a product).
> To use pstack skills on a real product, open a different project directory.

---

## What pstack is

A gstack-style Claude Code skill pack: Vision → PRD → Design brief, with persona-driven reviews, daily CEO/CPO challenges, and a self-improving knowledge engine. 14 skills total. Dual distribution: `./setup` (gstack-style) + `.claude-plugin`.

## Current build phase

**Phase 0 complete** (committed c2179ac). **Phase 0a complete** (`skills/onboard/`). **Phase 0b complete** (knowledge foundation — all 7 framework files with TL;DR headers, 9 calibration files, INDEX.md, glossary.md). **Phase 0c complete** (autonomy infrastructure).

Phase 0c deliverables (all done): `last-session.md` write pattern (`knowledge/schemas/last-session.schema.md`), `quality-log.yaml` append schema (`knowledge/schemas/quality-log.schema.yaml`), `feedback/<skill>-log.yaml` schema (`knowledge/schemas/feedback-log.schema.yaml`), `feedback/README.md` + gitignore entries, `.claude/settings.json` hook (artifact-write nudge, fixed to use stdin JSON). Note: `knowledge/rubrics/` remains empty — rubric YAML files build in Phases 1–3.

**All 14 skills complete.** All SKILL.md files, persona.yaml files, templates, rubric YAMLs, and config files are built. See layout below. Next phase: testing the skills work end-to-end, then setup script updates and symlink wiring for new skills.

**Bhaskar persona review required:** `skills/bhaskar-review/persona.yaml` was built from your expressed values — review and edit before using `/bhaskar-review` in production.

Full 16-phase build plan: `/Users/parents/.claude/plans/hi-before-you-start-typed-teapot.md`
Session state: `~/.config/pstack/last-session.md`

## How to orient at the start of every session

1. Read `~/.config/pstack/last-session.md` — tells you exactly where we are
2. Check `memory/` for key decisions: `~/.claude/projects/-Users-parents-Projects-pstack/memory/`
3. Suggest the correct next build phase before doing anything else

## Build conventions

- **Quality-first, one phase at a time.** Complete and verify each phase before advancing.
- **Push back** on assumptions; propose advanced thinking; future-proof.
- **Schemas first.** All new skill types must have a schema in `knowledge/schemas/` before files are written.
- **Attribution always.** Every framework file ends with a Sources & further reading section.
- **Internal quality loop.** Every generator SKILL.md must include the draft→self-critique→revise pattern before surfacing output.
- **Lazy loading.** Skills read `knowledge/INDEX.md` first; only pull specific framework files flagged as relevant.
- **Model selection.** Use `model: claude-opus-4-7` for vision/prd/critique/reviews; `model: claude-sonnet-4-6` for design-brief.

## Key locked decisions

- Profile path: `~/.config/pstack/` (XDG)
- Challenge cadence: daily (config.yaml default)
- Attribution: curated direct quotes allowed with source + license check per quote
- License: MIT
- Bhaskar persona.yaml: show to user mid-Phase-8 BEFORE writing SKILL.md

## Repository layout (quick reference)

```
skills/
  onboard/         → /onboard ✓
  vision/          → /vision (SKILL.md + template.md) ✓
  prd/             → /prd (SKILL.md + template.md) ✓
  design-brief/    → /design-brief (SKILL.md + template.md) ✓
  critique/        → /critique ✓
  cagan-review/    → /cagan-review (SKILL.md + persona.yaml) ✓
  shreyas-review/  → /shreyas-review (SKILL.md + persona.yaml) ✓
  lenny-review/    → /lenny-review (SKILL.md + persona.yaml) ✓
  bhaskar-review/  → /bhaskar-review (SKILL.md + persona.yaml) ✓ ← USER REVIEW NEEDED
  challenge/       → /challenge (SKILL.md + config.yaml) ✓
  pstack-status/   → /pstack-status ✓
  pstack-upgrade/  → /pstack-upgrade ✓
  pstack-help/     → /pstack-help ✓
  pstack-learn/    → /pstack-learn ✓
knowledge/
  INDEX.md         → lazy-loading reference + schemas section ✓
  frameworks/      → all 7 framework files with TL;DR headers ✓
  rubrics/         → vision.yaml, prd.yaml, design-brief.yaml ✓
  calibration/     → all 9 scored reference artifacts ✓
  schemas/         → 8 schemas total (5 Phase-0 + 3 Phase-0c) ✓
  glossary.md      → key terms ✓
feedback/
  README.md        → explains feedback dir structure ✓
  *-log.yaml       → gitignored; created on first use
tests/             → eval harness with fixtures and golden contracts ✓
```

## What NOT to do

- Don't write framework files without WebSearch grounding from the originator's public work
- Don't surface sub-par generator output — the internal critique loop handles it invisibly
- Don't commit CONVERSATIONS.md (gitignored); run ./publish-docs for the public version
