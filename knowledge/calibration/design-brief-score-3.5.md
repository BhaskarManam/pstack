<!-- calibration: design-brief score=3.5 -->
<!-- score-rationale: Primary flow is described end-to-end including the intention-setting step. Screen inventory lists screens with purpose but decision points are thin. JTBD is referenced in the user section but not consistently applied to each screen. Constraints are more specific (iOS 16+, SF Pro) but accessibility is generic ("WCAG AA"). Interaction principles are real but could be sharper. A solid first draft that needs one revision pass. -->

# Design Brief: FocusTimer — Session Start & Intention Flow

**Based on:** PRD v0.2 (score: 3.5)
**Platform:** iOS (iPhone primary, iPad not in scope)
**Designer:** [name] | **Status:** In review

---

## User & job

**User:** Solo founders and indie builders working remotely without external structure.

**Job to be done:** When I sit down to do important work, I want to enter a committed session with a clear intention, so I can end it knowing whether I accomplished what I set out to do.

**Emotional register:** The user is sitting down with intention and mild anxiety about the day ahead. The design should feel grounding — not motivational or energetic. Think "quiet confidence," not "let's go."

<!-- ✅ JTBD is stated. Emotional register is named ("quiet confidence" vs. "let's go") and gives clear design direction. -->
<!-- ⚠️ The emotional register is named but not connected to specific design choices below. The brief should close that loop. -->

---

## Primary flow

**Job: Start an intentional work session**

1. **App open → Home screen**
 - User sees a single large "Start Session" button and their last 3 sessions (intention + completion status)
 - Decision: Start a new session or review a past one

2. **Tap "Start Session" → Duration selection**
 - User selects duration: 25 / 50 / 90 minutes (three tappable options, nothing else)
 - Auto-selects their most recent duration as a default
 - Decision: Pick duration or keep default

3. **Duration confirmed → Intention input**
 - Single text field, full-screen focus, keyboard visible
 - Placeholder: "What are you working on?"
 - CTA: "Start focused session" (primary) | "Skip →" (secondary, gray)
 - Decision: Type an intention or skip

4. **Intention set → Session active**
 - Timer counts down; intention text shown in top bar (1 line, 60-char max)
 - Tap intention to expand full text (modal, 3 seconds, auto-collapse)
 - Only interactive: "End session early" (destructive, requires confirmation)

5. **Timer reaches 0 → Session close**
 - Intention shown verbatim in a card
 - Two tappable choices: "Meaningful ✓" | "Partial / not quite"
 - If "Partial": optional text input appears ("What got in the way?")
 - After choice: session saved, return to Home screen with updated history

**Skip path (no intention):** Steps 1–2 same. Step 3: user taps "Skip →" — session begins with no intention displayed in timer view. Close screen shows "No intention was set" with a single "Done" button.

<!-- ✅ End-to-end flow including the skip path. Decision points named at each step. Both happy path and skip path covered. -->
<!-- ⚠️ Error states missing: What if the app is backgrounded mid-session? What if the device receives a call? These are common iOS scenarios that affect the design. -->

---

## Screen inventory

| Screen | Primary job | Key elements | Entry from | Exits to |
|---|---|---|---|---|
| **Home** | Anchor + orient | Start button (hero), last 3 sessions | App launch / session close | Duration selection |
| **Duration selection** | Commit to a time box | 3 duration options, selected state | Home | Intention input |
| **Intention input** | Set the pre-session contract | Full-screen text input, "Start" CTA, "Skip" secondary | Duration selection | Session active |
| **Session active** | Execute the committed session | Timer (dominant), intention bar, "End early" (minimal) | Intention input | Session close |
| **Session close** | Assess completion | Intention card, Meaningful/Partial choice, optional text | Session active | Home |

<!-- ✅ Screen inventory has purpose, key elements, and navigation map. -->
<!-- ⚠️ Settings screen is missing — the PRD doesn't mention it, but duration preferences and notification settings will need a home. Should be noted as a deferred screen even if not in scope v1. -->

---

## Interaction principles

1. **One decision at a time.** Each screen presents exactly one primary decision. No optional distractions before the session starts.
2. **Commitment over convenience.** The "Skip" option is available but never the visual default. The design respects the user's right to skip while signaling that skipping is a lesser path.
3. **The timer is the anchor.** In the active session view, the timer is the dominant element — time remaining should be perceivable at a glance from across a desk.
4. **No achievement theater.** No animations celebrating session completion, no confetti, no streak counters. The close screen is quiet and reflective.

<!-- ✅ Four principles, each specific to this product and this job. Principle 2 embeds a value judgment ("lesser path") that gives design clear direction. -->
<!-- ⚠️ Principle 3 ("perceivable from across a desk") implies a minimum type size but doesn't specify it. Should call out: minimum 72pt for the countdown timer. -->

---

## Visual / voice

**Color:** Monochromatic with one accent. Background: near-white (#F7F7F5). Text: near-black (#1A1A1A). Accent: a single muted color for the primary CTA (not red — red implies urgency; not green — green implies gamification). Suggestion: slate blue (#4A6FA5) or warm terracotta (#C87941) — validate with 5 users.

**Typography:** SF Pro (system font, iOS). Headline: SF Pro Display Semibold, 34pt. Body: SF Pro Text Regular, 17pt. Timer: SF Pro Display Bold, 80pt minimum.

**Voice / copy tone:** Direct, not cheerful. "What are you working on?" not "What's your goal for today? 🎯" Error states: "Try something shorter" not "Oops! That's too long." Completion: "Session complete" not "Great job!"

<!-- ✅ Specific color values. Explicit font + size choices. Copy tone with examples of right and wrong. -->
<!-- ⚠️ Dark mode not addressed. iOS users expect dark mode support. -->

---

## Accessibility

- Target: WCAG AA (contrast ratio ≥4.5:1 for normal text, ≥3:1 for large text)
- Minimum touch target: 44×44pt (Apple HIG standard)
- All interactive elements must have accessibility labels for VoiceOver
- Timer text must remain legible at 200% Dynamic Type setting

<!-- ✅ Specific contrast ratios and touch target sizes cited. Dynamic Type called out. -->
<!-- ⚠️ Reduce Motion is not addressed — the modal auto-collapse animation (3 seconds) should check for Reduce Motion preference and skip if enabled. -->

---

## Open design questions

1. Does duration selection come before or after intention? PRD recommends before (intention shapes duration) but this needs 3-user validation. Create two prototype variants.
2. What does the Home screen show for a brand-new user with 0 sessions? The "last 3 sessions" component is empty — design the empty state.
3. What happens to the session if the app is backgrounded (phone call, another app)? Does the timer continue silently? Pause? Needs product + engineering decision before screen 4 is designed.
