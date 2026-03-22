# Elite Keyword Research Workflow

Claude + Ahrefs + Google Search Console + GA4

Complete SOP, prompts, templates, and output formats for repeatable keyword research.

Version 1.0

## Table of contents

- [01. How to use this document](#01-how-to-use-this-document)
- [02. Workflow A: Existing page research](#02-workflow-a-existing-page-research)
- [03. Workflow B: New page research from scratch](#03-workflow-b-new-page-research-from-scratch)
- [04. The master prompt](#04-the-master-prompt)
- [05. Output templates and deliverables](#05-output-templates-and-deliverables)
- [06. Decision trees and quick reference](#06-decision-trees-and-quick-reference)

## 01. How to use this document

This SOP defines a repeatable, tool-integrated keyword research process using Claude, Ahrefs, Google Search Console, and GA4. Every step, prompt, and output template is documented so the same research quality can be repeated consistently.

### Tools required

| Tool | Role |
| --- | --- |
| Claude | Reasoning layer for analysis, clustering, and prioritisation |
| Ahrefs | Keyword expansion, competitor analysis, keyword gap, SERP review |
| Google Search Console | Rankings, CTR, impressions, and real query performance |
| GA4 | Behaviour, engagement, and conversion quality by landing page |

### Two entry points

#### Case 1: Existing URL

- Paste the URL
- Confirm page type: Product, Collection or Category, or Blog or Article
- Run Workflow A

#### Case 2: Starting from scratch

- State that you are starting from scratch
- Provide the seed keyword and page type
- Run Workflow B

### Naming conventions

| Term | Definition |
| --- | --- |
| PK | Primary Keyword: the main target keyword |
| SK | Secondary Keywords: 3 to 5 supporting targets |
| LSI | Semantically related terms and concepts |
| KD | Keyword Difficulty from Ahrefs |
| SV | Monthly search volume |
| SERP | Search engine results page |
| QW | Quick win: position 11 to 30 and realistically pushable |
| Intent | Informational, Commercial, Transactional, or Navigational |

## 02. Workflow A: Existing page research

Use this when you have a live page and want to base the research on actual performance data.

### Step 1: GSC performance audit

Pull all queries for the target URL from the last 90 days. This is the ground truth for what Google already associates with the page.

#### Extract

- All ranking keywords for positions 1 to 100
- Position, impressions, clicks, CTR, and date range
- Sort by impressions descending

#### Buckets

| Bucket | Definition and action |
| --- | --- |
| `✅ GOLD` | Positions 1 to 10 with strong impressions. Core traffic drivers. Preserve and reinforce. |
| `⚡ QUICK WIN` | Positions 11 to 30 with 500+ impressions. Good candidates for page-1 gains. |
| `🩸 CTR BLEED` | 1000+ impressions with CTR under 2 percent. Rewrite title and meta immediately. |
| `💀 DEAD WEIGHT` | Low impressions and poor rankings. Deprioritise unless strategically important. |

#### Prompt

```text
Using Google Search Console, pull all search queries for this URL:
[PASTE URL]

Date range: Last 90 days.
Return a table with: Keyword | Avg Position | Impressions | Clicks | CTR
Then classify each keyword into one of these buckets:
  GOLD (pos 1-10, high impressions)
  QUICK WIN (pos 11-30, 500+ impressions)
  CTR BLEED (1000+ impressions, CTR < 2%)
  DEAD WEIGHT (pos 50+, low impressions)

Finally, identify the single keyword that best represents
what this page is currently MOST associated with (our seed keyword).
```

### Step 2: GA4 behaviour analysis

Validate whether the page is attracting the right audience after the click.

#### Pull from GA4

- Landing-page sessions for the URL over the last 90 days
- Engagement rate
- Average engagement time
- Bounce rate if available
- Conversion events triggered from this landing page
- Useful segments such as new versus returning, device, and geography

#### Green flags

- Engagement rate over 55 percent
- Average engagement time above about 90 seconds for blogs or 60 seconds for product or collection pages
- Conversion events firing from the page

#### Red flags

- Strong impressions or clicks in GSC but engagement rate under 30 percent
- Immediate exits suggesting intent mismatch
- Zero conversions from a page that should attract mid- or bottom-funnel traffic

#### Prompt

```text
Using GA4, pull landing page data for: [PASTE URL]
Date range: Last 90 days.

Return: Sessions | Engaged Sessions | Engagement Rate |
Avg Engagement Time | Conversions | Conversion Rate

Flag: Is there an intent mismatch between GSC traffic and GA4 engagement?
Recommend: Is this page attracting the right audience?
```

### Step 3: Primary keyword confirmation and seed expansion

Use GSC plus GA4 to confirm the PK, then expand it in Ahrefs.

#### Confirm the primary keyword

- Start with the highest-value keyword in the `✅ GOLD` bucket
- Require strong or acceptable GA4 engagement
- Match the keyword intent to page type
- If signals conflict, prefer the term with the best realistic path to rank 1 and stronger business fit

#### Ahrefs expansion pulls

| Pull type | Use case |
| --- | --- |
| Related keywords | Semantically similar terms for headings and body coverage |
| Suggested or also-rank-for | Terms top competitors also target |
| Questions | FAQ and PAA opportunities |
| Long-tail variants | Lower-KD, often higher-conversion versions |
| SERP features | Snippet, PAA, shopping, and other layout opportunities |
| Trending keywords | Rising terms with growth potential |

#### Prompt

```text
Using Ahrefs, take this seed keyword: [PK FROM STEP 1]

Pull and return 6 separate lists:
1. Related keywords (sort by volume DESC, filter KD < 40)
2. Suggested / also-rank-for keywords
3. Question-based keywords (who/what/how/why/best/vs)
4. Long-tail variants (4+ words)
5. SERP features triggered by top 10 keywords
6. Trending keywords (YoY growth > 20%)

For each keyword return: Keyword | SV | KD | CPC | Intent
```

### Step 4: Search intent mapping

Only keep keywords whose intent fits the page.

#### Intent types

| Intent type | Description and best page match |
| --- | --- |
| Informational | User wants to learn. Best for blogs, guides, and hubs. |
| Commercial Investigation | User compares options. Best for collection, category, and comparison pages. |
| Transactional | User wants to buy or act. Best for product and checkout pages. |
| Navigational | User wants a specific brand or site. Best for brand-led pages. |

#### Funnel stages

| Stage | Description |
| --- | --- |
| TOFU | Discovery |
| MOFU | Evaluation |
| BOFU | Purchase or conversion intent |

#### Prompt

```text
Take the keyword list from Step 3. For each keyword, define:
  - Intent Type: Informational / Commercial / Transactional / Navigational
  - Funnel Stage: TOFU / MOFU / BOFU
  - Intent Match Score (1-5): How well does this keyword match
    a [PAGE TYPE] page?

Flag any keywords with Intent Match Score < 3 as DISCARD.
Flag keywords with Score 4-5 as APPROVED.
Return: Keyword | Intent | Stage | Match Score | Status
```

### Step 5: Competitor keyword gap analysis

Find the terms competitors rank for that the page misses.

#### Process

- Identify the top 3 to 5 URLs ranking for the PK
- Run a keyword gap against the target URL
- Extract keywords ranked by all competitors but not by your page
- Extract keywords ranked by 2 of 3 or 2 of 5 competitors as medium-priority opportunities
- Remove branded terms, wrong-intent terms, and excessive-KD terms

#### Opportunity scoring

| Priority | Rule |
| --- | --- |
| High | 3+ competitors rank, KD under 40, SV above 200, intent matches |
| Medium | 2 competitors rank, KD under 55, SV above 100 |
| Low | Everything else |

#### Prompt

```text
Using Ahrefs, find the top 5 URLs ranking for: [PRIMARY KEYWORD]

Run a keyword gap analysis: show keywords these competitors rank for
in positions 1-20 that my URL ([PASTE URL]) does NOT rank for.

Sort by: number of competitors ranking (highest first).
Filter: remove branded keywords, KD > 60, SV < 50.

For each gap keyword return:
Keyword | SV | KD | # Competitors Ranking | Opportunity Score

Opportunity Score:
  HIGH = 3+ competitors + KD<40 + SV>200
  MEDIUM = 2 competitors + KD<55 + SV>100
  LOW = everything else
```

### Step 6: Final keyword selection and prioritisation

Combine all approved keywords into one action-oriented list.

#### Priority system

| Priority | Where to use it |
| --- | --- |
| `🔴 P1` | Title tag, H1, URL slug, first 100 words |
| `🟠 P2` | H2 or H3 headers and repeated naturally in body copy |
| `🟡 P3` | Body copy, FAQ, meta description, and support content |
| `🟢 P4` | Alt text, schema, internal links, and supporting mentions |

#### Sample master keyword table

| Keyword | Type | Volume | KD | Intent | Priority | Action |
| --- | --- | --- | --- | --- | --- | --- |
| [main keyword] | Primary | 8,100 | 38 | Transactional | `🔴 P1` | Title, H1, URL |
| [secondary kw 1] | Secondary | 2,400 | 29 | Commercial | `🟠 P2` | H2 header |
| [secondary kw 2] | Secondary | 1,900 | 31 | Transactional | `🟠 P2` | Body copy x3 |
| [question kw] | Question | 720 | 22 | Informational | `🟡 P3` | FAQ section |
| [long-tail kw] | Long-tail | 390 | 18 | Transactional | `🟡 P3` | Product description |
| [gap kw 1] | Gap | 1,200 | 35 | Commercial | `🟠 P2` | New H2 section |
| [lsi term] | LSI or Semantic | 340 | 15 | Informational | `🟢 P4` | Alt text, schema |

### Step 7: On-page optimisation brief

Turn the research into concrete implementation instructions.

#### Brief components

- Title tag with the PK inside the first 60 characters
- Meta description including PK and one SK with a CTA
- URL slug with the PK and no unnecessary words
- H1 aligned to the PK
- H2 and H3 structure mapped to SKs
- Body placement guidance for each keyword
- Internal links to and from relevant pages
- Image alt text opportunities
- Schema recommendations
- Content gaps to add based on competitor and question research

#### Prompt

```text
Using the finalised keyword master list, generate a complete
on-page optimisation brief for: [PAGE URL]
Page type: [Product / Collection / Blog]

Include:
1. Recommended Title Tag (max 60 chars, include PK)
2. Recommended Meta Description (150-160 chars, include PK + CTA)
3. Recommended URL Slug
4. H1 recommendation
5. Recommended H2/H3 structure with keyword mapping
6. Body copy instructions (where to place each keyword)
7. Internal linking opportunities (pages to link to/from)
8. Image alt text recommendations
9. Schema markup type recommendation
10. Content gap list (topics not covered that competitors cover)
```

## 03. Workflow B: New page research from scratch

Use this when no URL exists yet and you need to define the keyword foundation before content or development work begins.

### Step 1: Seed keyword universe expansion

Turn one root keyword into a broad opportunity set.

#### Process

- Enter the seed keyword into Ahrefs
- Pull matching terms, related terms, questions, and SERP overview
- Apply baseline filters such as KD under 50 and SV above 100, adjusted for niche realism
- Export or pass the results into Claude for clustering

#### Prompt

```text
Starting from scratch for a new [PAGE TYPE] page.
My root/seed keyword is: [SEED KEYWORD]

Using Ahrefs, expand this into a full keyword universe:
1. Matching terms (SV > 100, KD < 50)
2. Related terms
3. Question keywords
4. Long-tail variants
5. 'vs' and comparison keywords (for collection pages)
6. Best/top/buy variants (for product/collection pages)

Return: Keyword | SV | KD | Intent | Relevance (1-5)
```

### Step 2: Primary keyword selection

Choose one keyword to anchor the page.

#### Decision matrix

| Criterion | How to evaluate |
| --- | --- |
| SV sweet spot | Large enough to matter, not so large it becomes unrealistic |
| KD target | Stay at or under the site's realistic authority range |
| Intent match | Must precisely match the page type |
| Business value | Transactional and commercial terms usually matter more for product or collection pages |
| SERP winnability | Skip terms dominated entirely by unassailable mega-sites if the site cannot compete |

### Step 3: Competitor analysis and SERP study

Understand the shape of page 1 before planning the page.

#### Process

- Identify the top 10 results for the PK
- Note the dominant page types
- Pull the strongest competitors into Ahrefs
- Identify angles everyone covers and angles nobody covers

#### Prompt

```text
Using Ahrefs, analyse the top 10 results for: [PRIMARY KEYWORD]

For each result return: URL | DR | Keywords ranking for | Est. Traffic

Then run a content gap:
- What topics do ALL top 3 results cover? (non-negotiable content)
- What do 2/3 cover? (highly recommended content)
- What does NONE cover? (differentiation opportunity)

Finally: what page type dominates page 1?
(product / collection / blog / comparison / tool)
```

### Step 4: Keyword clustering and intent mapping

Cluster the research into page sections.

| Cluster type | Where it lives on page |
| --- | --- |
| Hero cluster | PK and closest variants for title, H1, and above-the-fold copy |
| Feature cluster | SKs describing features or benefits for H2-led sections |
| Comparison cluster | "vs", "alternative", or "best" terms for comparison sections or FAQs |
| Long-tail cluster | Specific variants for detailed sections or tables |
| Question cluster | FAQ and structured data opportunities |

### Step 5: Page blueprint and URL architecture

Define the final page plan before writing.

#### Prompt

```text
Based on the keyword research and competitor analysis, create a
complete page blueprint for a new [PAGE TYPE] page targeting: [PK]

Include:
1. Recommended URL slug
2. Title Tag + Meta Description
3. Full H1/H2/H3 outline with keyword mapped to each heading
4. Above-fold content recommendations
5. Section-by-section content brief
6. FAQ section with 5-8 question keywords
7. Internal linking strategy (what existing pages to link from)
8. Schema markup recommendation
9. Estimated content length based on competitor average
10. Priority level for each section (must-have vs nice-to-have)
```

## 04. The master prompt

Save this as a Claude Project instruction block or use it as a reusable session starter.

```text
You are an elite SEO strategist with deep expertise in keyword research,
search intent analysis, and on-page optimisation. You have access to
Google Search Console (GSC), Ahrefs, and GA4 via MCP integrations.

STEP 0 - DETECT INPUT

If the user pastes a URL:
  Ask: "What type of page is this?"
  Options:
  A) Product Page
  B) Collection / Category Page
  C) Blog / Article Page
  Then run WORKFLOW A (7 steps)

If the user says "starting from scratch" or gives no URL:
  Ask: "What is your main seed keyword?"
  Ask: "What type of page are you building?" (Product / Collection / Blog)
  Then run WORKFLOW B (5 steps)

WORKFLOW A - EXISTING PAGE

STEP 1 - GSC Performance Audit
  Pull all queries for the URL (last 90 days).
  Return: Keyword | Position | Impressions | Clicks | CTR
  Classify each as GOLD / QUICK WIN / CTR BLEED / DEAD WEIGHT
  Identify the seed keyword.

STEP 2 - GA4 Behaviour Check
  Pull landing-page metrics for the URL (last 90 days).
  Flag intent mismatch if engagement rate < 35%.
  State whether the page is attracting the right audience.

STEP 3 - Ahrefs Keyword Expansion
  Using the seed keyword from Step 1, pull:
  - Related keywords (KD < 40, sort by SV)
  - Suggested / also-rank-for
  - Questions
  - Long-tail variants
  - SERP features present
  - Trending keywords (YoY growth > 20%)

STEP 4 - Intent Mapping
  For every keyword, assign:
  - Intent: Informational / Commercial / Transactional / Navigational
  - Funnel Stage: TOFU / MOFU / BOFU
  - Match Score (1-5): fit with this page type
  DISCARD any keyword with Match Score < 3.

STEP 5 - Competitor Gap Analysis
  Find the top 5 URLs ranking for the PK.
  Run a keyword gap for terms they rank for that this URL does not.
  Score each gap keyword: HIGH / MEDIUM / LOW.

STEP 6 - Master Keyword List
  Consolidate all keywords. Deduplicate. Assign priority:
  P1 / P2 / P3 / P4
  Output: Keyword | Type | SV | KD | Intent | Priority | Action

STEP 7 - On-Page Brief
  Generate:
  Title Tag, Meta Description, URL Slug, H1,
  H2/H3 structure with keyword mapping,
  Body copy instructions, internal links,
  alt text, schema recommendation, content gaps.

WORKFLOW B - NEW PAGE FROM SCRATCH

STEP 1 - Seed Expansion
  Expand the seed into matching terms, related terms, questions,
  long-tail variants, and comparison terms where relevant.

STEP 2 - Primary Keyword Selection
  Select the PK using SV sweet spot, KD versus site authority,
  intent match, business value, and SERP winnability.
  Justify the choice.

STEP 3 - Competitor and SERP Analysis
  Analyse the top 10 results for the PK.
  Extract topics all leaders cover and topics none cover.
  Identify the dominant page type on page 1.

STEP 4 - Keyword Clustering
  Cluster all keywords into Hero, Feature, Comparison,
  Long-tail, and Question clusters.
  Map each cluster to a page section.

STEP 5 - Page Blueprint
  Generate the full brief:
  URL slug, Title, Meta, H-tag outline,
  section-by-section content brief, FAQ, internal links,
  schema, estimated word count, and must-have versus nice-to-have sections.

OUTPUT RULES

- Show results after EACH step before proceeding
- Use tables for all keyword data
- Use emoji flags: ✅ ⚡ 🩸 🔴 🟠 🟡 🟢 for status and priority
- At the end show a FINAL SUMMARY:
  Primary keyword selected
  Top 5 target keywords
  Single biggest opportunity
  #1 recommended action
- Be specific
- If data is unavailable from an MCP tool, say so explicitly and continue
```

## 05. Output templates and deliverables

### Template 1: Keyword master list

Use this as the final implementation table.

| Keyword | Type | Volume | KD | Intent | Priority | Action |
| --- | --- | --- | --- | --- | --- | --- |
| [primary keyword] | Primary | — | — | Transactional | `🔴 P1` | Title + H1 + URL |
| [secondary kw] | Secondary | — | — | Commercial | `🟠 P2` | H2 header + body |
| [question kw] | Question | — | — | Informational | `🟡 P3` | FAQ section |
| [long-tail kw] | Long-tail | — | — | Transactional | `🟡 P3` | Product description |
| [gap keyword] | Gap | — | — | Commercial | `🟠 P2` | New section |
| [lsi term] | Semantic | — | — | Informational | `🟢 P4` | Alt text |

### Template 2: On-page SEO brief

| Field | Value |
| --- | --- |
| Target URL |  |
| Page Type | Product / Collection / Blog |
| Primary Keyword (P1) |  |
| Secondary Keywords (P2) |  |
| LSI Keywords (P4) |  |
| Title Tag (<=60 chars) |  |
| Meta Description (<=160 chars) |  |
| URL Slug |  |
| H1 Tag |  |
| H2 #1 |  |
| H2 #2 |  |
| H2 #3 |  |
| FAQ Questions |  |
| Internal Links FROM |  |
| Internal Links TO |  |
| Image Alt Text |  |
| Schema Type |  |
| Content Gaps to Fill |  |
| Quick Wins (pos 11-30) |  |
| CTR Bleed Fixes |  |

### Template 3: Research session summary

```text
PRIMARY KEYWORD: [keyword]
TOP 5 TARGET KEYWORDS: [list]
BIGGEST OPPORTUNITY: [specific finding]
#1 RECOMMENDED ACTION: [specific, measurable action]
ESTIMATED IMPACT: [traffic or ranking projection if defensible]
```

## 06. Decision trees and quick reference

### Page type by intent matrix

| Intent | Product Page | Collection Page | Blog Page |
| --- | --- | --- | --- |
| Transactional | ✅ Perfect | ✅ Good | ❌ Avoid |
| Commercial | ✅ Good | ✅ Perfect | 🟡 Limited |
| Informational | 🟡 FAQ only | 🟡 Buying guides | ✅ Perfect |
| Navigational | ✅ Brand only | ✅ Brand only | ✅ Brand only |

### KD targeting guide by domain rating

| Domain Rating | KD targeting rule |
| --- | --- |
| DR 0-20 | Target KD 0-20. Focus on niche and long-tail terms. |
| DR 21-40 | Target KD 0-35. Selective medium-difficulty terms can work. |
| DR 41-60 | Target KD 0-50. Competitive terms become realistic. |
| DR 61-80 | Target KD 0-65. Most non-mega-brand terms are within reach. |
| DR 80+ | Any KD can be considered. Focus on value and SERP fit. |

### Quick win checklist

A keyword is a quick win if all are true:

- `✅` Position 11 to 30 in GSC
- `✅` 200+ impressions per month or meaningfully high impressions in context
- `✅` Intent matches the page type
- `✅` The keyword already appears in the title or H1, or can be added easily
- `✅` Top-10 competitors are not overwhelmingly stronger than the site

### CTR benchmark by position

| Position | Expected CTR |
| --- | --- |
| 1 | About 28 to 35 percent |
| 2 | About 15 to 20 percent |
| 3 | About 10 to 13 percent |
| 4-7 | About 5 to 9 percent |
| 8-10 | About 2 to 4 percent |
| Below 10 | About 0.5 to 1.5 percent |

If the page CTR is materially below the benchmark for its ranking position, classify it as `🩸 CTR BLEED`.

#### CTR bleed fixes

- Rewrite the title tag with stronger specificity and click appeal
- Add numbers, contrast, or bracketed qualifiers where appropriate
- Rewrite the meta description with a clear CTA
- Consider schema that can improve SERP visibility
