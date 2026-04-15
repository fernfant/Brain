---
name: kb-index
description: Rebuilds the wiki index, glossary, and category pages in the style of Wikipedia. Use this skill whenever the user wants to rebuild or refresh the wiki index, update the glossary, regenerate category pages, or run kb-index. Also runs automatically after kb-compile. Trigger on "rebuild index", "update index", "refresh wiki", "regenerate categories", or "kb-index".
---

# kb-index

Rebuild the wiki's navigation and discovery layer — index, glossary, and categories — in the style of Wikipedia. Fully automatic.

## What gets built

1. `wiki/index.md` — Main portal page (like Wikipedia's Main Page)
2. `wiki/glossary.md` — Alphabetical glossary of all concept pages
3. `wiki/categories/<Category>.md` — One page per category

---

## Step 1 — Scan the wiki

Read all `.md` files under `wiki/`, excluding `index.md`, `glossary.md`,
`lint-report.md`, and anything under `wiki/categories/`, `wiki/analyses/`,
`wiki/comparisons/`, or `wiki/reports/`. For each file extract:
- **Path** relative to `wiki/`
- **Title** (first `# Heading`, or filename)
- **Tags** from YAML frontmatter
- **Description** — Summary opening line or first non-heading sentence
- **Type** — `source` (in `wiki/sources/`) or `concept` (wiki root)
- **date_ingested** — from frontmatter if present

---

## Step 2 — Build `wiki/index.md`

```markdown
---
tags:
  - index
updated: YYYY-MM-DD
---

# Wiki — Main Page

> A personal knowledge base of N articles across N sources and N concepts.

## Recently added
(Last 5 ingested sources, most recent first)
- [[sources/slug]] — one-line description (ingested YYYY-MM-DD)

## From the sources
2–3 "Did you know?" teasers from the most recently ingested sources.

## Browse by category
| Category | Articles | Description |
|---|---|---|
| [[categories/Name]] | N | one-line description |

## All articles
### Sources
Alphabetical list with one-line descriptions.

### Concepts
Alphabetical list with one-line descriptions.
```

---

## Step 3 — Build `wiki/glossary.md`

Alphabetical, one entry per concept page, definition from `## Description`.

```markdown
---
tags:
  - glossary
updated: YYYY-MM-DD
---

# Glossary

## A
**[[Name]]** — one-sentence definition

## B
...
```

Skip letters with no entries.

---

## Step 4 — Build category pages

One page per category at `wiki/categories/<Name>.md`. Infer categories from
content clusters. Aim for 4–8 categories. It's fine for articles to appear
in multiple categories.

Preserve existing `## Key Insights` sections — only update the article list
and descriptions, not the synthesis content.

```markdown
---
tags:
  - category
---

# Category: <Name>

<One sentence describing what this category covers.>

## Articles in this category
- [[sources/slug]] — one-line description
- [[ConceptName]] — one-line description

## Related categories
- [[categories/Other]]

## Key Insights
(Preserve existing; only add if none exists)
```

---

## Step 5 — Update cross-links

Scan wiki pages for plain-text mentions of other wiki page titles that aren't
already wikilinks. Convert unambiguous matches. Don't over-link generic words.

---

## Output

```
Rebuilt wiki index:
  - wiki/index.md (N sources, N concepts)
  - wiki/glossary.md (N entries)
  - wiki/categories/ (N pages)

Cross-links added: N across N pages
```
