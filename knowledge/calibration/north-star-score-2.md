# North Star calibration — Score 2 (weak)

**Product:** FocusTimer (productivity app for remote workers)

---

## The North Star Metric

**Monthly Active Users** — the number of users who open the app at least once per month.

**Why this metric captures core value:**
More users using the app means more people are getting value from it. If people keep coming back, it means they find it useful. This grows with the business.

**What this metric is NOT:**
This is not revenue.

---

## The metric tree

```
North Star: Monthly Active Users
│
├── Input 1: New user signups
│   Why: More users = more actives
│
├── Input 2: App store rating
│   Why: Higher ratings drive downloads
│
└── Input 3: Push notification open rate
    Why: If users open notifications they come back
```

**Causal story:** If we get more signups and improve our app store rating, we'll have more MAUs. Push notifications help re-engage people.

---

## Guardrail metrics

None defined.

---

## Operationalization

We track MAUs in our analytics dashboard already.

---

## Known failure modes

None identified.

---

*Scoring notes (internal):*
- *nsm_quality: 1 — MAU is a vanity/lagging metric. Does not capture moment of value. No user-facing rationale.*
- *input_metrics: 1 — signups are a funnel metric, not a behavior indicator. App store rating is a consequence, not an input teams control. Push notification rate could game MAU without real value.*
- *metric_tree_coherence: 1 — no causal logic. "More users = more actives" is circular.*
- *guardrails: 1 — none present.*
- *operationalization: 3 — NSM is measurable, but inputs are not fully defined.*
- *Weighted average: ~1.4 — well below 3.5 passing floor.*
