---
name: kb-query
description: >
  Answers a question by searching the Brain wiki at /Users/fernando/Brain/wiki/,
  synthesising an answer from relevant pages, and filing the result as a
  permanent wiki page so the insight compounds. Use whenever the user asks a
  question that can be answered from existing wiki knowledge — analytical
  questions about trends, comparisons, summaries, or explanations. Trigger on
  any question phrased as "what is...", "how does...", "why did...", "compare...",
  "summarise...", "what's the trend in...", "explain...", or any question mark.
  Also trigger when the user says /query or "ask the wiki".
---

# kb-query — Wiki Query & Answer

## Purpose

Chat answers disappear. This skill makes every valuable answer permanent by
filing it back into the wiki as a citable page. The insight compounds: future
sessions can reference, update, and build on it rather than deriving it again
from scratch.

The query loop: read index → identify relevant pages → read them → synthesise
answer → file the answer → log the run.

---

## Step 1 — Understand the question

Read the user's question carefully. Identify:
- **Topic**: what domain or concept is this about?
- **Type**: is this a factual lookup, a trend analysis, a comparison, a
  synthesis, or an explanation?
- **Scope**: what time period, sources, or entities are relevant?

---

## Step 2 — Find relevant pages

Read `wiki/index.md` to get a full picture of what's in the wiki.

Then identify the most relevant pages:
- For factual questions: check concept pages first
- For trend/period questions: check source pages by date
- For cross-cutting questions: check category pages for clusters

Read the identified pages. If a page references others that seem relevant,
read those too. Aim to read all pages that could materially affect the answer
before writing anything.

---

## Step 3 — Synthesise the answer

Write the answer with:
- **Direct response** to the question upfront — don't bury the lede
- **Evidence**: specific numbers, dates, and source citations using `[[wikilinks]]`
- **Nuance**: surface tensions, limitations, or caveats where they exist
- **Confidence level**: if the answer is partial or uncertain, say so explicitly

Good answers are analytical, not just retrieval. Connect facts across sources,
note patterns the raw pages don't make explicit, and flag if the wiki lacks
sufficient data to answer confidently.

---

## Step 4 — Decide where to file the answer

| Answer type | File location |
|---|---|
| One-off factual lookup | Don't file — answer in chat only |
| Trend analysis or period summary | `reports/YYYY-MM-DD-<slug>.md` |
| Evergreen concept explanation | `wiki/analyses/<slug>.md` |
| Comparison between two topics | `wiki/comparisons/<slug>.md` (use kb-compare instead) |
| Cross-cutting synthesis | `wiki/analyses/<slug>.md` |

Only file answers that are non-trivial and likely to be useful again. A
one-line factual answer doesn't need its own page.

---

## Step 5 — Write the filed page

```markdown
---
tags:
  - analysis
query: "<the original question>"
date: YYYY-MM-DD
sources_consulted: N
---

# <Descriptive title for the answer>

## Question
<the original question, verbatim>

## Answer
<direct, well-structured answer>

## Evidence
<key data points and citations using [[wikilinks]]>

## Limitations
<what the wiki doesn't cover that would improve this answer>

## Sources consulted
[[sources/A]], [[sources/B]], [[ConceptPage]]
```

Keep it tight. The goal is a reusable reference, not a full essay.

---

## Step 6 — Surface the answer to the user

Present the answer directly in the conversation first. Then note where it
was filed (if filed), so the user can find it in Obsidian.

---

## Step 7 — Log the run

Append to `/Users/fernando/Brain/log.md`:

```
## [YYYY-MM-DD] query | "<question>"
- answer_filed: reports/YYYY-MM-DD-slug.md (or "not filed")
- sources_consulted: N
```
