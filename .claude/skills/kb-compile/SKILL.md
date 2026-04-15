---
name: kb-compile
description: Scans raw/ for new or changed files, summarizes them, and creates/updates Obsidian-compatible wiki pages, then triggers kb-index to rebuild the index. Use this skill whenever the user wants to ingest new sources, process new documents, update the wiki with new content, or run a compile/ingest pass. Trigger on any mention of "ingest", "compile", "process raw", "add to wiki", "new sources", or "update knowledge base" — even if they don't say "kb-compile" explicitly.
---

# kb-compile

Ingest new or changed files from `Raw/` into the wiki. Fully automatic — no human review needed.

## How it works

1. Read `log.md` to find already-processed files
2. Scan `Raw/` to identify new or changed files
3. For each new/changed file: read content, create a source summary page, update concept pages
4. Run kb-refinement on newly created source pages only
5. Append entries to `log.md`
6. Invoke `kb-index` to rebuild the index

---

## Step 1 — Identify what's new

Read `log.md` at `/Users/fernando/Brain/log.md`. Each processed file appears as:

```
## [2026-04-10] ingest | Raw/articles/foo.md
```

Extract already-processed paths. Scan `Raw/` recursively. Any file whose path
is not in the log is new. If a file has been modified since its log entry date
(use mtime), treat it as changed and reprocess it.

If `log.md` doesn't exist yet, create it (empty).

---

## Step 2 — Read each new file

Handle file types gracefully:
- **Markdown / text / HTML**: read directly
- **PDF**: use `pdftotext` if available, otherwise Python `pypdf`
- **Images**: describe visual content — layout, text, diagrams, key elements
- **Other**: do your best; note the file type in the wiki page

If a file can't be read, log it as `[unreadable]` and skip.

---

## Step 3 — Create a source summary page

Write `wiki/sources/<slug>.md` where `<slug>` is URL-friendly (lowercase, hyphens, no extension).

```markdown
---
tags:
  - source
source: "Raw/path/to/file.ext"
date_ingested: YYYY-MM-DD
type: article | pdf | image | webpage | other
---

# <Title>

## Summary
2–4 sentence narrative: what is this, what period/context, what's the dominant story?
(Avoid reciting metrics here — those go in Key Points)

## Key Points
- Distinct, non-overlapping data points with comparison context (vs target, WoW, YoY)

## Key Insights
- **[Insight title]**: [2–4 sentence analysis — what it means, what it signals,
  what risk or opportunity it surfaces. Not a restatement of Key Points.]

## Entities & Concepts
[[ConceptA]], [[PersonB]], [[TopicC]]

## Quotes / Excerpts
> Notable direct quotes (skip if none)
```

The `## Key Insights` section should be analytical, not factual. Ask: would a
smart reader already know this from the Key Points? If yes, push deeper.

---

## Step 4 — Update concept and entity pages

For each significant entity or concept in the source:

- **If the page exists**: append a bullet under `## Appearances` — do NOT
  overwrite or rewrite existing content; only add the new source link
- **If it doesn't exist**: create it:

```markdown
---
tags:
  - concept
---

# <Name>

## Description
One-sentence definition.

## Appearances
- [[sources/<slug>]] — one-line note on how this source relates
```

Only create pages for named entities and domain-specific concepts meaningfully
discussed — not generic terms.

---

## Step 5 — Append to log.md

```markdown
## [YYYY-MM-DD] ingest | Raw/path/to/file.ext
- wiki: [[sources/<slug>]]
- type: article | pdf | image | webpage | other
- hash: <first 8 chars of md5>
```

Append only — never modify existing entries.

---

## Step 6 — Rebuild the index

Invoke `kb-index` to rebuild `wiki/index.md`, the glossary, and category pages.

If `kb-index` is not available: "Run kb-index to rebuild the wiki index."

---

## Output

```
Processed N new files:
  - Raw/foo.pdf → [[sources/foo]]
  - Raw/bar.md  → [[sources/bar]]

Updated concept pages: [[ConceptA]], [[PersonB]]
Log updated. Running kb-index...
```

If nothing new: "No new files in Raw/. Wiki is up to date."
