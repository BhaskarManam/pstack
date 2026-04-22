# Design Brief: {Product Name} — {Flow Name} v1.0

**Based on:** `02-prd.md` v1.0
**Platform:** {platform + version}
**Designer:** {name} | **Reviewed by:** {name} | **Status:** Ready for design

---

## User & job

**User:** {One specific person — role, context, day. Mirror the vision's target user, not a new one.}

**Job to be done:**
> {The job in the user's own voice — the progress they are trying to make in this flow.}

**Entering emotional state:** {How does the user feel when they open this screen? What are they carrying?}

**Exiting emotional state (success):** {How do they feel when they've done the job?}

**Design implication:** {One sentence: what does the emotional arc mean for the product's tone, pace, or density?}

---

## Primary flow

**Entry condition:** {Who is this user and what brought them here — returning user, first-timer, specific trigger?}

```
[{Screen 1}] → [{Screen 2}] → [{Screen 3}] → [{Screen N}] → [{End state}]
```

**Step 1: {Screen name}**
{Description of what the user sees and does.}
*Decision:* {What choice does the user make here?}
*Exit (happy):* {Action → next screen.}
*Exit (edge):* {Alternative action → different next screen.}
*Error state:* {What happens if something goes wrong?}

**Step 2: {Screen name}**
{…repeat for every step in the flow…}

**Step N: {Screen name}**
{…}

---

## Screen inventory

| Screen | User's job | Dominant element | Secondary elements | Entry | Exit(s) |
|---|---|---|---|---|---|
| **{Screen 1}** | {why this screen exists in job terms} | {the single most important element} | {supporting elements} | {how user arrives} | {where user goes} |
| **{Screen 2}** | | | | | |
| **{Empty state}** | {first-time orientation} | | | {first launch} | |
| **{Error state}** | | | | | |

---

## Interaction principles

1. **{Principle name.}** {One concrete sentence describing the rule and what specific design decisions it implies.}

2. **{Principle name.}** {…}

3. **{Principle name.}** {…}

4. **{Principle name.}** {…}

5. **{Principle name.}** {…}

*Note: Each principle must imply at least one specific design decision. Generic principles ("minimize cognitive load") are not allowed.*

---

## Visual / voice

**Color system:**
- Background: `#{hex}` — {rationale}
- Primary text: `#{hex}`
- Secondary text: `#{hex}`
- Accent (CTAs only): `#{hex}` — {emotional rationale}
- Destructive: `#{hex}`

**Dark mode:** {Required / Not required}. Dark mode token mapping:
- Background dark: `#{hex}`
- Accent dark: `#{hex}` (lightened for contrast compliance)

**Typography:**
- Primary display: {font family}, {weight}, {size in pt}
- Body: {font family}, {weight}, {size in pt}
- Secondary / captions: {font family}, {weight}, {size in pt}
- CTAs: {font family}, {weight}, {size in pt}

**Copy tone rules:**

| Context | Right | Wrong |
|---|---|---|
| {CTA} | {right copy} | {wrong copy} |
| {Placeholder} | {right copy} | {wrong copy} |
| {Error state} | {right copy} | {wrong copy} |
| {Empty state} | {right copy} | {wrong copy} |
| {Success state} | {right copy} | {wrong copy} |

---

## Accessibility

| Requirement | Specification |
|---|---|
| Text contrast | WCAG {AA / AAA} minimum ({ratio}:1 normal text, {ratio}:1 large text) |
| Touch targets | {N}×{N}pt minimum (platform HIG). All interactive elements padded to minimum tap height. |
| VoiceOver / TalkBack | All interactive elements require `accessibilityLabel`. Examples: {element}: "{label text}". |
| Dynamic Type | All text must reflow correctly at sizes up to {X}% ({xxxLarge}). Test on smallest supported device. |
| Reduce Motion | The following animations must check `isReduceMotionEnabled` and use instantaneous transitions if true: {list animations} |
| Dark Mode | Full dark mode required. Test contrast ratios in dark mode separately — they differ from light mode. |

---

## Open design questions

| # | Question | Recommendation | Decision needed by | Owner |
|---|---|---|---|---|
| 1 | {specific, decision-ready question} | {recommended answer with reasoning} | {milestone} | {Design / Eng / Product} |
| 2 | | | | |
| 3 | | | | |
