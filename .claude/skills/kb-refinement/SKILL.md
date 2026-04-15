---
name: kb-refinement
description: >
  Refines all wiki source and category pages in the Brain knowledge base at
  /Users/fernando/Brain/wiki/. For each page it tightens the Summary, removes
  redundancies from Key Points, and adds a rich analytical "## Key Insights"
  section — not just restatements of facts but interpretations: what the data
  means, what trends it signals, what risks or opportunities it surfaces.
  Use this skill whenever the user says /refinement, asks to "refine the wiki",
  "add insights to wiki pages", "improve wiki summaries", or wants to enrich
  existing wiki content with analysis. Supports --new-only flag to refine only
  pages ingested since the last refinement run.
---

# kb-refinement — Wiki Refinement Skill

## Purpose

Transform wiki pages from summaries of facts into analytical knowledge assets.
Every source page and every category page gets:
- A tighter, non-redundant Summary
- Clean, non-overlapping Key Points
- A **Key Insights** section with real analysis — patterns, implications,
  risks, opportunities, comparisons to other periods or sources

---

## Scope

**Default (no arguments)**: refine all source pages and all category pages.

**`--new-only`**: refine only source pages whose `date_ingested` is after the
most recent refinement entry in `log.md`. Check the log for the last
`## [YYYY-MM-DD] refinement` entry and use that date as the cutoff.
Category pages are always skipped in `--new-only` mode (they need a full
cross-source pass to be meaningful).

---

## Execution Order

Process source pages first, then category pages (full mode only). Category
insights must synthesise across refined source content.

---

## Step 1 — Refine Source Pages (`wiki/sources/*.md`)

### Read the page
Note: period/context, all numbers and metrics, comparisons to targets/prior
periods/competitors, events and decisions mentioned.

### Rewrite the Summary
- 2–4 sentences max
- Narrative context, not metric recitation
- Answers: what period? dominant story? outcome?

### Clean the Key Points
- Remove bullets that duplicate the Summary
- Each bullet = one distinct, non-overlapping data point
- Include context (vs target, WoW, YoY) where present

### Add or update `## Key Insights`
Place immediately after `## Key Points`, before `## Entities & Concepts`.

Write 3–6 bullets:
```
- **[Short title]**: [2–4 sentences. Specific numbers. What it means, what
  it signals, what the risk or opportunity is, how it compares to a prior
  period or baseline.]
```

Quality test: would a smart analyst already know this from the Key Points?
If yes, it's not an insight — go deeper.

If a `## Key Insights` section already exists, review and improve it rather
than replacing wholesale — preserve good insights, strengthen weak ones.

### Preserve unchanged
- All YAML frontmatter
- `## Entities & Concepts` section and wikilinks
- `## Quotes / Excerpts` section

---

## Step 2 — Refine Category Pages (`wiki/categories/*.md`) — full mode only

### Read the page and referenced sources
Category insights must draw on actual source content.

### Clean the article list
One tight sentence per article; no redundancy.

### Add or update `## Key Insights`
4–8 bullets synthesising patterns, tensions, and open questions across all
articles in the category. Not a list of article summaries — cross-source
analysis only.

```
- **[Short title]**: [Rich synthesis — 2–4 sentences, specific, drawing on
  data from multiple sources where possible]
```

### Preserve unchanged
- All existing links and wikilink structure
- Page title and YAML frontmatter

---

## Step 3 — Log the run

```
## [YYYY-MM-DD] refinement | wiki/sources/* + wiki/categories/*
- pages_refined: N
- insights_added: N
- mode: full | new-only
```

---

## Quality bar

Re-read 2–3 Key Insights sections before finishing:
- Are these insights or reworded facts?
- Do they use specific numbers?
- Do they say something a reader wouldn't immediately see from the raw bullets?

If any fail, rewrite before saving.
