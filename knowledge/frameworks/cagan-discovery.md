---
tldr: "Every product faces four risks before building: value, usability, feasibility, viability. Reduce all four during discovery—before committing engineering resources."
use-when: ["PRD (risks & assumptions section — tag each with its primary risk type)", "cagan-review (four risks lens applied to any artifact)"]
---

# Cagan's Four Risks of Product Discovery

## Core idea

Strong product teams don't just build well—they discover what to build. At the heart of discovery is de-risking four categories of failure before committing to engineering. Most teams default to de-risking feasibility (can we build it?) while neglecting value and viability, which are the more common causes of product failure.

From Marty Cagan at SVPG:

> "At the core of product discovery are four major risks with everything you pursue: value, usability, feasibility and viability."
> — Marty Cagan, [The Four Big Risks](https://www.svpg.com/four-big-risks/), SVPG

## The four risks

### 1. Value risk
*Will customers buy it, or users choose to use it?*

The question is not "do customers want a solution to this problem?" but "will they want *this* solution enough to switch, pay, or change behavior?" Many products solve real problems but offer insufficient value relative to alternatives (including doing nothing).

Discovery technique: customer interviews, demand testing, prototypes with real users.

### 2. Usability risk
*Can users figure out how to use it?*

Even valuable products fail if users can't navigate them. Usability risk is not about aesthetics—it's about whether users can accomplish the job without instruction, support, or frustration.

Discovery technique: usability testing, task analysis, prototype walkthroughs.

### 3. Feasibility risk
*Can our engineers build what we need with the time, skills, and technology we have?*

Teams often underestimate the difficulty of what they're proposing. This is the one risk teams naturally over-invest in de-risking—because engineers are in the room.

Discovery technique: technical spikes, architecture reviews, proof-of-concept builds.

### 4. Business viability risk
*Does this solution work for the various aspects of our business?*

Will legal approve it? Does it conflict with partnerships, pricing, or brand? Can we support it post-launch? Can stakeholders actually back it? "Stakeholders" here means legal, finance, sales, marketing, customer success—not just executives.

Discovery technique: stakeholder review, legal/compliance check, financial modeling.

## The four questions in plain language

| Risk | Question |
|---|---|
| Value | Will customers buy it? |
| Usability | Can customers use it? |
| Feasibility | Can we build it? |
| Viability | Can our stakeholders support it? |

## How to use it

**Tag roadmap items by primary risk.** When you write a PRD or add an item to the backlog, identify which of the four risks is the biggest unknown. This forces discovery effort toward the highest uncertainty rather than toward comfortable technical exploration.

- Value risk → prioritize customer interviews and demand tests
- Usability risk → prioritize prototype testing with target users
- Feasibility risk → prioritize technical spikes
- Viability risk → loop in legal, finance, partnerships early

**Don't skip viability.** Cagan added viability to the original three (value, usability, feasibility from *Inspired* 1st edition) specifically because teams consistently overlooked business constraints and got blindsided late in development.

## Common failure modes

- Spending discovery budget almost entirely on feasibility (because engineers are available)
- Conflating "users want this" with "users will switch to this" (value risk is harder than it looks)
- Treating viability as a post-development gate rather than a discovery input
- Writing risks as general statements ("market competition") rather than tagging which of the four applies

## Application in pstack

- **PRD risks section:** Every material risk should be tagged to one of the four categories. If a PRD has only feasibility risks listed, that's a red flag.
- **/cagan-review:** The review applies all four lenses to the artifact. It checks whether discovery evidence exists for each risk type before the team builds.

---

## Sources & further reading

- Cagan, M. — ["The Four Big Risks"](https://www.svpg.com/four-big-risks/), SVPG.com (free article)
- Cagan, M. — *Inspired: How to Create Tech Products Customers Love*, 2nd ed. (2018, Wiley); Chapter on Product Discovery
- Cagan, M. — ["Product Risk Taxonomies"](https://www.svpg.com/product-risk-taxonomies/), SVPG.com (extended taxonomy)
- RoadmapOne — ["SVPG's Four Product Risks"](https://roadmap.one/blog/posts/blog6-6-svpg-product-risks/) (synthesis with application examples)

*License note: All Cagan quotes above are from his freely published SVPG articles. Paraphrased content follows the framework's published descriptions.*
