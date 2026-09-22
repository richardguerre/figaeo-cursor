---
name: fig-search-research
description: Research organic-search demand, intent, SERPs, competitors, and keyword opportunities with Fig MCP before choosing SEO targets or content priorities. Use for best-of, top, vs, alternative, and listicle queries that may influence AI recommendations.
metadata:
  version: 5
  managed-by: fig-skill-update
---

# Fig Search Research

Start from the target site's real coverage, baseline performance, business/conversion goal, and the User's context, not a random high-volume list. Read `fig/operator-memory.json` when present and reuse stored baselines and open observation windows.

## Research loop

1. Establish the baseline, target metric, observation window, assumptions, confounders, and authorized measurement surfaces before paid research. Prefer values already stored in operator memory; do not invent replacements. If Search Console is connected, use returned Search Analytics (query and page) as coverage, CTR, and position baselines — including low-CTR pages, striking-distance queries, and wrong-query/cannibalization when those rows exist. If GSC is not connected, mark Search Console measurement unavailable. Never invent GSC metrics. How-to: https://figaeo.com/gsc.md.
2. Call `balance`, then `research_domain` on the brand host. Do not mention remaining balance in User chat unless remaining is under $1 (or $0 / insufficient_credits). Call `balance` when the User asks or before Checkout — do not parrot Remaining $ after every paid tool.
3. Use `suggest_keywords` from strong existing terms only when more ideas are needed.
4. Use `get_keyword_metrics` on a short candidate set. Compact `suggest_keywords` and `get_keyword_metrics` include `competition` and `keyword_difficulty` when the provider returns them. Treat volume, CPC, competition, keyword_difficulty, and intent as evidence, not a verdict. `competition` is a keyword-metrics intensity score, not organic ranking difficulty. `keyword_difficulty` is the provider organic difficulty score when present; null means unknown — do not invent a score. When who ranks or ranking difficulty matters, use `get_serp` and `compare_serp_competitors`. Use `format: "detailed"` for monthly search trends. Null or missing metrics mean Google's keyword dataset had no coverage for that query (organic demand proxy) — the call succeeded. A batch can mix populated rows and null rows. Empty coverage is `[]`. Do not treat those as a broken tool or `provider_failure`. One 40501 (too many words or invalid field) fails the whole keyword array; shorten or split phrases and resubmit. Fig does not split the array and retry only valid phrases. Keyword metrics rate limit (12/min) is an upstream Live keyword-metrics cap, not a Fig quota — batch into few calls. On `rate_limiting`, wait `retry_after_seconds` and retry; do not dump raw `rate_limiting` or provider rate-limit text to the User. If they need a status, say keyword data is busy and you are retrying.
5. Use `get_serp` and `compare_serp_competitors` for the queries that could change the decision. Resolve an ambiguous city with `resolve_location` before local research.

Read each SERP as a specification: dominant format, intent, repeated domains, features, freshness, and gaps. Prefer opportunities where the site has a relevant URL or the SERP has an addressable intent or quality gap. When ranking actions for `fig-seo-aeo`, apply the Selection rubric there: repair, refresh, consolidate, and prune beat create when evidence is close.

## Best-of / listicle influence

Fig improves SEO/AEO here by showing commercial best-of demand, who already ranks, and whether the brand is named in observed Google/ChatGPT visibility. In Automatic mode, continue through owned-page or outreach-list implementation so the User reviews landed work. In Strategic mode, stop at Strategy Approval before any content change or PR. Listicles help extraction and often appear in citation mixes; they are not a ChatGPT switch. AI Overviews lean more on Google retrieval; ChatGPT and Perplexity often diverge from the Google top 10. Prefer Fig tool evidence over influencer anecdotes.

1. Find commercial `best` / `top` / `vs` / `alternative` queries for the brand's category with `suggest_keywords` from strong category seeds, then `get_keyword_metrics` on a short list. Treat null or empty metrics as no keyword-metrics coverage, not a failed lookup. Pace `get_keyword_metrics` (keyword metrics rate limit 12/min); do not dump raw `rate_limiting` text to the User.
2. Inventory who already ranks with `get_serp` (add `compare_serp_competitors` when a small query set needs comparison). Note blogs, YouTube, Reddit, directories, and any other format on the SERP. Do not assume only blogs and YouTube matter for every engine.
3. Check whether the brand is named today with `research_ai_visibility` on the same prompts. Fig observes Google and ChatGPT; ChatGPT mention data is United States and English only; `competitors` is ChatGPT-only. Claude, Gemini, and Perplexity mention scores are not supplied.
4. Choose the next action from this set:
   - Ship or improve an owned listicle or comparison on the brand site (brief via `fig-content-strategy`).
   - Build an outreach target list: URL, position, format, and whether the brand is already listed. Expand directories, digital PR, and unlinked mentions via `fig-offpage`. Fig does not send email, negotiate payment, or buy placements.
   - Add companion YouTube only when the User authorizes video work. Quality and transcripts still affect ranking and retrieval.
   In Strategic mode, rank options with the Selection rubric in `fig-seo-aeo` before Strategy Approval and wait. In Automatic mode, pick one primary action with that rubric (rationale vs alternatives), implement it through `fig-seo-aeo` (subagents / new bots / host-equivalent sessions for the write), and hand the User the landed work.
5. Recheck the same queries with `get_serp` and `research_ai_visibility` after changes have had time to be crawled. Report the observed results and tie each outcome to returned evidence.

Paid or affiliate placements on third-party listicles are outside Fig. Disclose sponsorships on owned comparisons. Follow host and Google policies.

## Output

Return a focused table of candidates with primary intent, target URL or page type, evidence, first-hand/original evidence available or missing, business fit, business/conversion goal, difficulty, competition, recommended action, confidence, baseline, target metric, observation window, assumptions, and confounders. Include 3–5 competing URLs and the specific gap to beat when proposing a content page. For best-of / listicle work, include the outreach target list (URL, position, format, brand already listed) when that action is in scope.

Use one primary query and intent per page as a heuristic; keep supporting queries on the page when they serve the same user need, and recommend a separate page only when the audience, intent, evidence, or desired action is materially different. Do not turn query variants into a mass-production queue.

Never invent metrics, difficulty scores, SERP features, competitors, ranking movement, or GSC clicks/impressions/CTR/position. Include named Search Console baselines when GSC is connected, or Search Console measurement unavailable when it is not. Recheck the same compact query set after the change has had time to be crawled. Return observed Fig query rows, GSC rows when connected, and baselines as an operator-memory patch for `fig-seo-aeo` to merge.
