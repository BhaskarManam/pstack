# PRD — Focus Timer (deliberately flawed fixture)
<!-- This file has intentional gaps for testing /critique gap detection -->

## Context & hypothesis

We believe that ADHD founders need a focus timer that coaches rather than just counts down.
If we ship a coaching-mode timer, we expect users will complete more deep-work sessions.

## User stories

1. As an ADHD founder, I want to start a focus session so I can block out distractions.
2. As a user, I want the timer to notice when I've switched context so I can get back on track.
3. As a user, I want to see a streak counter so I feel rewarded for consistency.

## Acceptance criteria

- Focus session can be started with one tap
- App detects foreground app switches and shows a one-line reminder
- Streak counter updates at session completion

## Scope

**In:** Session timer, context-switch detection, streak counter, session history.
**Out:** Social features, team mode, integrations in v1.

<!-- INTENTIONAL GAP: Success metrics section is missing entirely -->

## Risks & assumptions

- Context-switch detection may require screen-time permissions (feasibility risk)
- Users may find nudges annoying rather than helpful (usability risk)

## Open questions

- What is the ideal session length default?
- Should streaks reset at midnight or after 24h?

## Milestones

- Week 2: Core timer + context detection prototype
- Week 4: Beta with 10 ADHD founders
- Week 8: v1 launch
