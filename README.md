# Brain 🧠

A personal knowledge base maintained by an LLM. Raw documents go in, a structured, interlinked wiki comes out — and keeps compounding as you add more.

Built on the [LLM Wiki pattern](https://github.com/fernfant/Brain/blob/main/CLAUDE.md): instead of re-deriving answers from raw documents every time (like RAG), the LLM incrementally builds and maintains a persistent wiki. Cross-references are already there. Contradictions are flagged. Every question you ask gets filed as a permanent page.

## How it works

```
Raw/          ← drop articles, PDFs, web clips here
  └─ kb-compile ──→  wiki/sources/   ← one summary page per source
                      wiki/           ← concept & entity pages
                      wiki/categories/ wiki/index.md  wiki/glossary.md
                                    ↓
                              kb-index rebuilds navigation
                                    ↓
                           reports/ & wiki/analyses/
                           (queries, comparisons, insights)
```

## Skills

| Skill | What it does |
|---|---|
| `kb-compile` | Ingests new files from `Raw/` → creates source pages + updates concept pages |
| `kb-index` | Rebuilds `wiki/index.md`, `wiki/glossary.md`, and all category pages |
| `kb-refinement` | Tightens summaries, removes redundancies, adds analytical Key Insights |
| `kb-lint` | Health-check: finds orphans, broken links, contradictions, stale claims |
| `kb-query` | Answers questions from wiki knowledge, files non-trivial answers permanently |
| `kb-compare` | Side-by-side structured comparison of any two topics or time periods |
| `kb-sync` | Commits and pushes all changes to this GitHub repo |

All skills live in `.claude/skills/` as plain markdown `SKILL.md` files — readable, editable, version-controlled.

## Directory structure

```
Brain/
  Raw/              ← source documents (articles, PDFs, images, web clips)
  wiki/             ← LLM-maintained wiki (Obsidian-compatible markdown)
    sources/        ← one page per ingested source
    categories/     ← category index pages
    analyses/       ← kb-query evergreen answers
    comparisons/    ← kb-compare structured comparisons
  reports/          ← time-bound analyses and insight reports
  .claude/skills/   ← skill definitions
  log.md            ← append-only ingest log
  CLAUDE.md         ← instructions for the LLM agent
```

## Usage

Open the project in [Claude Code](https://claude.ai/code). The skills are auto-loaded via `CLAUDE.md`. Then:

- **Add a source**: drop a file in `Raw/` and say `compile`
- **Ask a question**: just ask — `kb-query` finds the answer and files it
- **Compare two things**: say `compare X vs Y`
- **Health-check**: say `lint`
- **Push to GitHub**: say `sync`

## Stack

- **LLM**: Claude (via Claude Code)
- **Wiki format**: Obsidian-compatible markdown with `[[wikilinks]]`
- **Version control**: Git + GitHub
- **Viewing**: [Obsidian](https://obsidian.md) (optional but recommended)

## Inspired by

- Vannevar Bush's [Memex](https://en.wikipedia.org/wiki/Memex) (1945)
- The [LLM Wiki pattern](https://github.com/fernfant/Brain/blob/main/CLAUDE.md)
