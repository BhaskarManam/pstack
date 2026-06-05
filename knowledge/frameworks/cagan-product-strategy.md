---
tldr: "Product strategy is how you make the vision real while meeting the company's needs. It rests on four pillars: focus (choosing the few things, and what you won't do), insights (from data, customers, tech, market), actions (turn insights into objectives for teams), and management (it's never static). Vision inspires; strategy focuses."
use-when: ["strategy (the whole artifact — the bet, sequencing, the insight, success definition)", "challenge (strategy / priorities lens)", "cagan-review (does the work flow from a real strategy, or jump vision→features?)"]
---

# Cagan's Product Strategy

## Core idea

Between the product **vision** (the future you're trying to create, 2–5 years out) and the **product** itself (the specific things you build) sits the **product strategy**: *how* you make the vision real while meeting the needs of the business as you go. This is the canonical "missing middle." Teams that skip it jump straight from an inspiring vision to a feature backlog — and end up building beautifully-specified solutions to the wrong problems.

> "Vision vs. strategy is analogous to the difference between leadership and management. Leadership inspires and sets the direction, and management helps us get there. The product vision needs to be *inspiring*, and the product strategy needs to be *focused*."
> — Marty Cagan, [Vision vs. Strategy](https://www.svpg.com/vision-vs-strategy/), SVPG

Strategy is not a roadmap and it is not a list of features. It is the set of *choices* — which bets, for whom, in what sequence, driven by what insight — that make the vision achievable.

## The four pillars of product strategy

Cagan frames product strategy as deep work on four elements:

### 1. Focus
*Choosing the few things that truly matter — and therefore everything you won't do.*

Focus is the hardest and most important pillar. A strategy that pursues everything is not a strategy. The test of focus is not the list of what you're doing; it's the list of what you're deliberately *not* doing this period, and why.

> "Focus means choosing. Deciding what few things you really need to do, and therefore all the things you won't do."
> — Marty Cagan, [Product Strategy – Focus](https://www.svpg.com/product-strategy-focus/), SVPG

### 2. Insights
*The leverage that makes the bet non-obvious.*

Insights come from study and thought — analyzing data, learning from customers, and understanding business dynamics, company capabilities, new technologies, the competitive landscape, and how the market is evolving. The strongest strategies are powered by one or more insights a competitor doesn't have or hasn't acted on. An insight is *why this bet, now, will work* — not a restatement of the problem.

### 3. Actions
*Converting insight into objectives for teams.*

Once you know what's critically important and where the opportunities are, you decide which objectives to pursue, assign them to which product teams, and give those teams the strategic context to solve the problems themselves. This is where strategy meets sequencing: which segment first, which bet first, what order de-risks the vision fastest.

### 4. Management
*Strategy is never static.*

Product strategy requires active management, choice, thinking, and effort over time. Insights age, markets move, and bets get resolved (won or lost). A strategy written once and filed away has already begun to rot.

## Strategy and the success definition

A bet you can't measure isn't a bet — it's a hope. Cagan's "actions" pillar connects strategy to **objectives** (often expressed as OKRs) and, at the product level, to a **North Star metric** with supporting input metrics. The strategy artifact should end by naming what *winning* looks like: the one metric that captures whether the bet is paying off, plus the leading indicators teams can move and at least one guardrail that says "not at any cost." (See [`north-star-metric.md`](north-star-metric.md).)

## How to use it (the strategy artifact)

A strong product strategy artifact answers, in order:

1. **The bet** — the few things we're choosing to do, stated as a focused wager, *and* the things we're explicitly not doing.
2. **Segment & sequencing** — who we optimize for first, and the order of bets that de-risks the vision fastest.
3. **The insight** — the non-obvious reason this bet will work now: what we know (from data, customers, tech, market) that makes this more than a guess.
4. **Success definition** — North Star + 2–4 input metrics + at least one guardrail; what evidence would tell us the bet is winning or losing.
5. **Trade-offs** — what we're sacrificing by making this bet, named honestly.

## Common failure modes

- **Vision-to-features leap:** an inspiring vision wired directly to a backlog, with no stated bet or sequencing in between.
- **Strategy as roadmap:** a list of dated features mistaken for a set of strategic choices.
- **No focus:** "our strategy is to grow / win the market / delight users" — a slogan, not a choice. No stated *won't-do*.
- **Insight-free:** the bet rests on no privileged knowledge; anyone with the same vision would make the same move.
- **Unmeasurable:** no success definition, so the bet can never be judged won or lost.

## Application in pstack

- **/strategy:** Produces `01-strategy.md` — the focused bet, segment & sequencing, the insight, and the success definition. It is the gated middle: `/prd` will not run until the strategy scores ≥ 2.5, so the bet is pressure-tested before any spec is written.
- **/opportunity:** A per-bet, optional discovery assessment that pressure-tests one bet the strategy chose against the four risks before it becomes a PRD. (See [`cagan-discovery.md`](cagan-discovery.md).)
- **/cagan-review:** Checks that the work flows vision → strategy → product, not vision → features.

---

## Sources & further reading

- Cagan, M. — ["Product Strategy – Overview"](https://www.svpg.com/product-strategy-overview/), SVPG.com (free article)
- Cagan, M. — ["Product Strategy – Focus"](https://www.svpg.com/product-strategy-focus/), SVPG.com (free article)
- Cagan, M. — ["Vision vs. Strategy"](https://www.svpg.com/vision-vs-strategy/), SVPG.com (free article)
- Cagan, M. — *Inspired: How to Create Tech Products Customers Love*, 2nd ed. (2018, Wiley) and *Transformed* (2024, Wiley)
- Cagan, M. — interview on [The Product Experience](https://www.mindtheproduct.com/product-vision-and-strategy-marty-cagan-on-the-product-experience-part-1-of-2/), Mind the Product (free)

*License note: All Cagan quotes above are from his freely published SVPG articles. Paraphrased content follows the framework's published descriptions (focus / insights / actions / management).*
