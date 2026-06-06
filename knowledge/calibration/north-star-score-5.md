# North Star calibration — Score 5 (excellent)

**Product:** FocusTimer (productivity app for remote workers)

---

## The North Star Metric

**Weekly focused hours logged** — the total number of hours in which a user completed at least one uninterrupted focus session of 25+ minutes in a given week, across all their devices.

**Why this metric captures core value:**
A user gets core value from FocusTimer at the moment they complete a real focus session — not when they open the app, not when they set a timer, but when they finish one. Weekly focused hours captures that moment at the right frequency (weekly, because remote workers' work rhythm is weekly) and is immune to passive opens or notification-driven re-engagement that doesn't produce real work.

**What this metric is NOT:**
Not MAU, not sessions opened, not timers started. Those measure engagement with the interface; this measures delivery of the core promise: protected time for deep work.

---

## The metric tree

```
North Star: Weekly focused hours logged (per active user, median)
│
├── Input 1: Focus session completion rate
│   Why: Users who start sessions must finish them. Low completion = interruption problem or timer friction.
│
├── Input 2: Sessions per active user per week
│   Why: A single session/week is minimal. Users who build a habit log 3–5+. This tracks habit formation.
│
├── Input 3: % users with a completed session in their first 3 days
│   Why: Time-to-value drives retention. Users who focus once in their first 3 days are 4x more likely to return in week 2 (hypothesis to validate).
│
└── Input 4: % users with a weekly streak of ≥3 weeks
    Why: Streak length predicts long-term retention. Users with a 3-week streak churn at <10% monthly (internal baseline).
```

**Causal story:** Users build a focus habit by completing sessions (not just starting them) and by returning consistently week-over-week. Input 3 captures the critical activation moment — do they get value before they leave? Input 4 captures habit formation depth. Inputs 1 and 2 capture the weekly session quality and frequency that aggregate into focused hours. If teams move all four inputs, weekly focused hours should rise because more users are completing more sessions and doing so habitually.

---

## Guardrail metrics

| Guardrail | Threshold | What it protects against |
|---|---|---|
| Session abandonment rate | Must not exceed 30% | Teams could inflate sessions-per-user by making sessions shorter and easier to start — abandonment rate catches this |
| User-reported satisfaction (monthly pulse, 5-point scale) | Must stay ≥ 3.8 | Optimizing streak mechanics could create anxiety rather than productive habit; satisfaction catches wellbeing deterioration |
| % sessions with sound/notification interruptions | Must not exceed 15% | Optimizing for starts while ignoring environment quality undermines the core value |

---

## Operationalization

| Metric | Currently measurable? | Instrumentation needed | Baseline / benchmark |
|---|---|---|---|
| Weekly focused hours (NSM) | Yes | Already tracked — session start/end timestamps by user | Median: 3.2 hrs/week (active users, last 90 days) |
| Focus session completion rate | Yes | Session start/end events already fire | 68% — target: 80% |
| Sessions per active user per week | Yes | Derived from existing events | 2.1 — industry comparison: Toggl ~2.8 |
| % users with session in first 3 days | Yes | Cohort query on existing events | 41% — target: 55% by Q3 |
| % users with ≥3-week streak | Partial | Streak tracking exists but not segmented by length — needs a query added | ~22% — target: 35% |

---

## Known failure modes

- **Streak anxiety anti-pattern:** Optimizing the 3-week streak input could produce compulsive behavior in users with anxiety tendencies. Guardrail: satisfaction pulse and opt-out rate on streak UI.
- **Long sessions ≠ quality sessions:** A 4-hour session with frequent interruptions (but no timer abandonment) would count fully. Does not distinguish genuine focus from marathon sitting. Mitigation: input 1 (completion rate) proxies quality; could add a self-reported quality signal in v2.
- **Metric breaks at scale:** At 10M users, median hours will flatten as casual users dilute it. May need to segment the NSM by user cohort (power users vs. casual) at that stage.

---

*Scoring notes (internal):*
- *nsm_quality: 5 — specific, user-facing, tied to core value moment, not gameable through passive opens.*
- *input_metrics: 5 — four inputs with explicit causal reasoning, all leading, all influenceable by teams.*
- *metric_tree_coherence: 5 — explicit causal story connecting inputs to NSM. Missing inputs noted (qualitative quality).*
- *guardrails: 5 — three guardrails with thresholds, covering three distinct gaming/degradation scenarios.*
- *operationalization: 5 — all metrics measurable today or with a specific plan; baselines and targets noted.*
- *Weighted average: 5.0 — clear pass.*
