<!-- calibration: design-brief score=2.0 -->
<!-- score-rationale: Primary flow is not described — only a screen list. Screen inventory names screens but doesn't state their purpose or decision points. Constraints are generic ("mobile-first," "clean design"). No JTBD connection — the brief could describe any timer app. No interaction principles. Accessibility not mentioned. -->

# Design Brief: FocusTimer — Session Start Flow

**Based on:** PRD v0.1
**Platform:** iOS

---

## User

Solo founders who need help focusing.

<!-- ❌ "Need help focusing" is a problem description, not a job context. Who is the user specifically? What are they trying to accomplish in this flow? The JTBD from the PRD/vision is absent. -->

---

## Primary flow

1. Open app
2. See home screen
3. Tap start
4. Enter session
5. Timer counts down
6. Session ends

<!-- ❌ This is a list of screens, not a flow. A primary flow describes what the user is trying to do at each step, what decision they face, and what happens as a result. No branching, no error states, no happy path vs. edge path distinction. -->

---

## Screen inventory

- Home screen
- Session active screen
- Session complete screen
- Settings screen

<!-- ❌ No purpose stated for each screen. What job does each screen advance? What is the user's mental state entering and leaving each screen? -->
<!-- ❌ The intention-setting screen (the entire subject of the PRD) is not listed. The screen inventory doesn't match the PRD scope. -->

---

## Interaction principles

- Keep it simple
- Mobile-first design
- Clean and minimal

<!-- ❌ These are generic adjectives, not principles. "Keep it simple" could apply to any product. Interaction principles should be specific to this product and this job — e.g., "no choices before the session starts" or "every tap should feel like a commitment, not a configuration." -->

---

## Visual / voice

- Clean, modern aesthetic
- White and blue color palette
- Friendly tone

<!-- ❌ "Clean, modern" and "white and blue" are not constraints — they're vague stylistic preferences. What is the emotional register of the product? What does it NOT look like? -->
<!-- ❌ "Friendly tone" for what? UI copy? Notifications? Error messages? No scope. -->

---

## Accessibility

(Not addressed)

<!-- ❌ Accessibility omitted entirely. At minimum: target WCAG level, text contrast ratio, touch target size minimum, and screen reader support expectation should be named. -->

---

## Open design questions

- What color should the start button be?
- Should we use tabs or a hamburger menu?

<!-- ❌ Both questions are implementation preferences, not design questions grounded in the user job. Neither of these questions emerges from understanding the JTBD. -->
