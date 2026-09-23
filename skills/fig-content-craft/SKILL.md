---
name: fig-content-craft
description: Polish SEO/AEO pages for scannability, answer-first openings, entity clarity, visuals/tables, and proprietary-data patterns. Use after fig-content-strategy when writing or revising copy, detecting AI-writing tells, or turning research into original-evidence pages. Do not use to fabricate stats, quotes, or "undetectable" AI text.
metadata:
  version: 1
  managed-by: fig-skill-update
---

# Fig Content Craft

Use this specialist after `fig-content-strategy` has a brief, or when revising shipped copy against that brief. Strategy chooses what to ship and why. Craft decides how the page reads, which table or figure belongs, and how original evidence is shown. Do not start here for prioritization or information architecture.

In Automatic mode, apply these patterns while implementing through `fig` (subagents / new bots / host-equivalent sessions). In Strategic mode, attach craft notes to the brief and wait until the User agrees the plan before writing.

## Route vs strategy

- `fig-content-strategy`: opportunities, format, brief, outreach list, acceptance criteria.
- `fig-content-craft`: polish pass, AI-writing tells, visuals/tables, proprietary-data page patterns, and research-brief recipes that fill strategy's proof slots.
- `fig-content-validation`: pass/fail against brief, sources, craft checks, and Fig rechecks.

If the User asked only what to publish, stay in strategy. If they asked to write, rewrite, humanize, add a table or chart, or publish original research, pull this skill. Recheck later with `fig-content-validation`. Follow the Selection rubric in `fig`: prefer polishing an existing URL over drafting a sibling page when evidence is close.

## Polish pass

Before shipping, run this checklist on the draft. Fail means revise, not invent.

- **Answer-first:** The H1 and first 40–80 words state the conclusion a searcher or answer engine would extract. Do not bury the claim under throat-clearing, "in today's landscape", or a table-of-contents dump.
- **Scannability:** One idea per heading. Short paragraphs. Lists only when the items are parallel. Descriptive H2/H3 lines that could stand as FAQ answers. Cut filler transitions.
- **Entity clarity:** Name the brand, product, category, and compared entities the same way the site and JSON-LD already do. Spell out ambiguous pronouns. The first mention of a product includes what it is. Do not invent entity aliases.
- **Intent match:** Opening, headings, and close serve the brief's primary query. Supporting questions stay on-page only when they share that need.
- **Proof placement:** Every specific number, quote, ranking, or capability sits next to its source or a `[needs User/source]` marker. Missing proof is a research task, never a guess.
- **Extraction shape:** Direct answers, comparison tables, and definition sentences are easier for SERP features and answer engines to lift than anecdote-only prose.

## AI-writing tells

Detect and remove generic LLM texture. The goal is specific, sourced, on-voice copy — not fake "human" quirks.

Remove or rewrite:

- Empty intensifiers ("robust", "seamless", "unlock", "leverage", "in today's fast-paced")
- Symmetrical three-item lists with identical cadence and no distinct facts
- Hedging stacks ("it is important to note that")
- Fake dialogue, invented customer stories, or "as a long-time user" when the Agent is not the User
- Em-dash chains, emoji decoration, and "In conclusion" restatements
- Keyword stuffing and heading-as-keyword lists

Keep:

- Site voice, product names, and claims from User sources
- Concrete constraints, trade-offs, and "we don't do X" where true
- Sentence length that follows the meaning, not a randomness quota

Do not add typos, slang, or personal anecdotes to "sound human". Fig does not guarantee undetectable AI text. Do not claim a detector score.

## Visuals and tables

Add a visual or table only when it carries a claim the prose cannot scan as well. Fig does not host an image CDN; describe the asset, alt text, and where the User's site should store it.

Use a **table** when:

- SERP winners are listicles, comparisons, pricing, or feature matrices (`get_serp` shows tables or comparison modules)
- Answer engines need extractable rows (vs, alternatives, specs, eligibility)
- Rankings, versions, or limits must stay aligned with visible HTML (and JSON-LD if present)

Use a **figure** (chart, screenshot, diagram) when:

- The User supplies or authorizes original data, UI, or architecture
- A process or architecture is the page's primary answer
- A screenshot is the proof (product UI, Search Console, lab result) — never a stock photo for decoration

For SERP/AEO:

- Caption and alt text restate the takeaway in a sentence an extractor can quote
- Tables are real HTML, not images of tables
- Do not invent chart values. If data is missing, ship the table structure with `[needs data]` cells or omit the figure
- Decorative hero images do not substitute for first-hand evidence

## Proprietary-data pages

Original research is a page pattern, not a blog adjective. Use it when the User has first-party data, a method, and a date — and the SERP/answer gap rewards a dataset, benchmark, or study over another recap.

Page pattern:

1. **Question and method** in the opening: what was measured, on what corpus, when, and what is excluded.
2. **Headline finding** with the number the searcher came for, sourced to the dataset on this page.
3. **Table or chart** of the core results (HTML table first).
4. **How to read it:** limitations, sample size, and what would change the conclusion.
5. **Implications** for the product or audience without turning every row into a pitch.
6. **Cite and reuse:** canonical URL, last-updated date, download or methodology appendix when the User has one. Other pages should link here instead of restating unsourced stats.

Do not fabricate surveys, quotes, sample sizes, rankings, or "internal data". Do not round someone else's study into "our research". Do not promise a ranking or citation lift from publishing a dataset. If the User lacks data, return a research brief instead of a fake study.

## Research-brief recipes

Feed `fig-content-strategy` with proof tasks, not outlines of more posts. Each recipe states the question, required inputs, Fig checks, output artifact, and what remains User-only.

- **SERP-format brief:** From `get_serp`, record the winning format (guide, listicle, table, video, forum). Output: recommended artifact plus which sections must be answer-first vs tabular. Missing: User product facts.
- **Entity/proof brief:** Inventory claims the outline needs (capabilities, pricing, customers, metrics). Mark each as User source, cited primary source, or missing. Output: proof list for the strategy brief. Never invent a customer or number.
- **Original-research brief:** Question, population, method, date range, fields, who can authorize publication, and the table the page will show. Output: go / no-go. No-go if method or data is missing.
- **Visual brief:** Which comparison or time series belongs, columns, source, alt/caption takeaway, HTML vs image. Output: asset list for implementation. Fig does not generate a hosted image pipeline.
- **Answer-extract brief:** The sentence(s) that should be lift-able for the primary query, plus FAQ-shaped H2s that match observed PAA/answer phrasing without stuffing. Recheck later with `research_ai_visibility` on the same prompts — that is validation, not a writing trick.

Hand these recipes to strategy so briefs include first-hand/original evidence slots instead of empty "add proof" bullets.

## Evidence rules

- Do not fabricate facts, statistics, quotes, competitor claims, testimonials, or product capabilities.
- Mark missing proof as a research or User input task.
- Pair craft choices with Fig evidence (`get_serp` for format, `research_ai_visibility` for whether the brand is named) without implying a guarantee.
- When Search Console is not connected, mark Search Console measurement unavailable. Never invent clicks, impressions, CTR, position, or coverage counts.
- Out of scope: Fig image CDN; guaranteeing undetectable AI text.
