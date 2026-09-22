---
name: fig-outcomes
description: Register a shipped SEO/AEO action and later score it against observed movement. Use at ship time to record hypothesis, change, window, and metric sources; use after the observation window to compare before/after from Fig rechecks and authorized GSC or analytics. Use when asked what worked, to attribute outcomes, or to update the selection rubric from this site's history. Never invent GSC, traffic, CTR, or ranking numbers.
metadata:
  version: 1
  managed-by: fig-skill-update
---

# Fig Outcomes

Keep a closed-loop ledger of shipped actions vs observed movement on this site. Immediate implementation validity stays in `fig-content-validation`. This specialist registers at ship time and scores after the observation window.

`fig-seo-aeo` delegates register and score here. Do not treat a passing HTML, schema, or crawl check as an SEO/AEO outcome.

## Record

Every outcomes record includes all of these fields. Omit none; mark a field `unavailable` when the evidence does not exist.

- `id` — stable id for this action (reuse it when scoring).
- `site` — hostname in scope.
- `hypothesis` — the expected movement and why this change should cause it.
- `change` — what shipped (URLs, summary, ship date or commit/PR).
- `window` — observation start and end (or duration) agreed at register time.
- `metrics_sources` — each source actually used: `fig_serp`, `fig_ai_visibility`, `gsc`, `analytics`, `agent_recorded`.
- `before` — baseline values with source, query set, country, language, platform, and capture time.
- `after` — same shape as `before`, captured at score time. At registration, set `after` to `unavailable`.
- `confounders` — labeled factors that could explain movement (seasonality, other deploys, algorithm volatility, sample size, mixed queries, crawl delay).
- `score` — one of `supported`, `unsupported`, `no_op`, `insufficient_evidence`, `confounded`. At registration, set `score` to `insufficient_evidence` until the window is scored.
- `rubric_note` — how this record should affect later tactic selection on this site.
- `measurement_path` — `gsc`, `analytics`, `fig_only`, or `mixed`.

Write only observed values. Null, empty, or missing tool data is not a number.

## Persist

Write records into the User's project. Preferred path: `fig/outcomes.jsonl` (one JSON object per line). Update the same `id` when scoring; do not start a second ledger for the same action.

Also patch `fig/operator-memory.json`: link `observation_windows[].action_id` and prepend an `actions` row (`shipped` at register, `measured` at score). The jsonl is the full outcomes ledger; operator memory is the last-20 run snapshot and does not replace the score fields. Fig does not require a dashboard. Do not keep the only copy in chat.

## Register

Register after a change has shipped (Automatic mode landed work, or `fig-content-validation` has judged the implementation). Strategic mode does not register until something actually shipped.

1. Copy hypothesis, target metric, window, and confounders from the brief or validation record.
2. Capture `before` with the same Fig calls that established the baseline (`get_serp` and/or `research_ai_visibility` on the same queries, country, language, and platform). If GSC or analytics is already authorized in this agent, record those returned slices too. If those connectors are absent, set `measurement_path` to `fig_only` and list only Fig sources.
3. Persist the record with `score` `insufficient_evidence` and `after` `unavailable` until the window is scored.
4. Tell the User the id, hypothesized metric, window, sources, and that ranking lift is not guaranteed.

Do not register a recommendation that was not shipped.

## Score

Score only after the stated window has elapsed. Recheck the same queries, country, language, platform, and operations used in `before`.

1. Load the record by `id`. If the window has not ended, keep `score` `insufficient_evidence` and `after` `unavailable`, and stop.
2. Fill `after` from returned evidence only.
3. Prefer GSC/analytics for CTR, clicks, impressions, average position over the window, and index/coverage-style measures when those tools actually returned values. Prefer Fig snapshots for SERP position on the sampled query set and supported AI mention/citation fields.
4. Label confounders before choosing `score`. If confounders dominate, use `confounded` and do not upweight or downweight the tactic.
5. Choose `score`:
   - `supported` — hypothesized metric moved in the hypothesized direction on evidence from an allowed source.
   - `unsupported` — hypothesized metric moved against the hypothesis, with evidence.
   - `no_op` — hypothesized metric did not materially change.
   - `insufficient_evidence` — window unmet, source missing, or sample too thin.
   - `confounded` — other changes or volatility can explain the delta.
6. `rubric_note`: on `supported`, candidate to upweight this tactic on this site; on repeated `unsupported` or `no_op` that is not `confounded`, candidate to downweight. Selection still belongs to `fig-seo-aeo` / `fig-content-strategy`. A quiet "nothing beat the bar" score is a valid result.

Report the score, sources, before/after, confounders, and rubric note. Separate Fig snapshots from GSC/analytics. Do not claim ranking, traffic, or citation lift beyond the measured fields.

## Degraded path (no GSC / analytics)

Work without GSC. Set `measurement_path` to `fig_only` and score only Fig-observable fields.

Explicit limits:

- Fig SERP snapshots are not Search Console impressions, clicks, CTR, or window-average position.
- One `get_serp` position is a sampled snapshot; it can move without the change causing it.
- `research_ai_visibility` is not traffic, CTR, or citation share. ChatGPT mention data is United States and English only; Claude, Gemini, and Perplexity mention scores are not supplied.
- Without GSC or analytics, do not score CTR, clicks, impressions, index coverage, or query cannibalization. Mark those metrics `unavailable`. Mark Search Console measurement unavailable.
- Fig-only scores cannot underwrite ranking lift. At most they compare the same query set before and after.
- Do not invent GSC or analytics numbers to fill the gap. If a Fig call returns no data, record that, and use `insufficient_evidence` when the hypothesized metric cannot be observed.

## Evidence rules

- Use Fig MCP for live SERP and supported AI-visibility rechecks. Use GSC or analytics only when the User's agent already has a connector or Fig MCP later exposes those reads; both paths are valid and neither is required for a Fig-only record.
- Do not invent volumes, rankings, CTR, traffic, citations, or movement.
- Recheck conditions stay constant with the baseline.
- A score is an observation plus a rubric note, not a guarantee.
