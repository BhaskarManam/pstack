# Contributing to pstack

pstack grows through community contributions. The highest-value contributions are:

1. **New framework distillations** — adding a product-leader framework to `knowledge/frameworks/`
2. **New persona reviewers** — adding a product thinker's lens to `skills/<name>-review/`
3. **New challenge seeds** — adding CEO/CPO provocations to `knowledge/challenges/`
4. **Rubric improvements** — sharpening scoring dimensions in `knowledge/rubrics/`

---

## Adding a framework

1. Create `knowledge/frameworks/<name>.md`
2. Required structure:
   ```markdown
   ---
   tldr: "One sentence that captures the essence."
   use-when: ["skill-name-1", "skill-name-2"]
   ---

   [Full distillation in pstack's own words]

   ---
   ## Sources & further reading
   - [Original source](url) — Author Name
   ```
3. Add a row to `knowledge/INDEX.md`
4. If it's the primary framework for an existing skill, update that skill's `framework.md` to reference it

**Attribution rule:** Every framework file must credit the originator by name with a link. No verbatim copying of copyrighted content — paraphrase, or use curated direct quotes with explicit source + license verification.

---

## Adding a persona reviewer

1. Create `skills/<name>-review/persona.yaml` — must validate against `knowledge/schemas/persona.schema.yaml`
2. Create `skills/<name>-review/SKILL.md` — copy the template from any existing persona skill
3. Add a row to the command table in `README.md`
4. Update `CLAUDE.md.snippet` with the new command
5. Add a symlink entry to the `SKILLS` list in `setup`
6. Add to `knowledge/INDEX.md` under "Personas"

**Persona quality bar:** The persona must have at least 3 published books, essays, or talks that can be cited. All `signature_questions` and `common_flags` must be traceable to the persona's documented thinking.

---

## Adding a challenge seed

1. Add an entry to the appropriate `knowledge/challenges/<lens>.yaml`
2. Must match the `challenge.schema.yaml` — required fields: `id`, `lens`, `prompt`, `why_it_matters`, `expected_action`
3. Prompt must reference a specific artifact section (not be generic)

---

## Pull request checklist

- [ ] `./setup` runs without errors (test on a clean directory)
- [ ] All new YAML files validate against their schema (`knowledge/schemas/`)
- [ ] Attribution footer present on all new framework/persona files
- [ ] `knowledge/INDEX.md` updated if new framework or persona added
- [ ] `CHANGELOG.md` updated under `[Unreleased]`
- [ ] No verbatim copyrighted content

---

## Code of conduct

Build with honesty, attribution, and respect for originators. pstack exists to distill and extend great product thinking — not to pass it off as our own.
