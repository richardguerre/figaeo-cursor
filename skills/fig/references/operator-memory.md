# Fig operator memory

Lite durable state for Automatic mode and Strategic mode. The consuming Agent writes this into the **User's project**. Fig MCP remains the live evidence layer. Hosted snapshots keyed by site + Fig account are optional and not required; when both exist, the project file is the source of truth.

Canonical path: `fig/operator-memory.json` at the site-repo root. If that folder is already used for something else, keep the filename and agree a path with the User (for example `.fig/operator-memory.json`). Commit the file so later Agent turns and other specialists can read it. `fig/product-truth.md` is a separate claims ledger; do not merge those files.

Do not invent metrics. Store only:

- values Fig MCP returned on this or a prior recorded run;
- Search Console (or other authorized analytics) values the Agent actually retrieved through the User's connector or a future Fig read tool;
- facts the Agent recorded from page, HTTP, `robots.txt`, repository inspection, or a named Lab/Field performance tool (TTFB, HTML weight, Lighthouse, PageSpeed, CrUX, authorized RUM). Label `speed` metrics Lab or Field; if Field is missing write `Field: unavailable` instead of inventing a score.

Missing data stays omitted or `"measurement_unavailable"`. Null/empty Fig arrays stay null/empty. Do not fill gaps with estimates, “typical CTR,” or assumed ranks.

A **quiet** outcome is success when memory supports it: nothing in the new evidence beats the current bar (open observation windows still running, no P0, no higher-evidence change than waiting). Record what was measured and skip implementation.

This file is not a selection rubric (repair vs create) and not a GSC connector. Those stay separate. Memory only holds observed slices those workflows can read.

## JSON shape (version 1)

```json
{
  "version": 1,
  "updated_at": "2026-09-21T18:00:00.000Z",
  "site": {
    "host": "example.com",
    "canonical_origin": "https://example.com",
    "market": { "country": "US", "language": "en" }
  },
  "vitals": {
    "observed_at": "2026-09-21T18:00:00.000Z",
    "fig": {
      "queries": [
        {
          "query": "hosted mcp server",
          "tool": "get_serp",
          "observed": { "target_url": "https://example.com/mcp", "position": 8 }
        }
      ],
      "ai_visibility": []
    },
    "gsc": { "status": "measurement_unavailable" },
    "inspection": {
      "pages": [
        {
          "url": "https://example.com/mcp",
          "http_status": 200,
          "indexable": true,
          "title": "MCP"
        }
      ]
    }
  },
  "baselines": [
    {
      "id": "serp:hosted-mcp-server",
      "metric": "serp_position",
      "value": 8,
      "observed_at": "2026-09-21T18:00:00.000Z",
      "source": "fig_mcp",
      "tool": "get_serp",
      "query_or_url": "hosted mcp server"
    }
  ],
  "observation_windows": [
    {
      "id": "win:title-refresh-mcp",
      "action_id": "act:2026-09-14-title",
      "metric": "serp_position",
      "query_or_url": "hosted mcp server",
      "starts_at": "2026-09-14T00:00:00.000Z",
      "ends_at": "2026-09-28T00:00:00.000Z",
      "status": "open"
    }
  ],
  "actions": [
    {
      "id": "act:2026-09-21-quiet",
      "at": "2026-09-21T18:00:00.000Z",
      "mode": "automatic",
      "specialist": "fig",
      "summary": "Rechecked the same SERP query; position unchanged; window still open.",
      "urls": ["https://example.com/mcp"],
      "outcome": "quiet",
      "evidence_refs": ["serp:hosted-mcp-server"]
    }
  ],
  "priorities": [
    {
      "id": "pri:internal-links-docs",
      "rank": "P1",
      "status": "open",
      "summary": "Docs index has no path to /mcp in rendered HTML.",
      "url": "https://example.com/docs",
      "rationale": "Observed missing internal link during site audit."
    }
  ]
}
```

Required top-level keys: `version`, `updated_at`, `site` (with `host` and `market`), `vitals`, `baselines`, `observation_windows`, `actions`, `priorities`.

## Field rules

- `site.market` is country + language the run used for Fig calls (defaults United States / English unless the User named another market).
- `vitals` is the latest snapshot. Keep `fig`, `gsc`, and `inspection` separate. If Search Console is not connected, set `gsc.status` to `measurement_unavailable` — do not guess CTR, impressions, or striking-distance lists.
- `baselines` are named observed starting values for later comparison. Reuse the same `id` when rechecking the same metric and query/URL.
- `observation_windows` track when a later recheck is meaningful. `status` is `open`, `due`, or `closed`. Close only after a recorded recheck (or an explicit User decision to drop it).
- `actions` is last **N = 20** completed run records, newest first. Trim older rows. `outcome` is `shipped`, `planned`, `measured`, `quiet`, or `deferred`.
- `priorities` are currently open (and recently closed) P0/P1/P2 items. Merge by `id`; do not blank another specialist's open item.

## Read / write protocol

`fig` owns the file. Specialists read it and return patches; the parent merges and writes, unless the specialist is running as the only session — then it may write the same merge itself.

1. **Start of Automatic mode and Strategic mode:** read the file if present. If missing, create it after site/market are known, with empty arrays. Reuse open windows and baselines; do not spend credits re-fetching a metric whose window is still `open` unless the User asked to recheck now.
2. **During specialist work:** pass `site`, `market`, relevant `vitals`, `baselines`, `priorities`, and `observation_windows`. `fig-site-audit` updates inspection vitals, technical baselines, and audit priorities. `fig-search-research` / `fig-answer-research` append observed Fig query rows. `fig-content-strategy` merges open content priorities. `fig-content-validation` updates vitals and window `status` after a recheck.
3. **End of the run:** set `updated_at`, prepend an `actions` row, keep last 20, merge priorities, and write the file. Strategic mode writes `planned` (or updates priorities) and does not ship content. Automatic mode writes `shipped`, `quiet`, `measured`, or `deferred`.
4. **Optional MCP snapshot:** if Fig later exposes account-keyed get/put for this JSON, copy the same object after a successful file write. Never treat a hosted snapshot as a required console. Project file wins on conflict.

## Merge

- Never replace the whole document with a specialist's partial object.
- Never delete `baselines` or closed windows solely to tidy; trim only `actions` to 20.
- On conflict for the same `id`, keep the newer `observed_at` / `updated_at` value when both are observed; if one side invented a number, discard the invented side.

## Out of scope

Full Initial Commit `.seo/` script suites, rank-tracking products, and buying a daily quota. Fig does not send outreach; outreach target lists may be mentioned in an action summary but are not a mail-out log.
