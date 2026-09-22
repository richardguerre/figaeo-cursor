---
name: fig-content-strategy
description: Turn SEO/AEO evidence and an aligned User strategy into prioritized content opportunities, information architecture, briefs, and implementation plans. Use for content census (prune, merge, refresh, decay, cannibalization, orphans, thin overlap), owned listicle or comparison briefs, outreach target lists, and mapping every factual product claim to User source or primary citation; Fig does not send outreach.
metadata:
  version: 8
  managed-by: fig-skill-update
---

# Fig Content Strategy

Use this specialist after research has established the baseline, audience, intent, evidence, business/conversion goal, and constraints. A content strategy is not a calendar of generic posts. Read `fig/operator-memory.json` when present so open priorities, observation windows, and baselines carry across runs. Run a content census before proposing a batch of new pages.

## Prioritize

Rank opportunities by business fit, audience need, search or answer intent, authority, evidence quality, competition, expected impact, implementation cost, and measurement feasibility. State the trade-off behind the order. Apply the Selection rubric in `fig-seo-aeo`: repair, refresh, consolidate, and prune beat create when evidence is close. When an owned URL already covers the intent, rank refresh, merge, or prune ahead of create. When `fig-site-audit` returns a `speed` vital, treat repairing that URL as a selection candidate that can beat net-new content when evidence is close. When Search Console is connected, prefer opportunities the returned rows already support (low-CTR pages with impressions, striking-distance queries, wrong-query/cannibalization). When GSC is not connected, mark Search Console measurement unavailable and do not invent those metrics. How-to: https://figaeo.com/gsc.md.

Choose the right artifact for the observed demand: product page, guide, listicle, comparison, documentation, FAQ, glossary, changelog, dataset, table, calculator, checker, generator, or another format. Match the winning SERP/answer format instead of forcing every opportunity into a blog post. When SERP and business evidence favor an interactive tool over a guide, call `fig-free-tool` instead of drafting a guide brief. Do not recommend a tool as a default lead magnet.

## Content census

Inventory the owned URL set and return ranked prune, merge, and refresh actions with evidence. Prefer consolidate, refresh, and prune over create. Output ranked actions plus briefs; never a mass page factory. Unpublish or delete a production URL only after Strategy Approval.

Label measurement at the top of the census:

- **GSC-connected** when a User-brought Search Console connector, read-only API, or export returned page or query rows for this host. Fig-hosted GSC MCP reads are specified at https://figaeo.com/gsc.md and are not shipped.
- **GSC-unavailable (degraded)** when those reads are missing. Mark Search Console measurement unavailable. Inventory, overlap, and orphan flags still run. Cannibalization, CTR-gap, and striking-distance flags stay qualitative. Do not invent Search Console numbers.

### Inventory

1. Read lite operator memory (`fig/operator-memory.json`; see `fig-seo-aeo` `references/operator-memory.md`) when present and reuse stored URLs, baselines, and open priorities. If it is absent, continue and label **memory-absent**.
2. Fetch `sitemap.xml` and nested sitemaps. Record URL, `lastmod` when present, and template/section when obvious from the path.
3. Crawl a sample: homepage, nav/footer hubs, and representative URLs per important template (product, guide, comparison, docs, blog). Record title, H1, canonical, indexability, approximate length band, inlinks from the sample, and visible publish or update date.
4. Call `research_domain` when existing coverage would change which URLs are important. Pace paid Fig calls; do not pull the whole site through Fig.

Important URLs = sitemap money pages + crawl sample + memory URLs when present.

### Flag

Cite URL(s), observed evidence, and confidence for each flag:

- **Decay** — dated claims, `lastmod` or on-page date lagging competing SERP freshness, or GSC clicks/impressions down versus a stated prior window (**GSC-connected** only).
- **Thin overlap** — same primary intent, near-identical title/H1, or overlapping outline with another owned URL.
- **Cannibalization** — **GSC-connected**: two or more owned URLs ranking for the same query. **GSC-unavailable (degraded)**: overlapping titles or intents plus `get_serp` showing both URLs or neither clearly winning.
- **Orphan** — in sitemap or memory with no inlinks from the crawl sample or known hubs; or linked internally but missing from the sitemap.
- **Refresh candidate** — still matches demand (`get_serp` or keyword metrics when those calls were made) but title, body, proof, or internal links lag the gap.

### Ranked actions

Score each important finding as **refresh**, **merge**, **prune**, **keep**, or **create**. Apply the Selection rubric in `fig-seo-aeo`: refresh, merge, and prune beat create when evidence is close. Create only when no owned URL can cover a distinct user need.

Each ranked action includes action type, target URL(s), evidence, the vital it should move (intent clarity, crawl waste, relevance, speed when a `fig-site-audit` vital is present; CTR only when **GSC-connected**), a brief or handoff, and whether Strategy Approval is required. Prune and unpublish always require Strategy Approval.

Merge names the survivor canonical, sources to redirect, and unique proof to keep. Prune names 410 versus redirect, the replacement URL, and why the page has no distinct user need.

Write census outcomes into lite operator memory (`fig/operator-memory.json`) when present — open priorities and last actions — or return a patch for `fig-seo-aeo` to merge. Return the ranked list to `fig-seo-aeo`. In Automatic mode, implement authorized refresh, merge, and internal-link work through the parent; wait for Strategy Approval before prune or unpublish. In Strategic mode, stop at the ranked census until Strategy Approval.

## Best-of / listicle influence

Fig improves SEO/AEO here by showing commercial best-of demand, who already ranks, and whether the brand is named in observed Google/ChatGPT visibility. In Automatic mode, continue through owned-page or outreach-list implementation so the User reviews landed work. In Strategic mode, stop at Strategy Approval before any content change or PR. Listicles help extraction and often appear in citation mixes; they are not a ChatGPT switch. AI Overviews lean more on Google retrieval; ChatGPT and Perplexity often diverge from the Google top 10. Prefer Fig tool evidence over influencer anecdotes.

1. Find commercial `best` / `top` / `vs` / `alternative` queries for the brand's category with `suggest_keywords` from strong category seeds, then `get_keyword_metrics` on a short list. Treat null or empty metrics as no keyword-metrics coverage, not a failed lookup. Pace `get_keyword_metrics` (keyword metrics rate limit 12/min); do not dump raw `rate_limiting` text to the User.
2. Inventory who already ranks with `get_serp` (add `compare_serp_competitors` when a small query set needs comparison). Note blogs, YouTube, Reddit, directories, and any other format on the SERP. Do not assume only blogs and YouTube matter for every engine.
3. Check whether the brand is named today with `research_ai_visibility` on the same prompts. Fig observes Google and ChatGPT; ChatGPT mention data is United States and English only; `competitors` is ChatGPT-only. Claude, Gemini, and Perplexity mention scores are not supplied.
4. Choose the next action from this set:
   - Ship or improve an owned listicle or comparison on the brand site (brief via `fig-content-strategy`).
   - Build an outreach target list: URL, position, format, and whether the brand is already listed. Hand general directories, digital PR, and unlinked-mention briefs to `fig-offpage`. Fig does not send email, negotiate payment, or buy placements.
   - Add companion YouTube only when the User authorizes video work. Quality and transcripts still affect ranking and retrieval.
   In Strategic mode, rank options with the Selection rubric in `fig-seo-aeo` before Strategy Approval and wait. In Automatic mode, pick one primary action with that rubric (rationale vs alternatives), implement it through `fig-seo-aeo` (subagents / new bots / host-equivalent sessions for the write), and hand the User the landed work.
5. Recheck the same queries with `get_serp` and `research_ai_visibility` after changes have had time to be crawled. Report the observed results and tie each outcome to returned evidence.

Paid or affiliate placements on third-party listicles are outside Fig. Disclose sponsorships on owned comparisons. Follow host and Google policies.

## Brief

For each approved priority, provide:

- target URL or page type and one primary query or answer need; treat one primary intent per page as a heuristic, not an absolute law;
- audience, intent, desired action, and the gap to address;
- baseline, target metric, observation window, business or conversion goal, assumptions, and likely confounders; include named Search Console baselines when GSC is connected, or Search Console measurement unavailable when it is not;
- title, H1, answer-first opening, and outline;
- internal links, first-hand/original evidence, proof, and citations needed;
- SEO/AEO implementation notes;
- for census merge work, the survivor canonical, sources to redirect, and unique proof to keep;
- for census prune work, 410 versus redirect, the replacement URL, and Strategy Approval status;
- for best-of work, the outreach target list when authorized, or the owned listicle/comparison brief;
- product-truth mapping: every planned factual claim with its User source or primary citation; missing proof as a User input task, not as copy to ship;
- craft notes from `fig-content-craft` when the page will be written: polish requirements, table/figure needs, proprietary-data pattern, and filled research-brief recipes (SERP-format, entity/proof, original-research, visual, answer-extract) instead of empty "add proof" bullets;
- acceptance criteria and the Fig calls to recheck (`get_serp` and `research_ai_visibility` on the same prompts).

## Product truth

Before briefing or drafting marketing copy, read `fig/product-truth.md` or the same sections in host Agent memory when present. Use the `fig-content-validation` template at `assets/product-truth.md` when the User needs a claims file. Fig MCP does not store the ledger.

Every factual claim in a brief maps to an approved ledger fact, a User source, or a cited primary source. Put unproven claims in the brief as research or User input. Keep forbidden ledger claims out of the outline. Competitor marketing copy is not product truth.

After an owned URL ships, call `fig-distribute`. Fig does not send outreach.

Do not fabricate facts, statistics, quotes, competitor claims, or product capabilities. Prefer improving, consolidating, or expanding useful pages over producing one page per keyword variant. Flag near-duplicate, doorway-like, or programmatic mass-production risk and require a distinct user need, evidence base, and canonical target for each proposed page. A census that recommends create for every keyword variant has failed; return prune, merge, or refresh instead unless the intent is uncovered. When SERP plus business evidence supports a bounded compare, alternatives, use-case, or for-persona **template set**, delegate to `fig-programmatic-seo` instead of queuing one brief per keyword variant.

Return open priorities (and observation windows for approved briefs) as an operator-memory patch for `fig-seo-aeo` to merge. Do not invent metrics.

This skill chooses what to ship and why. Hand writing, polish, visuals, and original-research page shape to `fig-content-craft`. Validate with `fig-content-validation`.
