---
name: fig-distribute
description: After a URL ships, produce a post-publish distribution checklist — social, newsletter, communities, IndexNow/Bing if connected, internal promo — plus timed measurement rechecks. Fig does not send outreach email or post on the User's behalf unless they explicitly ask their own agent to send.
metadata:
  version: 1
  managed-by: fig-skill-update
---

# Fig Distribute

Use this specialist **after a URL is live** (new page, refresh, or canonical change that shipped). It is a distribution and measurement checklist, not a content brief and not an outreach sender.

Fig does **not** send outreach email, post to social, blast a newsletter, or submit to directories. Fig does **not** negotiate paid placements or buy links. If the User explicitly asks **their** agent to post or send, that action is the User's agent — still not Fig, and still not paid-link buying.

For off-page target lists (directories, digital PR, unlinked mentions), use `fig-offpage`. For implementation validity of the page itself, use `fig-content-validation`.

## Preconditions

Confirm the URL is the final public URL: HTTP success, intended canonical, not blocked by `robots.txt` / `noindex`, and discoverable from sitemap or internal links. If those fail, stop and send the User back to `fig-site-audit` / `fig-content-validation`. Do not "distribute" a draft, preview, or blocked URL.

Record baseline, target metric, observation window, assumptions, confounders, and the authorized measurement surface **before** claiming movement. Score with the Selection rubric in `fig`. When Search Console is not connected, mark Search Console measurement unavailable.

## Channel checklist

Produce a short, prioritized checklist. Skip channels the User does not have. For each item: owner (User vs their agent), asset needed, and a success check.

- **Index / crawl** — sitemap ping if the site owns that process; IndexNow or Bing Webmaster URL submit **only if already connected** in the User's stack; Google Search Console URL Inspection **only if the User brought a GSC connector or Fig GSC tools exist**. Fig MCP does not submit IndexNow. Do not invent a Fig ping tool.
- **Internal promo** — relevant internal links, nav, docs, changelog, or in-app notice on the brand site. Implement those through `fig` when Automatic mode already authorizes on-site edits.
- **Owned social** — the User's existing profiles. Draft copy if asked; do not post unless the User explicitly asks their agent to post.
- **Newsletter / email to existing list** — draft a blurb if asked. Fig does not send to the list.
- **Communities** — only places the User already participates in and whose rules allow the post. No drive-by spam. Fig does not post.
- **Partners / off-page** — if earned mentions are in scope, hand the target list to `fig-offpage`. Do not mix "please share our URL" cold email into this checklist as if Fig will send it.

Mark each channel done, skipped (with reason), or blocked on User input.

## Timed rechecks

Separate immediate distribution actions from later SEO/AEO outcomes.

1. **Same day** — URL live, canonical, sitemap, IndexNow/Bing/GSC submit if connected, internal links shipped.
2. **After crawl time** (state the window; do not guarantee indexing) — Search Console or host index status if authorized; otherwise say measurement is unavailable.
3. **After the agreed observation window** — same `get_serp` / `research_ai_visibility` / `research_domain` queries used at baseline. Tie every reported ranking, citation, or traffic change to returned evidence. Do not call a successful post an SEO outcome.

If Search Console, analytics, server logs, or referral data are authorized, name the exact surface. Otherwise mark outcome measurement unavailable.

In Strategic mode, present the checklist and wait until the User agrees the plan before on-site promo edits. In Automatic mode, land the checklist and any authorized on-site promo through `fig`; still do not send outreach.
