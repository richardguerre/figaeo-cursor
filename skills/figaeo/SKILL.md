---
name: figaeo
description: Query FigAEO hosted SEO/AEO intelligence over MCP. Use after the User connects and, when remaining USD is $0, after User-confirmed Stripe Checkout.
---

# FigAEO in Cursor

Connect `https://figaeo.com/mcp` (Streamable HTTP). Complete MCP OAuth 2.1 in the connect card (GitHub or Google). The verified email is the FigAEO User shared with Grok Bot.

## First session

Two browser hops at $0: OAuth, then Checkout. Do not imply one-click paid access. After Checkout, retry the same tool. FigAEO does not notify you when payment completes.

## Tools

Use `research_domain`, `suggest_keywords`, `get_keyword_metrics`, `get_serp`, `compare_serp_competitors`, `get_backlink_overview`, `get_backlinks`, `get_local_serp`, `research_local_business`, `research_ai_visibility`, `resolve_location`, `balance`, and `create_checkout`. Prefer compact format. United States and English are defaults unless the User names another market. Local tools require an explicit city.

## Payment

`create_checkout()` defaults to $20. Minimum $10. Taxes are added at Checkout. Stripe Link is faster Checkout, not Agent payment. When a tool returns insufficient_credits, call create_checkout, wait for the User, retry the same tool.

About 2,000 live SERPs (top 10) per $10. About 250 keyword-idea lookups per $10 at the default of 20 ideas.

$20 is the recommended pack: about 4,000 live SERPs (top 10) or about 500 keyword-idea lookups (20 ideas each)—enough to research, act on, and recheck one website for about four weeks. Call create_checkout() with no amount to buy $20; minimum is $10. Deeper SERPs and site: queries cost more.

A typical focused pass is still about 20 idea lookups and about 120 SERPs per two weeks (about 30 keywords, 3 snapshots). A $20 pack is about four weeks of that headroom, not a spend target. Work a focused set. Do not plan daily snapshots of hundreds of keywords.

FigAEO returns data. You decide whether to change the site. Do not claim FigAEO edited pages or guaranteed rankings.
