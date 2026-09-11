---
name: fig-content-validation
description: Validate SEO/AEO content and implementation changes against the agreed strategy, source evidence, technical requirements, and repeatable Fig checks.
metadata:
  version: 2
  managed-by: fig-skill-update
---

# Fig Content Validation

Validate the delivered change, not the Agent's intention.

## Check

- Compare the implementation with the agreed strategy, target page, primary intent, and acceptance criteria.
- Record the requested goal, authorization, baseline, target metric, observation window, assumptions, and confounders before judging the result.
- Check HTTP status, redirect chain and final URL, response headers, source HTML, rendered HTML, sitemap and internal-link discovery, canonical, title, H1, headings, and mobile-visible content.
- Check `robots.txt`, meta/header `noindex`, `nosnippet`/snippet controls, and crawler/CDN/WAF access. Keep Googlebot, Google-Extended, OpenAI Search/training/user agents, and Anthropic search/training/user agents separate; do not change crawler policy without User approval.
- Parse JSON-LD and check syntax, visible-content agreement, required properties, and feature-specific eligibility. Validate with Google's [Rich Results Test](https://search.google.com/test/rich-results) and authorized Search Console [URL Inspection](https://support.google.com/webmasters/answer/9012289) where applicable. Never add a schema type solely because it might produce a rich result.
- Check every factual claim against the User's source material or cited primary source. Remove or flag unsupported claims.
- Re-run the same focused Fig queries and operations used to establish the baseline. Keep country, language, platform, and query set constant.

## Report

Return pass, fail, or needs-review for each criterion, with evidence and the smallest corrective action. Separate immediate implementation validity from longitudinal outcomes: a valid change does not guarantee rankings, mentions, citations, traffic, or conversions.

Record what Fig observed, what cannot yet be measured, the authorized Search Console/analytics/server-log/referral surface if any, the target metric, and when a later recheck is meaningful. Measure outcomes only after a stated observation window; do not call a passing HTML or schema check an SEO outcome.
