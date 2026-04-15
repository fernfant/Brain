---
tags:
  - source
source: "Raw/How I Learned to Prompt Claude Code Better - Four Modes.md"
date_ingested: 2026-04-11
type: webpage
author: Stéphane Derosiaux
published: 2025-08-25
original_url: "https://sderosiaux.medium.com/how-i-learned-to-prompt-ai-better-my-four-modes-177bddcfa6bd"
---

# How I Learned to Prompt Claude Code Better — Four Modes

## Summary
Stéphane Derosiaux describes four distinct prompting modes he identified by analysing his own Claude Code interactions with ChatGPT. The key insight: most prompting failures come not from bad technique but from mixing modes — asking Claude to build, debug, review, and explain all in the same prompt. Separating intentions by mode dramatically improves output quality.

## Key Points
- **Build Mode**: concrete deliverables — strip meta-instructions, be direct ("Implement X in Y")
- **Debug Mode**: diagnosis first — share full context (logs, versions, code) before requesting fixes
- **Rewrite/Critique Mode**: separate feedback from revision — first request critique, then request rewrite based on that critique
- **Learn Mode**: specify expertise level — Claude defaults to beginner-friendly without explicit context
- Meta-hooks like "AMA" force clarifying questions before generating; useful for ambiguous requests
- Explicitly naming mode switches ("switching to Debug mode now") resets expectations in long conversations
- Repeated instructions waste tokens and create noise without adding clarity

## Key Insights

- **Mode mixing is the most common and least discussed prompting failure**: Most prompt engineering guides focus on what to include — context, examples, role. This article identifies what to exclude: other modes. A Build request contaminated with Learn or Critique signals produces output that's neither fully executed nor fully explained. Mode purity is a quality control mechanism.

- **The self-analysis approach (using ChatGPT to analyse Claude prompts) is a meta-strategy worth copying**: Derosiaux discovered his modes by having an AI analyse patterns in his own prompting history. This is a way to surface unconscious habits and biases in how you use AI — and the resulting framework was personal and specific rather than generic advice. Applying AI to your AI usage patterns is underexplored.

- **Debug Mode's requirement for context-first mirrors how good engineers ask for help**: The pattern (share inputs, errors, environment → then ask for fix) is exactly how senior engineers expect junior engineers to report bugs. Prompting Claude in Debug Mode with insufficient context gets the same result as an underspecified bug report: a guess, not a fix. The four-mode framework translates engineering communication norms into prompting practice.

## Entities & Concepts
[[Claude Code]], [[Prompt Engineering]], [[Build Mode]], [[Debug Mode]]
