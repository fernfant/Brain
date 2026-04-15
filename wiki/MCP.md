---
tags:
  - concept
---

# MCP (Model Context Protocol)

## Description
Protocol enabling Claude to connect to external tools and services, including direct read/write access to an Obsidian vault via the mcp-obsidian server (3.3K GitHub stars), allowing Claude to edit notes, create files, and insert content under specific headings in real time.

## Appearances
- [[sources/karpathy-method-claude-skills-obsidian]] — Setup instructions for mcp-obsidian via Local REST API plugin; enables Claude to list files, search, patch content, append, and delete from vault
- [[sources/power-users-migrate-claude-productivity]] — MCP Tool Search reduces token usage by up to 46.9%; connect GitHub, Figma, Notion, Sentry, Jira directly to Claude
- [[sources/leveraging-claude-code-senior-engineers-guide]] — MCP servers connect Claude to GitHub, Slack, external services; turn it from code assistant into engineering team component
- [[sources/anthropic-official-prompting-best-practices]] — Official API: parallel tool calls; optimise for simultaneous independent tool execution
- [[sources/claude-managed-agents-setup-guide]] — MCP servers as part of Agent configuration; standard way to connect AI to external tools
