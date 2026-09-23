---
name: fig-free-tool
description: Gated playbook for free interactive tools (calculators, checkers, generators) when SERP and business evidence favor a tool over a guide. Use for lead-magnet tools the User's agent will build in their stack. Refuse thin gimmicks, tools without unique data, and policy-risk capture. Fig does not host customer tools or Marketplace widgets.
metadata:
  version: 1
  managed-by: fig-skill-update
---

# Fig Free Tool

Use this specialist only after search research shows an interactive tool would beat a static guide for the observed demand. A free tool is not a default growth trick.

Fig supplies the brief, page shell, proof plan, and measurement. The consuming Agent builds the tool in the User's repository or stack. Fig does not host customer tools, widgets, or a Marketplace.

## Gate

Proceed only when all of these are true:

- `get_serp` (and competing URLs) show calculators, checkers, generators, or other interactive results ranking, or the query clearly needs computation or configuration that prose cannot answer.
- The brand has unique inputs, formulas, product data, or first-hand methodology a generic widget cannot copy.
- The tool serves a real job-to-be-done on the way to the product, not a bait form.
- An agreed plan, or equally clear User authorization, names this specific tool before any build.

Score a new tool against repair or refresh of an existing URL with the Selection rubric in `fig`. When Search Console is not connected, mark Search Console measurement unavailable; never invent GSC numbers.

If a guide, table, or existing page wins the SERP and answers the intent, stay with `fig-content-strategy`. Do not invent a tool to chase leads.

In Automatic mode, still require that authorization for this tool. In Strategic mode, stop when the User agrees the plan, and include the brief. After authorization, implement through `fig` (subagents / new bots / host-equivalent sessions) in the User's stack, and hand the User the landed work.

## Refuse

Refuse and recommend a guide, table, or no page when:

- **Thin gimmick:** novelty widgets, generic BMI/age/tip calculators, or quizzes with no product-specific data.
- **No unique data:** the same public formula or API any competitor could embed; no first-hand dataset, product constraint, or proprietary method.
- **Policy risk:** medical diagnosis; individualized financial, legal, or safety advice presented as a verdict; deceptive capture; PII harvest without a stated legitimate purpose; cloaking; doorway tools.
- **Lead spam:** the primary job is list growth rather than answering the query. Optional email after the useful result is a User decision; required email before any result is out of scope.
- **Hosted Fig widget / Marketplace:** requests that Fig host, iframe, or list the tool. Direct the Agent to build it in the User's stack.

State the refuse reason, the Fig evidence, and the alternative artifact.

## Scope

Stay inside this brief. Do not ship application code unless the User authorized implementation in their repo.

1. **Problem framing** — audience, job-to-be-done, primary query, and why a tool beats a guide for this SERP.
2. **UX sketch** — inputs, outputs, empty and error states, mobile-visible result, no dark patterns.
3. **SEO/AEO page shell** — URL, title, H1, answer-first intro, how the tool works, FAQ, and indexable HTML for the explained or default state. Do not hide the core answer behind a script-only wall.
4. **Proof** — formulas, sample calculation, sources, limitations, last-reviewed date. Mark missing User facts instead of inventing them.
5. **Internal links** — from and to relevant product, docs, and guides. Treat one primary intent per URL as a heuristic.
6. **Measurement** — baseline, target metric, observation window, confounders, and the authorized analytics, Search Console, or server-log surface if any.

## Brief

For an approved tool, return:

- working name, target URL, and one primary query or answer need;
- audience, intent, desired action, and the gap versus ranking tools;
- unique data or method the brand owns, and what is still missing;
- UX sketch (inputs, outputs, states);
- title, H1, answer-first copy, outline, and FAQ;
- JSON-LD notes only when they match visible content — never add a schema type solely because it might produce a rich result;
- proof, citations, limitations, and claims that need User confirmation;
- internal links;
- baseline, target metric, observation window, assumptions, and confounders;
- acceptance criteria and the Fig calls to recheck;
- build notes for the User's stack (Fig does not host).

Do not fabricate formulas, sample outputs, competitor capabilities, or conversion rates.

## Validation recheck plan

After ship, call `fig-content-validation` with this checklist:

- HTTP status, canonical, title, H1, robots, and mobile-visible explanation plus a default or sample result without requiring email.
- Core explanation is available in source HTML; interactive output degrades honestly if scripts fail.
- Claims and sample math match User sources or cited primary sources.
- Internal links resolve.
- Re-run the same `get_serp` queries and `research_ai_visibility` prompts used at baseline (same country, language, and platform).
- If Search Console or analytics is authorized, record impressions, queries, and tool completions only after the stated observation window. Do not treat a passing HTML or schema check as an SEO or lead outcome.

Return pass, fail, or needs-review for each criterion, with evidence and the smallest corrective action. Separate immediate implementation validity from later SERP or mention movement.
