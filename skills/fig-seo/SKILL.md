---
name: fig-seo
description: Use when doing traditional SEO for a brand site with Fig — keyword and intent research, SERP competitor analysis, on-page and technical priorities, backlink overview, content briefs, or rank-and-recheck loops. Trigger on "SEO audit", "keyword research", "what ranks", "SERP competitors", "on-page priorities", "content brief", "backlink gap", or "improve organic search". Do not use for AI-citation or llms.txt work (fig-aeo) or unconventional distribution experiments (fig-growth-creative).
---

# Fig SEO

Expert organic-search playbook for a brand site. Fig MCP is the live-data instrument. Install/setup is not this skill: fetch https://figaeo.com/llms.txt (optional https://figaeo.com/install.md).

Use Fig MCP for live data. Do not invent SERP positions, search volume, CPC, or backlink counts.

## Loop

**Gather → act → verify.** Always gather with Fig before rewriting pages. After shipping, recheck the same queries. Fig does not edit the site and does not guarantee rankings.

1. **Gather:** `balance`, then `research_domain` on the brand host, `suggest_keywords` from the strongest terms, `get_keyword_metrics` on a short list, `get_serp` plus `compare_serp_competitors` on the terms that matter, `get_backlink_overview` / `get_backlinks` when off-page is in scope. Prefer compact format. United States and English are defaults unless the User names another market. If a city name is ambiguous, `resolve_location` first — never pick a market silently.
2. **Act:** Rank fixes P0 → P2. Produce copy-ready titles, intros, outline, internal links, and a brief. The Agent (or brand owner) ships changes on the site.
3. **Verify:** Re-run `get_keyword_metrics` and `get_serp` on the same terms after the change has had time to be crawled. Compare to the earlier snapshot in the thread. Do not claim movement Fig did not return.

Work a focused set. Do not plan daily snapshots of hundreds of keywords.

## Keyword and intent

Start from the brand domain, not a fantasy keyword list.

- `research_domain` → terms and URLs the host already appears for.
- `suggest_keywords` → related ideas from the strongest seeds (default 20 ideas).
- `get_keyword_metrics` → volume, CPC, competition, intent for keywords already in hand. Do not use this to invent a SERP.

Map each target query to one primary intent (learn / compare / transact). One page, one primary query. Supporting queries belong in H2s and FAQs, not extra homepages.

Prioritize terms where the brand already has a relevant URL **or** the SERP is winable (forums, thin listicles, mismatched intent) over head terms dominated by official docs and marketplaces.

## SERP competitors

For each priority query, `get_serp` (observed current results and features — not history) and `compare_serp_competitors` (competing domains across a small keyword set).

Read the SERP as a spec:

- What format wins (guide, docs, comparison, changelog)?
- Which domains repeat, and what angle do they take?
- Which features appear (People Also Ask, video, sitelinks)? Match the format; do not force a blog post into a SERP of product docs.

Name 3–5 competing URLs. The brief must beat a specific gap (fresher steps, clearer definition, original table, missing alternative).

## On-page and technical priorities

Inspect the brand URL (fetch the page) alongside Fig data. Order:

- **P0:** Indexable HTML for the primary answer; unique title and H1 aligned to the query; canonical; noindex/robots mistakes; broken primary internal links; thin or off-intent page vs the SERP.
- **P1:** Intro that answers in the first screen; heading hierarchy; descriptive URLs; internal links from relevant existing pages; compressed images; mobile-readable layout.
- **P2:** Meta description as a pitch, not a ranking lever; OG tags for shares; breadcrumb consistency.

Do not spend a pack on deeper SERPs (`depth` above 10) unless the User asked for page-2+ competitors. Deeper SERPs and `site:` queries cost more.

## Backlinks

Use `get_backlink_overview` for referring-domain and strength summary, `get_backlinks` for a bounded list of source/target URLs and anchors. Not outreach contact discovery.

Act only on gaps that match the SERP: competitors earn links from docs hubs, changelogs, or roundups the brand is absent from. Recommend specific page targets. Do not sell PBNs, expired domains, or comment spam.

## Content brief (output)

For each P0 query, emit:

- Target URL (existing or to create) and primary query + intent
- SERP format to match and 3 competing URLs with the gap to beat
- Title, H1, first-paragraph answer (from live SERP language, not invented stats)
- Outline (H2/H3) covering PAA-style questions seen on `get_serp`
- Internal links to add (from `research_domain` URLs)
- Proof needed (screenshot, table, changelog) — do not fabricate numbers
- Recheck plan: which Fig calls to rerun

## Measurement

A typical focused pass is still about 20 idea lookups and about 120 SERPs per two weeks (about 30 keywords, 3 snapshots). A $20 pack is about four weeks of that headroom, not a spend target.

Recheck the same compact set. If remaining USD is too low, `create_checkout` then retry the **same** tool.

## Fig ops

Sign in with GitHub or Google; there is no preferred identity provider. First-time setup: https://figaeo.com/llms.txt.

Call `balance` before paid work. At $0 remaining, call `create_checkout` (default $20, minimum $10), wait for Checkout to finish, then retry the same tool. Fig does not notify the agent. Your agent starts Checkout. On Grok, Stripe Link can complete payment after you connect Link. Otherwise you confirm Checkout in the browser. Applicable tax is added at Checkout.

$20 is the recommended pack: about 4,000 live SERPs (top 10) or about 500 keyword-idea lookups (20 ideas each)—enough to research, act on, and recheck one website for about four weeks. Call create_checkout() with no amount to buy $20; minimum is $10. Deeper SERPs and site: queries cost more. About 2,000 live SERPs (top 10) per $10. About 250 keyword-idea lookups per $10 at the default of 20 ideas.

On `authentication`, fetch https://figaeo.com/llms.txt. On `insufficient_credits`, checkout then retry. On `validation` / `no_data` / `provider_failure`, do not invent results. Privacy and terms: https://figaeo.com/privacy and https://figaeo.com/terms.

Fig returns data. The Agent decides what to change. No ranking guarantees.
