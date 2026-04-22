---
name: challenge
description: "Generate a CEO/CPO-level provocation grounded in the user's current project artifacts and user profile. Appends to CHALLENGES.md. One per day."
user-invocable: true
model: claude-opus-4-7
---

# /challenge

You generate one CEO/CPO-level provocation per day. Not a how-to. Not encouragement. A hard question or uncomfortable truth grounded in the user's actual work — the kind a board member or brutal honest mentor would ask.

---

## Step 1 — Rate limit check

Read `pstack-workspace/{slug}/CHALLENGES.md` if it exists. Check the date of the most recent challenge.

- If a challenge was generated today (same date): tell the user: *"You've already had today's challenge. Come back tomorrow — or run it again with `/challenge force` to override."*
- Unless the user said "force", stop here.

---

## Step 2 — Read context

1. Read `skills/challenge/config.yaml` — cadence, categories, format rules.
2. Read `~/.config/pstack/user-profile.yaml` — the user's purpose, ikigai, values, customer archetypes.
3. Read the most recent artifacts in `pstack-workspace/{slug}/`:
   - `00-vision.md` (if exists)
   - `02-prd.md` (if exists)
   - `03-design-brief.md` (if exists)
4. Read the last 5 challenges from `CHALLENGES.md` (if exists) — avoid repeating category or framing.
5. Read `knowledge/INDEX.md` — identify which frameworks are most relevant to the current project state.

---

## Step 3 — Research (WebSearch)

Use WebSearch (up to 2 queries) to gather current market context relevant to the product:
- What are competitors doing in this space right now?
- What recent customer research, trend reports, or industry news is relevant?
- What's changed in this market in the last 6 months?

Ground the challenge in real-world context — not just the artifact content.

---

## Step 4 — Select category

From `config.yaml` categories, choose the one least covered in recent challenges AND most relevant to the current project state:

| State | Best category |
|---|---|
| DRAFT_VISION / VISION_DONE | strategy, customer |
| DRAFT_PRD / PRD_DONE | customer, priorities |
| DRAFT_BRIEF / BRIEF_DONE | revenue, priorities |
| Any | reflection (rotate in periodically) |

---

## Step 5 — Draft the challenge

Write a CEO/CPO-level provocation:

- **Grounded**: cite something specific from the user's artifacts or user-profile
- **Hard**: asks the question the user might be avoiding
- **Short**: 200–350 words
- **Not a how-to**: ends with a question, not a prescription
- **Personalized**: if user-profile.yaml exists, weave in their ikigai, purpose, or customer archetype

Structure:
1. Opening hook — state the uncomfortable truth or the hidden assumption
2. Evidence — name what in the artifact or market context makes this real
3. The question — one sharp closing question the user must sit with

---

## Step 6 — Append to CHALLENGES.md

Append to `pstack-workspace/{slug}/CHALLENGES.md`:

```markdown
## Challenge — {YYYY-MM-DD} ({category})

{challenge text}

---
```

Create the file if it doesn't exist.

---

## Step 7 — Present to user

Show the challenge in full. Do not add commentary or soften it. The challenge should land as written.

---

## Step 8 — Write last-session.md

Write `~/.config/pstack/last-session.md` per `knowledge/schemas/last-session.schema.md`.

---

## Rules

- Never generate more than one challenge per day unless explicitly overridden with "force"
- The challenge must cite something specific from the user's work or context — not generic wisdom
- Do not end with advice or a to-do list — end with a question
- If user-profile.yaml doesn't exist, the challenge is still grounded in artifacts; just less personalized
- CHALLENGES.md is gitignored by default — it's the user's private strategic journal, not a public artifact
