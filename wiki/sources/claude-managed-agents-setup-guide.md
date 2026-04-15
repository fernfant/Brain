---
tags:
  - source
source: "Raw/How to Deploy Your First Claude Managed Agent.pdf"
date_ingested: 2026-04-11
type: pdf
---

# Claude Managed Agents — The Complete Setup Guide

## Summary
A comprehensive guide to Anthropic's Managed Agents platform (public beta as of April 2026) — cloud-hosted Claude agents that run 24/7 without local infrastructure. Covers the four core concepts (Agent, Environment, Session, Events), pricing, security (Vaults, permissions, guardrails), resources (Files, GitHub, Memory), and production deployment. Positions Managed Agents at the far end of the deployment spectrum: Cowork (personal) → Claude Code (developer) → Agent SDK (self-hosted) → Managed Agents (Anthropic-hosted).

## Key Points
- Managed Agents run on Anthropic's cloud; no servers, containers, or DevOps required
- Four concepts: Agent (config: model + system prompt + tools + MCP + skills), Environment (container template), Session (running instance), Events (SSE streaming between app and agent)
- One agent can power thousands of simultaneous sessions; each gets its own isolated container
- Prerequisites: Anthropic API key, Python 3.10+, `ant` CLI (`brew install anthropics/tap/ant`)
- Beta header required: `managed-agents-2026-04-01`; SDKs available in Python, TypeScript, Java, Go, C#, Ruby, PHP
- Pricing: standard token rates + $0.08/session-hour (active only, idle is free) + $10/1,000 web searches
- Security: Vaults for secrets, permissions scoping, guardrails for content/action boundaries
- Resources: Files (in-session uploads), GitHub integration, Memory (cross-session persistence)
- Production checklist: environment pinning, session limits, monitoring, graceful failure handling

## Key Insights

- **Managed Agents completes the spectrum from personal to client-deployable AI**: The four-tier landscape (Cowork → Claude Code → Agent SDK → Managed Agents) maps cleanly to four deployment scenarios: personal automation, developer workflows, self-hosted products, and client-facing services. Understanding which tier applies to a given use case is the first architectural decision — and most builders default to the wrong one.

- **The idle-is-free pricing model changes the economics of always-on agents**: At $0.08/session-hour (active only), an agent that runs for 10 minutes per trigger costs $0.013 per activation regardless of how long it waits between triggers. This makes event-driven agents (triggered by webhooks, cron, or user action) dramatically cheaper than persistent polling agents — and rewards the correct architectural pattern.

- **The Vault + permissions + guardrails security stack is what makes client deployment viable**: Running an agent for a client requires trust boundaries: the agent should access only what it needs (permissions), store secrets safely (Vaults), and be constrained from harmful actions (guardrails). Without this stack, every Managed Agent deployment is a liability. The fact that Anthropic provides it as a platform primitive rather than requiring builders to implement it is the key unlock for non-security-expert builders.

- **The fact that this guide was saved as a PDF (not a web clip) and appeared in Raw/ as new content suggests it was manually added** — indicating active interest in the Managed Agents platform. Combined with the LLM Wiki pattern already implemented here, Managed Agents is the logical next evolution: moving from a personal wiki maintained by a local Claude session to an always-on agent that maintains and queries the wiki autonomously.

## Entities & Concepts
[[Claude Code]], [[Anthropic]], [[MCP]], [[Claude Managed Agents]], [[Claude Cowork]]
