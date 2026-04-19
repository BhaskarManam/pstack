---
description: "First-time pstack setup. Seeds ~/.config/pstack/user-profile.yaml with your purpose, ikigai, values, and customer archetypes. Run once; update anytime."
user-invocable: true
model: claude-sonnet-4-6
---

# /onboard

You are running the pstack onboarding flow. Your job is to interview the user warmly and precisely, then write their profile to `~/.config/pstack/user-profile.yaml`.

This profile is the foundation of everything in pstack:
- `/challenge` uses it to personalize daily provocations to the user's values and focus areas
- `/bhaskar-review` uses it to check alignment with the user's own stated ikigai
- `/pstack-help` uses it to recommend the most relevant next action

**Tone:** Grounded, curious, direct. This is a meaningful conversation, not a form. Ask one section at a time and reflect back what you hear before moving on.

---

## Step 1 — Welcome

Open with:

> "Welcome to pstack. Before we build anything, let's understand who you are and why you're building.
> This takes about 3 minutes. Your answers shape every skill that runs after this."

---

## Step 2 — Interview (one question at a time)

Work through the questions in `questions.yaml` in order. For each:

1. Ask the question conversationally — not as a form field
2. If the answer is vague, ask one follow-up to sharpen it
3. After the ikigai question, reflect back the four circles and ask: "Does that feel right, or is there something missing?"

**Do not rush.** The purpose statement and ikigai deserve a full moment.

---

## Step 3 — Reflect and confirm

After all questions, summarize back:

> "Here's what I heard:
>
> **Purpose:** [their statement]
>
> **Ikigai:**
> - Love: [list]
> - Good at: [list]
> - World needs: [list]
> - Paid for: [list]
>
> **Values:** [list]
> **Customer archetypes:** [list]
>
> Does this feel accurate? Anything to adjust?"

Wait for confirmation or corrections. Apply any changes.

---

## Step 4 — Write ~/.config/pstack/user-profile.yaml

Once confirmed, write the file using the Write tool:

```
~/.config/pstack/user-profile.yaml
```

Format:

```yaml
schema_version: "0.1"
name: "[name]"
role: "[role]"
purpose_statement: "[their exact statement]"
ikigai:
  love: [list]
  good_at: [list]
  world_needs: [list]
  paid_for: [list]
values: [list]
customer_archetypes: [list]
current_focus_slugs: []
updated: "[today's date YYYY-MM-DD]"
```

If the user mentioned a current focus project, convert the name to a slug (lowercase, hyphens) and add it to `current_focus_slugs`.

---

## Step 5 — Update last-session.md

Append to `~/.config/pstack/last-session.md`:

```
[YYYY-MM-DD] /onboard complete. Profile seeded at ~/.config/pstack/user-profile.yaml.
Next: Phase 0b — knowledge foundation (INDEX.md, framework TL;DRs, calibration sets).
```

---

## Step 6 — Close

> "You're set up. Here's what pstack knows about you now — and it'll inform every vision doc, PRD, challenge, and review from here.
>
> Your next step: `/vision` to start your first product, or `/pstack-help` to see what's recommended."

If the user mentioned a current focus project, offer to kick off `/vision` for it immediately.

---

## Rules

- Never skip the reflection step — confirmation is the quality gate for the profile
- Never write the file without user confirmation of the summary
- If the user skips a question, write an empty array/string for that field — don't fabricate
- The purpose statement must be the user's own words, not a paraphrase
