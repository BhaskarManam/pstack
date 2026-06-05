---
name: pstack-status
description: "Dashboard across all pstack projects: current state, artifact rubric scores, staleness, last challenge date. Read-only snapshot."
user-invocable: true
model: claude-sonnet-4-6
---

# /pstack-status

You generate a read-only status dashboard across all pstack projects the user is working on.

---

## Step 1 — Discover projects

Scan `pstack-workspace/` in the current directory for subdirectories containing `.pstack-meta.json`.

Also check any additional project directories if the user mentions them.

---

## Step 2 — Read each project

For each project directory found, read:
1. `.pstack-meta.json` — project name, slug, state, artifact list with scores and dates
2. The most recent artifact modification dates from the filesystem
3. `CHALLENGES.md` — date of the most recent challenge (if file exists)

---

## Step 3 — Compute staleness

An artifact is **stale** if it was last modified more than 14 days ago and the project is in an incomplete state (not BRIEF_DONE).

A challenge is **overdue** if the last challenge was more than 1 day ago (daily cadence) or 7 days ago (weekly cadence).

---

## Step 4 — Present the dashboard

Format:

```
## pstack status — {YYYY-MM-DD}

────────────────────────────────────────────────

### {Project Name} [{slug}]

State: {STATE_MACHINE_STATE}
Last active: {N} days ago

Artifacts:
  ✓ 00-vision.md         score: {X.X}/5  ({YYYY-MM-DD}) {STALE? ⚠️}
  ✓ 01-strategy.md       score: {X.X}/5  ({YYYY-MM-DD})
  ○ opportunity-{bet}.md score: {X.X}/5  ({YYYY-MM-DD})  (optional, per-bet)
  ✓ 02-prd.md            score: {X.X}/5  ({YYYY-MM-DD})
  ✗ 03-design-brief.md   (not started)

Reviews: {N} reviews in reviews/
Last challenge: {YYYY-MM-DD} — {N} days ago  {OVERDUE? ⚠️}

Next recommended action: {one-line recommendation based on state}

────────────────────────────────────────────────

### {Project 2 Name} ...

────────────────────────────────────────────────

Summary:
  {N} project(s) active
  {N} artifact(s) below passing floor (< 3.5) — consider /critique
  {N} challenge(s) overdue — run /challenge
```

---

## Step 5 — Surface recommendations

After the dashboard, list:
- Any artifact with score below 3.5 → recommend `/critique` and then revision
- Any project with stale artifacts → recommend resuming
- Any overdue challenges → recommend `/challenge`

---

## Rules

- This skill is read-only — it never writes to any artifact or meta file (except last-session.md)
- If no projects are found, tell the user how to start: *"No pstack projects found. Run `/vision` in your project directory to begin."*
- Do not hallucinate artifact scores — only report what's in `.pstack-meta.json`. If score is missing, show as "unscored — run /critique"
