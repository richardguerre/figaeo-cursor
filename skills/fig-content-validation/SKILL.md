---
name: fig-content-validation
description: Validate SEO/AEO content and implementation changes against the agreed strategy, source evidence, product truth, technical requirements, and repeatable Fig checks. Use before merge or publish of marketing pages for a verify-product pass on factual and pricing claims. After a change ships, register it with fig-outcomes and score movement only after the observation window.
metadata:
  version: 5
  managed-by: fig-skill-update
---

# Fig Content Validation

Validate the delivered change, not the Agent's intention. When judging whether a shipped repair, refresh, consolidate, prune, or create matched the plan, use the Selection rubric in `fig` as the agreed action class.

## Check

- Compare the implementation with the agreed strategy, target page, primary intent, and acceptance criteria.
- Read `fig/operator-memory.json` when present and reuse stored baselines, observation windows, and the same query set. Record the requested goal, authorization, baseline, target metric, observation window, assumptions, and confounders before judging the result.
- Check HTTP status, redirect chain and final URL, response headers, source HTML, rendered HTML, sitemap and internal-link discovery, canonical, title, H1, headings, and mobile-visible content.
- Check `robots.txt`, meta/header `noindex`, `nosnippet`/snippet controls, and crawler/CDN/WAF access. Keep Googlebot, Google-Extended, OpenAI Search/training/user agents, and Anthropic search/training/user agents separate; do not change crawler policy without User approval.
- Parse JSON-LD and check syntax, visible-content agreement, required properties, and feature-specific eligibility. Validate with Google's [Rich Results Test](https://search.google.com/test/rich-results) and authorized Search Console [URL Inspection](https://support.google.com/webmasters/answer/9012289) where applicable. Never add a schema type solely because it might produce a rich result.
- Check every factual claim against the User's source material or cited primary source. Remove or flag unsupported claims. Fail fabricated statistics, quotes, testimonials, competitor claims, or "internal data" without a source.
- Run the Product truth pass below on every marketing or product page in the change.
- Run the `fig-content-craft` polish checks: answer-first opening, scannable headings, entity names consistent with the site, and no empty LLM texture or fake-human theater.
- If the brief called for a table or figure, check that tables are HTML (not images of tables), figures are authorized assets with caption/alt that restate the takeaway, and cell values match sources. Fig does not host an image CDN; missing assets are fail or needs-review, not invented charts.
- If the page claims original research, check method, date, and dataset against User material. A recap of someone else's study is not proprietary data.
- Re-run the same focused Fig queries and operations used to establish the baseline. Keep country, language, platform, and query set constant.
- When the change set included a performance repair, re-run the same URL, tool, strategy, and Lab/Field source used in the baseline. Record pass, fail, or needs-review against the stated target; report only values that tool returned.

## Product truth (verify-product)

Run this pass before merge or publish of marketing pages. Load [`assets/product-truth.md`](assets/product-truth.md) when creating or updating the User's claims file.

Read, in order, whatever exists: `fig/product-truth.md` in the User's project, the same sections in host Agent memory, then User source material in the request. The ledger is optional. A missing ledger is not a fail; every factual claim still needs a User source or a cited primary source. Fig MCP does not store the ledger.

For each factual claim (capability, pricing, comparison, statistic, quote, certification, customer, or outcome):

1. Map it to an approved fact or pricing rule in the ledger, a User source, or a reachable primary citation.
2. Remove or rewrite claims that have no source.
3. Score the Product truth criterion for every factual-claim category listed above:
   - **fail** — factual claim with no source (capability, pricing, comparison, statistic, quote, certification, customer, or outcome); claim that contradicts the ledger; claim listed as forbidden.
   - **needs-review** — wording stronger than the source supports; missing ledger when those claims are central; citation that cannot be fetched in this run.
   - **pass** — every remaining factual claim maps to ledger, User source, or primary citation, and none are forbidden.

Competitor marketing copy is not product truth. This pass is editorial accuracy, not a legal review.

When maintaining claims, copy `assets/product-truth.md` to `fig/product-truth.md` (or record the same sections in host memory) and keep approved facts, pricing rules, and forbidden claims current with User confirmation.

## Report

Return pass, fail, or needs-review for each criterion, with evidence and the smallest corrective action. Product truth **fail** blocks merge or publish until the claim is sourced, rewritten, or removed. Product truth **needs-review** must be shown to the User before publish. Separate immediate implementation validity from longitudinal outcomes, and label the latter as observations from later rechecks.

Record what Fig observed, what cannot yet be measured, the target metric, and when a later recheck is meaningful. If Search Console is connected, name the GSC property, date range, and baseline/recheck metrics from returned rows only (including low-CTR, striking-distance, cannibalization, or index fields when those rows exist). If GSC is not connected, mark Search Console measurement unavailable. Name authorized analytics/server-log/referral surfaces the same way, or mark those unavailable. Measure outcomes only after a stated observation window; do not call a passing HTML or schema check an SEO outcome. Never invent GSC numbers. How-to: https://figaeo.com/gsc.md. For post-publish channels and timed distribution rechecks, call `fig-distribute`.

After a shipped change is judged, register it with `fig-outcomes` (hypothesis, change, window, sources, before). When the window has elapsed, score through `fig-outcomes` — including the Fig-only degraded path when GSC/analytics is unavailable. Validation reports implementation pass/fail; `fig-outcomes` owns the later movement score.

Write observed vitals and window status (`open` / `due` / `closed`) into operator memory, or return a patch for `fig` to merge. Never invent movement.
