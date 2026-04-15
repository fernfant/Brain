---
tags:
  - source
source: "Raw/Best Practices for Prompt Engineering - Anthropic.md"
date_ingested: 2026-04-11
type: webpage
author: Anthropic
published: 2026-01-01
original_url: "https://claude.com/blog/best-practices-for-prompt-engineering"
---

# Best Practices for Prompt Engineering (Anthropic Blog)

## Summary
Anthropic's official blog post on prompt engineering fundamentals and advanced techniques. Covers the core principle (clarity over cleverness) through concrete examples, then advances to prefilling, chain-of-thought, output format control, and prompt chaining. Aimed at general Claude users rather than API developers. The consistent theme: prompts work because they provide clarity, not because they trigger hidden behaviours.

## Key Points
- Be explicit: use direct action verbs; state what to include, not what to avoid
- Provide context and motivation — explaining why helps Claude generalise to the underlying intent
- Use examples (one-shot or few-shot) especially when format or tone matters
- Allow expression of uncertainty: explicit permission reduces hallucinations
- Prefill the response start to enforce format (JSON, skip preambles)
- Chain of thought / extended thinking for structured reasoning on complex tasks
- Control format by specifying what to do (not what not to do); match prompt style to desired output
- Prompt chaining: break complex tasks into sequential smaller prompts (trades latency for accuracy)
- Key mistakes: over-engineering, ignoring fundamentals, assuming mind-reading, using every technique simultaneously

## Key Insights

- **"Tell it what to do, not what not to do" is the most practically impactful single rule**: Negative instructions (no bullet points, don't be verbose) require the model to suppress a default behaviour, which is unreliable. Positive instructions (write in flowing prose) establish the target state directly. This asymmetry in instruction effectiveness is counter-intuitive but well-documented.

- **Prompt chaining trades latency for accuracy — this is an explicit quality/speed tradeoff**: Breaking a complex task into sequential steps produces more reliable results than a single large prompt, but requires more round-trips. For latency-sensitive use cases (real-time interfaces), single prompts with good structure may be preferable even at some quality cost. For accuracy-sensitive use cases (analysis, legal, financial), chaining is worth the latency.

- **"Start simple, test additions, refine iteratively" is advice most users ignore**: The common failure pattern is writing a maximally complex prompt on the first try, getting mediocre results, and concluding the technique doesn't work. The correct approach — minimal prompt → test → add one element → test — is methodical and slower up front but produces much higher-quality final prompts.

## Entities & Concepts
[[Prompt Engineering]], [[Claude Code]], [[Extended Thinking]], [[Anthropic]]
