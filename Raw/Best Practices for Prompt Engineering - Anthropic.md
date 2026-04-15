---
title: "Best Practices for Prompt Engineering"
source: "https://claude.com/blog/best-practices-for-prompt-engineering"
author: Anthropic
published: 2026-01-01
created: 2026-04-10
tags:
  - clippings
---

# Best Practices for Prompt Engineering

## Overview

Prompt engineering involves structuring instructions to elicit better outputs from AI models. The quality of your prompts directly impacts response quality—well-crafted prompts can achieve desired results in a single interaction, while vague instructions often require multiple clarifications.

## Core Techniques

### Be Explicit and Clear

State exactly what you want without assuming the model will infer your intent. Use direct action verbs and skip preambles.

**Example**: Rather than "Create an analytics dashboard," specify "Create a fully-featured analytics dashboard with multiple relevant features and interactions beyond basic functionality."

### Provide Context and Motivation

Explaining *why* something matters helps models understand your underlying objectives. Share your reasoning for preferences and constraints.

**Example**: Instead of saying "No bullet points," explain that flowing prose feels more conversational and easier to read.

### Be Specific

Include explicit guidelines: word counts, formats, timelines, target audience, desired structure, and any constraints or restrictions.

### Use Examples

Demonstrate the desired format through one or more examples (one-shot or few-shot prompting). This proves especially valuable when format or tone matters.

### Allow Expression of Uncertainty

Give permission to acknowledge limitations rather than guessing, which reduces hallucinations and increases reliability.

## Advanced Techniques

### Prefill the AI's Response

Start the response for the model to guide format or structure. Useful for enforcing JSON output or skipping preambles.

### Chain of Thought Prompting

Request step-by-step reasoning. Modern Claude offers "extended thinking" for automated structured reasoning.

### Control Output Format

Tell the model what *to do* rather than what not to do. Match your prompt's style to desired output formatting.

### Prompt Chaining

Break complex tasks into sequential smaller prompts, with each output feeding into the next instruction. This trades latency for higher accuracy.

## Common Issues & Solutions

| Problem | Solution |
|---------|----------|
| Too generic | Add specificity, examples, requests for comprehensive output |
| Off-topic/missed intent | Be explicit about goals; provide context |
| Inconsistent format | Use examples or prefilling |
| Complex, unreliable results | Break into multiple focused prompts |
| Hallucinations | Explicitly permit saying "I don't know" |

## Key Mistakes to Avoid

- Over-engineering unnecessarily complex prompts
- Ignoring fundamentals while pursuing advanced techniques
- Assuming the model reads minds—be specific
- Using every technique simultaneously
- Skipping iteration and testing

## Final Guidance

Effective prompt engineering balances clarity with efficiency. The best prompt achieves your goals reliably with minimal necessary structure. Start simple, test additions, and refine iteratively.
