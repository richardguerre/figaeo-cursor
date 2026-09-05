---
name: fig-growth-creative
description: Use when running creative, unconventional SEO/AEO growth plays that still need live data from Fig — content angles, distribution, entity building, co-citation, prompt-shaped pages, or measurement of experiments. Trigger on "growth experiment", "content angle", "co-citation", "entity building", "unconventional SEO", "distribution idea", or "prompt-shaped content". Do not use for standard rank audits (fig-seo), AEO crawl/schema/llms.txt compliance (fig-aeo), or spammy black-hat tactics.
---

# Fig growth creative

Unconventional plays that stay evidence-based. Fig MCP is how the Agent checks whether an idea is real on the SERP or in AI citations. Install/setup is not this skill: fetch https://figaeo.com/llms.txt (optional https://figaeo.com/install.md).

Use Fig MCP for live data. Do not invent SERP gaps, volumes, or AI mentions to justify a stunt.

**Refuse:** PBNs, cloaking, scraped spun pages, fake reviews, bought comments, malware, hidden text, doorway networks, or "guarantee page-one" packages.

## Loop

**Hypothesis → smallest shippable artifact → Fig recheck.**

1. **Gather:** `balance`, then a tight Fig pass: `get_serp` / `compare_serp_competitors` on the experiment query, `research_domain` for what the brand already owns, `research_ai_visibility` (google / chat_gpt only) if the bet is AI citation. Prefer compact format.
2. **Act:** One artifact per experiment (a page section, a public dataset, a comparison table, a changelog, a guest explainer). Ship it.
3. **Verify:** Same Fig calls as the hypothesis. Kill, iterate, or double-down. Do not declare a win from anecdotes.

## Angle finding (data first)

From `get_serp` and `compare_serp_competitors`, look for:

- Intent mismatch (SERP is docs; everyone writes lifestyle blogs — or the reverse)
- Stale winners (dates, version numbers, APIs that have moved)
- Missing comparison or "vs" page the SERP still ranks listicles for
- Questions in People Also Ask that no ranking URL answers directly
- Competing domains that rank without a canonical explainer the brand could own

`suggest_keywords` and `get_keyword_metrics` size the idea **after** the SERP says it exists. Do not start from a clever headline and then hunt for a query.

## Distribution and entity

Creative does not mean "more blog posts." Prefer surfaces that create **citable facts** and **off-site mentions**:

- Public, dated source-of-truth (limits, pricing ops, architecture diagrams) that other writers can quote
- Original tables (feature matrices, protocol differences) built from documented facts, not invented benchmarks
- Co-citation: earn mentions next to category incumbents via useful explainers, not widget spam
- sameAs-consistent profiles (GitHub, docs, X) so entity skills in fig-aeo have something to bind
- Prompt-shaped content: pages that answer the actual prompts people type into ChatGPT ("how do I connect X to Y") with copy-paste steps — then check `research_ai_visibility` on those queries where Fig supports the platform

Use `get_backlink_overview` / `get_backlinks` to see which referring hosts already talk about competitors and which brand URLs they skip. Pitch **those** hosts a specific artifact, not a generic guest post.

## Experiment design

Each experiment fits in a $10–$20 pack, not a quarter-long content calendar.

Write down before shipping:

- Query + platform (organic SERP vs google AI mentions vs chat_gpt mentions)
- Artifact URL
- Success signal Fig can measure (position on `get_serp`, mention/citation on `research_ai_visibility`)
- Time box (for example one recheck at two weeks — not daily snapshots of hundreds of keywords)

A typical focused pass is still about 20 idea lookups and about 120 SERPs per two weeks (about 30 keywords, 3 snapshots). A $20 pack is about four weeks of that headroom, not a spend target.

## Collaboration

- Classic keyword/on-page/backlink work: fig-seo
- Crawlers, schema, brand llms.txt, citability prose: fig-aeo
- This skill: only the bet that is weird **and** measurable

## Fig ops

Sign in with GitHub or Google; there is no preferred identity provider. First-time setup: https://figaeo.com/llms.txt.

Call `balance` before paid work. At $0 remaining, call `create_checkout` (default $20, minimum $10), wait for Checkout to finish, then retry the same tool. Fig does not notify the agent. Your agent starts Checkout. On Grok, Stripe Link can complete payment after you connect Link. Otherwise you confirm Checkout in the browser. Applicable tax is added at Checkout.

$20 is the recommended pack: about 4,000 live SERPs (top 10) or about 500 keyword-idea lookups (20 ideas each)—enough to research, act on, and recheck one website for about four weeks. Call create_checkout() with no amount to buy $20; minimum is $10. Deeper SERPs and site: queries cost more. About 2,000 live SERPs (top 10) per $10. About 250 keyword-idea lookups per $10 at the default of 20 ideas.

On `authentication`, fetch https://figaeo.com/llms.txt. On `insufficient_credits`, checkout then retry. On `validation` / `no_data` / `provider_failure`, do not invent results. Privacy and terms: https://figaeo.com/privacy and https://figaeo.com/terms.

Fig returns data. The Agent decides what to change. No ranking or citation guarantees.
