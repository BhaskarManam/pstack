<!-- calibration: prd score=5.0 -->
<!-- score-rationale: Hypothesis is crisp and falsifiable. Success metrics are outcome-based with explicit targets, baselines, and time windows. Scope has clear rationale for each exclusion. All four Cagan risks addressed with specific hypotheses and discovery actions. Acceptance criteria are fully testable in Given/When/Then format with measurable outcomes. Open questions are specific and decision-ready. -->

# PRD: FocusTimer — Intention-Setting Flow v1.0

**Version:** 1.0 | **Author:** [name] | **Status:** Ready for build
**Strategy:** `pstack-workspace/focus-timer/01-strategy.md` (score: 4.7) — bet: the intention ritual is the wedge
**Quality gate:** Strategy score ≥ 2.5 ✅

---

## Context

FocusTimer's North Star is *intentional sessions completed per active user per week*. An intentional session requires the user to type an intention before starting. Without this flow, no session can qualify as intentional — which means the North Star cannot move.

**Discovery evidence:**
- Prototype A (timer only): 34% session completion rate, 5-day retention 22%
- Prototype B (prompted verbally to state intention): 61% session completion, 5-day retention 41%
- Exit interviews (n=14): "I kept going because I remembered what I said I was going to do" was cited by 9 of 14 users in Prototype B as the reason they didn't stop early

**Hypothesis:** A structured, frictionless intention prompt — shown for ≤45 seconds before each session — will increase session completion rate from 34% to ≥58% at 30 days, because founders who articulate what they're working on activate a self-accountability mechanism that persists mid-session.

*Falsification condition:* If completion rate is <50% at day 30 post-launch OR if >45% of sessions are started without an intention (skip rate), we will treat this as a product hypothesis failure — not an execution problem — and redesign the ritual.

<!-- ✅ Context grounds the PRD in the North Star. Discovery evidence is specific (n=14, exact figures, verbatim user quote). Hypothesis follows full format. Falsification condition is explicit and distinguishes product failure from execution failure. -->

---

## User stories

**Story 1 — Setting an intention**
As a solo founder about to start deep work, I want to type one sentence about what I'm working on before the timer starts, so I have a clear internal contract for this session.

| # | Given | When | Then |
|---|---|---|---|
| 1.1 | The user taps "Start Session" | The intention screen appears | A single full-width text field is the only interactive element; no navigation, no back button, no settings icon visible |
| 1.2 | The user is on the intention screen | 3 seconds pass with no interaction | A placeholder text "What are you working on?" fades in — no animation, no sound |
| 1.3 | The user has typed ≥5 characters | They tap "Start focused session" | The session begins; the intention text is persisted to local storage; the timer screen shows the intention text in the top 20% of the screen in 14px gray |
| 1.4 | The user has typed 0–4 characters | They tap "Start focused session" | The button label changes to "Skip intention →" for 2 seconds, then becomes active — the user can tap again to skip; the skip is logged as `intention_skipped: true` |
| 1.5 | The user types an intention >200 characters | They type past the limit | The field stops accepting input at 200 characters; a character count "180/200" appears below the field at 150 characters |

<!-- ✅ Table format enables unambiguous test case mapping. Each row is independently testable. "Single full-width text field" is testable (count interactive elements). "Fades in — no animation, no sound" is a design constraint embedded in the AC, not left to interpretation. -->

**Story 2 — Mid-session intention visibility**
As a founder in an active session, I want to see my intention without it dominating my focus, so it anchors me without becoming a distraction itself.

| # | Given | When | Then |
|---|---|---|---|
| 2.1 | An active session with a typed intention | The timer screen is displayed | The intention text appears in 1 line, truncated at 60 characters with "…" if longer, in the top bar above the timer |
| 2.2 | The user taps the truncated intention text | The tap registers | The full intention text expands in a modal overlay for 3 seconds, then auto-collapses |
| 2.3 | An active session started without an intention (skip) | The timer screen is displayed | The top bar area shows "No intention set — tap to add" in gray italic; tapping opens the intention input without pausing the timer |

**Story 3 — Session close and meaningful marking**
As a founder whose session is complete, I want to assess whether I accomplished my intention, so I have an honest record of what I actually did vs. what I planned.

| # | Given | When | Then |
|---|---|---|---|
| 3.1 | The timer reaches 0 OR the user taps "End Session" | The close screen appears | The user's original intention text is shown verbatim in a bordered card; below it are two tappable options: "Meaningful ✓" and "Partial / not quite" |
| 3.2 | The user taps "Meaningful ✓" | The tap registers | Session is saved with `completion_status: meaningful`; this session qualifies for the North Star metric count |
| 3.3 | The user taps "Partial / not quite" | The tap registers | Session is saved with `completion_status: partial`; an optional 1-line text input appears: "What got in the way? (optional)" with a 100-character limit |
| 3.4 | The close screen is shown for a session where no intention was set | The close screen renders | The intention card shows "No intention was set for this session" in gray; only one option appears: "Done" — no meaningful/partial split (cannot assess against nothing) |

<!-- ✅ Every scenario is covered including the skip path (3.4). Status values are explicit strings, not descriptions. The North Star connection is explicit in 3.2. -->

---

## Success metrics

| Metric | Type | Baseline | Target | Timeframe |
|---|---|---|---|---|
| Session completion rate | Primary (NSM input) | 34% | ≥58% | Day 30 post-launch |
| % sessions with intention typed | Activation quality | — (new metric) | ≥60% | Week 2 |
| Intentional sessions/active user/week | North Star | — (new metric) | ≥3.0 | Day 60 |
| 14-day retention | Health | 22% | ≥38% | Day 14 |

**Segment to watch:** Users who type an intention vs. users who skip — track completion rate and retention separately. If the gap is >20pp, the ritual is the mechanism and we double down. If the gap is <10pp, the ritual is not the driver and we revisit the hypothesis.

<!-- ✅ Four metrics with type, baseline, target, and timeframe. Key segment explicitly named. Interpretation rules for the segment gap given. -->

---

## Scope

**In scope — v1.0:**
- Pre-session intention input (1 field, 200-char max, skip allowed with logging)
- Intention displayed in timer view (collapsed, expandable on tap)
- Post-session close screen with meaningful/partial assessment
- Skip-path handling (all screens work without an intention)
- All data stored locally (no server sync in v1)

**Out of scope — v1.0, with rationale:**
- AI-generated intention suggestions: We need to learn what users naturally write before we optimize it. Adding suggestions now would corrupt the signal. → Revisit at 1,000 sessions of training data.
- Intention templates/categories: Adds friction to a flow where speed is critical. The free-text field is the hypothesis; categories are a different hypothesis. → Only consider if >30% of users write identical intentions (indicating they want templates).
- Analytics dashboard: Session history is in scope (show raw text + status); aggregate trends are not — they add complexity and the founder persona doesn't want to manage themselves like a company. → Explicitly a non-goal per the vision.
- Server sync/cloud backup: Privacy-first design means local-only in v1. → v2 decision pending privacy policy review.

<!-- ✅ Every exclusion has a rationale and a condition for reconsideration. No vague "future consideration" entries. -->

---

## Risk assessment

| Risk | Category | Hypothesis | Discovery action |
|---|---|---|---|
| Founders find intention-setting feel like homework | Value | Skip rate >45% signals this | A/B test: "What are you working on?" vs. "One thing I'm focused on:" — which framing gets fewer skips? Run on first 200 users. |
| Keyboard covers timer interface on small screens | Usability | Causes session abandonment at input step | Usability test: 5 participants on iPhone SE (smallest common screen). Time from screen appearance to session start. Target <45s median. |
| Local storage limits on older iOS devices | Feasibility | Sessions stored as JSON; 1,000 sessions ≈ 200KB — well within limits | Engineering spike: Test on iOS 15 + iPhone 8 (2017). Confirmed safe. ✅ |
| Apple App Store review flags "meaningful" self-assessment | Viability | Self-assessment features have been approved for similar apps (e.g., Day One) | App Store guideline review complete. Section 1.4 (User Generated Content) applies; no issue with self-assessment. Data stays local. ✅ |

<!-- ✅ All four Cagan risks addressed. Feasibility and viability risks have been partially de-risked and are marked ✅. Value and usability risks have specific discovery actions. -->

---

## Open questions

1. **Intention field order:** Does the intention come before or after duration selection? Hypothesis: before (the intention should shape the duration, not vice versa). Validate with 3 user interviews before finalizing design.
2. **Partial session re-start:** If a user ends a session early and immediately starts a new one, does the original intention pre-fill? Recommendation: yes, pre-fill with "[original intention] — continued" to signal this is a continuation, not a new session.
3. **Accessibility:** Is 14px gray for the in-session intention display legible under high-contrast mode? Engineering to verify WCAG AA compliance before launch.
