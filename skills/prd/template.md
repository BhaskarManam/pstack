# PRD: {Product Name} — {Slice Name} v1.0

**Based on:** `00-vision.md` v1.0
**Platform:** {platform}
**PM:** {name} | **Eng lead:** {name} | **Design lead:** {name}
**Status:** Draft | **Target:** {YYYY-Qn}

---

## Context & hypothesis

**Problem slice:** {one sentence — the specific user need this PRD addresses within the broader vision}

**Hypothesis:**
> We believe **{specific user}** will **{specific behavior}** because **{specific mechanism}**, and we'll know we're right when **{measurable outcome}** moves from **{baseline}** to **{target}** within **{timeframe}**.

**Falsification condition:** {explicit statement of what evidence would prove this hypothesis wrong}

---

## User stories & acceptance criteria

### Story 1: {name}

**As a** {user}, **I want to** {action} **so that** {outcome}.

| Given | When | Then |
|---|---|---|
| {precondition} | {user action} | {measurable, testable result} |
| {edge case precondition} | {edge case action} | {edge case result} |

### Story 2: {name}

**As a** {user}, **I want to** {action} **so that** {outcome}.

| Given | When | Then |
|---|---|---|
| {precondition} | {user action} | {measurable, testable result} |

### Story 3: {name}

**As a** {user}, **I want to** {action} **so that** {outcome}.

| Given | When | Then |
|---|---|---|
| {precondition} | {user action} | {measurable, testable result} |

---

## Scope

**In scope (v1):**
- {feature or behavior 1}
- {feature or behavior 2}
- {feature or behavior 3}

**Out of scope:**

| Not in v1 | Why |
|---|---|
| {thing 1} | {rationale — wrong user, wrong moment, wrong phase} |
| {thing 2} | {rationale} |

---

## Success metrics

| Metric | Type | Baseline | Target | Timeframe |
|---|---|---|---|---|
| {primary outcome metric} | outcome / leading | {baseline} | {target} | {timeframe} |
| {secondary metric} | outcome / lagging | | | |
| {guardrail metric} | guardrail | | | |

**Segment interpretation:** {how metrics are cut — e.g., "measure only users who completed onboarding; exclude internal test accounts"}

---

## Risks & assumptions (Cagan)

| Risk type | Description | Level | Discovery action |
|---|---|---|---|
| **Value** | {Will target users want this enough to change behavior?} | High / Med / Low | {how to validate before build} |
| **Usability** | {Can users accomplish the core task without guidance?} | | |
| **Feasibility** | {Can the team build this with current capabilities in the target timeframe?} | | |
| **Viability** | {Does this work legally, financially, and ethically for the business?} | | |

---

## Open questions

| # | Question | Owner | Decision needed by |
|---|---|---|---|
| 1 | {question that must be resolved before or during build} | {PM / Eng / Design} | {milestone} |
| 2 | | | |

---

## Milestones

| Milestone | Definition of done | Target |
|---|---|---|
| Discovery complete | {criteria — e.g., "3 user interviews validate value risk"} | |
| Design handoff | {criteria} | |
| Engineering handoff | {criteria} | |
| Beta / internal test | {criteria} | |
| Launch | {criteria} | |
