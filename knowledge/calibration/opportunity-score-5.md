<!-- calibration: opportunity score=5.0 -->
<!-- score-rationale: One specific bet from the strategy, framed as a discovery question (not a spec). All four risks assessed for THIS bet with reasoning. The true leap-of-faith assumption named, with a cheap, well-designed test and signal thresholds. Concrete kill criteria with a date and a fallback. -->

# Opportunity Assessment: Streak-Based Reward Loop

**Strategic bet this serves:** "Widen the ritual's reward loop" (Q2 bet, `01-strategy.md`)
**Segment:** solo founders (same as strategy — no new segment)
**Status:** Discovery — not yet a PRD

---

## The question

Should we build a streak mechanic around *intentional sessions completed* to deepen the retention loop — or would streaks corrupt the intention ritual by turning honest reflection into streak-protection behavior? This assessment decides whether the bet is worth a PRD.

<!-- ✅ One specific bet, tied to a named strategic objective and the same segment. Framed as a go/no-go discovery question, explicitly upstream of a PRD — not a solution spec. -->

---

## The four risks for this bet

| Risk | Assessment for THIS bet | Rating |
|---|---|---|
| **Value** | Streaks reliably lift habit retention in adjacent apps (Duolingo), and our segment already self-reports "momentum" as motivating. But our value is *intentional* sessions — a streak might drive sessions that are intentional in name only. Genuinely uncertain. | **High** |
| **Usability** | Streak UI is well-trodden; low novel usability risk. One wrinkle: showing a streak must not crowd the calm, single-field intention screen our guardrail protects. | **Low–Med** |
| **Feasibility** | Streak state is a local counter over existing session records. No new infra. A 2-day spike confirms. | **Low** |
| **Viability** | No legal/brand conflict. Risk is brand-internal: streaks can feel manipulative, which contradicts our "honest reflection" positioning. | **Med** |

<!-- ✅ All four risks assessed specifically for this bet (not copied generically), each rated with reasoning, honestly flagging value as the real unknown. -->

---

## Riskiest assumption + smallest viable test

**Leap of faith:** *Streaks will increase intentional sessions without degrading intention honesty* — i.e., users won't start logging low-quality "meaningful" sessions just to protect a streak.

**Smallest viable test:** 2-week holdback experiment with 200 users (100 streak, 100 control).
- **Confirms** if: streak group shows higher intentional-sessions/week AND the "meaningful vs. partial" honesty ratio stays within 5pp of control (they're not gaming it).
- **Disconfirms** if: streak group's "meaningful" rate jumps >10pp above control while session *duration* drops — the signature of streak-gaming.

<!-- ✅ Names the true leap of faith (not a safe assumption), with a cheap, well-designed test, an explicit method/sample, and quantified confirm vs. disconfirm thresholds — including a clever gaming-detection signal. -->

---

## Kill criteria

If the test disconfirms (gaming signature appears) **by end of the 2-week experiment (target: 2026-05-15)**, we kill the streak mechanic for this bet and instead test a *non-streak* reward (e.g., a private "intentions honored" log with no public count). We do not iterate on streaks past one failed honesty read — protecting the ritual outranks the retention bump.

<!-- ✅ Concrete kill threshold with a date, plus a defined fallback. Pre-commits against sunk-cost continuation and ranks the ritual above the metric. -->
