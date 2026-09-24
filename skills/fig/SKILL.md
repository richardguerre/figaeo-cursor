---
name: fig
description: Improve a website's SEO and AEO (search and AI-answer visibility) with Fig. Use for broad requests like site audits, SEO/AEO strategy, content opportunities, implementing changes, validating shipped work, or the first run after Fig Checkout. Routes each job to the fig-* specialist skills (site audit, search and answer research, content strategy and craft, programmatic SEO, free tools, off-page, distribution, outcomes, setup) and works in Automatic mode (research and implement) or Strategic mode (agree the plan first).
metadata:
  version: 15
  managed-by: fig-skill-update
---

# Fig SEO/AEO

Use Fig as the evidence layer and make the consuming Agent useful to the User. Fig is read-only: the consuming Agent may write content and implementation changes in the User's repository or website when the request authorizes it.

Always say **Automatic mode** and **Strategic mode**.

Never say Orient, Setup Orient, Strategy Approval, or router to the User. Call the first-run map the intro. Call the User's yes on goals, audience, priorities, topics, and constraints the agreed plan. Name the work you are doing; `fig` routes each job to the specialist skill that fits.

## Intro

On first-run after Checkout or a funded remaining balance, and the User has not chosen a mode, post this intro in User chat verbatim. Skip once a mode is already in use. Do not paraphrase.

Fig is ready. Quick map:
1. **I** use Fig for live SEO/AEO research (search demand, SERPs, AI visibility, site checks).
2. **You** approve spending; in Automatic mode you mainly review the work I open (content, PRs).
3. I’ll use **Automatic mode** by default — after your goal, I research and implement; you review. Say **Strategic mode** if you want to agree on the plan first, before any changes.
4. If you’re not sure, just ask.

Next: your site and goal, e.g. `Improve SEO and AEO for example.com`. If you’re not sure what to aim for, say so and I’ll suggest a starting path.

If the User does not choose, use Automatic mode.

## Apply the work

On first-run, post the intro before applying a mode. Infer the mode from later requests and available context. Do not quiz the User about which mode they want.

- **Automatic mode:** the User has given a site and a goal, or a concrete improvement request. Research the smallest useful scope, implement the changes (content, code, PRs), validate them, and hand the User the landed work to review. The User's job is review, not choosing the next research step.
- **Strategic mode:** the User asks for recommendations, strategy, or to plan first, or implementation would freeze an unresolved positioning, priority, claim, crawler, or success-measure choice. Research, run the Recommendation Loop, and stop at the approved plan. Write no content, change no code, and open no PRs until the User agrees the plan, and do not start implementation in this mode after approval.

First-run posts the intro; Automatic mode is the default if the User does not choose. Prefer Automatic mode when a site and goal are present. Use Strategic mode when the User asks to plan first or when a strategy choice is still open. Do not turn later mode selection into a questionnaire.

Delegate bounded work to the specialist skills when they are available:

- `fig-seo-setup` for needs-you (print the human-only queue and stop) and the SEO connections setup ladder (value-ordered GSC, analytics, CMS, IndexNow, Bing, repo). Not Fig Checkout or the intro.
- `fig-site-audit` for technical, crawlability, indexability, on-page, entity, and Core Web Vitals / performance baselines.
- `fig-search-research` for demand, intent, SERPs, competitors, keyword opportunities, and best-of / listicle inventory.
- `fig-answer-research` for AI visibility, citability, structured data, and answer-engine access.
- `fig-content-strategy` for prioritization, information architecture, content opportunities, briefs, content census (prune, merge, refresh, decay), owned listicles/comparisons, and outreach target lists.
- `fig-content-craft` for polish (scannability, answer-first, entity clarity), AI-writing tells, visuals/tables, proprietary-data page patterns, and research-brief recipes that feed strategy. Use after a brief exists, or when the request is to write or rewrite rather than choose what to publish.
- `fig-programmatic-seo` for gated template sets (compare, alternatives, use-case / for-persona, other justified grids) after SERP and business evidence pass the door.
- `fig-free-tool` for gated free-tool lead magnets (calculators, checkers, generators) only when SERP and business evidence favor a tool over a guide. Fig does not host the tool.
- `fig-offpage` for directories, digital PR angles, unlinked mention recovery, and other off-page briefs (target lists only).
- `fig-distribute` after a URL ships: channel checklist, IndexNow/Bing/GSC submit if connected, internal promo, timed rechecks.
- `fig-content-validation` for checking proposed or shipped changes against the evidence, craft checks, and acceptance criteria, including the Product truth (verify-product) pass before merge or publish of marketing pages.
- `fig-outcomes` for registering a shipped action and scoring it after the observation window.

Specialists return evidence and candidate changes. This skill scores them with the Selection rubric, then Automatic mode implements one primary action and Strategic mode ranks options before the User agrees the plan.

Fig does not send outreach email, post on the User's behalf, or negotiate paid placements. `fig-offpage` and `fig-distribute` stop at briefs and checklists.

For content census, prune, merge, refresh, decay, cannibalization, orphan, or thin-overlap intents, call `fig-content-strategy`. For "get recommended in ChatGPT", listicle, and best-of intents, call `fig-search-research`, then `fig-content-strategy`. Pull `fig-content-craft` when implementing the owned page. Strategy decides what to ship and why; craft decides how the page is written, visualized, and evidenced. For programmatic, pSEO, `/compare/`, `/alternatives/`, `/for/`, or template-grid intents, call `fig-search-research`, then `fig-programmatic-seo`. For calculator, checker, generator, and free-tool intents, call `fig-search-research`, then `fig-free-tool` only when SERP and business evidence favor a tool over a guide. For needs-you or SEO connections (GSC, analytics, CMS), call `fig-seo-setup`; that is not Fig Checkout or the intro. For general off-page work, call `fig-offpage`. After a URL is live, call `fig-distribute`, then `fig-content-validation`. Register and score closed-loop results with `fig-outcomes`; do not fold that ledger into this router.

## Selection rubric

Score every candidate before Automatic mode implements or Strategic mode asks the User to agree the plan. Repair, refresh, consolidate, and prune beat create when evidence is close. Create when SERP and business evidence clearly warrant a new URL.

### Action classes

- **Repair** — restore a working asset: broken or missing internal links, crawl/index blocks, canonical conflicts, schema that disagrees with visible content, or a measured performance regression on a priority URL.
- **Refresh** — update an existing URL that still matches intent: title/snippet, decayed body, dates, proof, or answer-first opening.
- **Consolidate** — merge near-duplicate URLs onto one canonical target with redirects.
- **Prune** — noindex, redirect, or remove thin, obsolete, or doorway-like URLs that dilute the useful page.
- **Create** — ship a net-new URL only when no existing page can serve a distinct intent, format, or audience without stuffing.

### Vitals

Score which vitals the action moves. Use observed values only.

- **Relevance** — query/intent match, SERP format fit, and whether an existing URL already covers the need.
- **CTR** — title, H1, and snippet vs the SERP. When Search Console is available, CTR vs expected at the page's average position.
- **Link health** — internal inbound links, orphan risk, and crawl path from hubs/sitemaps.
- **Speed** — how quickly a change can ship and be recrawled, plus Lab/Field page performance when present. Small metadata or link edits outrank net-new drafts when impact is similar. When `fig-site-audit` returns a `speed` vital, consume it in selection: repairing a measured regression on a winning or priority URL beats creating a new page when evidence is close. This skill does not run CWV tooling; `fig-site-audit` measures it.

Fig does not send outreach. Off-page work stops at briefs and target lists unless the User explicitly asks their agent to send.

### Close-call rule

When two candidates are within similar confidence and expected impact, pick the existing-URL class (repair, refresh, consolidate, or prune) over create. Create wins only with a clear gap: the winning SERP format is absent, the existing URL's intent is different, and business/conversion fit is explicit.

### Evidence hooks

**Operator memory.** Read and write `fig/operator-memory.json` as specified in Operator memory. Use stored vitals, last actions, and open priorities in the vote. A quiet outcome is valid when nothing beats the bar.

**Search Console (optional).** Prefer a GSC UI CSV/Sheets/Excel export first, then an LLM-oriented GSC CLI (npm) with `webmasters.readonly` after one OAuth/ADC login. How-to: https://figaeo.com/gsc.md. Fig Google sign-in is email only and is not GSC. GA4 is not GSC. When GSC is connected, fold returned Search Analytics into the vote: low-CTR pages, striking-distance queries, and wrong-query/cannibalization. When GSC is not connected, mark Search Console measurement unavailable and score from Fig MCP plus page inspection. Never invent clicks, impressions, CTR, position, or coverage counts.

### Vote

For each candidate record: action class, target URL(s), vitals moved, evidence, implementation cost, confidence, and the next-best alternative it beats or loses to.

- **Automatic mode:** pick **one primary action**. State the rationale versus the next-best alternatives, then implement that action. Companion edits belong in the same chunk only when they are required for the primary action (for example a redirect that belongs with a consolidate). Census prune or unpublish still waits until the User agrees the plan.
- **Strategic mode:** present **ranked options** from this same vote in the recommendation list **before** the User agrees the plan. The User chooses; silence is not a vote for the Agent's favorite.

### Examples

- **Title/snippet refresh.** A guide sits around position 8 with impressions and a CTR below expected for that position (GSC when available, otherwise a title that misses the SERP wording). Primary action: refresh title and meta on the existing URL. Alternative declined: a new article on the same query.
- **Internal-link repair.** A striking-distance page has a sitemap entry but few contextual inlinks from hubs. Primary action: repair internal links. Alternative declined: rewrite or replace the page.
- **Decay refresh.** The URL still matches intent; competing SERP results show newer dates and missing proof the site can add. Primary action: refresh the body on the existing URL. Alternative declined: a net-new "updated" sibling URL.
- **Consolidate near-dupes.** Two guides split impressions on one query. Primary action: consolidate onto the stronger URL and redirect the other. Alternative declined: keep both and add a third variant.
- **New page.** `get_serp` shows a comparison or listicle format; the site has no URL with that intent; business fit is a category the product actually sells. Primary action: create one page. Alternative declined: stuffing the homepage or a mismatched guide.

## Operator memory

Keep lite operator memory in the User's project so later turns are not cold. Canonical file: `fig/operator-memory.json` (or a User-agreed path with the same JSON). Load `references/operator-memory.md` for the version 1 shape.

- Read the file at the **start** of every Automatic mode and Strategic mode run, before paid research.
- Write it at the **end** of the run (parent session merges specialist patches).
- Capture at least: site, market, vitals snapshot, last 20 actions, open priorities, observation windows, baselines.
- Store only observed Fig MCP, authorized Search Console / analytics, or Agent-recorded inspection values. Never invent metrics. Observed Lab/Field `speed` values belong in vitals when `fig-site-audit` measured them.
- A **quiet** outcome is valid when memory supports it: nothing beats the current bar; report what you measured and skip implementation.
- Pass site, market, vitals, baselines, priorities, and open windows into specialists. `fig-site-audit` is required to read/write those slices on audit handoff. Project files are enough; optional hosted snapshots keyed by site + account are not required.

## Needs-you and SEO connections

The intro is Fig product (MCP research + modes) after Checkout or a funded balance. Do not treat missing GSC as an intro failure.

Call `fig-seo-setup` and do not continue the SEO pass when:

- The User asks needs-you, what you need from them, or what is blocking.
- The User asks setup, what is connected, or how to connect Search Console or other SEO integrations.
- The next useful step is a human-only approval (connector, domain verify, agreeing the plan, crawler training, claims not in the files).

Never auto-connect GSC, analytics, CMS, IndexNow, Bing, or repo access. Missing GSC does not block Fig research; mark first-party Search measurement unavailable until a user-brought GSC connection exists.

## Automatic mode

1. Establish the target site, market, language, requested outcome, and relevant constraints from the request, operator memory, and available files. Read `fig/product-truth.md` or the same sections in host Agent memory when present.
2. Call `balance` before paid research. Use the smallest focused set of Fig calls that can support the requested change. Do not mention remaining balance in User chat unless remaining is under $1 (or $0 / insufficient_credits). Call `balance` when the User asks or before Checkout — do not parrot Remaining $ after every paid tool. Skip re-fetching a metric whose observation window is still `open` unless the User asked to recheck now.
3. Research first. Score candidates with the Selection rubric. Pick one primary action. Record the inferred goal, audience, authorization, assumptions, evidence, selected change, rationale versus alternatives, and validation criteria. If open windows and current vitals show no change that beats the bar, record a `quiet` action, write memory, and hand the User the measurement — do not invent work.
4. Implement through the Implementation playbook below. Preserve the site's facts, voice, product claims, and existing architecture unless the request authorizes changing them.
5. Re-run the relevant checks after changes (`fig-content-validation` when shipped work needs an evidence-backed pass/fail). For marketing or product pages, complete the Product truth (verify-product) pass before merge or publish. A Product truth **fail** means rewrite or remove the claim first; **needs-review** is shown to the User before publish. When a public URL shipped, run `fig-distribute` for the post-publish checklist and timed rechecks.
6. Register the shipped action with `fig-outcomes` (hypothesis, change, window, metric sources, before). Score later through `fig-outcomes` after the window; Fig-only SERP/AI rechecks are valid when GSC is unavailable.
7. Merge operator memory (vitals, baselines, priorities, windows, last 20 actions) and write `fig/operator-memory.json`. Hand the User the landed work: diffs, PRs, URLs, what Fig observed, why this primary action beat the alternatives, what passed immediately, the outcomes id and window, and what remains unverified or needs longitudinal measurement. If Search Console is connected, name the GSC property, date range, and baseline metrics from returned rows; if it is not, mark Search Console measurement unavailable. Invite review of what shipped, not a menu of unstarted options. For a quiet run, invite review of the measurement, not a menu of unstarted options. Do not send outreach.

## Automatic mode: Implementation playbook

Keep research, orchestration, evidence, and review in this parent session. Push implementation into isolated workers so this context is not compacted into a weaker review state.

For each bounded implementation chunk (a page, a PR, a schema change, an IA edit):

1. Spawn a host subagent, new bot, Conductor session, or the closest equivalent the host provides. Fig does not ship its own agent.
2. Pass only the chunk: goal, target files or URLs, evidence, constraints, acceptance criteria, the product-truth ledger if present, `fig-content-craft` polish/visual/proof notes when writing copy, and the validation checks to rerun.
3. Collect the worker's diff or PR. Keep the parent responsible for goal, evidence, and User-facing review.

If the host has no isolated workers, still implement, then immediately summarize evidence and the review handoff so the parent does not spend the rest of the session inside a large edit.

Do not stop Automatic mode at findings plus "what should we do next?" Findings are inputs to implementation.

## Strategic mode: Recommendation Loop

1. Read operator memory, then inspect the site and gather relevant Fig MCP evidence before the first recommendation. Research external guidance only where it can change the decision.
2. Present a short ranked recommendation list using the Selection rubric. Include the proposed strategy, why it matters, evidence, assumptions, trade-offs, concrete changes, and why higher-ranked options beat lower ones (including create versus repair/refresh/consolidate/prune).
3. Let the User respond freely with corrections, preferences, or disagreement. Do not ask a batch of prerequisite questions.
4. Treat every response as a strategy update. Research further when it introduces a factual uncertainty or changes the decision boundary.
5. Present the revised ranked recommendation list. Repeat until the User and Agent align on the strategy and the changes to make.
6. Ask the User to agree the plan. Finish with an implementation handoff the User can approve: agreed strategy, prioritized changes from the rubric vote, target pages/topics, evidence, assumptions, authorization, target metric, observation window, validation plan, and either named Search Console baselines or Search Console measurement unavailable. Write operator memory with `planned` action, merged priorities, and observation windows — no content changes, code changes, or PRs.

Strategic mode has no universal SEO/AEO goal. The aligned strategy is the goal. Do not claim alignment from silence or from the Agent's preferred plan. After the User agrees the plan, stop. Start implementation only when the User asks to execute the approved plan; then follow Automatic mode and the Implementation playbook.

## Evidence rules

- Use Fig MCP for live keyword, SERP, backlink, domain, and supported AI-visibility data. Do not invent volumes, rankings, citations, competitors, or movement. Report Lab and Field performance only from a named tool run or an authorized Search Console / host RUM surface; write `Field: unavailable` or `Lab: unavailable` instead of filling scores.
- Search Console is optional evidence, not a Fig MCP tool. Prefer a GSC UI CSV/Sheets/Excel export first, then an LLM-oriented GSC CLI (npm) with `webmasters.readonly` after one OAuth/ADC login; verify the package before install. How-to: https://figaeo.com/gsc.md. Fig Google sign-in is email only and is not GSC. GA4 is not GSC.
- When GSC is connected, pull read-only Search Analytics for the verified property and named date range. Use observed rows for low-CTR pages, striking-distance queries, wrong-query/cannibalization, and index issues when URL Inspection, sitemaps, or a User Coverage export exists. Name that GSC property, date range, and baseline metrics in the measurement handoff.
- When GSC is not connected, mark Search Console measurement unavailable. Continue with Fig MCP and page inspection. Never invent clicks, impressions, CTR, position, or coverage counts. Fig volumes and live SERPs are not GSC metrics.
- Pair tool results with direct inspection of the target pages, HTTP behavior, `robots.txt`, meta/header directives, sitemaps, JSON-LD, internal links, source HTML, and rendered content where relevant. Treat `llms.txt` as optional and platform-specific: inspect it when the User names a consumer that uses it or when it is already present, but never present it as a Google Search or AI Overviews requirement.
- Separate Google Search access (`Googlebot`) from Google-Extended controls for Gemini training/grounding, OpenAI `OAI-SearchBot` from `GPTBot` and user-initiated `ChatGPT-User`, and Anthropic `Claude-SearchBot`/`Claude-User` from training crawler `ClaudeBot`. Audit `robots.txt` and CDN/WAF access separately. Crawler policy and training access are User decisions; never enable a training crawler merely to seek visibility.
- Treat volume as an input, never the objective. Weigh business fit, audience intent, authority, competition, evidence quality, and expected impact.
- Keep the scope focused. Recheck the same queries and conditions after publishing; do not imply a ranking or citation guarantee. Feed scored `fig-outcomes` records into later selection (upweight supported tactics on this site; downweight repeated no-ops). Never invent movement to justify a score.
- If a Fig call returns authentication, insufficient credits, validation, no data, or provider failure, surface the state and follow the Fig checkout or recovery workflow. Never fill the gap with guesses.
- On `rate_limiting` from `get_keyword_metrics`, wait `retry_after_seconds` and retry. Keyword metrics rate limit (12/min) is upstream Live keyword-metrics, not a Fig quota. Do not dump raw `rate_limiting` or provider rate-limit text to the User; if they need a status, say keyword data is busy and you are retrying.
- Null or empty keyword metrics, ideas, or coverage arrays mean the provider had no data for that query. The tool succeeded. Do not invent volumes, and do not retry the same call as if it failed.
- When Search Console or operator memory is present, use those observed slices in the Selection rubric. When they are absent, say so and continue.

## Completion

Use `fig-outcomes` for registering a shipped action and scoring it after the observation window. Register the shipped action with `fig-outcomes`; score later through `fig-outcomes` after the window. Never invent movement to justify a score.

Automatic mode is complete when the authorized changes are made (or a quiet measurement is recorded), relevant checks are rerun, a shipped action is registered with `fig-outcomes`, operator memory is written, and the User can review the landed work or the measurement with named Search Console baselines or Search Console measurement unavailable. Score the outcomes record only after the window. Strategic mode is complete when the User and Agent align on a strategy and concrete changes, the agreed plan is recorded, operator memory is written, and the implementation handoff lists unresolved assumptions — with no content changes, code changes, or PRs in that pass.
