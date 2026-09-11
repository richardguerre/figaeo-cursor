---
name: fig-content-strategy
description: Turn SEO/AEO evidence and an aligned User strategy into prioritized content opportunities, information architecture, briefs, and implementation plans. Use for owned listicle or comparison briefs and outreach target lists; Fig does not send outreach.
metadata:
  version: 3
  managed-by: fig-skill-update
---

# Fig Content Strategy

Use this specialist after research has established the baseline, audience, intent, evidence, business/conversion goal, and constraints. A content strategy is not a calendar of generic posts.

## Prioritize

Rank opportunities by business fit, audience need, search or answer intent, authority, evidence quality, competition, expected impact, implementation cost, and measurement feasibility. State the trade-off behind the order.

Choose the right artifact for the observed demand: product page, guide, listicle, comparison, documentation, FAQ, glossary, changelog, dataset, table, or another format. Match the winning SERP/answer format instead of forcing every opportunity into a blog post.

## Best-of / listicle influence

Fig improves SEO/AEO here by showing commercial best-of demand, who already ranks, and whether the brand is named in observed Google/ChatGPT visibility — then the Agent asks what to ship. Listicles help extraction and often appear in citation mixes; they are not a ChatGPT switch. AI Overviews lean more on Google retrieval; ChatGPT and Perplexity often diverge from the Google top 10. Prefer Fig tool evidence over influencer anecdotes.

1. Find commercial `best` / `top` / `vs` / `alternative` queries for the brand's category with `suggest_keywords` from strong category seeds, then `get_keyword_metrics` on a short list. Treat null or empty metrics as no Ads coverage, not a failed lookup.
2. Inventory who already ranks with `get_serp` (add `compare_serp_competitors` when a small query set needs comparison). Note blogs, YouTube, Reddit, directories, and any other format on the SERP. Do not assume only blogs and YouTube matter for every engine.
3. Check whether the brand is named today with `research_ai_visibility` on the same prompts. Fig observes Google and ChatGPT; ChatGPT mention data is United States and English only; `competitors` is ChatGPT-only. Claude, Gemini, and Perplexity mention scores are not supplied.
4. Ask the User which actions to authorize (Strategy Approval in Strategic Mode):
   - Ship or improve an owned listicle or comparison on the brand site (brief via `fig-content-strategy`).
   - Build an outreach target list: URL, position, format, and whether the brand is already listed. Fig does not send email, negotiate payment, or buy placements.
   - Add companion YouTube only when the User authorizes video work. Quality and transcripts still affect ranking and retrieval.
5. Recheck the same queries with `get_serp` and `research_ai_visibility` after changes have had time to be crawled. Report observed results; Fig does not guarantee rankings or citations.

Paid or affiliate placements on third-party listicles are outside Fig. Disclose sponsorships on owned comparisons. Follow host and Google policies.

## Brief

For each approved priority, provide:

- target URL or page type and one primary query or answer need; treat one primary intent per page as a heuristic, not an absolute law;
- audience, intent, desired action, and the gap to address;
- baseline, target metric, observation window, business or conversion goal, assumptions, and likely confounders;
- title, H1, answer-first opening, and outline;
- internal links, first-hand/original evidence, proof, and citations needed;
- SEO/AEO implementation notes;
- for best-of work, the outreach target list when authorized, or the owned listicle/comparison brief;
- acceptance criteria and the Fig calls to recheck (`get_serp` and `research_ai_visibility` on the same prompts).

Do not fabricate facts, statistics, quotes, competitor claims, or product capabilities. Mark missing proof as a research or User input task. Prefer improving, consolidating, or expanding useful pages over producing one page per keyword variant. Flag near-duplicate, doorway-like, or programmatic mass-production risk and require a distinct user need, evidence base, and canonical target for each proposed page.
