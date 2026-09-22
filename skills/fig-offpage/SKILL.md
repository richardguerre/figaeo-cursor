---
name: fig-offpage
description: Build prioritized off-page briefs for directories, digital PR angles, unlinked mention recovery, and outreach target lists. Use after search or content strategy when the next work is off-site. Fig does not send outreach email, buy links, or negotiate paid placements.
metadata:
  version: 1
  managed-by: fig-skill-update
---

# Fig Off-page

Turn evidence into **briefs and target lists only**. Fig does **not** send outreach email, cold messages, or follow-ups. Fig does **not** negotiate paid placements or buy links. If the User explicitly asks **their** agent to send a message, that send is the User's agent acting outside Fig — still do not impersonate Fig as the sender, and still do not buy links.

Use this specialist for general off-page work (directories, digital PR, unlinked mentions, citations). Keep commercial **listicle** outreach inventories in `fig-content-strategy` / `fig-search-research` unless the User asks to expand them here.

## Non-goals

- Sending email or any outreach from Fig
- Link buying, paid guest-post negotiation, or marketplace link orders
- Scraping personal inboxes or inventing contact details
- Treating `get_backlinks` as a contact-discovery tool

## Prioritize

Rank targets by business fit, audience overlap, observed authority or SERP presence, evidence quality, implementation cost to the User, and measurement feasibility. State the trade-off behind the order. Score with the Selection rubric in `fig-seo-aeo`. When Search Console is not connected, mark Search Console measurement unavailable.

Typical lanes (pick what the evidence supports; do not run all of them):

1. **Directories and citations** — category, local, or industry listings that already rank or that competitors occupy.
2. **Digital PR angles** — newsworthy facts, data, product proof, or first-hand assets that could earn a mention. Mark missing proof as a User input task.
3. **Unlinked mention recovery** — pages that name the brand without a link. Use bounded `get_backlinks` / `get_backlink_overview` plus page inspection; do not invent mentions.
4. **Other earned placements** — resources, roundups, or partner pages where a genuine editorial fit exists.

Paid or affiliate placements on third-party pages are outside Fig. Follow host and Google policies.

## Brief

For each approved target, provide:

- **URL / target** — destination page or listing, plus the owned URL that should be cited;
- **angle** — why this target should care, in one sentence, tied to their page not a generic pitch;
- **evidence** — Fig tool results, live page inspection, SERP/AI visibility, or User-supplied proof. Never invent volumes, referring-domain counts, journalists, or "they mentioned us";
- **assets needed** — screenshots, data, quotes, bios, product facts, or canonical URLs the User must supply;
- **success metric** — what "won" looks like (indexed listing, followed link, corrected NAP, named citation) plus observation window and authorized measurement surface (Search Console, analytics, referral logs, or Fig rechecks). If none is authorized, mark outcome measurement unavailable.

Also record assumptions, confounders, and whether the brand is already listed or mentioned.

In Strategic mode, ask which targets to brief (Strategy Approval) and wait. In Automatic mode, produce the prioritized brief as landed work (a file or chat artifact the User can review) through `fig-seo-aeo`, and **do not send**.

## Recheck

After the User or their agent acts, recheck the same URLs and queries. Report observed listings, links, or mentions only from returned evidence. Hand post-publish channel work to `fig-distribute`.
