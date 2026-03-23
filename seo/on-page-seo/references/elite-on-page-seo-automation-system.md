# Elite On-Page SEO Automation System

Human-first workflow, rules, and prompt library for data-driven on-page SEO using Claude with Google Search Console, GA4, SERP analysis, Ahrefs, Keyword Planner, and Google Trends.

## Table of contents

- [01. System overview](#01-system-overview)
- [02. The 5-phase workflow](#02-the-5-phase-workflow)
- [03. Step-by-step workflow](#03-step-by-step-workflow)
- [04. On-page priority matrix](#04-on-page-priority-matrix)
- [05. Human-first system prompt](#05-human-first-system-prompt)
- [06. Element and copy rules](#06-element-and-copy-rules)
- [07. Prompt library](#07-prompt-library)
- [08. Data formatting guides](#08-data-formatting-guides)
- [09. Anti-cannibalization protocol](#09-anti-cannibalization-protocol)
- [10. Quick reference checklists](#10-quick-reference-checklists)
- [11. E-E-A-T signal guidelines](#11-e-e-a-t-signal-guidelines)
- [12. Glossary](#12-glossary)

## 01. System overview

### What this system does

This framework turns raw SEO inputs into publication-ready, human-first on-page recommendations. It is designed to improve rankings, CTR, intent alignment, content depth, and internal linking without keyword stuffing or robotic copy.

### Target outcomes

- Clear primary keyword targeting per page
- Stronger CTR from better title tags and meta descriptions
- Better intent alignment between the page and the SERP
- Deeper topical coverage than competing pages without padding
- Fewer cannibalization issues
- Stronger E-E-A-T and trust signals where needed

### Data source roles

- Google Search Console: live query data, impressions, CTR, average position, and quick wins
- Google Analytics 4: behavior signals such as engagement time, drop-off points, and conversion context
- SERP analysis: intent validation, heading patterns, PAA questions, and content formats
- Ahrefs: keyword difficulty, competitor URLs, rankings, and link context
- Keyword Planner: search volume and competition estimates
- Google Trends: seasonality and rising-topic validation

## 02. The 5-phase workflow

Complete each phase in sequence. Data from earlier phases informs later ones.

### Phase 01: Keyword intelligence extraction

Sources: GSC, Ahrefs, Keyword Planner, Google Trends, SERP analysis

- Pull GSC queries for the target URL, including impressions, CTR, and average position
- Identify position 4 to 20 quick-win keywords with meaningful impression demand
- Cross-reference those terms with Ahrefs KD and volume data when available
- Validate search intent using SERP evidence and Trends
- Flag cannibalization between similar URLs
- Map one primary keyword, 2 to 3 secondary keywords, and 5 to 8 semantic terms

### Phase 02: Competitor SERP deconstruction

Sources: Ahrefs, SERP analysis, Claude

- Extract the top-ranking URLs for the target keyword
- Analyze heading structure, content depth, entities, and subtopics
- Identify product types, proof points, FAQs, and snippet formats competitors cover
- Map featured snippet opportunities such as paragraph, list, or table
- Collect recurring terms or entities appearing across multiple competitors

### Phase 03: On-page element optimization

Sources: Claude, GSC, Ahrefs, SERP analysis

- Generate a title tag that uses the primary keyword once and leads with a real benefit or USP
- Write a natural meta description that mentions what the page offers and why to click
- Restructure the H1 so it supports the title without duplicating it
- Rewrite H2s around real subtopics, not keyword variations
- Review the URL slug and decide whether to keep it or replace it
- Recommend schema markup such as FAQ, Article, CollectionPage, Product, or HowTo

### Phase 04: Content architecture and depth

Sources: Claude, Google Trends, GA4, competitor analysis

- Build an outline that beats competitors on depth by roughly 20 percent without padding
- Add semantic entities and missing subtopics
- Insert E-E-A-T signals such as expert commentary, studies, policies, or first-hand experience
- Optimize the intro so the primary keyword appears in the first sentence and the copy still reads naturally
- Add a GSC-led FAQ section or use PAA questions when GSC query data is unavailable
- Suggest internal links with descriptive anchors and destination logic

### Phase 05: Performance tracking and iteration

Sources: GSC, GA4, Ahrefs

- Log the baseline: position, impressions, CTR, traffic, and engagement where available
- Set 14-day and 30-day review checkpoints
- Monitor GSC impression spikes after publishing as a reindex signal
- Track rank movement and CTR changes
- Re-run the optimization if no improvement appears after 30 days
- A/B test title angles when CTR lags impressions

## 03. Step-by-step workflow

Follow these steps in order for every page.

### 1. Data aggregation sprint

- Start with the human-first system prompt in section 05
- Gather the current page elements, GSC queries, baseline metrics, and competitor evidence
- If Ahrefs is unavailable, capture a manual SERP summary instead

### 2. Keyword mapping decision

- Assign 1 primary keyword
- Assign 2 to 3 secondary keywords
- Assign 5 to 8 semantic terms
- Check for cannibalization risk before proceeding
- Confirm search intent before rewriting any page element

### 3. SERP gap analysis

- Review the top 3 to 5 competitor URLs or a structured SERP summary
- Identify missing topics, proof points, questions, and content formats
- Save the gap findings for Phase 4

### 4. On-page elements rewrite

- Use the on-page optimizer prompt
- Generate title tag, meta description, H1, H2 structure, URL slug verdict, schema type, and intro paragraph
- Validate each element against the over-optimization checklist

### 5. Content enhancement

- Use the content architecture prompt
- Produce a revised outline that fills all identified gaps
- Add FAQ, internal linking suggestions, and E-E-A-T improvements
- Mark where images, tables, comparison blocks, or proof elements should appear

### 6. Publish and log baseline

- Run the pre and post checklist
- Log baseline GSC position, impressions, CTR, and GA4 engagement metrics
- Submit the URL for reindexing in GSC after publishing

### 7. Performance loop

- At 14 days, check for impression and CTR movement
- At 30 days, compare updated GSC and Ahrefs data
- Re-run the workflow for pages still underperforming or still misaligned with intent

## 04. On-page priority matrix

Always fix P1 elements before P2 or P3.

| On-page element | SEO impact | Effort | Primary evidence | Priority |
| --- | --- | --- | --- | --- |
| Title tag | High | Low | GSC CTR | P1 - Do first |
| Meta description | Medium | Low | GSC CTR | P1 - Do first |
| H1 tag | High | Low | GSC + SERP | P1 - Do first |
| H2 / H3 structure | High | Medium | SERP | P1 - Do first |
| Content depth | High | High | Competitors | P2 - Important |
| URL slug | Medium | Low | Page architecture | P2 - Important |
| Schema markup | Medium | Medium | SERP features | P2 - Important |
| Internal links | High | Medium | Site structure | P2 - Important |
| Image alt text | Low | Low | Accessibility review | P3 - Batch later |
| FAQ section | Medium | Low | GSC / PAA | P3 - Batch later |
| E-E-A-T signals | High | Medium | Topic risk | P2 - Important |

Triage rule: always fix P1 elements first. A better title tag or H1 can improve CTR or intent alignment faster than deeper rewrites.

## 05. Human-first system prompt

Use this at the start of a fresh SEO session if you want the exact standalone prompt outside the skill itself.

```text
SYSTEM PROMPT [START OF EVERY SESSION]
You are an expert on-page SEO strategist. You write for humans first and search engines second. Your recommendations must feel natural, brand-appropriate, and never over-optimized.

Core philosophy
- Natural language first. If a title tag, meta description, H1, or paragraph sounds robotic, rewrite it.
- Never repeat the same keyword or close synonym more than once in any single title tag, meta description, or H1.
- Spread keyword targets across elements. Use the primary keyword in the title tag, a close synonym in the H1 when useful, and long-tail variations in H2s and body copy.
- Benefits and USPs beat keyword repetition. Prefer one keyword plus a genuine differentiator over stacked synonyms.
- Ground every recommendation in real data. Use GSC as ground truth when sources conflict. When Ahrefs is unavailable, use GSC plus SERP analysis.
- Label assumptions clearly. Never invent search volume, CTR, rankings, or traffic.

Required output
1. Snapshot - goal, URL, intent, cannibalization status, key metrics, missing inputs
2. Keyword map - primary, secondary, semantic terms, quick wins with GSC evidence
3. Priority fixes - P1, P2, P3 with current vs proposed and rationale
4. Ready-to-publish rewrites - title, meta, H1, H2 structure, intro paragraph, slug verdict
5. Content improvements - gaps, FAQ ideas, internal links, schema, E-E-A-T
6. Measurement plan - baselines, 14-day check, 30-day review, title test ideas
7. Implementation checklist - prioritized tasks with effort and impact ratings

Final validation
- Confirm the title does not repeat the keyword or close synonym.
- Confirm the meta description reads like a sentence, not a keyword list.
- Confirm the H1 is not a copy of the title tag.
- Confirm the intro is genuinely useful to the reader.
- Confirm H2s are real section headings, not keyword variations.
- Confirm FAQ questions come from real user demand when data exists.
```

## 06. Element and copy rules

Apply these rules when rewriting page elements.

### Title tag rules

- Formula: `[Root Keyword] | [Benefit or USP] | [Brand Name]`
- Maximum 60 characters
- Place the root keyword once at the front
- Use a close synonym only if it reads naturally and does not feel repetitive
- Use the standard three-part format with two pipe separators; do not add extra separators or hyphen lists
- Include one genuine benefit, USP, or differentiator
- Avoid filler words such as `Best`, `Top`, or `Premium` unless the data supports them
- If the full formula is too long, shorten the USP before changing the structure

Good examples:

- `Dog Leashes | Durable & Comfortable | EzyDog`
- `Dog Harnesses | Shock Absorbing & No-Pull | EzyDog`

Bad examples:

- `Dog Leashes & Leads Australia | Shop EzyDog Leashes`
- `Dog Leashes - Dog Leads - Dog Walking Leash | EzyDog`

### Meta description rules

- Formula: what the page offers + key product types or categories + trust signal or soft CTA
- Maximum 155 characters
- Use the primary keyword once in the first sentence
- Use a close synonym once only if it reads naturally
- Mention 2 to 3 specific product types, use cases, or categories
- End with a trust signal or soft CTA
- Write a complete sentence, not a keyword list
- Never start with `Shop` or `Buy`

Good example:

- `EzyDog dog leashes are built for Aussie adventures. Shock absorbing, hands-free & training leads for all breeds. 1-year warranty.`

Bad example:

- `Shop dog leashes and dog leads. Best dog leash Australia. Dog lead for walking, training, running. Buy dog leash online now.`

### H1 rules

- Use one H1 only
- Keep it close to the primary keyword while varying it from the title tag
- Prefer 2 to 6 words for collection pages and up to 10 words for articles
- If the title uses the primary keyword, the H1 can use the close synonym or a natural variation
- Never duplicate the title tag word for word

### H2 and H3 structure rules

- Each H2 should target a different subtopic or long-tail cluster
- Phrase H2s as genuine section titles a human would expect
- Cover missing competitor topics, proof points, use cases, and decision criteria
- Use H3s for subsections inside an H2, not as slight keyword variations
- Avoid stuffing the target keyword into every heading

### Body content rules

- Put the primary keyword in the first sentence of the intro
- Use the close synonym within the first 100 words only if it reads naturally
- Integrate semantic terms throughout the page without forcing them
- Match the depth and format to the page intent: commercial pages need buying confidence; informational pages need depth and expertise
- Remove paragraphs that exist only to carry keywords
- Aim to beat competitors on coverage by about 20 percent without padding

### FAQ rules

- Base FAQ questions on real GSC query data whenever possible
- If GSC is missing, use PAA or SERP evidence and label the source
- Write questions the way users would actually ask them
- Keep answers to 2 to 4 sentences and answer directly
- Add internal links where genuinely helpful
- Recommend `FAQPage` schema when the final FAQ block qualifies

### Internal linking rules

- Use descriptive anchor text, not `click here` or raw URLs
- Link to the most relevant page, not the easiest page
- Vary anchor text naturally for the same destination
- Use 3 to 5 internal links for collection pages and 5 to 8 for long-form content
- Prioritize pages that need authority, such as new pages or underperformers

### Data rules

- Ground every recommendation in real data from GSC, GA4, SERP analysis, Ahrefs, Keyword Planner, or Google Trends
- Never invent search volume, CTR, rankings, or traffic
- Use GSC as the ground truth when sources conflict
- Label assumptions clearly
- When Ahrefs is unavailable, use GSC plus SERP analysis as the primary evidence set

## 07. Prompt library

Use these prompts verbatim when you want exact reusable prompt blocks.

### Prompt 1: Keyword intelligence

```text
KEYWORD INTELLIGENCE EXTRACTION [PHASE 1]
You are an expert on-page SEO strategist.
Analyze the following data for the URL: [TARGET URL]

GSC DATA: [paste queries, impressions, CTR, position]
AHREFS DATA: [paste keyword rankings + KD + volume, if available]
KW PLANNER: [paste monthly search volume + competition, if available]
TRENDS DATA: [paste 12-month trend for main topic, if available]
SERP SUMMARY: [paste manual SERP notes if Ahrefs is unavailable]

Output:
1. PRIMARY keyword (best opportunity)
2. SECONDARY keywords (2-3, supporting intent)
3. SEMANTIC terms (5-8 terms)
4. Keyword cannibalization risk (yes/no + URLs)
5. Quick-win opportunities (position 4-20 terms with meaningful impressions)
6. Search intent classification (informational/commercial/transactional)
7. Assumptions or missing inputs
```

### Prompt 2: Competitor gap analysis

```text
COMPETITOR SERP GAP ANALYSIS [PHASE 2]
Act as an expert SEO content analyst.

MY PAGE URL: [URL]
MY CURRENT CONTENT: [paste or summarize current content]
TOP COMPETITOR URLS:
  - [Competitor 1 URL]
  - [Competitor 2 URL]
  - [Competitor 3 URL]
TARGET KEYWORD: [primary keyword]
SEARCH INTENT: [informational/commercial/transactional]

Produce a structured gap report:
- Topics my page misses vs competitors
- Entities, proof points, or decision criteria not covered
- Content formats I should add (tables, FAQs, comparisons, trust blocks, etc.)
- Average word count of competitors vs mine, if known
- Recurring terms or entities appearing across 2+ competitor pages
- Featured snippet opportunity (yes/no + format)
```

### Prompt 3: On-page elements optimizer

```text
ON-PAGE ELEMENTS OPTIMIZER [PHASE 3]
You are an expert on-page SEO strategist. Write for humans first and search engines second.

PRIMARY KEYWORD: [keyword]
SECONDARY KEYWORDS: [keyword2, keyword3]
SEARCH INTENT: [informational/commercial/transactional]
CURRENT TITLE: [current title tag]
CURRENT META: [current meta description]
CURRENT H1: [current H1]
PAGE TOPIC: [brief description]
BRAND NAME: [brand]
CURRENT URL SLUG: [slug]

Rules:
- Title tag: [Root Keyword] | [Benefit or USP] | [Brand Name], max 60 chars, primary keyword once at front
- Meta description: max 155 chars, primary keyword once in the first sentence, mention 2-3 specific types or categories, end with a trust signal or soft CTA, never start with Shop or Buy
- H1: one H1 only, not identical to the title tag
- H2s: each H2 covers a different subtopic or long-tail cluster
- Intro: primary keyword in the first sentence, close synonym within the first 100 words only if natural
- Avoid repeating the same keyword or close synonym more than once in any single title, meta, or H1

Return:
1. TITLE TAG + character count
2. META DESCRIPTION + character count
3. H1
4. H2 STRUCTURE
5. URL SLUG VERDICT (keep/update + proposed slug if needed)
6. SCHEMA recommendation
7. INTRO PARAGRAPH
```

### Prompt 4: Content architecture builder

```text
CONTENT ARCHITECTURE & DEPTH [PHASE 4]
Act as a topical authority content strategist.

TARGET KEYWORD: [keyword]
CONTENT GAPS IDENTIFIED: [paste from gap analysis]
COMPETITOR AVG WORD COUNT: [number, if known]
MY CURRENT WORD COUNT: [number, if known]
GSC QUERY THEMES: [paste notable query clusters if available]
PAGE TYPE: [collection/product/article/service]

Create a winning content outline that:
- Beats competitors by about 20% on depth and usefulness without padding
- Fills all identified gaps
- Includes FAQ questions sourced from GSC queries when available
- Includes 3-5 internal link suggestions for collection pages or 5-8 for long-form pages
- Adds 2-3 E-E-A-T signals
- Marks where to add images, tables, comparison blocks, reviews, or proof elements
- Ends with a strong conversion or engagement CTA
```

### Prompt 5: Performance review

```text
POST-OPTIMIZATION PERFORMANCE REVIEW [PHASE 5]
You are an SEO performance analyst.
Compare these two data sets:

BASELINE (pre-optimization):
  - GSC Position: [X]
  - GSC Impressions: [X]
  - GSC CTR: [X%]
  - Organic Traffic: [X/month]

CURRENT (post-optimization, 30 days later):
  - GSC Position: [X]
  - GSC Impressions: [X]
  - GSC CTR: [X%]
  - Organic Traffic: [X/month]

Analyze:
1. Improvement or regression assessment
2. If no improvement: likely root causes
3. Next 3 specific actions to improve ranking
4. Title tag A/B test suggestion based on CTR data
```

### Prompt 6: Internal link audit

```text
INTERNAL LINK ARCHITECTURE AUDIT [BONUS]
Act as a technical SEO and internal linking specialist.

TARGET PAGE: [URL + topic summary]
SITE STRUCTURE (pillar pages): [list your main categories]
RELATED CONTENT URLS:
  - [URL1 - topic]
  - [URL2 - topic]
  - [URL3 - topic]

Provide:
1. Which pages should link to this page (with anchor text)
2. Which pages this page should link out to (with anchor text)
3. Anchor text variations (exact, partial, branded, generic)
4. Any anchor text over-optimization risks
5. Breadcrumb or navigation recommendation
```

## 08. Data formatting guides

Use these formats to keep inputs consistent and grounded.

### GSC data format

Navigate to: GSC -> Performance -> Pages -> click target URL -> Queries

```text
GSC DATA for [YOUR URL]:
Query                       | Impressions | Clicks | CTR  | Avg Position
"best keyword example"      | 12,400      | 340    | 2.7% | 11.3
"related keyword"           | 8,200       | 180    | 2.2% | 14.8
"long tail keyword phrase"  | 3,100       | 210    | 6.8% | 6.2
[continue for top queries]
```

### Ahrefs data format

Navigate to: Site Explorer -> enter URL -> Organic Keywords

```text
AHREFS KEYWORD DATA for [URL]:
Keyword            | Volume | KD | Position | URL
"primary keyword"  | 18,000 | 42 | 8        | /your-page
"secondary term"   | 5,400  | 28 | 15       | /your-page
```

```text
AHREFS COMPETITOR URLS for "[target keyword]":
1. https://competitor1.com/page
2. https://competitor2.com/page
3. https://competitor3.com/page
```

### SERP summary format

Use this when Ahrefs is unavailable.

```text
SERP SUMMARY for "[target keyword]":
- Search intent:
- Top ranking page types:
- Common H2 themes:
- Common product types / proof points:
- PAA questions:
- Featured snippet format:
- Notes on title tag patterns:
```

### GA4 behavior data format

Navigate to: GA4 -> Reports -> Engagement -> Pages and Screens

```text
GA4 BEHAVIOR DATA for [URL]:
- Monthly Organic Sessions: 1,240
- Avg. Engagement Time: 1m 43s
- Engaged Sessions: 38%
- Scroll Depth: 45% avg
- Top Exit Section: [section name if tracked]
```

### Batch triage format

Use this first when optimizing 10 or more pages.

```text
BATCH PAGE TRIAGE [MULTI-PAGE]
Here is my GSC data for [N] pages. Rank them by optimization
priority using this scoring system:

- Positions 4-10 with strong impressions = HIGH PRIORITY
- Positions 11-20 with clear demand = MEDIUM PRIORITY
- Positions 1-3 = MAINTENANCE ONLY
- Positions 20+ with low impressions = LOW PRIORITY

[paste your full GSC page performance data]

Output: ranked priority list with one recommended action per page.
```

## 09. Anti-cannibalization protocol

Run this before any page optimization.

```text
CANNIBALIZATION CHECK [RUN BEFORE EVERY OPTIMIZATION]
I'm about to optimize a page targeting: "[primary keyword]"

Here are all pages on my site currently ranking for related terms:
[paste GSC data showing URL + ranking queries]

Check:
1. Are multiple URLs competing for the same or similar queries?
2. Which URL should be the canonical page for this keyword?
3. What should happen to competing pages? Options:
   - Consolidate: 301 redirect to canonical
   - Differentiate: change focus to different intent
   - Internal link: from secondary to primary
   - Keep both: if confirmed different intent
```

Warning: never optimize two pages for the same primary keyword at the same time. Resolve overlap first.

### Decision framework

- Same keyword plus same intent -> consolidate
- Same keyword plus different intent -> differentiate
- Similar keywords plus different intent -> keep both
- Thin page cannibalizing a rich page -> redirect the thin page and fold useful content into the stronger page

## 10. Quick reference checklists

### Pre-optimization checklist

- Identify the target URL and pull GSC data for the last 90 days
- Pull Ahrefs keyword rankings and top competitor URLs, or prepare a SERP summary
- Run the cannibalization check before proceeding
- Log baseline metrics: position, impressions, CTR, and GA4 organic traffic
- Confirm intent: informational, commercial, or transactional
- Identify any schema type already in use

### On-page elements checklist

- Title tag: at or under 60 characters, primary keyword near the start, one real USP, no keyword repetition
- Meta description: at or under 155 characters, reads like a sentence, includes product or content specifics, ends with trust or CTA
- H1: one H1 only, distinct from the title tag, aligned to intent
- H2s: full topic coverage, real section headings, no keyword stuffing
- URL slug: concise, lowercase, hyphenated, and worth changing only if there is a clear benefit
- First 100 words: primary keyword in the first sentence, close synonym only if natural
- Schema markup: appropriate type added
- Internal links: descriptive anchors, relevant destinations, natural variation
- FAQ section: based on GSC or PAA questions with concise answers

### Over-optimization checklist

- [ ] Does the title tag repeat any word or close synonym more than once?
- [ ] Does the meta description read like a natural sentence, not a keyword list?
- [ ] Is the H1 different from the title tag?
- [ ] Would a real user find the intro paragraph helpful?
- [ ] Are H2s written as genuine section headings, not keyword variations?
- [ ] Does the FAQ answer real questions instead of restating keywords as questions?
- [ ] If I read the page aloud, would it sound natural?

### Post-optimization checklist

- Submit the URL for reindexing in GSC
- Confirm changes are live and render correctly
- Log the optimization date and baseline metrics
- Set a 14-day reminder for impression or CTR movement
- Set a 30-day reminder for a full performance review
- Update internal links from related pages

## 11. E-E-A-T signal guidelines

Use this add-on for pages that need stronger trust and authority signals, especially YMYL pages.

```text
E-E-A-T SIGNAL ENHANCEMENT [PHASE 4 ADD-ON]
Review this content and identify where to add E-E-A-T signals.

CONTENT: [paste article or outline]
TOPIC CATEGORY: [YMYL / General / Technical]
SITE AUTHORITY: [describe your credentials/expertise]

Add the following E-E-A-T improvements:
1. EXPERIENCE: Where to add first-hand experience statements
2. EXPERTISE: Where to cite credentials, certifications, or studies
3. AUTHORITY: Which external authoritative sources to cite
4. TRUST: Where to add data points, dates, and accuracy statements
5. AUTHOR BIO: Draft a 50-word author bio reflecting expertise
6. FRESHNESS: Mark 3 sections to update with the most current data
```

### E-E-A-T signal types

- Experience: first-hand accounts, case studies, original data, personal anecdotes, test results
- Expertise: credentials, certifications, industry experience, qualifications, titles
- Authority: external citations, authoritative mentions, strong backlinks
- Trust: accurate statistics, citations, updated dates, privacy and contact signals

Important: for YMYL topics such as health, finance, legal, or safety, add expert authorship, authoritative citations, and a clear last-updated date before calling the page publish-ready.

## 12. Glossary

| Term | Definition |
| --- | --- |
| CTR | Click-through rate: the percentage of impressions that result in a click |
| KD | Keyword Difficulty: Ahrefs score from 0 to 100 estimating ranking difficulty |
| Semantic terms | Closely related terms and entities that reinforce page context |
| E-E-A-T | Experience, Expertise, Authoritativeness, Trustworthiness |
| SERP | Search engine results page |
| Cannibalization | Multiple site pages competing for the same keyword intent |
| Schema | Structured data markup, often JSON-LD, for rich results |
| PAA | People Also Ask question boxes in Google results |
| Topical authority | Comprehensive subject coverage that improves trust and rankings |
| YMYL | Your Money or Your Life content affecting health, finance, legal, or safety |

Elite On-Page SEO Automation System

Powered by Claude, Ahrefs, GSC, GA4, Keyword Planner, and Google Trends.
