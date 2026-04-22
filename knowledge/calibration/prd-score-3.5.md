<!-- calibration: prd score=3.5 -->
<!-- score-rationale: Hypothesis is present and testable. Success metrics are outcome-focused but missing targets and baselines. Scope is reasonably defined — in/out clear, but rationale for exclusions is thin. Value risk is identified. Acceptance criteria are partially testable (Given/When/Then format attempted) but some lack measurable "Then" clauses. Viability risk absent. A solid mid-tier PRD that needs one more pass. -->

# PRD: FocusTimer — Intention-Setting Flow

**Version:** 0.2 | **Author:** [name] | **Status:** Ready for review
**Vision:** `pstack-workspace/focus-timer/00-vision.md` (score: 4.1)

---

## Context & hypothesis

**Context:** FocusTimer's vision is built on a single bet: founders who define an intention before starting a session ship more and feel better about their day. The current prototype (v0.1) has a timer with no pre-session ritual. Early testers skip straight to the timer and abandon sessions at 3x the rate of testers who were verbally prompted to state an intention.

**Hypothesis:** We believe that adding a structured, 1-field intention prompt before each session will increase session completion rate from 34% (current baseline) to ≥55%, because founders who articulate what they're working on are less likely to drift mid-session.

<!-- ✅ Context explains why this feature exists and what data triggered it. Hypothesis follows "We believe... will... because..." format. -->
<!-- ✅ Includes a current baseline (34%) and a target (55%). -->
<!-- ⚠️ "Less likely to drift mid-session" is a mechanism claim. It should be stated as an assumption to be validated, not a known fact. -->

---

## User stories

**Story 1 — Setting an intention**
As a solo founder about to start a deep work session, I want to type what I'm working on in one sentence before the timer starts, so I have a clear contract with myself about this session.

*Acceptance criteria:*
- Given the user taps "Start Session," when the intention prompt appears, then it is the only interactive element on screen (no back button, no settings)
- Given the user types an intention of at least 5 characters, when they tap "Start," then the session begins and the intention is displayed persistently during the session
- Given the user taps "Start" with no intention typed, when the validation fires, then the app surfaces a prompt: "What are you working on? (tap to skip)" — the user can proceed without an intention but the skip is logged

<!-- ✅ Given/When/Then format applied. "Only interactive element" is testable. 5-character minimum is testable. -->
<!-- ⚠️ "Displayed persistently" needs a precision definition — above the timer? Full width? What happens if the intention is >140 characters? -->

**Story 2 — Reviewing the intention at close**
As a founder completing a session, I want to see my intention alongside the session duration at the close screen, so I can assess whether I accomplished what I set out to do.

*Acceptance criteria:*
- Given a session completes (timer reaches zero or user taps "End Session"), when the close screen appears, then the user's original intention text is shown verbatim above the session duration
- Given the close screen is shown, when the user taps "Mark as meaningful," then the session is saved with status = "complete:meaningful" and included in the North Star metric count

<!-- ✅ "Verbatim" is testable. "complete:meaningful" status is specific. -->
<!-- ⚠️ What happens if the user set no intention? What does the close screen show? -->

---

## Success metrics

**Primary (North Star input):** Session completion rate — % of sessions that run to ≥80% of intended duration
**Target:** 55% at 30 days post-launch (baseline: 34%)

**Secondary:** % of sessions started with an intention typed (not skipped)
**Signal threshold:** If <60% of users type an intention in week 1, investigate UX friction before assuming value problem.

<!-- ✅ Primary metric tied to the North Star input. Target and baseline stated. -->
<!-- ✅ Secondary metric with a diagnostic threshold (not just a number). -->
<!-- ⚠️ No time window specified for the secondary metric target. When should 60% be achieved? Day 7? Day 30? -->
<!-- ⚠️ No segment breakdowns. Will the completion rate differ between users who type intentions vs. those who skip? This would be the most important segment. -->

---

## Scope

**In scope (v1):**
- Single free-text intention field, max 200 characters, shown before every session
- Intention displayed persistently in the timer view (collapsed to 1 line, expandable)
- "Mark as meaningful" option on the session close screen
- Skip option with logging (skip is allowed, not blocked)
- Intention stored locally and visible in session history

**Out of scope (v1):**
- Intention suggestions or AI-generated prompts (v2 consideration)
- Intention templates or categories
- Sharing intentions publicly
- Intention analytics or trends (session history shows raw text, not aggregates)

<!-- ✅ Clear in/out split. Skip option is explicitly in-scope and handled. -->
<!-- ⚠️ "v2 consideration" should be moved to ROADMAP.md rather than mentioned here — creates scope creep risk. -->
<!-- ⚠️ No explanation for why "intention analytics" is deferred. A reviewer will ask. -->

---

## Risks

**Value risk (high):** The intention ritual might feel like homework rather than a useful tool. Founders under time pressure may skip it habitually. We're validating this with a skip-rate threshold: if >40% of users skip in week 1, we'll iterate on the framing (not the feature).

**Usability risk (medium):** The free-text input on mobile may create friction — keyboard covers the timer interface, unclear what constitutes a "good" intention. Prototype testing required before launch.

**Feasibility risk (low):** Local storage of session intentions is straightforward. No novel technical risk.

<!-- ✅ Three of four Cagan risks addressed with specific indicators. Value risk has a numeric threshold for intervention. -->
<!-- ❌ Viability risk not addressed. Are there App Store review implications for the "meaningful" self-assessment feature? Any data privacy consideration for storing user session notes? -->

---

## Open questions

1. Should the intention field be shown before duration selection or after? (Design decision — needs UX testing)
2. What's the right character limit? 200 characters is a hypothesis — test with 5 users writing intentions.
3. If a user abandons mid-session and restarts, does the intention persist to the new session?
