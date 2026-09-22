---
name: fig-site-audit
description: Audit a website's technical SEO, crawlability, indexability, on-page structure, internal links, structured data, crawler policy, entity consistency, and Core Web Vitals / page performance (TTFB, HTML weight, Lighthouse or PageSpeed) when improving SEO or AEO with Fig.
metadata:
  version: 5
  managed-by: fig-skill-update
---

# Fig Site Audit

Produce an evidence-backed baseline for the target site. Inspect the relevant pages directly and use Fig MCP where its live data can change the priority.

## Audit

- Read `fig/operator-memory.json` (see `fig-seo-aeo` `references/operator-memory.md`) when present. Reuse site, market, baselines, open priorities, and observation windows. Do not invent missing vitals.
- Establish the canonical host, important page types, market, language, business goal, and baseline/target metric from the request, operator memory, or available project context.
- Fetch representative pages plus `robots.txt`, `sitemap.xml`, optional `llms.txt` when present or relevant to a named platform, and JSON-LD. Treat `llms.txt` as an optional platform-specific integration, not a Google Search or AI Overviews requirement.
- Record HTTP status, redirect chain and final URL, response headers, source HTML, rendered HTML, canonical URL, title, H1, heading hierarchy, indexability, `noindex`, `nosnippet`/snippet controls, internal links, sitemap discovery, breadcrumbs, and mobile-readable content.
- Parse every JSON-LD block and compare it with visible content. Check feature-specific eligibility and required properties before recommending a schema type; valid syntax alone does not make a page eligible.
- Check organization/product naming and sameAs links for consistency across the site.
- Distinguish crawler intent: Googlebot controls Google Search and its AI features; Google-Extended controls specified Gemini training/grounding and is not a Search ranking signal; OpenAI `OAI-SearchBot` is Search, `GPTBot` is training, and `ChatGPT-User` is user-initiated; Anthropic `Claude-SearchBot` is search, `Claude-User` is user-directed retrieval, and `ClaudeBot` is training. Inspect CDN/WAF logs and rules separately from `robots.txt`.
- Report crawler policy as an observed state and a User decision. Never recommend enabling Google-Extended, GPTBot, or ClaudeBot merely to gain Search or answer visibility.
- Use `research_domain` to understand existing coverage. Use `get_backlink_overview` or bounded `get_backlinks` only when off-page evidence affects the priority.
- If Search Console is connected, pull read-only Search Analytics and any available URL Inspection, sitemap, or User Coverage export for the same host. Use returned rows for low-CTR pages, striking-distance queries, wrong-query/cannibalization, and index issues. If GSC is not connected, mark Search Console measurement unavailable. Never invent GSC metrics. How-to and the unshipped Fig-hosted MCP design: https://figaeo.com/gsc.md.

Recheck the current platform rules before changing crawler policy: [Google AI features](https://developers.google.com/search/docs/appearance/ai-features), [Google common crawlers](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers), [OpenAI crawlers](https://developers.openai.com/api/docs/bots), and [Anthropic crawlers](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler).

## Performance

Fig MCP does not return Core Web Vitals. Measure priority URLs with tools the Agent can run in this session. Priority URLs are the homepage, money pages, and winning or striking-distance pages from `research_domain` or authorized Search Console.

Measure in this order, stopping at the strongest available evidence:

1. Timed HTTP fetch for each priority URL: TTFB, document bytes, status, redirect chain, and cache headers. Record the client, timestamp, and whether the request was warm or cold.
2. Source HTML: image weight and missing width/height, render-blocking scripts and stylesheets, and HTML weight that delays first paint or LCP.
3. Lab: Lighthouse in the host (Chrome, CLI, or equivalent) or the PageSpeed Insights API when a key or quota is available. Record tool, version if known, strategy (mobile or desktop), and timestamp.
4. Field: CrUX inside a PageSpeed or CrUX response, Search Console Core Web Vitals, or host RUM the User authorized.

Label every metric **Lab** or **Field**. Report only values a named tool returned. If Field is missing, write `Field: unavailable` and keep Lab separate. Recheck Google's published thresholds before using them as comparison: [Core Web Vitals](https://web.dev/articles/vitals).

## Prioritize

Return P0/P1/P2 findings. P0 means a crawl, indexability, intent, primary-answer, or speed problem on a priority URL blocks the requested outcome. A Field CWV failure, or a Lab-plus-TTFB/weight failure when Field is unavailable, on a winning or money page is P0/P1 over net-new content when the requested outcome depends on that URL.

Each finding includes the URL, observed evidence, impact, recommended change, confidence, baseline, target metric, observation window, assumptions, and confounders. Performance findings also include Lab/Field, tool, strategy, timestamp, and vital `speed`.

When ranking what `fig-seo-aeo` should do next, apply the Selection rubric in `fig-seo-aeo`: repair, refresh, consolidate, and prune beat create when evidence is close. Label each finding with an action class from that rubric.

Do not call a page broken because a convention is absent. Tie each priority to a requested outcome or observed search/answer behavior.

## Handoff

End with the smallest useful change set and the checks that should be rerun after implementation. Performance repairs name the concrete change: images (compress, dimensions, modern formats, defer offscreen), blocking CSS/JS (defer or split; inline critical CSS only when Lab shows it helps), caching (`Cache-Control` / CDN), HTML weight (trim unused markup). Recheck the same URLs with the same tool, strategy, and Lab/Field source.

If Search Console is connected, name the GSC property, date range, and baseline metrics from returned rows; if it is not, mark Search Console measurement unavailable. If analytics, server logs, or referral data are authorized, name those surfaces; otherwise mark those outcome measurements unavailable. Separate immediate implementation validity from later ranking, traffic, conversion, or answer-surface outcomes. This specialist returns the change set; `fig-seo-aeo` owns writing. In Automatic mode the parent implements via subagents / new bots / host-equivalent sessions. In Strategic mode the change set stays a recommendation until Strategy Approval.

Pass `speed` vitals to `fig-seo-aeo` and `fig-content-strategy` so selection can consume them when present.

Merge operator memory before returning: inspection vitals (including observed Lab/Field `speed` when measured), observed baselines, open P0/P1/P2 priorities, and observation windows for recommended changes. Write `fig/operator-memory.json` when this session is not already parented by `fig-seo-aeo`; otherwise return a patch for the parent to merge. Store only observed values.
