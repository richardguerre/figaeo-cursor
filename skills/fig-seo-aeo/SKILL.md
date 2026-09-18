---
name: fig-seo-aeo
description: Improve a website's SEO and AEO with Fig MCP. Use for broad optimization requests, audits, strategy, content opportunities, implementation changes, or validation. Call fig-search-research then fig-content-strategy for get-recommended-in-ChatGPT, listicle, and best-of requests. Infer whether the request is clear enough for Automatic Mode or needs Strategic Mode, and preserve Strategy Approval before strategic implementation.
metadata:
  version: 3
  managed-by: fig-skill-update
---

# Fig SEO/AEO

Use Fig as the evidence layer and make the consuming Agent useful to the User. Fig is read-only: the consuming Agent may write content and implementation changes in the User's repository or website when the request authorizes it.

## Apply the work

Infer the mode from the request and available context.

- **Automatic Mode:** the User has supplied a concrete outcome, audience or market, relevant site, and enough constraints to act. Research the smallest useful scope, make the changes directly, and validate them.
- **Strategic Mode:** intent, audience, positioning, priorities, success measures, or acceptable changes are materially unclear, or the User asks for recommendations. Research before recommending, then run the Recommendation Loop. Do not implement until the User gives Strategy Approval for the agreed strategy and change set.

When uncertain, use Strategic Mode. Do not turn mode selection into a questionnaire.

Delegate bounded work to the specialist skills when they are available:

- `fig-site-audit` for technical, crawlability, indexability, on-page, and entity baselines.
- `fig-search-research` for demand, intent, SERPs, competitors, keyword opportunities, and best-of / listicle inventory.
- `fig-answer-research` for AI visibility, citability, structured data, and answer-engine access.
- `fig-content-strategy` for prioritization, information architecture, content opportunities, briefs, owned listicles/comparisons, and outreach target lists.
- `fig-content-validation` for checking proposed or shipped changes against the evidence and acceptance criteria.

For "get recommended in ChatGPT", listicle, and best-of intents, call `fig-search-research`, then `fig-content-strategy`.

## Strategic Mode: Recommendation Loop

1. Inspect the site and gather relevant Fig MCP evidence before the first recommendation. Research external guidance only where it can change the decision.
2. Present a short bullet-point recommendation list. Include the proposed strategy, why it matters, evidence, assumptions, trade-offs, and concrete changes.
3. Let the User respond freely with corrections, preferences, or disagreement. Do not ask a batch of prerequisite questions.
4. Treat every response as a strategy update. Research further when it introduces a factual uncertainty or changes the decision boundary.
5. Present the revised recommendation list. Repeat until the User and Agent align on the strategy and the changes to make.
6. Ask for explicit Strategy Approval before writing content, changing code, or publishing. Finish with an implementation handoff: agreed strategy, prioritized changes, target pages/topics, evidence, assumptions, authorization, target metric, observation window, and validation plan.

Strategic Mode has no universal SEO/AEO goal. The aligned strategy is the goal. Do not claim alignment from silence or from the Agent's preferred plan.

## Automatic Mode

1. Establish the target site, market, language, requested outcome, and relevant constraints from the request and available files.
2. Call `balance` before paid research. Use the smallest focused set of Fig calls that can support the requested change. Do not mention remaining balance in User chat unless remaining is under $1 (or $0 / insufficient_credits). Call `balance` when the User asks or before Checkout — do not parrot Remaining $ after every paid tool.
3. Research first, then write content or make implementation changes directly in the consuming Agent's scope.
4. Preserve the site's facts, voice, product claims, and existing architecture unless the request authorizes changing them.
5. Record the inferred goal, audience, authorization, assumptions, evidence, selected change, and validation criteria before editing.
6. Re-run the relevant checks after changes. Report what changed, what Fig observed, what passed immediately, and what remains unverified or requires longitudinal measurement.

## Evidence rules

- Use Fig MCP for live keyword, SERP, backlink, domain, and supported AI-visibility data. Do not invent volumes, rankings, citations, competitors, or movement.
- Pair tool results with direct inspection of the target pages, HTTP behavior, `robots.txt`, meta/header directives, sitemaps, JSON-LD, internal links, source HTML, and rendered content where relevant. Treat `llms.txt` as optional and platform-specific: inspect it when the User names a consumer that uses it or when it is already present, but never present it as a Google Search or AI Overviews requirement.
- Separate Google Search access (`Googlebot`) from Google-Extended controls for Gemini training/grounding, OpenAI `OAI-SearchBot` from `GPTBot` and user-initiated `ChatGPT-User`, and Anthropic `Claude-SearchBot`/`Claude-User` from training crawler `ClaudeBot`. Audit `robots.txt` and CDN/WAF access separately. Crawler policy and training access are User decisions; never enable a training crawler merely to seek visibility.
- Treat volume as an input, never the objective. Weigh business fit, audience intent, authority, competition, evidence quality, and expected impact.
- Keep the scope focused. Recheck the same queries and conditions after publishing; do not imply a ranking or citation guarantee.
- If a Fig call returns authentication, insufficient credits, validation, no data, or provider failure, surface the state and follow the Fig checkout or recovery workflow. Never fill the gap with guesses.
- Null or empty keyword metrics, ideas, or coverage arrays mean the provider had no data for that query. The tool succeeded. Do not invent volumes, and do not retry the same call as if it failed.

## Completion

Automatic Mode is complete when the authorized changes are made and relevant checks are rerun. Strategic Mode is complete when the User and Agent align on a strategy and concrete changes, and the implementation handoff records unresolved assumptions.
