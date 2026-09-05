---
name: fig-aeo
description: Use when optimizing a brand for answer engines and AI search with Fig — AI Overviews, ChatGPT visibility, citability, FAQ/schema, entity signals, AI crawler access, or llms.txt. Trigger on "AEO", "GEO", "AI Overviews", "get cited by ChatGPT", "Perplexity", "Claude search", "Gemini mentions", "llms.txt", "FAQ schema", "citability", or "AI crawler robots.txt". Do not use for classic keyword/SERP ranking work (fig-seo) or growth experiments (fig-growth-creative).
---

# Fig AEO

Answer-engine playbook: make the brand extractable, citable, and reachable by AI systems. Fig MCP supplies **observed** mention and citation data where the product supports it. Install/setup is not this skill: fetch https://figaeo.com/llms.txt (optional https://figaeo.com/install.md).

Use Fig MCP for live data. Do not invent AI-mention counts, cited-domain lists, or SERP/AI-Overview screenshots.

## Honest Fig coverage

`research_ai_visibility` returns observed LLM mentions, visibility, or citations — not a live generated answer and not Fig historical tracking.

- Platforms Fig supports: `google` (AI Overview-style mentions/citations) and `chat_gpt`.
- `competitors` is `chat_gpt` only. Google cited domains are not competitor brands; do not invent rivals from citations.
- ChatGPT mention data is United States and English only.
- Claude, Gemini, and Perplexity **mentions are not supported** by Fig. For those surfaces, audit crawler access and on-page citability, then say Fig has no mention row. Never fabricate a Perplexity/Claude/Gemini score.

Default: operation `mentions`, platform `google`, compact format. Pair with `get_serp` when the query also has a classic SERP or an AI Overview feature.

## Loop

**Audit → fix → recheck** on a small query set the brand should own.

1. **Audit (gather):** `balance`, then `research_ai_visibility` for the brand domain and 3–8 priority queries (`mentions`, `visibility`, `citations`; `competitors` on `chat_gpt` only). Fetch the page, `/robots.txt`, `/llms.txt`, and JSON-LD. Score four vectors below. Prefer compact format. United States and English are defaults unless the User names another market.
2. **Fix (act):** P0 crawl/index/crawler blocks, then citability (answer-first, stats, quotes), then schema/FAQ, then entity pages. Produce paste-ready HTML, JSON-LD, robots, and llms.txt — the Agent or brand owner ships them.
3. **Recheck (verify):** Re-run the same `research_ai_visibility` arguments after publish. Compare mentions/citations to the thread. Do not claim ChatGPT/Claude/Perplexity/Gemini rankings Fig did not return.

## Four vectors (prioritize in this order)

Inspired by GEO practice: Technical, Citability, Schema, Entity. Use Fig where it measures; use page fetch for the rest.

### 1. Technical (AI can reach the page)

P0 if crawlers are blocked.

- Fetch `robots.txt`. Allow Googlebot. For AI retrieval, allow commonly documented user-agents such as `GPTBot`, `OAI-SearchBot`, `ClaudeBot`, `PerplexityBot`, and `Google-Extended` **unless the brand owner opted out**. Do not treat `Google-Extended` as an AI Overviews off switch.
- HTML should contain the answer without requiring a unique client-only render for the first paragraph.
- Confirm `https://example.com/llms.txt` (brand host) exists and is accurate — informational, not a ranking factor.
- `noindex` / `nosnippet` hide pages from search and often from AI snippets; only keep them on purpose.

### 2. Citability (models have something to quote)

P0 for pages that should be the answer.

- First sentence answers the query, then detail.
- Replace hedges with attributed facts (changelog dates, documented limits, named APIs). Do not invent statistics — pull from the brand's own published numbers or omit.
- Expert-attributed quotes and outbound citations to primary sources increase extractability.
- Unique tables and definitions beat synonymous fluff.
- Keep a visible updated date when the topic changes.

### 3. Schema (machines parse the page)

Load `references/schema.md` when adding JSON-LD.

- Article + FAQPage are the usual pair for guides. BreadcrumbList when there is a real crumb trail.
- FAQ answers must appear in visible HTML, not only JSON-LD.
- Do not add deprecated rich-result types the brand does not qualify for. Do not fake reviews or awards.

### 4. Entity (the brand is a consistent thing)

- Organization/SoftwareApplication JSON-LD with canonical name, URL, sameAs (docs, GitHub, X) that match public profiles.
- One spelling of the product name on title, H1, and schema.
- Disambiguate from similarly named tools in the intro.

## Query set

Build queries from `research_domain` / `suggest_keywords` only when needed to choose AEO targets; then spend the pack on `research_ai_visibility` + a few `get_serp` checks. Example shape: "[category] for [job]", "what is [product]", "best [category] for [stack]" — using the User's real product, not fictional local services.

## llms.txt for the brand

Ship a small llmstxt.org file on the **brand** origin (not figaeo.com unless the brand is Fig): H1 product name, blockquote summary, how an agent should use the product, H2 link lists to markdown docs. Fig's own install file is https://figaeo.com/llms.txt and is not a template to copy verbatim.

## Recheck

Same queries, same country/language, same `research_ai_visibility` operation. If remaining USD is $0, `create_checkout` then retry the **same** tool.

## Fig ops

Sign in with GitHub or Google; there is no preferred identity provider. First-time setup: https://figaeo.com/llms.txt.

Call `balance` before paid work. At $0 remaining, call `create_checkout` (default $20, minimum $10), wait for Checkout to finish, then retry the same tool. Fig does not notify the agent. Your agent starts Checkout. On Grok, Stripe Link can complete payment after you connect Link. Otherwise you confirm Checkout in the browser. Applicable tax is added at Checkout.

$20 is the recommended pack: about 4,000 live SERPs (top 10) or about 500 keyword-idea lookups (20 ideas each)—enough to research, act on, and recheck one website for about four weeks. Call create_checkout() with no amount to buy $20; minimum is $10. Deeper SERPs and site: queries cost more. About 2,000 live SERPs (top 10) per $10. About 250 keyword-idea lookups per $10 at the default of 20 ideas.

On `authentication`, fetch https://figaeo.com/llms.txt. On `insufficient_credits`, checkout then retry. On `validation` / `no_data` / `provider_failure`, do not invent results. Privacy and terms: https://figaeo.com/privacy and https://figaeo.com/terms.

Fig returns data. The Agent decides what to change. No ranking or citation guarantees.
