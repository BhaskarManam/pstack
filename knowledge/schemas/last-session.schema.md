---
name: last-session-write-pattern
description: Template and write instructions for ~/.config/pstack/last-session.md — written by every skill at completion; read by /pstack-help on session start
type: schema
version: "0.1"
---

# last-session.md write pattern

Every pstack skill writes this file at the end of its run. It is always **overwritten**, never appended. `/pstack-help` reads it at session start to surface the correct next action without requiring the user to recap.

## File location

`~/.config/pstack/last-session.md`

Create the directory if it does not exist: `~/.config/pstack/`

---

## Template

```markdown
# Last pstack session — {ISO_DATE}

**Skill:** {skill-name}
**Project:** {project-name} (`{slug}`)
**Working directory:** {absolute-path}

**What happened:**
{1–3 sentence summary. For generators: what artifact was written and its score. For reviewers: which artifact was reviewed and the key finding. For meta skills: what the skill did.}

**Artifact:** {filename} (score: {score}/5.0) — omit score line for meta and reviewer skills; reviewer skills use "Review written: {review-filename}"
**State:** {state-machine-state}

**Suggested next:**
- Primary: {next-skill} — {one-line reason}
- Alternative: {alternative-skill or action} — {one-line reason}

**Open loops:**
{Bulleted list of unresolved decisions, flags raised during the run, or "none". Always list Bhaskar persona.yaml user-review flag if Phase 8 has not yet occurred.}

**Key decisions made this run:**
{Bulleted list of significant choices the user confirmed, or "none".}
```

---

## Field-by-field rules

| Field | Source | Rule |
|---|---|---|
| ISO_DATE | Current datetime | UTC format: `YYYY-MM-DDThh:mmZ` |
| skill-name | Hardcoded per skill | `/vision`, `/prd`, `/cagan-review`, etc. |
| project-name | `.pstack-meta.json → project.name` | Fall back to current directory name if not found |
| slug | `.pstack-meta.json → project.slug` | kebab-case; fall back to `unknown` |
| absolute-path | Working directory | Full absolute path |
| What happened | Generated narrative | Concise — never more than 3 sentences |
| Artifact | Filename + score | Generators only. Score = post-revision rubric score. Reviewers write their output path instead |
| State | `.pstack-meta.json → project.state` | Reflect state **after** this skill's update |
| Suggested next | State machine table below + context | Always at least one primary, one alternative |
| Open loops | Items raised this run | Track unresolved AskUserQuestion answers, deferred decisions |
| Key decisions | User inputs captured | Only decisions with lasting consequence — skip routine answers |

---

## State → next-skill mapping

Skills use this table to populate "Suggested next." If no `.pstack-meta.json` exists, state is `NO_PROJECT`.

| State | Primary next | Alternative |
|---|---|---|
| `NO_PROJECT` | `/onboard` to set up the project | `/vision` to start directly |
| `DRAFT_VISION` | `/vision` (continue) | `/cagan-review` for early risk scan on draft |
| `VISION_DONE` | `/strategy` | `/cagan-review` or `/shreyas-review` on the vision |
| `DRAFT_STRATEGY` | `/strategy` (continue) | `/critique` to score the current draft |
| `STRATEGY_DONE` | `/prd` | `/opportunity` to pressure-test a risky bet; `/cagan-review` on the strategy |
| `DRAFT_PRD` | `/prd` (continue) | `/critique` to score the current draft |
| `PRD_DONE` | `/design-brief` | `/cagan-review`, `/lenny-review`, or `/shreyas-review` on the PRD |
| `DRAFT_BRIEF` | `/design-brief` (continue) | `/critique` on the brief draft |
| `BRIEF_DONE` | `/cagan-review` on the brief | `/challenge` for today's CEO/CPO provocation |
| `(any)` | `/challenge` for the daily provocation | `/pstack-status` for a cross-project dashboard |

---

## Skill-type examples

### Generator example (after /prd)

```markdown
# Last pstack session — 2026-04-19T15:30Z

**Skill:** /prd
**Project:** Focus Timer (`focus-timer`)
**Working directory:** /Users/manam/Projects/focus-timer

**What happened:**
Drafted PRD for "Session Start & Intention Flow v1." Internal critique scored draft 3.2/5 (weak success metrics); revised to 4.1/5 before surfacing. User confirmed scope and accepted the artifact.

**Artifact:** 02-prd.md (score: 4.1/5.0)
**State:** PRD_DONE

**Suggested next:**
- Primary: /design-brief — PRD is ready; design brief translates the PRD into UX direction
- Alternative: /cagan-review — four-risk analysis before committing to design

**Open loops:**
- Viability risk (monetization model) deferred — user said "TBD for now"
- Bhaskar persona.yaml: show to user mid-Phase-8 for approval before writing SKILL.md

**Key decisions made this run:**
- Scope: session start flow only (not history or analytics) in v1
- Target segment: solo founders and indie builders (not enterprise teams)
```

### Reviewer example (after /cagan-review)

```markdown
# Last pstack session — 2026-04-19T17:00Z

**Skill:** /cagan-review
**Project:** Focus Timer (`focus-timer`)
**Working directory:** /Users/manam/Projects/focus-timer

**What happened:**
Reviewed 02-prd.md through Marty Cagan's four-risk lens. Usability risk flagged as under-addressed — no user testing planned before engineering handoff. Value risk and feasibility risk rated adequate.

**Review written:** pstack-workspace/focus-timer/reviews/2026-04-19-cagan-review.md
**State:** PRD_DONE

**Suggested next:**
- Primary: /design-brief — address usability risk by adding prototype-test step in the brief
- Alternative: /shreyas-review — execution quality check before moving to design

**Open loops:**
- Usability risk: plan a prototype test before engineering handoff (flagged in review)

**Key decisions made this run:**
- none
```

### Meta example (after /pstack-help)

```markdown
# Last pstack session — 2026-04-19T09:00Z

**Skill:** /pstack-help
**Project:** Focus Timer (`focus-timer`)
**Working directory:** /Users/manam/Projects/focus-timer

**What happened:**
Read prior session context. PRD_DONE state with one open viability-risk loop. Recommended /design-brief as primary next action.

**Artifact:** none
**State:** PRD_DONE

**Suggested next:**
- Primary: /design-brief — natural next step from PRD_DONE
- Alternative: /cagan-review — four-risk review before committing to design direction

**Open loops:**
- Viability risk (monetization) still deferred

**Key decisions made this run:**
- none
```
