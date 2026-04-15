---
name: kb-compare
description: >
  Compares two or more topics, sources, time periods, or concepts from the
  Brain wiki at /Users/fernando/Brain/wiki/ and produces a structured comparison
  page filed to wiki/comparisons/. Use whenever the user asks to compare things,
  wants a side-by-side view, asks "X vs Y", "how does X differ from Y",
  "which is better", or "contrast X and Y". Also trigger on /compare.
  Works across any domain in the wiki — WBR periods, Claude tools, SEO
  metrics, prompting frameworks, real estate segments, etc.
---

# kb-compare — Structured Comparison

## Purpose

Cross-source comparisons are one of the highest-value things a wiki can
produce — and one of the hardest to do in a single chat without persistence.
This skill reads the relevant wiki pages, builds a structured comparison,
and files it permanently so the analysis compounds.

---

## Step 1 — Parse the comparison request

Identify:
- **What is being compared**: two or more named topics, sources, time periods,
  or concepts
- **Comparison dimensions**: what aspects matter? (metrics, approach, outcome,
  time period, risk, cost, etc.) If the user hasn't specified, infer the most
  useful dimensions from the content.
- **Output format**: table (structured data), prose (nuanced narrative), or
  both. Default to both — table for at-a-glance, prose for depth.

---

## Step 2 — Read all relevant pages

For each item being compared:
- Find its primary wiki page(s) — concept pages and/or source pages
- Read them fully
- Note: key metrics, dates, claims, positions, outcomes

If comparing time periods (e.g. "Jan vs March performance"), read all source
pages covering each period.

---

## Step 3 — Identify comparison dimensions

Choose 4–8 dimensions that meaningfully differentiate the items. Good
dimensions are:
- Specific and measurable where possible ("revenue vs target" not "performance")
- Parallel — the same dimension can be assessed for each item
- Revealing — dimensions where the items actually differ

Avoid dimensions where all items are the same — they add no signal.

---

## Step 4 — Write the comparison page

File to `wiki/comparisons/<slug>.md`:

```markdown
---
tags:
  - comparison
items: ["Item A", "Item B"]
date: YYYY-MM-DD
---

# <Item A> vs <Item B>: <Short descriptive title>

## Overview
1–2 sentence framing of what's being compared and why it's interesting.

## Comparison table

| Dimension | <Item A> | <Item B> |
|---|---|---|
| [Dimension 1] | [value] | [value] |
| [Dimension 2] | [value] | [value] |
| ... | | |

## Key differences

- **[Most important difference]**: [2–3 sentence explanation with specific
  evidence and implications]
- **[Second difference]**: ...

## Key similarities

- **[Shared characteristic]**: [Why this matters for understanding both]

## Verdict / synthesis

A direct, opinionated synthesis: given the comparison, what should the reader
take away? What decision does this inform? What does the contrast reveal about
the domain?

## Sources
[[sources/A]], [[sources/B]], [[ConceptPage]]
```

The verdict section is important — don't end with a neutral "both have
pros and cons." Take a position, even if tentative.

---

## Step 5 — Surface the comparison

Present the comparison table and key differences directly in the conversation.
Note where the full page was filed.

---

## Step 6 — Log the run

Append to `/Users/fernando/Brain/log.md`:

```
## [YYYY-MM-DD] compare | <Item A> vs <Item B>
- filed: wiki/comparisons/<slug>.md
- dimensions: N
```
