# pstack

> From idea to design brief in an afternoon — with a senior PM, four world-class reviewers, and a daily CEO/CPO challenge in the loop.

pstack is a [Claude Code](https://claude.ai/code) skill pack for product builders. Inspired by [Garry Tan's gstack](https://github.com/garrytan/gstack), it distils the product-thinking canon — Cagan, Doshi, Rachitsky, Hustle Badger, JTBD, North Star, ikigai — into a set of skills you invoke directly in your AI-assisted workflow.

---

## Install

### Option A — gstack-style (recommended)

```bash
git clone --single-branch --depth 1 https://github.com/<username>/pstack.git \
  ~/.claude/skills/pstack
cd ~/.claude/skills/pstack && ./setup
```

Flat commands: `/vision`, `/prd`, `/design-brief`, …

### Option B — Claude Code plugin

```bash
git clone https://github.com/<username>/pstack.git
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
| `/prd` | Draft a rigorous PRD grounded in the vision |
| `/design-brief` | Produce a design brief from a PRD |
| `/critique` | Score any artifact against its rubric; list top gaps |
| `/cagan-review` | Review through Marty Cagan's lens (four risks, outcomes > output) |
| `/shreyas-review` | Review through Shreyas Doshi's lens (LNO, high agency) |
| `/lenny-review` | Review through Lenny Rachitsky's lens (growth loops, activation) |
| `/bhaskar-review` | Review through a heart-centric, purpose-led, ikigai lens |
| `/challenge` | Surface a daily CEO/CPO provocation grounded in your current project |
| `/onboard` | Seed your user profile for cross-project personalization |
| `/pstack-status` | Dashboard across all your pstack projects |
| `/pstack-upgrade` | Pull latest pstack + diff new skills |
| `/pstack-help` | Context-aware next-action recommendation |
| `/pstack-learn` | Distil feedback logs into framework improvement proposals |

---

## How it works

**Generators** (`/vision`, `/prd`, `/design-brief`) run an internal draft→critique→revise loop before surfacing output — you only see post-revision work. Each reads prior artifacts for context, interviews you with 3-5 focused questions, references the knowledge base, then writes a numbered artifact to `./pstack-workspace/<project>/`.

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

skills/                # 14 skill directories (one per command)
tests/                 # Eval harness with golden snapshots
feedback/              # Per-skill user feedback logs (gitignored)
```

---

## Roadmap

See [ROADMAP.md](ROADMAP.md). v0.2 adds `/strategy`, `/metrics-plan`, and two more persona reviewers. v0.3 adds team-mode.

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
- **Garry Tan** — [gstack](https://github.com/garrytan/gstack) for the install pattern and inspiration

MIT License — see [LICENSE](LICENSE).
