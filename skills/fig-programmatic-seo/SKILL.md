---
name: fig-programmatic-seo
description: Gated programmatic SEO playbook for evidence-backed template sets. Use for compare, alternatives, use-case, for-persona, and other justified URL grids after SERP plus business evidence supports templates. Refuse doorway pages, thin keyword-variant spam, and unlimited pSEO. Call fig-search-research first; validate shipped templates with fig-content-validation. Fig does not host the User's site.
metadata:
  version: 1
  managed-by: fig-skill-update
---

# Fig Programmatic SEO

Use this specialist only when live SERP evidence and business facts support a **bounded template set**. Fig does not generate thousands of pages by default, does not sell programmatic SEO as unlimited content, and does not host the User's site. The consuming Agent implements in the User's repository.

Prefer repair, refresh, consolidation, or pruning of existing URLs over net-new templates when the same user need is already covered. Apply the Selection rubric in `fig`: repair, refresh, consolidate, and prune beat create when evidence is close.

`fig` owns Automatic mode vs Strategic mode. `fig` routes each job to the specialist skill that fits. This skill does not start a second path.

- **Strategic mode:** research the gate, propose the template set, and wait until the User agrees the plan. Write no pages, change no code, and open no PRs until then.
- **Automatic mode:** proceed with templates only when the request clearly authorizes a bounded programmatic set (named routes, named entities, or an approved plan). Inferring "they asked for more SEO" is not authorization.

## Gate

Proceed only when **every** item is true. Otherwise refuse the template set and recommend a non-programmatic path (`fig-content-strategy` for one-off pages, `fig-search-research` if evidence is missing).

1. **SERP evidence:** `get_serp` (and `compare_serp_competitors` when the query set is small) shows the winning format is a comparison, alternatives list, use-case/for-persona page, or another justified grid — not a one-off blog that happened to mention a keyword. Use `get_keyword_metrics` as supporting demand, never as the reason to stamp pages. Null metrics mean no coverage, not a failed tool.
2. **Business evidence:** the User's product, catalog, pricing, personas, or first-party data can supply **distinct facts per URL**. Shared boilerplate plus a swapped token is not a catalog.
3. **Distinct user need:** each template instance answers a different audience, job, constraint, or decision. Query variants of the same need stay on one URL.
4. **Evidence base:** each URL has proof it can uniquely show (specs, screenshots, limits, pricing dimensions, customer proof, or sourced competitor facts). Mark missing proof as a User input task; do not invent it.
5. **Canonical strategy:** one canonical per need; no A-vs-B plus B-vs-A duplicates; no parameterized doorway URLs; near-duplicates consolidate.
6. **Quality bar:** every instance meets the same outline, unique title/H1, answer-first opening, and internal-link contract defined in the brief. If the set cannot meet that bar, shrink or refuse it.
7. **Bound:** name the entity list and a maximum URL count. Do not leave the generator open-ended.

If the User asks for mass location, synonym, or "one page per keyword" coverage without those gates, refuse.

## Refuse vs proceed

**Refuse**

- "Create a page for every city we might serve" with the same 200 words and a city name swap.
- "Build all X vs Y combinations for every competitor we can name" with no distinct buyer question or first-party comparison data.
- "Programmatic SEO for thousands of keywords" or selling pSEO as unlimited content.
- Thin `/for/{token}` pages whose only difference is the heading.
- Doorway parameter URLs (`?keyword=`) meant to rank for variants of one intent.

**Proceed (bounded)**

- `get_serp` for `{product} vs {rival}` and `{product} alternatives` consistently returns comparison tables from product sites, and the User can supply a short, sourced comparison matrix for a named rival list (for example 6 rivals, not "the internet").
- Use-case demand is real (`{product} for {persona}` SERPs show dedicated for-pages), each persona has a different job-to-be-done, and the product actually behaves differently for them.
- An existing `/compare/` or `/alternatives/` IA already ranks or is linked internally, and the gap is filling **missing justified slots** or repairing thin ones — not exploding the tree.

When refusing, say what evidence failed the gate, what one-off page or repair would serve the need, and that Fig will not stamp a grid to chase volume.

## Patterns

Use only the pattern the SERP specifies:

- **Compare** (`/compare/{a}-vs-{b}`): two (rarely three) named options, a decision table, and a recommendation rule. Do not emit both directions.
- **Alternatives** (`/alternatives/{anchor}`): who this is for, when to pick each option, honest gaps. Not a keyword-stuffed listicle clone of `{anchor} alternatives` with identical blurbs.
- **Use-case / for-persona** (`/for/{persona}` or `/use-cases/{job}`): one persona or job, constraints, workflow, proof. Not a synonym of the homepage.
- **Other justified grids:** category × integration, plan × job, or similar, only when searchers and the catalog both treat those cells as different decisions.

Listicles and best-of influence stay with `fig-search-research` then `fig-content-strategy`. This skill is for **template sets**, not a second listicle playbook.

## Brief, IA, and internal links

After the gate passes, produce one brief for the **template**, plus an IA map for the set.

**Template brief**

- pattern, URL rule, and entity list with the bound;
- primary query pattern and intent (heuristic: one primary intent per URL);
- audience, desired action, and the gap versus current winners;
- baseline, target metric, observation window, business/conversion goal, assumptions, confounders;
- title/H1 pattern, answer-first opening rule, outline slots that **must** be unique vs slots that may be shared chrome;
- required first-party or cited proof per instance;
- canonical, robots, and pagination rules;
- acceptance criteria and Fig rechecks (`get_serp` on the same query pattern; `research_ai_visibility` when answer-engine mention is in scope);
- for Automatic mode, the authorization that allows this set.

**IA**

- parent hub (for example `/compare`, `/alternatives`, `/for`) that explains the set and links every live instance;
- no orphan template URLs;
- hubs do not duplicate a child's unique table;
- new instances attach to existing product, docs, or pricing URLs instead of forming a silo.

**Internal links**

- hub → every instance; each instance → hub, the relevant product/docs URL, and one sibling that shares a real decision (not a random next slug);
- do not cross-link every instance to every other instance;
- anchor text names the user need, not "click here" or the raw keyword stuffed three times;
- when two instances overlap, pick a canonical and 301 or noindex the weaker URL.

## Stack notes (guidance only)

Optional notes for the implementing Agent in the User's repo. Fig does not host, deploy, or operate the site.

For Next.js App Router (and similar file-based routers): bounded dynamic segments such as `app/compare/[pair]/page.tsx` or `app/for/[persona]/page.tsx`; `generateStaticParams` (or equivalent) from the **named entity list**, not from an open keyword dump; unique `title`, description, canonical, and H1 per param; sitemap entries only for URLs that pass the quality bar; skip generating A-vs-B and B-vs-A. ISR/SSG is a performance choice, not an SEO strategy. If the stack is not Next.js, keep the same IA and quality rules in that framework's routing.

Pass these notes into the `fig` implementation worker with the brief. Do not treat stack notes as a reason to proceed when the gate failed.

## Ship and validate

In Automatic mode, implement through `fig` (host subagents, new bots, or equivalent isolated sessions). Ship a **pilot slice** of the set first when the bound is larger than a handful of URLs; expand only if the pilot meets the quality bar.

After ship, call `fig-content-validation` on the hub plus each new or repaired instance:

- HTTP, canonical, title, H1, indexability, sitemap, and internal-link discovery for every URL in the set;
- uniqueness: instance body is not a token-swap of a sibling;
- claims vs User source material;
- the same `get_serp` query pattern and country/language used at the gate.

Report pass/fail/needs-review per URL. Immediate validity is not a ranking outcome. Recheck the same queries after the stated observation window. If several instances fail uniqueness or proof, stop expansion and repair or prune. Register the shipped set with `fig-outcomes`; score after the observation window. Never invent movement.

## Handoff

Return: gate result (proceed or refuse with the failed items); entity list and bound; template brief; IA and internal-link map; stack notes if useful; authorization and agreed-plan state; validation plan via `fig-content-validation`; register/score handoff to `fig-outcomes`. This specialist does not write production pages; `fig` owns writing after authorization.
