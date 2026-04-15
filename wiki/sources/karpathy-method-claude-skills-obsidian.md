---
tags:
  - source
source: "Raw/(18) Mr. Buzzoni on X \"Andrej Karpathy Method Claude Skills + Obsidian Explained\".md"
date_ingested: 2026-04-10
type: webpage
author: "@polydao (Mr. Buzzoni)"
published: 2026-04-09
original_url: "https://x.com/polydao/status/2042203352054771748"
---

# Andrej Karpathy Method: Claude Skills + Obsidian Explained

## Summary
An X thread by @polydao explaining how to build a persistent, self-improving personal knowledge base using Obsidian, Claude Code, and Skills — inspired by Andrej Karpathy's observation that a large share of his LLM use has shifted from writing code to manipulating markdown knowledge files. The core argument: standard AI chat is stateless and ephemeral; a wiki-based system where the LLM acts as compiler and librarian compounds knowledge over time, making each query more valuable than the last.

## Key Points
- Mental model: LLM as compiler and librarian, not chatbot
- Karpathy's observation: more LLM time spent on knowledge manipulation than code writing
- Workflow: raw/ → LLM compiles → wiki/ → query → reports/ → filed back into wiki/
- "Never answer in chat, always answer in files" — answers become permanent wiki assets
- LLM health checks: periodic scans for contradictions, orphan pages, duplicates, unsourced claims
- Claude Code Skills: reusable workflows packaged as SKILL.md + scripts
- Obsidian features leveraged: backlinks, graph view, Dataview plugin, Marp for slides
- MCP for Obsidian: Claude reads/writes vault directly via Local REST API plugin (3.3K GitHub stars)
- Advanced option: wiki as finetuning corpus to bake knowledge into model weights
- Fully local option: Obsidian + Ollama (no data leaves the machine)

## Key Insights

- **The statelessness problem is the central insight**: Most LLM interactions reset to zero every session — you ask a question, get an answer, and the model retains nothing. The wiki pattern solves this by making the knowledge accumulation layer external to the model and persistent. Each ingested source, each filed query, each lint pass makes the wiki richer. The LLM is interchangeable; the wiki is the irreplaceable asset.

- **"Never answer in chat, always answer in files" changes the economics of querying**: Every time you ask a question and get an answer in chat, that answer disappears. Every time the same answer is written to a wiki page, it compounds — it becomes cross-linkable, referable, and improvable in future sessions. The practical implication is that the quality of the knowledge base scales with usage in a way that pure chat usage never does.

- **The LLM health check (lint pass) is what prevents wiki rot**: Static knowledge bases go stale because human maintenance is expensive and no one does it. The lint pass — having the LLM scan for contradictions, orphan pages, duplicate articles, and unsourced claims — offloads the maintenance burden that causes wikis to fail. The LLM doesn't get bored or forget to update a cross-reference. This is the operational insight that makes the system sustainable at scale.

- **The wiki-as-finetuning-corpus endpoint is the most ambitious implication**: If the wiki becomes rich and structured enough, it can be used as training data to create a personalised model that has the knowledge baked into its weights. This would eliminate the need for retrieval entirely at scale — the model would just know. This is speculative for personal use today but is the logical long-term evolution of the pattern.

## Entities & Concepts
[[Andrej Karpathy]], [[LLM Wiki]], [[Obsidian]], [[Claude Skills]], [[MCP]], [[Obsidian Web Clipper]]

## Quotes / Excerpts
> "The mental shift: LLM as compiler and librarian — not chatbot."

> "Karpathy's key observation: the human mostly reads, the LLM mostly writes."

> "Standard AI usage is stateless. You ask, get an answer, close the tab. Next session, the model remembers nothing. You start from zero. Forever."

> "Your queries literally compound into better future answers."
