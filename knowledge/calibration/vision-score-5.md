<!-- calibration: vision score=5.0 -->
<!-- score-rationale: All five dimensions strong. Problem is specific with cited evidence. JTBD covers functional, emotional, and social dimensions. Vision statement is distinctive and memorable. Why Now is grounded in a specific, documentable inflection point. North Star metric captures genuine value delivered and includes a clear operational definition. Non-goals are specific and explain the "why not." Key risks use Cagan's four-risk taxonomy. -->

# Vision: FocusTimer

---

## Problem

Indie founders and solo builders spend 40% of their working hours in reactive mode — answering messages, switching contexts, reading feeds — according to a 2023 survey of 312 bootstrapped founders by Indie Hackers. They describe their days not as "unproductive" but as "vaporized": hours disappear without a sense of what was accomplished or why. The root cause is not distraction but absence of pre-commitment: most founders start work sessions without defining what success looks like for the next 90 minutes, which means any interruption becomes equally valid as the work itself.

<!-- ✅ Specific target (indie founders, solo builders). Quantified cost (40%, "vaporized"). Cited evidence (2023 Indie Hackers survey). Root cause named (pre-commitment absence, not distraction). -->

---

## Target user & JTBD

**Target user:** Solo founders and indie builders, 3–10 years into their careers, working remotely without a manager or team structure to externally create accountability. They care deeply about output quality and feel the moral weight of time wasted.

**Job to be done:**
> When I sit down to do important work, I want to enter a committed, bounded session where I know exactly what I'm working toward, so I can end the day with proof that I moved the needle — not just evidence that I was busy.

*Functional dimension:* Enter a distraction-resistant work sprint with a clear definition of done.
*Emotional dimension:* End the day with a sense of honest accomplishment, not the guilt of motion without progress.
*Social dimension:* Be the kind of founder who ships, not one who is always "working on it."

<!-- ✅ Full JTBD format. All three dimensions explicit. Emotional and social dimensions are specific and connected to the persona's identity. -->

---

## Vision statement

FocusTimer is the session layer for solo founders: a lightweight companion that turns vague work time into accountable, reviewable sprints. In a world where founders have dismantled every external accountability structure, FocusTimer is the internal contract they make with their future self — and the record that proves they kept it.

<!-- ✅ Clear positioning ("session layer"), clear differentiation ("internal contract"), distinctive framing ("record that proves they kept it"). Memorable and quotable. -->

---

## Why now

Three conditions have converged in the last 24 months:

1. **The async-remote normalization.** Post-2022, solo founders have permanently left office structures. The tools catching up are still team-first (Notion, Linear, Slack). There is no solo-first operating system yet.
2. **The AI distraction multiplier.** AI assistants have made interruption frictionless — asking GPT a question takes 10 seconds and derails 20 minutes of deep thinking. Focus protection is now more necessary, not less.
3. **The creator/builder identity shift.** Indie Hackers, Twitter/X builder community, and the "build in public" movement have established a social identity for indie builders who ship — and social shame for those who don't. There is now latent demand for a tool that produces proof of shipping.

Without condition 3, FocusTimer is a productivity tool. With it, it is an identity tool — and identity tools have dramatically higher retention.

<!-- ✅ Three specific, named inflection points. Each is documentable. Condition 3 distinguishes between a productivity tool and an identity tool — a non-obvious insight that changes the retention hypothesis. -->

---

## 3-year picture

In three years, 75,000 solo founders run FocusTimer sessions daily. The product has a session archive: each user has a logged history of every intention they set and whether they completed it — their personal operating record. When a founder closes a deal, applies to YC, or ships a product, they can point to 1,200 sessions of focused work as the evidence. The session archive becomes a founder's portfolio.

The North Star is not sessions started — it is sessions completed with a pre-defined intention that the user marks as "meaningful" at the close. That's when value is delivered.

<!-- ✅ Specific scale (75,000 founders). Specific artifact (session archive). Specific use case (deal, application, launch). "Sessions completed + marked meaningful" is the value-delivery moment — not engagement. -->

---

## Non-goals

- **Not a team product.** No shared workspaces, manager views, or team dashboards — in v1 or v2. Solo-first is the architecture, not a phase.
- **Not a task manager.** The session is the unit, not the task. We will not compete with Things 3, Linear, or Notion on task lists.
- **Not a habit tracker.** No streaks, no gamification, no push notifications celebrating consistency. The session log is intrinsic motivation — we will not manufacture extrinsic rewards.
- **Not a website blocker.** Distraction blocking creates a dependency on the tool. We believe intention-setting removes the desire to distract; blocking is a crutch for tools that don't work.
- **Not an analytics dashboard.** Aggregate productivity stats per week are not in scope. Individual session review is in scope; performance management is not.

<!-- ✅ Five specific non-goals, each with a "why not" rationale. The website blocker non-goal includes a product philosophy ("intention-setting removes the desire to distract") that reveals the product's theory. -->

---

## North Star metric

**Intentional sessions completed per active user per week**

*Operational definition:*
- An **intentional session** = the user typed an intention before starting AND the session ran for at least 80% of its planned duration without the user abandoning it.
- An **active user** = someone who has completed ≥1 intentional session in the last 7 days.
- Target at 12 months: **4.0 intentional sessions per active user per week.**

*Why this metric:* It captures the exact moment value is delivered — the user did the thing that FocusTimer is designed for. It cannot be gamed by passive opens, notifications, or session starts that don't complete.

*Input metrics that drive it:*
1. % of sessions with a pre-typed intention (activation quality)
2. Session completion rate (% started → ≥80% complete)
3. Week-2 retention (% of users completing ≥1 session in week 2 after signup)

<!-- ✅ Single metric. Clear operational definition with specific rules. Explicit target. Reason why this metric and not another. Three input metrics identified. -->

---

## Key risks

| Risk type | Hypothesis being tested | How we'll reduce it |
|---|---|---|
| **Value** | Founders will form a lasting habit if the intention-setting ritual creates genuine accountability | Test with 20 founders in week 1: does session completion rate increase after the first week of using intentions? |
| **Usability** | The 60-second intention ritual won't feel like friction | Prototype test: time how long first-time users spend on intention input; target ≤45 seconds median |
| **Feasibility** | Low risk. Core product = timer + structured text + local storage. No novel technical dependencies in v1. | Engineering spike not required |
| **Viability** | Apple App Store guidelines for focus/screen-time apps are evolving; API constraints may limit session interruption detection on iOS | Legal/platform review in Week 2 before building iOS version |

<!-- ✅ All four Cagan risks addressed. Each has a specific hypothesis and a discovery action. Feasibility is correctly assessed as low and handled proportionately. -->
