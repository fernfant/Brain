---
title: "How I Learned to Prompt Claude Code Better — Four Modes"
source: "https://sderosiaux.medium.com/how-i-learned-to-prompt-ai-better-my-four-modes-177bddcfa6bd"
author: Stéphane Derosiaux
published: 2025-08-25
created: 2026-04-10
tags:
  - clippings
---

# How I Learned to Prompt Claude Code Better — Four Modes

## Introduction

The author spent considerable time working with AI tools for various tasks—building applications, debugging code, creating strategy documents, and learning new technologies. Initially, they believed prompting was straightforward, but this assumption led to confusion.

A turning point came when they analyzed their own Claude Code prompts using ChatGPT, asking it to identify patterns in their prompting approach. The analysis revealed that while the prompts weren't fundamentally flawed, they suffered from messiness: repetition, mixed intentions within single requests, and excessive meta-instructions that obscured the actual goal.

## The Four Modes of Prompting

### 1. Build Mode: "Give me something I can use."

This is execution mode for concrete deliverables. The user knows exactly what they want and needs the AI to produce it.

**Examples:**
- "Implement a Kafka consumer in Java that retries with exponential backoff."
- "Write me a bash script to tail logs and color errors in red."
- "Create a marketing email for our upcoming webinar, short and direct."

**Common Pitfall:** Burying requests under excessive meta-instructions like "don't be verbose" creates unnecessary clutter.

**Key Takeaway:** Strip away meta-language. Be direct and concrete, allowing the AI to deliver without instruction noise.

### 2. Debug Mode: "Why is this happening?"

This mode addresses confusion—when something breaks or remains unexplained.

**Examples:**
- "Is it normal that my Kafka consumer is rebalancing every 30 seconds?"
- "Why is this CSS leaking into my React component?"
- "My SQL query is running slow—can you spot the issue?"

**Common Pitfall:** Jumping to solutions before providing sufficient context (logs, versions, minimal code examples).

**Key Takeaway:** Share comprehensive context first—inputs, errors, and environment details—before requesting fixes.

### 3. Rewrite/Critique Mode: "Make this sharper."

This applies when the user has existing work that needs improvement: drafts, concepts, or text requiring refinement.

**Examples:**
- "Here's my blog draft. Critique it for clarity and impact."
- "Rewrite this function with better readability."
- "Analyze my LinkedIn post and suggest how to make it more engaging."

**Common Pitfall:** Requesting both critique and rewriting simultaneously produces polite revisions instead of substantive feedback.

**Key Takeaway:** Separate these steps. First request feedback on problems, then request revision based on that analysis.

### 4. Learn Mode: "Teach me like I'm new."

This mode prioritizes understanding over quick answers—diving deeply into complex concepts.

**Examples:**
- "Explain CROSS JOIN LATERAL in Postgres with simple examples."
- "Walk me through Flink checkpoints—aligned vs unaligned."
- "Help me understand OAuth2 step by step, as if implementing from scratch."

**Common Pitfall:** Failing to specify expertise level means the AI defaults to beginner-friendly explanations.

**Key Takeaway:** Declare your knowledge level and context to receive appropriately targeted education.

## Additional Insights

- **Repetition:** Repeated instructions waste tokens and create noise without adding clarity
- **Mode Mixing:** Combining Build, Learn, and Critique in one prompt produces scattered, unfocused output
- **Meta-Hooks:** Using shorthand triggers like "AMA" (Ask Me Anything) forces clarifying questions before generating responses
- **Context Drift:** Explicitly naming mode switches ("switching to Debug mode now") helps reset expectations during long conversations

## The Core Rule

Before sending any prompt, pause and ask: "Am I building? Debugging? Rewriting? Learning?"

This simple labeling act fundamentally transforms interaction quality.

## Conclusion

Effective prompting isn't about sophisticated techniques or magical formulations. It centers on clarity about the specific role you want the AI to play, then maintaining consistency with that role throughout the interaction.
