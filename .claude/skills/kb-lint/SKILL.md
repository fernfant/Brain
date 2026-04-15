---
name: kb-lint
description: >
  Health-checks the Brain wiki at /Users/fernando/Brain/wiki/ and produces a
  lint report with specific fixes. Finds orphan pages (no inbound links),
  contradictions between sources, stale claims superseded by newer content,
  concepts mentioned repeatedly without their own page, broken wikilinks, and
  duplicate content across sources. Writes wiki/lint-report.md with prioritised
  issues and suggested actions. Use whenever the user says /lint, "health check
  the wiki", "find problems in the wiki", "audit the wiki", or "clean up the
  wiki". Run periodically — weekly is ideal — to prevent knowledge decay.
---

# kb-lint — Wiki Health Check

## Purpose

A wiki that isn't maintained decays. This skill is the maintenance pass —
it finds the issues that accumulate silently: orphan pages no one links to,
contradictions between sources that were added weeks apart, concepts mentioned
across a dozen pages but never given their own entry, wikilinks pointing
nowhere. Fix these and the wiki stays trustworthy and navigable.

---

## Step 1 — Build the link graph

Read every `.md` file under `wiki/` (excluding `lint-report.md`). For each file:
- Extract all `[[wikilinks]]` it contains (outbound links)
- Record the file as a node with its path and title

Build two maps:
- **outbound**: file → list of pages it links to
- **inbound**: page → list of files that link to it

A page is an **orphan** if `inbound[page]` is empty or contains only `index.md`
and `glossary.md` (index links don't count as real connections).

---

## Step 2 — Check for broken wikilinks

For every `[[Link]]` found anywhere in the wiki, verify that a corresponding
`.md` file exists under `wiki/`. Flag any link where no match is found.

Common causes: renamed files, typos, concept pages that were referenced before
being created.

---

## Step 3 — Find missing concept pages

Scan all source pages (`wiki/sources/*.md`) for recurring proper nouns,
named entities, and domain terms that appear in 2+ sources but have no
dedicated concept page in `wiki/`. These are high-value gaps — the wiki
is cross-referencing something without defining it.

Focus on: named tools, platforms, people, organisations, metrics, and
frameworks. Ignore generic words even if repeated.

---

## Step 4 — Detect contradictions

Compare claims across source pages that cover the same topic or time period.
Look for:
- Metrics reported differently for the same period
- Claims in newer sources that contradict or supersede older ones
- Sources that take opposing positions on the same question

For each contradiction found, identify: which pages, what the conflicting
claims are, and which source is likely more current or authoritative.

---

## Step 5 — Find stale content

Check source pages' `date_ingested` frontmatter. For pages ingested more than
90 days ago that reference forward-looking claims ("forecast", "planned",
"expected by", "upcoming"), flag them as potentially stale — the future they
described may now be the past.

Also check concept pages: if a concept page's `## Description` contradicts
information in a more recently ingested source page, flag it for update.

---

## Step 6 — Detect duplicate or near-duplicate sources

Compare source page summaries for high overlap. If two sources cover the
same topic with substantially similar content, flag them — one may be
redundant or they could be merged into a richer single page.

---

## Step 7 — Write `wiki/lint-report.md`

```markdown
---
tags:
  - lint
generated: YYYY-MM-DD
---

# Wiki Lint Report — YYYY-MM-DD

## Summary
- Orphan pages: N
- Broken wikilinks: N
- Missing concept pages: N
- Contradictions: N
- Stale claims: N
- Duplicate sources: N

Total issues: N | High priority: N | Medium: N | Low: N

---

## 🔴 High Priority

### Broken wikilinks
- `[[PageName]]` in `wiki/sources/foo.md` — no matching page exists

### Contradictions
- **[Topic]**: `wiki/sources/A.md` claims X; `wiki/sources/B.md` (newer) claims Y

---

## 🟡 Medium Priority

### Orphan pages
- `wiki/ConceptName.md` — linked from nowhere except index

### Missing concept pages
- "TermName" — appears in sources/A.md, sources/B.md, sources/C.md; no concept page

---

## 🟢 Low Priority

### Stale forward-looking claims
- `wiki/sources/foo.md` — "planned for Q2" ingested 2026-01-10; may be outdated

### Potential duplicates
- `wiki/sources/A.md` and `wiki/sources/B.md` — high content overlap

---

## Suggested next actions
1. [Most impactful fix first]
2. ...
```

Prioritise ruthlessly: broken links and contradictions are high; orphans and
missing concepts are medium; stale claims and duplicates are low.

---

## Step 8 — Log the run

Append to `/Users/fernando/Brain/log.md`:

```
## [YYYY-MM-DD] lint | wiki/
- issues_found: N
- high: N | medium: N | low: N
- report: [[wiki/lint-report]]
```
