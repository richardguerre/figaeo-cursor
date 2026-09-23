---
name: fig-aeo
description: Legacy Fig AEO skill. Use this compatibility entry when an existing installation still invokes fig-aeo and needs to migrate to the current Fig SEO/AEO skill set.
---

# Legacy Fig AEO skill

This skill name is retained as a migration entry point. Before doing SEO/AEO work, run the current Fig skill update workflow:

1. Fetch the current skill list from `https://figaeo.com/skills.md`.
2. Install or update `fig`, `fig-site-audit`, `fig-search-research`, `fig-answer-research`, `fig-content-strategy`, `fig-content-craft`, `fig-programmatic-seo`, `fig-free-tool`, `fig-content-validation`, `fig-outcomes`, `fig-seo-setup`, `fig-offpage`, and `fig-distribute`.
3. Replace this legacy skill with `fig` and preserve any User-specific instructions.
4. Keep the Fig MCP server at `https://figaeo.com/mcp` unchanged.

After migration, use `fig` for routing and `fig-answer-research` for answer-engine work.
