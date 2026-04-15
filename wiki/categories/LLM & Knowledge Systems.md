---
tags:
  - category
---

# Category: LLM & Knowledge Systems

LLM-powered knowledge bases, Claude Skills, Obsidian workflows, and the Andrej Karpathy method for building a self-improving second brain.

## Articles in this category

- [[sources/karpathy-method-claude-skills-obsidian]] — Full breakdown of the LLM Wiki architecture, Claude Skills system, and MCP Obsidian integration
- [[sources/claude-obsidian-second-brain-defileo]] — Operational implementation: ingest/lint/morning briefing commands; call transcript processing
- [[LLM Wiki]] — The pattern this wiki implements: raw/ → wiki/ → reports/ compounding loop
- [[Andrej Karpathy]] — Originator of the LLM-as-librarian insight; observations on shifting from code to knowledge work
- [[Claude Skills]] — Reusable Claude Code workflows packaged as SKILL.md + scripts (kb-compile, kb-index, kb-refinement)
- [[Obsidian]] — Markdown IDE for browsing, navigating, and visualising the wiki graph
- [[Obsidian Web Clipper]] — Capture tool: saves web pages to raw/ as markdown for ingestion
- [[MCP]] — Model Context Protocol; enables Claude to read and write the Obsidian vault directly in real time

## Related categories
- [[categories/Technology & Data]]
- [[categories/Claude Usage & Prompting]]

## Key Insights

- **The value of the LLM Wiki pattern is in the maintenance cost, not the creation cost**: Any LLM can summarise a document. The hard part of a knowledge base is keeping it maintained — updating cross-references when new sources contradict old claims, flagging orphan pages, keeping the index current. The LLM Wiki pattern works because it offloads maintenance to the same system that creates the content. A human-maintained wiki fails because maintenance cost grows faster than the value; an LLM-maintained wiki doesn't have this failure mode.

- **The skill-as-workflow pattern (SKILL.md + scripts) is what separates repeatable automation from one-off prompts**: A raw prompt to "ingest this document" produces variable results across sessions. A SKILL.md that defines exactly what steps to follow, what the output format should be, and how to log the run produces consistent results that compound. The kb-compile/kb-index/kb-refinement skill stack built here is a direct instantiation of the pattern described in the Karpathy source article.

- **Obsidian's graph view is the best diagnostic tool for the health of the knowledge base**: Orphan pages (nodes with no inbound links), hub pages (nodes with many connections), and disconnected clusters all become visible immediately in graph view. This makes it possible to identify, at a glance, where the wiki has gaps or where synthesis is missing — something that would require reading every page to discover manually.

- **The raw/ → wiki/ → reports/ → back into wiki/ loop is more powerful than it sounds**: The report-filing step is the key insight most implementations miss. When a query produces a valuable analysis (like the 30-day and 90-day WBR insight reports generated in this session), filing that report back into the wiki makes it a first-class knowledge asset rather than a chat artifact. Future sessions can cite, update, or build on it — compounding the analytical work rather than repeating it.

- **MCP for Obsidian (Local REST API plugin) unlocks real-time bidirectional editing**: Without MCP, Claude Code reads and writes markdown files via the filesystem, with Obsidian refreshing on file save. With MCP, Claude can read the current vault state (including links Obsidian has resolved), write directly, and observe the vault as a live graph. This enables more sophisticated operations — like detecting whether a new source has already been partially covered before deciding how to route it.
