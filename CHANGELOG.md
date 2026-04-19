# pstack changelog

All notable changes to pstack are documented here.
Format: [Semantic Versioning](https://semver.org/).

---

## [Unreleased] — v0.1.0

### Added
- Dual distribution: gstack-style install (`./setup` + symlinks) and `.claude-plugin` format
- 14 skills: vision, prd, design-brief, critique, cagan-review, shreyas-review, lenny-review, bhaskar-review, challenge, onboard, pstack-status, pstack-upgrade, pstack-help, pstack-learn
- Two-tier CLAUDE.md memory (user-level identity + project-level pstack commands)
- Five architecture pillars: context persistence, knowledge quality, skill design patterns, autonomy, performance
- Internal draft→critique→revise quality loop in every generator skill
- Structured YAML schemas for personas, rubrics, challenges, user-profile, artifact-meta
- Knowledge calibration sets (score-2 / score-3.5 / score-5) per artifact type
- `knowledge/INDEX.md` for lazy-loading framework files
- `~/.config/pstack/` global state (user-profile.yaml, last-session.md, quality-log.yaml)
- `CONVERSATIONS.md` + `./publish-docs` privacy pipeline
- `CHALLENGES.md` per-project (gitignored by default)
- `ROADMAP.md` and `CONVERSATIONS.md` as living memory docs
- Eval harness skeleton in `tests/`
