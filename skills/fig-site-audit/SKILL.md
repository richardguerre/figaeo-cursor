---
name: fig-site-audit
description: Audit a website's technical SEO, crawlability, indexability, on-page structure, internal links, structured data, crawler policy, and entity consistency when improving SEO or AEO with Fig.
metadata:
  version: 2
  managed-by: fig-skill-update
---

# Fig Site Audit

Produce an evidence-backed baseline for the target site. Inspect the relevant pages directly and use Fig MCP where its live data can change the priority.

## Audit

- Establish the canonical host, important page types, market, language, business goal, and baseline/target metric from the request or available project context.
- Fetch representative pages plus `robots.txt`, `sitemap.xml`, optional `llms.txt` when present or relevant to a named platform, and JSON-LD. Treat `llms.txt` as an optional platform-specific integration, not a Google Search or AI Overviews requirement.
- Record HTTP status, redirect chain and final URL, response headers, source HTML, rendered HTML, canonical URL, title, H1, heading hierarchy, indexability, `noindex`, `nosnippet`/snippet controls, internal links, sitemap discovery, breadcrumbs, and mobile-readable content.
- Parse every JSON-LD block and compare it with visible content. Check feature-specific eligibility and required properties before recommending a schema type; valid syntax alone does not make a page eligible.
- Check organization/product naming and sameAs links for consistency across the site.
- Distinguish crawler intent: Googlebot controls Google Search and its AI features; Google-Extended controls specified Gemini training/grounding and is not a Search ranking signal; OpenAI `OAI-SearchBot` is Search, `GPTBot` is training, and `ChatGPT-User` is user-initiated; Anthropic `Claude-SearchBot` is search, `Claude-User` is user-directed retrieval, and `ClaudeBot` is training. Inspect CDN/WAF logs and rules separately from `robots.txt`.
- Report crawler policy as an observed state and a User decision. Never recommend enabling Google-Extended, GPTBot, or ClaudeBot merely to gain Search or answer visibility.
- Use `research_domain` to understand existing coverage. Use `get_backlink_overview` or bounded `get_backlinks` only when off-page evidence affects the priority.

Recheck the current platform rules before changing crawler policy: [Google AI features](https://developers.google.com/search/docs/appearance/ai-features), [Google common crawlers](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers), [OpenAI crawlers](https://developers.openai.com/api/docs/bots), and [Anthropic crawlers](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler).

## Prioritize

Return P0/P1/P2 findings. P0 means a crawl, indexability, intent, or primary-answer problem blocks the requested outcome. Each finding includes the URL, observed evidence, impact, recommended change, confidence, baseline, target metric, observation window, assumptions, and confounders.

Do not call a page broken because a convention is absent. Tie each priority to a requested outcome or observed search/answer behavior.

## Handoff

End with the smallest useful change set and the checks that should be rerun after implementation. If Search Console, analytics, server logs, or referral data are authorized, name the exact measurement surface; otherwise mark outcome measurement unavailable. Separate immediate implementation validity from later ranking, traffic, conversion, or answer-surface outcomes. Do not edit the site from this specialist skill unless the consuming Agent explicitly owns the implementation.
