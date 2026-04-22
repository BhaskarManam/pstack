---
name: pstack-upgrade
description: "Pull the latest pstack, re-run setup, and show a diff of new and changed skills. Keeps the install current without losing user config."
user-invocable: true
model: claude-sonnet-4-6
---

# /pstack-upgrade

You upgrade the user's pstack installation to the latest version while preserving their user profile, feedback logs, and project artifacts.

---

## Step 1 — Locate the pstack install

Check symlinks in `~/.claude/skills/` to find where pstack is installed. The pstack directory is the one containing `setup`, `CHANGELOG.md`, and `skills/`.

Common locations:
- `~/.claude/skills/pstack/` (if installed as a subdirectory)
- Wherever `~/.claude/skills/vision` symlinks to (parent of `skills/vision/`)

If the install directory cannot be found, tell the user and stop: *"Can't locate your pstack install. Run `ls -la ~/.claude/skills/` and tell me where pstack lives."*

---

## Step 2 — Check git status

Run `git -C {install_dir} status`. If there are uncommitted local changes, warn the user:

> "Your pstack install has local changes. Upgrading will pull from origin — local changes could conflict. Proceed? (yes/no)"

Wait for confirmation before continuing.

---

## Step 3 — Record current version

Read `{install_dir}/CHANGELOG.md` and note the current version (first version header).

Run `git -C {install_dir} log --oneline -5` to note the last 5 commits.

---

## Step 4 — Pull latest

Run: `git -C {install_dir} pull --ff-only origin main`

If pull fails (diverged, conflict), tell the user:

> "Pull failed — your local branch has diverged from origin. You may need to reset: `git -C {install_dir} reset --hard origin/main` (this will lose any local changes). Or contact the pstack maintainer."

Do not run `reset --hard` without explicit user approval.

---

## Step 5 — Diff new skills and changes

Compare the skills before and after pull:

- **New skills**: skill directories in `skills/` that weren't there before
- **Updated skills**: `SKILL.md` files with a newer modification date
- **New framework files**: files in `knowledge/frameworks/` added since last pull
- **New rubrics or calibration files**: same

Present the diff clearly.

---

## Step 6 — Re-run setup

Run `{install_dir}/setup` to:
- Re-symlink any new skills into `~/.claude/skills/`
- Update the pstack block in `~/.claude/CLAUDE.md` with the new version

If setup fails, report the error and suggest manual steps.

---

## Step 7 — Present summary

```
## pstack upgraded

Previous version: {old version}
New version: {new version}

New skills:
  + /{skill-name} — {one-liner from SKILL.md}

Updated skills:
  ~ /{skill-name} — {what changed, from CHANGELOG.md}

New knowledge:
  + {framework or rubric file} — {TL;DR}

Your profile and project artifacts are unchanged.

Next: restart your Claude Code session for new skills to appear in autocomplete.
```

---

## Rules

- Never run `git reset --hard` without explicit user approval
- Never overwrite `~/.config/pstack/user-profile.yaml` — user data is never touched by upgrade
- Never overwrite `feedback/*-log.yaml` files — user feedback is never touched
- If the user's pstack was installed via clone rather than the primary path, adapt the location detection
