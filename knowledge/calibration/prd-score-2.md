<!-- calibration: prd score=2.0 -->
<!-- score-rationale: Hypothesis is missing — the PRD doesn't state what bet is being placed. Success metrics are output metrics (sessions created), not outcome metrics (value delivered). Scope is a feature list, not a boundary. No Cagan risk taxonomy applied. Acceptance criteria are UI descriptions, not testable behaviors. -->

# PRD: FocusTimer — Session Start Flow

**Version:** 0.1 | **Author:** [name] | **Status:** Draft

---

## Context

FocusTimer needs a way for users to start a session. This PRD covers the session start screen.

<!-- ❌ "FocusTimer needs a way for users to start a session" is a requirement statement, not a context. What problem does this specific feature solve? What is the user state before this flow? -->

---

## Hypothesis

We will build a session start screen that is clean and easy to use.

<!-- ❌ This is a description of the feature, not a testable hypothesis. A hypothesis states: "We believe [user] will [behavior] because [insight], and we'll know we're right when [measurable outcome]." -->

---

## User stories

- As a user, I want to start a session so I can do focused work.
- As a user, I want to see my session timer so I know how much time is left.
- As a user, I want to stop my session if I need to.

<!-- ❌ Stories are generic and don't reflect the specific job (pre-commitment intention-setting). "Do focused work" is the entire product, not this feature. -->
<!-- ❌ No acceptance criteria per story. "So I can do focused work" is not testable. -->

---

## Success metrics

- Number of sessions created per day
- App opens per week
- User rating in app store

<!-- ❌ Sessions created is an output metric — it measures usage, not value delivered. A user who creates 10 sessions and abandons all of them is counted as successful. -->
<!-- ❌ App opens is an engagement vanity metric. -->
<!-- ❌ App store rating is a sentiment proxy, not a success metric for this feature. -->
<!-- ❌ No baseline, no target, no timeframe. -->

---

## Scope

**In scope:**
- Session start button
- Timer display
- Session duration selector (25 min, 50 min, 90 min)
- Stop session button
- Session complete screen

**Out of scope:**
- Notifications

<!-- ❌ "In scope" is a feature list, not a scope boundary. What problems is this flow solving and which adjacent problems are explicitly deferred? -->
<!-- ❌ Out of scope has only one item. What else is excluded? Analytics? Social sharing? Integration with calendars? -->

---

## Risks

- Users might not like the design.
- There could be bugs in the timer.

<!-- ❌ Neither of these is a product risk in Cagan's taxonomy. "Users might not like the design" approaches usability risk but states it as an aesthetic preference, not a behavior risk. -->
<!-- ❌ "There could be bugs" is a quality concern, not a product risk. -->
<!-- ❌ No value risk (will users actually use the intention-setting ritual?), no feasibility risk, no viability risk. -->

---

## Acceptance criteria

- The session start button should be visible on the home screen.
- The timer should count down correctly.
- The stop button should work.

<!-- ❌ None of these are acceptance criteria — they are implementation descriptions. An AC is: Given [context], When [action], Then [measurable outcome]. -->
<!-- ❌ "Should count down correctly" is untestable — what is "correctly"? From what start time? With what precision? -->
