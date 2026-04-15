# Brain — Knowledge Base

## Skills

This project uses custom skills. At the start of each session, copy each skill's `SKILL.md`
from `.claude/skills/<name>/` into the active session skills directory and add it to `manifest.json`.

- Skill: `kb-compile` — Scans `Raw/` for new files and compiles them into Obsidian-compatible wiki pages in `wiki/`
- Skill: `kb-index` — Rebuilds `wiki/index.md`, `wiki/glossary.md`, and `wiki/categories/` in Wikipedia style
- Skill: `kb-refinement` — Refines all wiki source and category pages: tightens summaries, removes redundancies, adds detailed `## Key Insights` sections with analytical interpretations
- Skill: `kb-lint` — Health-checks the wiki: finds orphan pages, broken wikilinks, contradictions, stale claims, and missing concept pages; writes `wiki/lint-report.md`
- Skill: `kb-query` — Answers questions from wiki knowledge, synthesises an answer, and files non-trivial results as permanent pages in `wiki/analyses/` or `reports/`
- Skill: `kb-compare` — Structured side-by-side comparison of any two topics/periods/concepts; files result to `wiki/comparisons/`

All six skills are stored in `.claude/skills/` and should be registered in the active session manifest at startup.

## Directory Structure

```
Brain/
  Raw/              ← drop source files here (articles, PDFs, images, web clips)
  wiki/             ← LLM-maintained wiki pages (Obsidian)
    sources/        ← one page per ingested source
    categories/     ← category index pages
    analyses/       ← kb-query evergreen answers
    comparisons/    ← kb-compare structured comparisons
  reports/          ← time-bound analyses and daily briefs
  log.md            ← append-only ingest log (auto-created)
```
