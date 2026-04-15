---
tags:
  - source
source: "Raw/5 Rules for CLAUDE.md to Make Claude AI Dramatically Smarter.md"
date_ingested: 2026-04-11
type: webpage
author: MindwiredAI
published: 2026-04-05
original_url: "https://mindwiredai.com/2026/04/05/5-rules-claude-md-smarter/"
---

# 5 Rules for CLAUDE.md to Make Claude AI Dramatically Smarter

## Summary
A practical guide to "harness engineering" — structuring AI interactions through a persistent CLAUDE.md file. The five rules cover standing instructions, automated verification, role separation (builder vs reviewer agents), bug logging, and scope narrowing. The underlying argument: predictability and consistency come from structure, not from prompting skill.

## Key Points
- Rule 1: Write standing instructions in CLAUDE.md (≤300 lines) — Claude reads it automatically each session
- Rule 2: Include verification checkpoints (lint, tests, screenshots) so Claude self-checks before handing back work
- Rule 3: Use separate context windows for building and reviewing to prevent self-evaluation bias
- Rule 4: Maintain a Bug Log in CLAUDE.md documenting recurring errors — prevents re-learning mistakes across sessions
- Rule 5: Narrow scope deliberately — one feature per session, break larger work into confirmed sub-tasks

## Key Insights

- **The Bug Log is the most underutilised CLAUDE.md pattern**: Claude has no memory between sessions, so every repeated mistake is a tax on time and quality. Logging errors with root causes and fixes in CLAUDE.md turns past failures into standing instructions. The first time a mistake is corrected, it's free; every subsequent prevention is pure gain.

- **Builder/Reviewer split solves the self-critique problem systematically**: A model that built something is poorly positioned to critique it — it has priors about why the choices were correct. A fresh context window (Reviewer Agent) evaluates without those priors and finds problems the builder would rationalise away. This isn't a workaround; it's the correct architecture for quality-sensitive work.

- **The 300-line limit on CLAUDE.md is a quality constraint, not an arbitrary cap**: A CLAUDE.md that's too long dilutes the signal — Claude treats all instructions with equal weight, and a bloated file buries the most important rules. Keeping it under 300 lines forces prioritisation: only the rules that pay back most often earn a slot.

## Entities & Concepts
[[CLAUDE.md]], [[Claude Code]], [[Prompt Engineering]], [[Harness Engineering]]
