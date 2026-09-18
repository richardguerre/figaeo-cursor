---
name: fig-search-research
description: Research organic-search demand, intent, SERPs, competitors, and keyword opportunities with Fig MCP before choosing SEO targets or content priorities. Use for best-of, top, vs, alternative, and listicle queries that may influence AI recommendations.
metadata:
  version: 3
  managed-by: fig-skill-update
---

# Fig Search Research

Start from the target site's real coverage, baseline performance, business/conversion goal, and the User's context, not a random high-volume list.

## Research loop

1. Establish the baseline, target metric, observation window, assumptions, confounders, and authorized measurement surfaces before paid research.
2. Call `balance`, then `research_domain` on the brand host. Do not mention remaining balance in User chat unless remaining is under $1 (or $0 / insufficient_credits). Call `balance` when the User asks or before Checkout — do not parrot Remaining $ after every paid tool.
3. Use `suggest_keywords` from strong existing terms only when more ideas are needed.
4. Use `get_keyword_metrics` on a short candidate set. Treat volume, CPC, competition, and intent as evidence, not a verdict. Null or missing metrics mean Google Ads had no coverage for that query — the call succeeded. A batch can mix populated rows and null rows. Empty coverage is `[]`. Do not treat those as a broken tool or `provider_failure`. One 40501 (too many words or invalid field) fails the whole keyword array; shorten or split phrases and resubmit. Fig does not split the array and retry only valid phrases.
5. Use `get_serp` and `compare_serp_competitors` for the queries that could change the decision. Resolve an ambiguous city with `resolve_location` before local research.

Read each SERP as a specification: dominant format, intent, repeated domains, features, freshness, and gaps. Prefer opportunities where the site has a relevant URL or the SERP has an addressable intent or quality gap.

## Best-of / listicle influence

Fig improves SEO/AEO here by showing commercial best-of demand, who already ranks, and whether the brand is named in observed Google/ChatGPT visibility — then the Agent asks what to ship. Listicles help extraction and often appear in citation mixes; they are not a ChatGPT switch. AI Overviews lean more on Google retrieval; ChatGPT and Perplexity often diverge from the Google top 10. Prefer Fig tool evidence over influencer anecdotes.

1. Find commercial `best` / `top` / `vs` / `alternative` queries for the brand's category with `suggest_keywords` from strong category seeds, then `get_keyword_metrics` on a short list. Treat null or empty metrics as no Ads coverage, not a failed lookup.
2. Inventory who already ranks with `get_serp` (add `compare_serp_competitors` when a small query set needs comparison). Note blogs, YouTube, Reddit, directories, and any other format on the SERP. Do not assume only blogs and YouTube matter for every engine.
3. Check whether the brand is named today with `research_ai_visibility` on the same prompts. Fig observes Google and ChatGPT; ChatGPT mention data is United States and English only; `competitors` is ChatGPT-only. Claude, Gemini, and Perplexity mention scores are not supplied.
4. Ask the User which actions to authorize (Strategy Approval in Strategic Mode):
   - Ship or improve an owned listicle or comparison on the brand site (brief via `fig-content-strategy`).
   - Build an outreach target list: URL, position, format, and whether the brand is already listed. Fig does not send email, negotiate payment, or buy placements.
   - Add companion YouTube only when the User authorizes video work. Quality and transcripts still affect ranking and retrieval.
5. Recheck the same queries with `get_serp` and `research_ai_visibility` after changes have had time to be crawled. Report the observed results and tie each outcome to returned evidence.

Paid or affiliate placements on third-party listicles are outside Fig. Disclose sponsorships on owned comparisons. Follow host and Google policies.

## Output

Return a focused table of candidates with primary intent, target URL or page type, evidence, first-hand/original evidence available or missing, business fit, business/conversion goal, difficulty, competition, recommended action, confidence, baseline, target metric, observation window, assumptions, and confounders. Include 3–5 competing URLs and the specific gap to beat when proposing a content page. For best-of / listicle work, include the outreach target list (URL, position, format, brand already listed) when that action is in scope.

Use one primary query and intent per page as a heuristic; keep supporting queries on the page when they serve the same user need, and recommend a separate page only when the audience, intent, evidence, or desired action is materially different. Do not turn query variants into a mass-production queue.

Never invent metrics, SERP features, competitors, or ranking movement. Recheck the same compact query set after the change has had time to be crawled.
