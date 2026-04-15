---
tags:
  - source
source: "Raw/Claude + Obsidian have to be illegal.md"
date_ingested: 2026-04-11
type: webpage
author: "@defileo (Leo)"
published: 2026-04-09
original_url: "https://x.com/defileo/status/2042241063612502162"
---

# Claude + Obsidian Have to Be Illegal (@defileo)

## Summary
An X thread by @defileo presenting a practical "second brain" setup combining Claude Code and Obsidian, with full Karpathy LLM Wiki prompt included. Unlike the @polydao thread (which explains the pattern), this thread focuses on the day-to-day operations — ingest commands, lint commands, morning briefing scripts, and call transcript processing. It's the most operationally concrete implementation guide in this collection.

## Key Points
- Setup: Obsidian vault + Claude Code pointed at the vault folder — Obsidian is the window, the terminal is the engine
- Ingest command pattern: `claude -p "I just added an article to /raw-sources. Read it, write summary to /wiki/summaries/, update index.md, update concept pages. Show every file you touched." --allowedTools Bash,Write,Read`
- Lint command: weekly scan for contradictions, orphan pages, missing concept pages, outdated claims → writes lint-report.md
- Morning briefing: Python script reading Memory.md for open actions + new raw-sources files + cron job at 7:30am
- Call transcript processing: extract decisions, action items, 3-bullet summary → auto-files to Action-Tracker.md, Decision-Log.md, client notes
- Why wikis fail: maintenance overhead exceeds value → Claude eliminates the maintenance tax permanently
- "The human's job is to curate sources, ask good questions, think about what it means. Claude's job is everything else."

## Key Insights

- **The "show every file you touched" instruction is the most important line in the ingest command**: Transparency about changes is what keeps the human in the loop without requiring hands-on supervision. Knowing which 10–15 pages were touched in a single ingest lets you spot unexpected connections, catch mistakes, and build confidence in the system — all without reading every file yourself.

- **The morning briefing cron job is the compound interest play**: Setting up a 7:30am digest that reads Memory.md and scans new raw sources once is leveraged infinitely — every morning thereafter, the system surfaces what matters without any human effort. This is the pattern that separates a wiki that helps occasionally from a second brain that works every day.

- **The call transcript processing workflow is a high-value business application hiding in plain sight**: Most organisations lose 80% of the value from meetings — decisions go unrecorded, action items slip, context is forgotten. A prompt that extracts decisions → Decision-Log, action items with owners/deadlines → Action-Tracker, and creates a client note in one pass is not a productivity hack; it's a systematised knowledge management process.

- **The inclusion of the full Karpathy LLM Wiki prompt in the thread is significant**: It means the pattern is spreading via copy-paste, with Karpathy's original framing (raw/ → wiki/ → compound knowledge) explicitly attributed and propagated. The @defileo thread is both a how-to and a distribution mechanism for the idea itself.

## Entities & Concepts
[[LLM Wiki]], [[Obsidian]], [[Claude Code]], [[Andrej Karpathy]], [[Claude Skills]], [[MCP]]
