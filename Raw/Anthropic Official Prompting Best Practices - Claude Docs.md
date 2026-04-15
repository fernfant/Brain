---
title: "Prompting Best Practices — Claude API Docs (Official)"
source: "https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices"
author: Anthropic
published: 2026-04-01
created: 2026-04-10
tags:
  - clippings
---

# Prompting Best Practices — Official Anthropic Docs

The single reference for prompt engineering with Claude Opus 4.6, Sonnet 4.6, and Haiku 4.5.

---

## General Principles

### Be Clear and Direct

Claude responds well to clear, explicit instructions. Think of Claude as a brilliant but new employee who lacks context on your norms and workflows.

- Be specific about the desired output format and constraints
- Provide instructions as sequential steps when order matters

**Less effective:** `Create an analytics dashboard`
**More effective:** `Create an analytics dashboard. Include as many relevant features and interactions as possible. Go beyond the basics to create a fully-featured implementation.`

### Add Context to Improve Performance

Explain *why* instructions matter. Claude is smart enough to generalize from explanations.

**Less effective:** `NEVER use ellipses`
**More effective:** `Your response will be read aloud by a text-to-speech engine, so never use ellipses since the text-to-speech engine will not know how to pronounce them.`

### Use Examples Effectively

Few-shot or multishot prompting dramatically improves accuracy and consistency. Make examples:
- **Relevant:** Mirror your actual use case closely
- **Diverse:** Cover edge cases
- **Structured:** Wrap in `<example>` tags

Include 3–5 examples for best results.

### Structure Prompts with XML Tags

XML tags help Claude parse complex prompts: `<instructions>`, `<context>`, `<input>`. Use consistent, descriptive tag names. Nest tags when content has a natural hierarchy.

### Give Claude a Role

Setting a role in the system prompt focuses Claude's behavior:
```
system="You are a helpful coding assistant specializing in Python."
```

### Long Context Prompting

For large documents (20k+ tokens):
- Put longform data at the top of the prompt, above your query (improves quality up to 30%)
- Structure document content with XML tags
- Ask Claude to quote relevant parts before carrying out tasks

---

## Output and Formatting

### Control the Format

1. **Tell Claude what to do instead of what not to do:** "Your response should be composed of smoothly flowing prose paragraphs" instead of "Do not use markdown"
2. **Match your prompt style to desired output**
3. **Use XML format indicators:** "Write the prose sections in `<smoothly_flowing_prose_paragraphs>` tags"

### Communication Style (Claude 4.6)

Claude's latest models are more concise and natural:
- More direct and grounded
- More conversational
- Less verbose (may skip summaries after tool calls)

---

## Tool Use

### Be Explicit About Actions

**Less effective (Claude will only suggest):** `Can you suggest some changes to improve this function?`
**More effective (Claude will act):** `Change this function to improve its performance.`

### Optimize Parallel Tool Calling

Claude 4.6 excels at parallel tool execution — running multiple searches, reading several files simultaneously. To maximize:
```
If you intend to call multiple tools and there are no dependencies between the tool calls,
make all of the independent tool calls in parallel.
```

---

## Thinking and Reasoning

### Adaptive Thinking (Claude 4.6)

Claude 4.6 uses adaptive thinking (`thinking: {type: "adaptive"}`), dynamically deciding when and how much to think. Control depth with the `effort` parameter: `high`, `medium`, `low`.

**For agentic workloads:** Start at `high` effort.
**For latency-sensitive workloads:** Use `medium` or `low`.

### Overthinking Prevention

Claude Opus 4.6 may do extensive upfront exploration. To constrain:
```
When you're deciding how to approach a problem, choose an approach and commit to it.
Avoid revisiting decisions unless you encounter new information that directly contradicts your reasoning.
```

---

## Agentic Systems

### Balancing Autonomy and Safety

```
Consider the reversibility and potential impact of your actions. Take local, reversible
actions freely, but for actions that are hard to reverse or affect shared systems,
ask the user before proceeding.
```

### Subagent Orchestration

Claude 4.6 proactively delegates to subagents. To prevent excessive subagent use:
```
Use subagents when tasks can run in parallel or require isolated context.
For simple tasks or single-file edits, work directly rather than delegating.
```

### Minimize Overengineering

```
Avoid over-engineering. Only make changes that are directly requested or clearly necessary.
Keep solutions simple and focused. Don't add features, refactor code, or make "improvements"
beyond what was asked.
```

---

## Migration to Claude 4.6

1. Be specific about desired behavior
2. Frame instructions with quality modifiers
3. Update thinking configuration to adaptive thinking
4. Migrate away from prefilled responses (deprecated in 4.6)
5. Tune anti-laziness prompting — Claude 4.6 is already more proactive, so dial back aggressive language
