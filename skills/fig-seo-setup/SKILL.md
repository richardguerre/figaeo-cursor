---
name: fig-seo-setup
description: Print the human-only SEO decision queue (needs-you) or the SEO connections setup ladder (repo/CMS, GSC, analytics, IndexNow, Bing). Use when the User asks what they need to do, what is connected, how to connect Search Console, or when work is blocked on a human approval. Distinct from Fig Checkout and Setup Orient.
metadata:
  version: 1
  managed-by: fig-skill-update
---

# Fig SEO Setup

Two invocations: **needs-you** and the **setup ladder**. Both are SEO-site HITL. They are not Fig Checkout, remaining balance, or Setup Orient.

Never auto-connect accounts. The human approves every connector.

## When `fig-seo-aeo` surfaces this

Call this specialist and stop the parent workflow for that pass when:

- The User asks needs-you, what you need from them, or what is blocking.
- The User asks setup, what is connected, or how to connect GSC, analytics, CMS, IndexNow, Bing, or repo access.
- The next useful step is a decision only the human can make (connector OAuth, domain verify, Strategy Approval, crawler training, claims the files do not contain).

Do not run this instead of Setup Orient on first-run after Checkout or a funded Fig balance. Orient is Fig product (MCP research + Automatic mode vs Strategic mode). This skill is SEO connections for the website.

If Fig MCP is missing or remaining balance cannot cover the next Fig lookup, follow install/Checkout, then Orient — do not list Checkout as a GSC-style connector on this ladder.

## Needs-you

Build a queue of items the Agent cannot complete. Print it and stop. Do not research, write content, or open PRs in this pass.

Include a line only when it is actually open. Typical items, in this order:

1. Fig product (label it as Fig, not Search Console): approve MCP sign-in or Checkout.
2. Grant write access to the repo, CMS, or host so Automatic mode can ship.
3. Connect Google Search Console and pick the property.
4. Connect analytics (GA4 or equivalent).
5. Verify the domain for GSC or Bing if that step is still required.
6. Place or share an IndexNow key on the origin.
7. Record Strategy Approval when Strategic mode is waiting.
8. Decide crawler training access (`GPTBot`, `ClaudeBot`, `Google-Extended`) separately from Search crawlers.
9. Supply product claims, legal, or brand facts that are not in the files.

Format in User chat:

Needs-you (stop here):
1. [action] — why only the human can do it — what it unblocks

If nothing is open: `Nothing needs you. Continue in fig-seo-aeo.` Then return to the parent.

## Setup ladder

Inspect MCP servers, project files, env, authorized exports, and the live site. Classify each rung **connected** or **missing**. Print connected rungs first, then missing rungs in this unlock order (do not shuffle):

1. **Write surface (repo / CMS / hosting)** — unlocks implementation. User-brought: grant the Agent repo or CMS access. Fig does not host CMS OAuth.
2. **Google Search Console** — unlocks queries, pages, CTR vs position, index/coverage, striking distance. User-brought: connect GSC (or Google) in the Agent with read access to the property (host Google/GSC MCP, read-only Search Console API, or a User export). Fig Google sign-in is email only and is not GSC. Fig-hosted GSC OAuth and MCP reads are specified at https://figaeo.com/gsc.md and are not shipped. Checkout and Fig MCP OAuth do not imply GSC. If GSC is not connected, mark Search Console measurement unavailable. Never invent clicks, impressions, CTR, position, coverage counts, or other Search evidence.
3. **Analytics (GA4 or equivalent)** — unlocks on-site behavior, conversions, and ChatGPT `utm_source=chatgpt.com` referrals. User-brought. Fig does not host analytics.
4. **IndexNow** — unlocks post-publish pings. User places the key; the Agent may POST after approval.
5. **Bing Webmaster Tools** — unlocks Bing index data. User-brought. After GSC, not instead of it.
6. **Local / extra trackers the User already pays for** (for example Google Business Profile) — only if the goal needs them. Vanity connectors stay last.

For each missing rung, state the unlock, how to connect (user-brought vs Fig-hosted), and that the human must approve. Do not auto-connect.

Checkout, remaining Fig balance, and Setup Orient are not rungs on this ladder.

## Handoff

After needs-you, stop. After the ladder, return to `fig-seo-aeo`. Missing GSC does not block Fig keyword, SERP, or AI-visibility research; it blocks first-party Search measurement. Other specialists should keep naming the authorized measurement surface, or mark outcome measurement unavailable.
