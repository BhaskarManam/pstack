# feedback/

Per-skill user feedback logs. One file per generator skill.

```
feedback/
├── vision-log.yaml        # feedback from /vision runs
├── prd-log.yaml           # feedback from /prd runs
└── design-brief-log.yaml  # feedback from /design-brief runs
```

**These files are gitignored.** They capture personal feedback from your skill runs and are not pushed to the public repo.

**Schema:** `knowledge/schemas/feedback-log.schema.yaml`

**Read by:** `/pstack-learn` — distills patterns across entries to propose framework improvements.

**Written by:** Generator skills at the end of each run, after presenting the artifact.

---

The log files will be created automatically on first use. To initialize them manually:

```bash
touch feedback/vision-log.yaml
touch feedback/prd-log.yaml
touch feedback/design-brief-log.yaml
```

Each file is a YAML list. Entries are appended, never overwritten.
