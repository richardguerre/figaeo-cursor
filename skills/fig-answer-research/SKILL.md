---
name: fig-answer-research
description: Research answer-engine visibility and improve AI reachability, citability, structured data, entity consistency, and platform-specific answer access with Fig. Recheck whether the brand is named on the same commercial prompts after listicle or citability work. Use llms.txt only when a named consumer or existing integration makes it relevant.
metadata:
  version: 3
  managed-by: fig-skill-update
---

# Fig Answer Research

Audit the pages that should be extracted, cited, or named by answer engines. Separate observed Fig data from recommendations based on page inspection.

## Research

- Use `research_ai_visibility` on a small set of priority queries. Fig supports observed Google and ChatGPT visibility/citation data; `competitors` is ChatGPT-only. ChatGPT mention data is United States and English only.
- When the User wants to be named on commercial `best` / `top` / `vs` / `alternative` prompts, include those queries in the baseline and recheck the same arguments after owned-page or citability changes. Listicles help extraction and often appear in citation mixes; they are not a ChatGPT switch.
- Establish a baseline, target metric, business/conversion goal, observation window, assumptions, and confounders before interpreting visibility. Preserve the same query, country, language, platform, and format for rechecks.
- Fetch the page, `robots.txt`, relevant headers/meta directives, sitemap/internal-link path, source HTML, rendered HTML, and JSON-LD. Inspect `llms.txt` only when it is already present or a named platform documents using it; Google says it is not required for Search or AI Overviews.
- Prioritize crawl and CDN/WAF access, indexability, visible and attributable answers, first-hand/original evidence, useful tables or definitions, visible updated dates, structured data that matches the page, and consistent organization/product entities.
- Distinguish Googlebot from Google-Extended, OpenAI `OAI-SearchBot` from `GPTBot` and `ChatGPT-User`, and Anthropic `Claude-SearchBot`/`Claude-User` from `ClaudeBot`. Report each policy separately and leave training crawler choices to the User.

Recheck the current platform rules before making an access recommendation: [Google AI features](https://developers.google.com/search/docs/appearance/ai-features), [Google's generative AI guide](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide), [Google common crawlers](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers), [OpenAI crawlers](https://developers.openai.com/api/docs/bots), and [Anthropic crawlers](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler).

Claude, Gemini, and Perplexity mention scores are not supplied by Fig. Say when a surface is unmeasured; never invent a score or citation.

## Structured data

- Use JSON-LD when practical, but recommend only a type and properties the page genuinely qualifies for under Google's feature-specific guidelines. Structured data must describe visible content and must not be used to add hidden, unsupported, or misleading claims.
- Validate JSON-LD syntax, then use Google's [Rich Results Test](https://search.google.com/test/rich-results) and authorized Search Console [URL Inspection](https://support.google.com/webmasters/answer/9012289) to check rendered eligibility and indexing. A valid test does not guarantee a rich result, ranking, or AI citation.
- Treat schema as ordinary SEO support, not special AEO markup. Google does not require special schema for AI Overviews or AI Mode.

## Output

Return P0/P1/P2 findings with URL, observed evidence, proposed copy or implementation change, confidence, baseline, target metric, observation window, assumptions, confounders, and recheck query. Keep first-hand evidence and the business/conversion goal explicit. Do not turn query variants into a mass-production queue; one primary intent per page is a useful heuristic, not an absolute law.

Re-run the same `research_ai_visibility` arguments after publishing. Report immediate implementation validity separately from longitudinal Search Console, analytics, referral, or answer-surface outcomes. Do not claim improved visibility without returned evidence.
