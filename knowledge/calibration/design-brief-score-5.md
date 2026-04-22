<!-- calibration: design-brief score=5.0 -->
<!-- score-rationale: Primary flow is complete end-to-end with decision points, error states, and edge cases. Screen inventory maps every screen with purpose, key elements, and navigation. All constraints are specific and cited (WCAG level, font sizes, touch targets, Reduce Motion, Dark Mode). Interaction principles are product-specific and actionable. JTBD is applied screen by screen — each screen's existence is justified by the job. Open questions are specific, decision-ready, and assigned. -->

# Design Brief: FocusTimer — Session Start & Intention Flow v1.0

**Based on:** PRD v1.0 (score: 5.0)
**Platform:** iOS 16+ (iPhone 15 Pro primary; iPhone SE 3rd gen minimum viable)
**Designer:** [name] | **Reviewed by:** [name] | **Status:** Ready for design

---

## User & job

**User:** Solo founders and indie builders, 3–10 years into independent work, remote, without a manager or standup to create daily structure.

**Job to be done:**
> When I sit down to do important work, I want to enter a committed session with a clear intention, so I can end it with proof that I moved the needle — not just evidence that I was busy.

**Entering emotional state:** Low-level anxiety + anticipation. The founder is aware of the gap between what they want to accomplish and what they typically accomplish. They are not looking for encouragement — they are looking for a container.

**Exiting emotional state (success):** Quiet satisfaction. They know what they did. They can name it. They are not proud of volume — they are at peace with intentionality.

**Design implication:** The product should feel like a closed, protected space — not a dashboard. No scores, no badges, no external reference points. The user is the only audience.

<!-- ✅ Full JTBD. Emotional states at entry and exit explicitly named. Design implication derived directly from the emotional states — not from aesthetics. -->

---

## Primary flow

**Entry condition:** User opens FocusTimer with intent to work. This is the golden path — a returning user who knows the ritual.

```
[Home] → [Duration selection] → [Intention input] → [Session active] → [Session close] → [Home]
```

**Step 1: Home**
User arrives. They see their session history (last 5 sessions: intention + completion status + duration). The primary CTA is a single large button: "Start Session." Nothing else is interactive except a settings icon (top right, ghost button).
*Decision:* Start a session or review history.
*Exit:* Tap "Start Session" → Duration selection.

**Step 2: Duration selection**
Three tappable pills: 25 min / 50 min / 90 min. Their most recent duration is pre-selected (gray background, no border). No other choices. No custom input in v1.
*Decision:* Accept default or select a different duration.
*Exit:* Tap any duration → duration confirmed with a 200ms scale animation → Intention input.
*Error state:* None — it's impossible to have no selection (one is always pre-selected).

**Step 3: Intention input**
Full-screen keyboard-forward view. The text field occupies the top half of the screen above the keyboard. Placeholder text: "What are you working on?" disappears on first keystroke.
- Primary CTA: "Start focused session" (full-width, primary button) — enabled when ≥5 characters typed
- Secondary CTA: "Skip →" (text link, gray, 12pt, right-aligned below the primary button) — always available
- Character counter appears at 150 characters: "150/200"

*Decision:* Type intention and start, or skip.
*Exit (with intention):* Tap "Start focused session" → Session active, intention stored.
*Exit (skip):* Tap "Skip →" → Skip logged as `intention_skipped: true` → Session active, no intention stored.
*Error state:* User types 4 characters and taps start → Primary button remains inactive. No error message. The inactivity of the button is the signal.

**Step 4: Session active**
Timer dominates the screen (80pt+ digit display, center-screen). Intention text is shown in a top bar: 1 line, SF Pro Text 14pt, gray (#6B6B6B), truncated at 60 characters with "…".
- Tap intention bar → modal overlay with full intention text, dark scrim, auto-dismisses after 3 seconds or on tap
- "End session early" is available in a bottom-right ghost button (12pt, destructive color, requires a confirmation tap: "End session? You're 23 minutes in." + "End it" / "Keep going")
- No other interactive elements. No settings. No navigation bar.

*Decision:* Continue or end early.
*Background / interruption state:* If app is backgrounded (phone call, other app), timer continues silently. On return, user sees session still active with time elapsed accurately updated. A passive banner at the bottom: "Session continued in background." No alarm, no alert.
*Exit (complete):* Timer reaches 0 → 400ms fade → Session close.
*Exit (early):* User confirms "End it" → Session close with elapsed time recorded.

**Step 5: Session close**
The close screen is the quietest screen in the app.
- Intention text in a bordered card (full verbatim text, no truncation)
- Below the card: two tappable options, equal visual weight: "Meaningful ✓" | "Partial / not quite"
- If "Partial": a small text input fades in below: "What got in the way? (optional, 100 chars)" with a gray "Done" button
- After any choice: session saved → 300ms fade to Home screen with updated history

*Skip path close:* Intention card shows "No intention was set for this session" in gray italic. One option: "Done." No meaningful/partial split.
*Early end close:* Same as normal close, but the card shows the elapsed time prominently: "You ran for 23 of 50 minutes."

<!-- ✅ Every step has: user decision, both paths (happy + edge), error states, and animation specs. Background state addressed. Skip path tracked through every screen. -->

---

## Screen inventory

| Screen | User's job | Dominant element | Secondary elements | Entry | Exit(s) |
|---|---|---|---|---|---|
| **Home** | Orient + initiate | "Start Session" CTA (hero) | Session history list (last 5), Settings icon | App launch, Session close | Duration selection |
| **Duration selection** | Commit to a time box | Duration pills (25/50/90) | Back gesture (swipe right) | Home | Intention input |
| **Intention input** | Pre-commit in writing | Full-screen text field | "Start" CTA, "Skip →" link, character counter | Duration selection | Session active |
| **Session active** | Execute the committed session | Countdown timer (80pt+) | Intention bar (top), "End early" ghost button | Intention input | Session close |
| **Session close** | Assess completion honestly | Intention card | Meaningful/Partial buttons, optional "what got in the way" | Session active | Home |
| **Empty state (Home)** | First-time orientation | "Start your first session" hero | Subtle prompt explaining the intention ritual | First app launch | Duration selection |
| **Settings** | Configure without disrupting | Duration defaults, notification preferences | (Deferred — listed here to avoid surprise; not designed in v1) | Settings icon (Home) | Home |

<!-- ✅ 7 screens inventoried including the empty state and a placeholder for settings. Each has dominant + secondary elements and full navigation map. -->

---

## Interaction principles

1. **One decision per screen, nothing extra.** Every screen has a single primary decision. No navigation bars, no settings icons, no secondary flows visible — except on the Home screen which is the intentional starting point.

2. **Commitment over convenience.** "Skip" is always available but never prominent. The visual hierarchy is: start with intention (primary) → skip (secondary). We respect the user's right to skip; we do not celebrate it.

3. **The timer is the anchor.** The countdown timer is the dominant element at 80pt minimum. It should be legible from 60cm (reading distance) without glasses. The user should never need to squint at the time remaining.

4. **Closing is as important as opening.** The session close screen is not a confirmation dialog — it is a moment of reflection. It gets the same design attention as the start flow. It should not feel like an exit; it should feel like a landing.

5. **No achievement theater.** No animations celebrating completion, no confetti, no streak counts, no "great job" copy. The session history is the record. The record speaks for itself.

6. **Error states are silent.** An inactive button is the only signal needed when input is insufficient. Never show a red error message for a user who is trying to focus — it is disproportionate feedback.

<!-- ✅ 6 principles, each specific and actionable. Each principle implies specific design decisions (e.g., "80pt minimum" from principle 3, "no red error message" from principle 6). -->

---

## Visual / voice

**Color system:**
- Background: `#F7F5F0` (warm off-white — not clinical white; references paper, calm)
- Primary text: `#1C1C1E` (iOS system near-black, not pure black)
- Secondary text: `#6B6B6B` (for labels, captions, skip link)
- Accent (primary CTA only): `#4A6FA5` (muted slate blue — calm, trustworthy, not aggressive)
- Destructive (end early): `#B04040` (muted red — visible but not alarming)
- Session close cards: `#FFFFFF` with `1px solid #E0DDD9` border

**Dark mode:** Required. Map every token above to a dark-mode equivalent. Background: `#1C1C1E`. Cards: `#2C2C2E`. Accent: lightened to `#6A9FD5` for contrast compliance.

**Typography:**
- Timer: SF Pro Display Bold, 80pt minimum (72pt on iPhone SE), tabular figures
- Intention text (session active bar): SF Pro Text Regular, 14pt, secondary text color
- Intention text (session close card): SF Pro Text Regular, 17pt, primary text color
- Body copy: SF Pro Text Regular, 17pt
- Secondary copy: SF Pro Text Regular, 15pt
- CTAs: SF Pro Text Semibold, 17pt

**Copy tone rules:**
| Context | Right | Wrong |
|---|---|---|
| Placeholder | "What are you working on?" | "What's your goal today? 🎯" |
| Skip confirmation | No confirmation needed — just proceed | "Are you sure? Intentions help!" |
| Session complete | "Session complete" | "Great job! You did it! 🎉" |
| Early end confirm | "End session? You're 23 minutes in." | "Giving up already?" |
| Error state | (no text — inactive button is the signal) | "Oops! Need at least 5 characters." |

<!-- ✅ Full color system with hex values including dark mode. Typography with pt sizes and specific font weights. Copy tone rules with explicit right/wrong examples — removes ambiguity for copy review. -->

---

## Accessibility

| Requirement | Specification |
|---|---|
| Text contrast | WCAG AA minimum (≥4.5:1 normal text, ≥3:1 large text). Timer display: target WCAG AAA (≥7:1). |
| Touch targets | 44×44pt minimum (Apple HIG). "Skip →" link padded to 44pt tap height even if visually smaller. |
| VoiceOver | All interactive elements require `accessibilityLabel`. Timer: "42 minutes remaining." Intention bar: "You are working on: [intention text]." "End early" button: "End session early." |
| Dynamic Type | All text must reflow correctly at sizes up to 200% (xxxLarge). Timer can scale down to 60pt at xxxLarge without truncation — test on iPhone SE. |
| Reduce Motion | The 200ms duration-selection animation, the modal auto-collapse, and the close-to-home fade must check `UIAccessibility.isReduceMotionEnabled` and use instantaneous transitions if true. |
| Dark Mode | Full dark mode support required. Test contrast ratios in dark mode separately — they differ from light mode. |

<!-- ✅ Six specific accessibility requirements with exact values. VoiceOver labels with example strings. Reduce Motion calls out which specific animations need the check. -->

---

## Open design questions

| # | Question | Recommendation | Decision needed by | Owner |
|---|---|---|---|---|
| 1 | Does duration selection come before or after intention? | Before — intention should inform the time box, not vice versa. Validate with 3 prototype tests. | Before design of Step 2 | UX |
| 2 | What does the Home screen empty state say? | "Start your first session. Write one sentence about what you're working on before the timer starts." — then the CTA. | Before launch | Copy + Design |
| 3 | What is the exact copy for "End session early" confirmation? | "End session? You're [N] minutes in. [End it] [Keep going]" — N is dynamic. | Before design of Step 4 | Copy |
| 4 | Does the timer vibrate on completion (haptic)? | Yes — a single, medium-weight haptic at 0:00. Silent for backgrounded sessions. | Engineering input needed | Engineering + Design |
| 5 | Should past sessions be tappable on the Home screen? | Yes — tapping opens a read-only session detail (intention + duration + status). Not in scope for v1 design; placeholder only. | v1.5 | Product |
