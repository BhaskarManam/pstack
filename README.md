# pstack

> From idea to design brief in an afternoon — with a senior PM, four world-class reviewers, and a daily CEO/CPO challenge in the loop.

pstack is a [Claude Code](https://claude.ai/code) skill pack for product builders. Inspired by [Garry Tan's gstack](https://github.com/garrytan/gstack), it distils the product-thinking canon — Cagan, Doshi, Rachitsky, Hustle Badger, JTBD, North Star, ikigai — into a set of skills you invoke directly in your AI-assisted workflow.

---

## Install

### Option A — gstack-style (recommended)

```bash
git clone --single-branch --depth 1 https://github.com/bhaskarmanam/pstack.git \
  ~/.claude/skills/pstack
cd ~/.claude/skills/pstack && ./setup
```

Flat commands: `/vision`, `/prd`, `/design-brief`, …

### Option B — Claude Code plugin

```bash
git clone https://github.com/bhaskarmanam/pstack.git
claude --plugin-dir ./pstack
```

Namespaced commands: `/pstack:vision`, `/pstack:prd`, …

**Start here after install:**

```
/onboard
```

---

## Commands

| Command | What it does |
|---|---|
| `/vision` | Draft or refine a product vision doc |
| `/strategy` | Turn the vision into a focused bet: segment, sequencing, the insight, success definition |
| `/opportunity` | Optional per-bet discovery assessment (four risks, riskiest assumption, kill criteria) before a PRD |
| `/north-star` | Optional metric design session: one North Star Metric + 3–5 inputs with causal story + guardrails |
| `/prd` | Draft a rigorous PRD grounded in the strategy |
| `/design-brief` | Produce a design brief from a PRD |
| `/critique` | Score any artifact against its rubric; list top gaps |
| `/cagan-review` | Review through Marty Cagan's lens (four risks, outcomes > output) |
| `/shreyas-review` | Review through Shreyas Doshi's lens (LNO, high agency) |
| `/lenny-review` | Review through Lenny Rachitsky's lens (growth loops, activation) |
| `/ravi-review` | Review through Ravi Mehta's lens (12 competencies, outcome accountability, strategy stack) |
| `/julie-review` | Review through Julie Zhuo's lens (problem-first, intentionality, simplicity as discipline) |
| `/bhaskar-review` | Review through a heart-centric, purpose-led, ikigai lens |
| `/challenge` | Surface a daily CEO/CPO provocation grounded in your current project |
| `/onboard` | Seed your user profile for cross-project personalization |
| `/pstack-status` | Dashboard across all your pstack projects |
| `/pstack-upgrade` | Pull latest pstack + diff new skills |
| `/pstack-help` | Context-aware next-action recommendation |
| `/pstack-learn` | Distil feedback logs into framework improvement proposals |

---

## How it works

**The gated spine** is `vision → strategy → PRD → design brief`. Each stage requires the prior artifact to score ≥ 2.5 on its rubric — so you can't write a PRD until the *bet* itself has survived a scored critique. That's the point: most tools generate artifacts; pstack refuses to let you spec the wrong thing. `/opportunity` is an optional, per-bet discovery step between strategy and PRD — it pressure-tests one risky bet and gates nothing.

**Generators** (`/vision`, `/strategy`, `/prd`, `/design-brief`) run an internal draft→critique→revise loop before surfacing output — you only see post-revision work. Each reads prior artifacts for context, interviews you with 3-5 focused questions, references the knowledge base, then writes a numbered artifact to `./pstack-workspace/<project>/`.

**Reviewers** (`/critique`, `/*-review`) are read-only. Output goes to `pstack-workspace/<slug>/reviews/`. They never modify your source artifacts.

**Personas** are structured `persona.yaml` files — adding a new reviewer is a one-file drop.

**Challenges** fire daily, read your current artifacts, and produce a provocation grounded in *this product, right now* — not generic leadership advice.

---

## What's inside

```
knowledge/
├── INDEX.md           # Quick-reference for all frameworks
├── frameworks/        # Distilled product-leader canon
├── rubrics/           # YAML scoring rubrics per artifact type
├── calibration/       # Score-2 / score-3.5 / score-5 reference artifacts
├── challenges/        # 40+ CEO/CPO lens seeds across 6 lenses
└── schemas/           # YAML/JSON schemas for all structured files

skills/                # 19 skill directories (one per command)
tests/                 # Eval harness with golden snapshots
feedback/              # Per-skill user feedback logs (gitignored)
```

---

## Roadmap

See [ROADMAP.md](ROADMAP.md). v0.2.1 shipped three new skills: `/ravi-review`, `/julie-review`, and `/north-star`. Next: `/metrics-plan` and `/pstack-status` enhancements. v0.3 adds team-mode.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). The highest-value contributions are new framework distillations, new persona reviewers, and new challenge seeds.

---

## Credits

pstack stands on the shoulders of:

- **Marty Cagan** — [SVPG / Inspired](https://www.svpg.com)
- **Shreyas Doshi** — [Writings and talks on product leadership](https://shreyasdoshi.com)
- **Lenny Rachitsky** — [Lenny's Newsletter](https://www.lennysnewsletter.com)
- **Hustle Badger** — [hustlebadger.com](https://www.hustlebadger.com)
- **Héctor García & Francesc Miralles** — Ikigai
- **Brené Brown** — Dare to Lead (heart-centric leadership)
- **Ravi Mehta** — [ravi-mehta.com](https://www.ravi-mehta.com) / [Reforge](https://www.reforge.com) (12 competencies, product strategy stack)
- **Julie Zhuo** — [The Making of a Manager](https://www.juliezhuo.com/book/manager.html) / [The Looking Glass](https://lg.substack.com) (design leadership, intentionality)
- **Garry Tan** — [gstack](https://github.com/garrytan/gstack) for the install pattern and inspiration

MIT License — see [LICENSE](LICENSE).
