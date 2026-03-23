---
name: on-page-seo
description: Human-first on-page SEO workflow for improving rankings, CTR, intent alignment, content depth, and internal linking using Google Search Console, GA4, SERP analysis, Ahrefs, Keyword Planner, and Google Trends. Use when the user wants to optimize an underperforming URL, rewrite title/meta/H1-H2s without keyword stuffing, analyze competitors, fix cannibalization, add FAQ or E-E-A-T sections, or review 14-day or 30-day SEO performance using pasted exports, tables, or summaries from those sources.
---

# On-Page SEO

Follow a data-grounded, human-first workflow for on-page SEO. Keep core instructions in this file and open the reference manual only when you need the detailed system prompt, exact copy rules, prompt blocks, data templates, or checklists: [references/elite-on-page-seo-automation-system.md](references/elite-on-page-seo-automation-system.md).

## Core rules

- Write for humans first and search engines second. Recommendations must sound natural, brand-appropriate, and never over-optimized.
- Ground every recommendation in user-provided data or clearly labeled assumptions.
- Never invent search volume, CTR, rankings, organic traffic, or keyword difficulty.
- Ask only for the minimum missing input that blocks a defensible recommendation. Otherwise continue and label assumptions.
- Treat GSC as the ground truth for live query performance when sources disagree.
- When Ahrefs is unavailable, rely on GSC plus live SERP analysis instead of guessing.
- Resolve cannibalization before optimizing a page for a primary keyword.
- Keep one clear primary keyword per page unless the data proves distinct intent.
- Match all recommendations to search intent: informational, commercial, or transactional.
- Prioritize highest-impact, lowest-effort fixes first: title tag, meta description, H1, and H2/H3 structure.
- Respect hard limits: title tag at or under 60 characters, meta description at or under 155 characters, and intro around 100 words.
- Never repeat the same keyword or close synonym more than once inside a single title tag, meta description, or H1.
- Distribute keyword variants across elements: primary keyword in the title, close synonym in the H1 when useful, and long-tail variations in H2s or body copy.
- Prefer benefits, trust signals, and genuine USPs over synonym stacking or filler modifiers.
- Front-load the primary keyword in the first sentence of the intro and place the close synonym within the first 100 words only if it reads naturally.
- Source FAQ questions from GSC queries whenever possible and keep answers concise, useful, and schema-ready.
- Use descriptive internal-link anchors and vary them naturally.
- Make E-E-A-T remediation mandatory for YMYL topics.
- Run the over-optimization checklist before finalizing any rewrite.

## Choose the workflow

### Single-page full optimization

Run the full 5-phase workflow when the user wants to improve one URL and provides enough data.

### Partial optimization

Run only the requested phase when the user asks for a narrower task, but still perform a lightweight intent and cannibalization check before rewriting page elements.

### Multi-page triage

If the user provides multiple URLs or page-level GSC data, rank pages by opportunity before optimizing any single page. Use the batch triage method in the reference manual.

### 14-day or 30-day review

Use the performance review workflow when the user wants to compare baseline versus post-optimization data.

## Required inputs

Ideal inputs:

- Target URL
- GSC query data
- Ahrefs keyword data and top competitor URLs
- Keyword Planner volume and competition data
- Google Trends trend validation
- GA4 behavior data
- Current title tag, meta description, H1, H2/H3s, URL slug, and current content or outline
- SERP notes or competitor URLs when Ahrefs is missing

Minimum viable inputs for partial work:

- Rewrites: current page elements plus target keyword and intent clues
- Gap analysis: page summary plus 3 competitor URLs or a SERP summary and a target keyword
- Performance review: baseline and current GSC or Ahrefs metrics

## 5-phase execution

### Phase 1: Keyword intelligence

- Extract one primary keyword, 2 to 3 secondary keywords, and 5 to 8 semantic terms.
- Identify quick wins in positions 4 to 20 with meaningful impressions.
- Flag cannibalization and recommend one action: consolidate, differentiate, internally link, or keep both.
- Classify search intent.

### Phase 2: Competitor SERP deconstruction

- Compare top-ranking pages for structure, depth, entities, subtopics, snippets, and PAA coverage.
- Identify topics, terms, and formats missing from the current page.

### Phase 3: On-page element optimization

- Generate title tag, meta description, H1, H2 structure, URL slug verdict, schema recommendation, and intro paragraph.
- Keep outputs publication-ready and within limits.

### Phase 4: Content architecture and depth

- Build an outline that beats competitors on depth without padding.
- Add semantic entities, E-E-A-T improvements, FAQ ideas, internal linking opportunities, and visual or table placements.

### Phase 5: Performance tracking and iteration

- Log pre-optimization baselines.
- Define 14-day and 30-day review checks.
- Suggest next actions and title tests if performance stalls.

## Output format

Use this structure unless the user asks for something else:

1. Snapshot
   State the goal, URL, key metrics, missing inputs, intent, and cannibalization status.
2. Keyword map
   List the primary keyword, secondary keywords, semantic terms, and quick wins with GSC evidence.
3. Priority fixes
   List P1 changes first, then P2 or P3 only when they materially help. Show current versus proposed and a brief rationale.
4. Ready-to-publish rewrites
   Provide title, meta, H1, H2s, slug verdict, schema, and intro.
5. Content improvements
   Provide content gaps, FAQ ideas, internal links, E-E-A-T additions, and visual suggestions.
6. Measurement plan
   Provide baseline metrics, 14-day checks, 30-day review points, and title test ideas.
7. Implementation checklist
   Provide a prioritized task list with effort and impact ratings.

## Reference map

Open the reference manual only when needed:

- Sections 05 to 06 for the human-first system prompt and copy rules
- Section 07 for the prompt library
- Section 08 for data input templates
- Section 09 for cannibalization handling
- Section 10 for execution and over-optimization checklists
- Section 11 for E-E-A-T guidance

## Failure handling

- If the data conflicts across tools, call out the conflict explicitly and anchor recommendations in GSC for live query performance.
- If competitor URLs are missing, ask for them or proceed with on-page work only.
- If two site pages appear to target the same primary keyword, stop and resolve intent overlap first.
- If a YMYL page lacks credible authority signals, require E-E-A-T fixes before claiming the page is publish-ready.
