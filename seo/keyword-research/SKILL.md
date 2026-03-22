---
name: keyword-research
description: Keyword research workflow for existing URLs and brand-new pages using Ahrefs, Google Search Console, and GA4 data. Use when the user wants to audit live page rankings, confirm a primary keyword, expand a seed keyword, classify intent and funnel stage, find quick wins and CTR leaks, run competitor keyword gap analysis, cluster keywords, prioritise opportunities, or generate a keyword master list and on-page brief for product, collection, category, or blog pages.
---

# Keyword Research

Run keyword research as a repeatable, tool-grounded workflow. Keep this file focused on execution rules and open the full operating guide only when you need the exact prompts, templates, scoring models, or decision trees: [references/elite-keyword-research-workflow.md](references/elite-keyword-research-workflow.md).

## Core rules

- Ground every conclusion in Ahrefs, GSC, or GA4 data provided through MCP or pasted exports.
- Never invent search volume, keyword difficulty, impressions, CTR, traffic, conversions, or domain rating.
- Treat GSC as the ground truth for existing live pages.
- Use GA4 to validate intent fit and traffic quality, not just rankings.
- Use Ahrefs for expansion, gap analysis, difficulty, SERP review, and competitor coverage.
- Show results after each step before moving to the next step unless the user asks for a compressed answer.
- Use tables for keyword datasets whenever practical.
- If an MCP source is unavailable, say so explicitly and continue with the available inputs.

## Entry detection

### Existing URL

If the user provides a live URL, ask for page type if it is not obvious, then run Workflow A.

Accepted page types:

- Product page
- Collection or category page
- Blog or article page

### Starting from scratch

If the user says "starting from scratch" or gives no URL, ask for:

- Seed keyword
- Page type

Then run Workflow B.

## Workflow A: Existing page research

Use this flow for pages that already exist.

### Step 1: GSC performance audit

- Pull queries for the URL for the last 90 days.
- Return keyword, average position, impressions, clicks, and CTR.
- Bucket keywords into:
  - `✅ GOLD`
  - `⚡ QUICK WIN`
  - `🩸 CTR BLEED`
  - `💀 DEAD WEIGHT`
- Identify the current seed keyword.

### Step 2: GA4 behaviour check

- Pull landing-page sessions, engaged sessions, engagement rate, average engagement time, conversions, and conversion rate.
- Flag intent mismatch when rankings exist but engagement is weak.

### Step 3: Ahrefs keyword expansion

- Expand the seed keyword into related terms, also-rank-for terms, questions, long-tail variants, SERP features, and trending terms.

### Step 4: Intent mapping

- Assign intent, funnel stage, and page-fit score.
- Discard keywords with weak page fit.

### Step 5: Competitor gap analysis

- Find what top competitors rank for that the page does not.
- Score each gap by opportunity.

### Step 6: Master keyword list

- Deduplicate all approved keywords.
- Assign keyword type, priority, and implementation action.

### Step 7: On-page brief

- Turn the final keyword set into an implementation brief covering title, meta, slug, H1, headings, body guidance, links, alt text, schema, and content gaps.

## Workflow B: New page research

Use this flow when building a page from zero.

### Step 1: Seed universe expansion

- Expand the root keyword into matching terms, related terms, question terms, long-tail variants, and comparison or buy-intent variants where relevant.

### Step 2: Primary keyword selection

- Choose one primary keyword based on search volume, difficulty, page-type fit, business value, and SERP winnability.

### Step 3: Competitor and SERP study

- Analyze page-1 winners, dominant page type, required topics, and whitespace opportunities.

### Step 4: Keyword clustering

- Group keywords into hero, feature, comparison, long-tail, and question clusters.
- Map each cluster to a page section.

### Step 5: Page blueprint

- Produce the URL structure, title, meta, heading outline, section briefs, FAQ, internal links, schema, and estimated content length.

## Output structure

Use this sequence unless the user requests a different format:

1. Step output
   Provide the findings for the current step in a table or compact bullets.
2. Decision
   State what is approved, rejected, or deprioritized and why.
3. Next step
   Move to the next workflow step with the selected inputs.
4. Final deliverables
   End with:
   - Keyword master list
   - On-page brief or page blueprint
   - Final summary with:
     - primary keyword
     - top 5 target keywords
     - biggest opportunity
     - number 1 recommended action
     - estimated impact if defensible from the data

## Key scoring rules

- Quick win: position 11 to 30 with meaningful impressions and intent fit
- CTR bleed: high impressions with weak CTR for the ranking position
- Existing page keyword priority:
  - `🔴 P1` critical
  - `🟠 P2` high
  - `🟡 P3` medium
  - `🟢 P4` supporting
- Reject keywords when page intent clearly mismatches the keyword intent.

## Reference map

Open the reference manual only when needed:

- Workflow prompts: sections 02 to 04
- Templates and deliverables: section 05
- Decision trees, matrices, and benchmarks: section 06

## Failure handling

- If GSC data is absent for an existing page, continue with Ahrefs and note the missing ground-truth data.
- If GA4 shows weak engagement, call out likely intent mismatch instead of blindly scaling that keyword set.
- If SERP intent does not match the requested page type, say so explicitly and recommend the correct page type.
- If the current page is trying to rank for mixed intents, separate the keyword set by page intent before creating the brief.
