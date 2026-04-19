# pstack — Claude Code project context

This is the **pstack repository** — a Claude Code skill pack being actively built.

> You are working ON pstack (building it), not WITH pstack (using it to build a product).
> To use pstack skills on a real product, open a different project directory.

---

## What pstack is

A gstack-style Claude Code skill pack: Vision → PRD → Design brief, with persona-driven reviews, daily CEO/CPO challenges, and a self-improving knowledge engine. 14 skills total. Dual distribution: `./setup` (gstack-style) + `.claude-plugin`.

## Current build phase

**Phase 0 complete** (committed c2179ac). **Phase 0a is next:** `/onboard` skill.

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
skills/          → 14 skill directories (build one at a time)
knowledge/
  INDEX.md       → lazy-loading reference (build in Phase 0b)
  frameworks/    → distilled product-leader canon (Phase 0b)
  rubrics/       → YAML rubrics (Phase 0b)
  calibration/   → scored reference artifacts (Phase 0b)
  challenges/    → CEO/CPO provocation bank (Phase 9)
  schemas/       → all 5 schemas (Phase 0 ✓)
feedback/        → per-skill user feedback logs (gitignored on user's side)
tests/           → eval harness with fixtures and golden contracts (Phase 0 ✓)
```

## What NOT to do

- Don't skeleton all skills at once — build one completely, verify, advance
- Don't write framework files without WebSearch grounding from the originator's public work
- Don't surface sub-par generator output — the internal critique loop handles it invisibly
- Don't commit CONVERSATIONS.md (gitignored); run ./publish-docs for the public version
