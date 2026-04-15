---
tags:
  - source
source: "Raw/Anthropic Official Prompting Best Practices - Claude Docs.md"
date_ingested: 2026-04-11
type: webpage
author: Anthropic
published: 2026-04-01
original_url: "https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices"
---

# Prompting Best Practices — Official Anthropic API Docs

## Summary
The authoritative reference for prompt engineering with Claude Opus 4.6, Sonnet 4.6, and Haiku 4.5 — aimed at API developers and agentic system builders. Covers general principles, output formatting, tool use optimisation, adaptive thinking configuration, and agentic safety guidelines. The Claude 4.6 section is particularly valuable: it documents breaking changes from prior versions (prefill deprecated, adaptive thinking replacing extended thinking) and new defaults (more concise, less verbose).

## Key Points
- Put longform data at the top of prompts (above the query) — improves quality up to 30% for 20k+ token documents
- Use XML tags (`<instructions>`, `<context>`, `<input>`, `<example>`) with consistent, descriptive names
- Claude 4.6: adaptive thinking (`thinking: {type: "adaptive"}`); control depth with `effort` parameter (high/medium/low)
- For agentic workloads: start at `high` effort; for latency-sensitive: use `medium` or `low`
- Overthinking prevention for Opus 4.6: "choose an approach and commit to it; avoid revisiting decisions"
- Parallel tool calls: make all independent tool calls simultaneously (not sequentially)
- Agentic safety: "Take local, reversible actions freely; for hard-to-reverse actions, ask user first"
- Prefilled responses: deprecated in Claude 4.6
- Anti-laziness prompting: dial back in 4.6 — it's already more proactive than prior versions
- Migration: update thinking config; remove prefill; tune instructions for 4.6's more direct style

## Key Insights

- **The 30% quality improvement from placing long documents at the top of prompts is the highest-ROI single change for document-heavy work**: Position matters in long-context prompts — the model attends differently to content at different positions. For RAG-style document queries, putting the source material before the question (not after) is a structural change that requires no other modification and delivers measurable quality improvement.

- **Adaptive thinking's `effort` parameter is a latency/quality dial that most developers aren't aware of**: The ability to control thinking depth programmatically — high for complex analysis, low for simple tasks — means different subtasks within the same workflow can have different thinking budgets. A research synthesis step warrants `high`; a reformatting step warrants `low`. The default may not be optimal for any individual use case.

- **The agentic safety guideline ("reversible actions freely, hard-to-reverse actions with confirmation") is a deployable policy, not just advice**: This is specific enough to implement as a check in any agentic workflow. Before any write, delete, or external API call, classify it: reversible (proceed) or hard-to-reverse (confirm). This classification step, built into the agent's decision logic, is the difference between a safe and an unsafe autonomous system.

- **Deprecating prefill in 4.6 is a breaking change that matters for format-enforcement workflows**: Many prompt patterns relied on prefilling to enforce JSON output or skip preambles. With 4.6, these need to be replaced with XML format indicators and positive format instructions. Any production prompt using prefill needs to be migrated.

## Entities & Concepts
[[Claude Code]], [[Prompt Engineering]], [[Extended Thinking]], [[MCP]], [[Anthropic]]
