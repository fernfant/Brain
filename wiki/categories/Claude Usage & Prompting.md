---
tags:
  - category
---

# Category: Claude Usage & Prompting

How to use Claude effectively — prompting frameworks, Claude Code workflows, Skills, agentic systems, and the tools that extend Claude's capabilities.

## Articles in this category

- [[sources/leveraging-claude-code-senior-engineers-guide]] — Senior engineer workflows: CLAUDE.md, Plan Mode, validation loops, parallel worktrees, MCP integrations
- [[sources/youre-using-claude-wrong-levels-guide]] — Three-level progression: prompts → Skills → agentic execution (Code/Cowork)
- [[sources/5-rules-claude-md-smarter]] — 5 rules for CLAUDE.md: standing instructions, verification, builder/reviewer split, bug log, scope narrowing
- [[sources/four-modes-prompting-claude-code]] — Four prompting modes: Build, Debug, Rewrite/Critique, Learn — mode separation as quality control
- [[sources/power-users-migrate-claude-productivity]] — Power user guide: Claude's 2026 rise, prompt-as-contract, XML tags, MCP, multi-agent workflows
- [[sources/claude-ai-prompt-codes-2026]] — Debunking viral "secret codes"; March 2026 codebase leak reveals hidden feature flags and benchmarks
- [[sources/best-practices-prompt-engineering-anthropic]] — Anthropic blog: fundamentals, prefill, chain-of-thought, prompt chaining
- [[sources/beginners-guide-claude-helena-dibiase]] — Business owner guide: CRISP framework, Projects, Artifacts, Cowork, pricing
- [[sources/anthropic-official-prompting-best-practices]] — Official API docs: adaptive thinking, XML tags, long-context positioning, agentic safety, 4.6 migration
- [[sources/claude-managed-agents-guide-pmf]] — Founder guide: removes infrastructure bottleneck; coordinator-specialist multi-agent pattern; competitive intel use case
- [[sources/ultimate-beginners-guide-managed-agents]] — Non-technical business guide: permission modes, service pricing model, professional services market opportunity
- [[sources/claude-code-tutorial-beginners-2026]] — Beginner guide to Claude Code: 200K context, installation, Plan Mode, tool comparison
- [[sources/claude-managed-agents-setup-guide]] — Managed Agents platform: 24/7 cloud agents, four core concepts, security, pricing
- [[Claude Code]] — Terminal-native agentic coding assistant
- [[CLAUDE.md (concept)]] — Persistent project configuration file
- [[Claude Skills]] — Reusable workflow packages
- [[Claude Cowork]] — Desktop app for non-developer agentic execution
- [[Claude Managed Agents]] — Cloud-hosted agent deployment platform
- [[Plan Mode]] — Read-only analysis mode before code changes
- [[Extended Thinking]] — Adaptive reasoning with effort parameter
- [[Prompt Engineering]] — Structuring instructions for consistent LLM outputs
- [[Harness Engineering]] — AI behaviour via persistent config and verification

## Related categories
- [[categories/LLM & Knowledge Systems]]
- [[categories/Technology & Data]]

## Key Insights

- **CLAUDE.md is the highest-leverage single investment across all guides**: Every source in this category — from the senior engineer's guide to the beginner tutorial to the official API docs — independently converges on CLAUDE.md as the most impactful thing a Claude user can build. It appears in 6 of 12 sources. This isn't a coincidence; it's the community discovering the same truth: persistent context compounds, ad-hoc prompting does not.

- **The prompting advice across all sources reduces to two core principles — mode clarity and positive framing**: Mode clarity (Build vs Debug vs Rewrite vs Learn; don't mix them) and positive framing (tell Claude what to do, not what not to do) appear in every guide from beginner to official API docs. Everything else — XML tags, prompt chaining, CRISP, prompt-as-contract — is elaboration on these two foundations.

- **The Claude ecosystem has a clear deployment spectrum that most users don't know exists**: Cowork (personal/non-technical) → Claude Code (developer/local) → Agent SDK (self-hosted/production) → Managed Agents (client-facing/cloud). Most users are stuck at Level 0 (chat) or Level 1 (prompts). Each level up multiplies the value of the previous, but requires understanding what tier matches your use case.

- **The March 2026 codebase leak revealed that KAIROS (background agent mode) is in development**: This suggests Anthropic is building always-on background agents into the mainstream Claude product, not just Managed Agents. The gap between what's publicly available and what's in the product roadmap is likely 6–12 months, meaning background agents will be a standard capability by late 2026.

- **Adaptive thinking's effort parameter is the most underutilised API feature for production systems**: The ability to set `effort: high` for complex reasoning tasks and `effort: low` for simple reformatting within the same workflow gives developers programmatic control over cost and latency. A production system that applies maximum effort uniformly is paying a 3–5x token premium on every call that doesn't need deep reasoning.

- **The 46.9% token reduction from MCP Tool Search has compounding economic implications**: For any system making thousands of tool-selection decisions per day, nearly halving token usage on selection alone represents a significant cost saving. MCP is not just an integration layer — it's an economic optimisation that improves with the number of available tools.

- **Claude's rise to #1 App Store in March 2026 was values-driven, not just capability-driven**: Anthropic's refusal to support mass surveillance and autonomous weapons turned an internal policy decision into a public differentiator. The Claude user base skews toward people who chose it deliberately, not by default — which means Claude's power user community is likely more engaged and more willing to invest in advanced usage patterns.
