# Elite On-Page SEO Automation System

Complete workflow, instructions, and prompt library for data-driven on-page SEO using Claude with Ahrefs, Google Search Console, GA4, Keyword Planner, and Google Trends.

## Table of contents

- [01. System overview](#01-system-overview)
- [02. The 5-phase workflow](#02-the-5-phase-workflow)
- [03. Step-by-step workflow](#03-step-by-step-workflow)
- [04. On-page priority matrix](#04-on-page-priority-matrix)
- [05. Master system prompt](#05-master-system-prompt)
- [06. Prompt library](#06-prompt-library)
- [07. Data formatting guides](#07-data-formatting-guides)
- [08. Anti-cannibalization protocol](#08-anti-cannibalization-protocol)
- [09. Quick reference checklists](#09-quick-reference-checklists)
- [10. E-E-A-T signal guidelines](#10-e-e-a-t-signal-guidelines)
- [11. Glossary](#11-glossary)

## 01. System overview

### What this system does

This framework orchestrates five SEO data sources through precise Claude prompting to produce publication-ready, rank-focused on-page optimizations. It is designed to move an underperforming page from raw data to a full optimization plan in under 30 minutes.

### Target outcomes

- Target: top 3 SERP position
- Goal: +40% click-through rate
- Goal: 95+ content relevance score
- Goal: under 3 minutes per page after the system is fully operational
- Goal: zero cannibalization issues
- Goal: full E-E-A-T compliance

### Data source roles

- Ahrefs: keyword difficulty, competitor analysis, backlink data, rank tracking, SERP analysis
- Google Search Console: real query impressions, CTR, average position per page, and fastest win opportunities
- Google Analytics 4: user behavior signals including engagement time, drop-off patterns, and segmentation
- Keyword Planner: monthly search volume, competition levels, bid estimates, and related term discovery
- Google Trends: seasonality, rising topics, geographic demand, and trend validation

## 02. The 5-phase workflow

Complete each phase in sequence. Data from earlier phases informs later ones.

### Phase 01: Keyword intelligence extraction

Sources: Ahrefs, GSC, Keyword Planner, Google Trends

- Pull GSC queries for the target URL, including impressions, CTR, and average position
- Identify position 4 to 20 quick-win keywords with 500+ impressions
- Cross-reference those terms with Ahrefs KD and volume data
- Validate search intent using Trends and SERP evidence
- Flag cannibalization between similar URLs
- Map primary, secondary, and LSI keywords per page

### Phase 02: Competitor SERP deconstruction

Sources: Ahrefs and Claude

- Extract the top 5 ranking URLs for each target keyword via Ahrefs
- Analyze average word count, heading structure, and content depth
- Identify entities, topics, and subtopics competitors cover
- Map featured snippet opportunities such as paragraph, list, or table
- Extract NLP terms appearing across 2 or more competitor pages
- Identify People Also Ask questions for FAQ inclusion

### Phase 03: On-page element optimization

Sources: Claude, GSC, Ahrefs

- Generate an optimized title tag with keyword-first emphasis and a 60-character ceiling
- Write a compelling meta description with a 155-character ceiling and a CTA
- Restructure the H1 to match the primary keyword and search intent
- Rewrite H2s with semantic coverage across the topic
- Optimize the URL slug to be concise, keyword-rich, and free of stop words
- Recommend schema markup such as FAQ, Article, or HowTo

### Phase 04: Content architecture and depth

Sources: Claude, Google Trends, GA4

- Build an enhanced outline that beats competitors on depth by about 20%
- Add semantic entities missing from the original content
- Insert E-E-A-T signals such as stats, expert viewpoints, and citations
- Optimize the intro with a hook and keyword placement in the first 100 words
- Add a PAA-based FAQ section with 5 questions
- Suggest 3 to 5 relevant internal link anchors

### Phase 05: Performance tracking and iteration

Sources: GA4, GSC, Ahrefs

- Log the baseline: position, impressions, CTR, and traffic
- Set 14-day and 30-day review checkpoints
- Monitor GSC impressions spikes after publishing as a reindex signal
- Track rank movement in Ahrefs Rank Tracker
- Re-run the optimization if no improvement appears after 30 days
- A/B test title tags using GSC CTR data

## 03. Step-by-step workflow

Follow these 7 steps in order for every page. Typical time: 25 to 30 minutes per page.

### 1. Data aggregation sprint

Time: about 5 minutes

- Start with the master system prompt in section 05
- Provide four core inputs: GSC data, Ahrefs rankings, Keyword Planner volumes, and Google Trends data

### 2. Keyword mapping decision

Time: about 2 minutes

- Assign 1 primary keyword
- Assign 2 to 3 secondary keywords
- Assign 5 to 8 LSI or semantic terms
- Check for cannibalization risk before proceeding

### 3. SERP gap analysis

Time: about 3 minutes

- Paste the top 3 to 5 competitor URLs from Ahrefs
- Run the competitor gap analysis prompt
- Save the output for Phase 4

### 4. On-page elements rewrite

Time: about 5 minutes

- Use the on-page optimizer prompt
- Generate title tag, meta description, H1, H2 structure, URL slug, schema type, and intro paragraph

### 5. Content enhancement

Time: about 10 minutes

- Use the content architecture prompt
- Produce a revised outline that fills all identified gaps
- Include a 5-question FAQ section
- Include internal linking suggestions and E-E-A-T data points

### 6. Publish and log baseline

Time: about 2 minutes

- Run the pre and post checklist
- Log baseline GSC position, impressions, and CTR
- Set reminders for 14-day and 30-day reviews
- Submit the URL for reindexing in GSC after publishing

### 7. Performance loop

Time: ongoing

- At 14 days, check for a GSC impressions spike
- At 30 days, compare updated GSC and Ahrefs data
- Re-run the full workflow for pages still underperforming

## 04. On-page priority matrix

Always fix P1 elements before P2 or P3.

| On-page element | SEO impact | Effort | Data source | Priority |
| --- | --- | --- | --- | --- |
| Title tag | High | Low | GSC CTR | P1 - Do first |
| Meta description | Medium | Low | GSC CTR | P1 - Do first |
| H1 tag | High | Low | Ahrefs | P1 - Do first |
| H2 / H3 structure | High | Medium | SERP | P1 - Do first |
| Content depth | High | High | Competitors | P2 - Important |
| URL slug | Medium | Low | Keyword Planner | P2 - Important |
| Schema markup | Medium | Medium | Claude | P2 - Important |
| Internal links | High | Medium | Ahrefs | P2 - Important |
| Image alt text | Low | Low | Claude | P3 - Batch later |
| FAQ section | Medium | Low | PAA / Trends | P3 - Batch later |
| E-E-A-T signals | High | Medium | Claude | P3 - Batch later |

Triage rule: always fix P1 elements first. A better title tag alone can improve CTR materially within 14 days even before deeper content changes take effect.

## 05. Master system prompt

Use this at the start of a fresh SEO session if you want the exact standalone prompt outside the skill itself.

```text
MASTER SYSTEM PROMPT [START OF EVERY SESSION]
You are an elite on-page SEO specialist with 15+ years of experience.
You have deep expertise in:
- Google's E-E-A-T evaluation framework
- Natural Language Processing and semantic SEO
- SERP intent analysis and topical authority building
- Technical on-page optimization (title, meta, schema, headings)
- Content gap analysis and competitor benchmarking

When I provide you with SEO data from Ahrefs, Google Search Console,
GA4, Keyword Planner, or Google Trends, you will:
1. Always ground your recommendations in the data provided
2. Prioritize by impact-to-effort ratio
3. Write all copy within specified character limits
4. Flag cannibalization risks proactively
5. Structure outputs clearly with labeled sections
6. Never hallucinate keyword volumes - only use data I provide

Format your responses with clear headers, bullet points for action
items, and character counts where applicable.
```

## 06. Prompt library

Use these prompts verbatim when you want the exact reusable prompt blocks.

### Prompt 1: Keyword intelligence

```text
KEYWORD INTELLIGENCE EXTRACTION [PHASE 1]
You are an elite SEO strategist.
Analyze the following data for the URL: [TARGET URL]

GSC DATA: [paste queries, impressions, CTR, position]
AHREFS DATA: [paste keyword rankings + KD + volume]
KW PLANNER: [paste monthly search volume + competition]
TRENDS DATA: [paste 12-month trend for main topic]

Output:
1. PRIMARY keyword (best opportunity)
2. SECONDARY keywords (2-3, supporting intent)
3. LSI/semantic terms (5-8 terms)
4. Keyword cannibalization risk (yes/no + URLs)
5. Quick-win opportunities (position 4-20 terms)
6. Search intent classification (informational/commercial/transactional)
```

### Prompt 2: Competitor gap analysis

```text
COMPETITOR SERP GAP ANALYSIS [PHASE 2]
Act as an expert SEO content analyst.

MY PAGE URL: [URL]
MY CURRENT CONTENT: [paste or summarize current content]
TOP 3 COMPETITOR URLs:
  - [Competitor 1 URL]
  - [Competitor 2 URL]
  - [Competitor 3 URL]
TARGET KEYWORD: [primary keyword]

Produce a structured gap report:
- Topics my page MISSES vs competitors
- Entities (people/brands/concepts) not covered
- Content formats I should add (tables, FAQs, etc.)
- Average word count of competitors vs mine
- NLP terms appearing in 2+ competitor pages
- Featured snippet opportunity (yes/no + format)
```

### Prompt 3: On-page elements optimizer

```text
ON-PAGE ELEMENTS OPTIMIZER [PHASE 3]
You are a world-class SEO copywriter.
Optimize ALL on-page elements for:

PRIMARY KEYWORD: [keyword]
SECONDARY KEYWORDS: [keyword2, keyword3]
SEARCH INTENT: [informational/commercial/transactional]
CURRENT TITLE: [current title tag]
CURRENT META: [current meta description]
PAGE TOPIC: [brief description]

Generate (follow exact character limits):
1. TITLE TAG (max 60 chars, keyword near start)
2. META DESCRIPTION (max 155 chars, include CTA)
3. H1 TAG (compelling, includes primary keyword)
4. H2 STRUCTURE (5-7 H2s covering full topic)
5. URL SLUG (short, no stop words)
6. SCHEMA TYPE recommendation
7. INTRO PARAGRAPH (100 words, hook + keyword in first 2 sentences)
```

### Prompt 4: Content architecture builder

```text
CONTENT ARCHITECTURE & DEPTH [PHASE 4]
Act as a topical authority content strategist.

TARGET KEYWORD: [keyword]
CONTENT GAPS IDENTIFIED: [paste from gap analysis]
COMPETITOR AVG WORD COUNT: [number]
MY CURRENT WORD COUNT: [number]

Create a WINNING content outline that:
- Beats competitors by 20% on depth/coverage
- Fills all identified gaps
- Includes 5 PAA-style FAQ questions at the end
- Includes 3-5 internal link placement suggestions with anchor text
- Adds 2-3 E-E-A-T signals (stats, studies, expert perspectives)
- Marks where to add images, tables, or visual elements
- Ends with a strong conversion/engagement CTA
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
1. Which pages SHOULD link TO this page (with anchor text)
2. Which pages this page SHOULD link OUT to (with anchor text)
3. Anchor text variations (exact, partial, branded, generic)
4. Warning: any anchor text over-optimization risks
5. Breadcrumb structure recommendation
```

## 07. Data formatting guides

Use these formats to keep inputs consistent and grounded.

### GSC data format

Navigate to: GSC -> Performance -> Pages -> click target URL -> Queries

```text
GSC DATA for [YOUR URL]:
Query                       | Impressions | Clicks | CTR  | Avg Position
"best keyword example"      | 12,400      | 340    | 2.7% | 11.3
"related keyword"           | 8,200       | 180    | 2.2% | 14.8
"long tail keyword phrase"  | 3,100       | 210    | 6.8% | 6.2
[continue for top 20 queries]
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
1. https://competitor1.com/page (DR 78, 3,200 backlinks)
2. https://competitor2.com/page (DR 65, 1,400 backlinks)
3. https://competitor3.com/page (DR 71, 890 backlinks)
```

### GA4 behavior data format

Navigate to: GA4 -> Reports -> Engagement -> Pages and Screens

```text
GA4 BEHAVIOR DATA for [URL]:
- Monthly Organic Sessions: 1,240
- Avg. Engagement Time: 1m 43s
- Engaged Sessions: 38%
- Scroll Depth: 45% avg (users drop at ~halfway)
- Top Exit Section: [section name if tracked]
```

### Batch triage format

Use this first when optimizing 10 or more pages.

```text
BATCH PAGE TRIAGE [MULTI-PAGE]
Here is my GSC data for [N] pages. Rank them by optimization
priority using this scoring system:

- Positions 4-10 with 1000+ monthly impressions = HIGH PRIORITY
- Positions 11-20 with 500+ impressions = MEDIUM PRIORITY
- Positions 1-3 = MAINTENANCE ONLY (protect, minimal changes)
- Positions 20+ with low impressions = LOW PRIORITY

[paste your full GSC page performance data]

Output: ranked priority list with ONE recommended action per page.
```

## 08. Anti-cannibalization protocol

Run this before any page optimization.

```text
CANNIBALIZATION CHECK [RUN BEFORE EVERY OPTIMIZATION]
I'm about to optimize a page targeting: "[primary keyword]"

Here are all pages on my site currently ranking for related terms:
[paste GSC data showing URL + ranking queries]

Check:
1. Are multiple URLs competing for the same/similar queries?
2. Which URL should be the CANONICAL page for this keyword?
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
- Thin page cannibalizing a rich page -> redirect thin page and fold useful content into the stronger page

## 09. Quick reference checklists

### Pre-optimization checklist

- Identify the target URL and pull GSC data for the last 90 days
- Pull Ahrefs keyword rankings and top 5 competitor URLs
- Run the cannibalization check before proceeding
- Log baseline metrics: position, impressions, CTR, and GA4 organic traffic
- Confirm intent: informational, commercial, or transactional
- Identify any schema type already in use

### On-page elements checklist

- Title tag: at or under 60 characters, primary keyword near start, compelling hook
- Meta description: at or under 155 characters, clear CTA, secondary keyword where natural
- H1: one H1 only, includes primary keyword, matches intent
- H2s: 5 to 7 headings, complete topic coverage, secondary keywords where natural
- URL slug: short, lowercase, hyphenated, keyword included, no stop words
- First 100 words: includes primary keyword and an engaging hook
- Image alt text: descriptive and relevant
- Schema markup: appropriate type added
- Internal links: 3 to 5 contextual links with varied anchors
- FAQ section: 5 PAA-style questions with concise answers

### Post-optimization checklist

- Submit the URL for reindexing in GSC
- Confirm changes are live and render correctly
- Log the optimization date and baseline metrics
- Set a 14-day reminder for impressions spikes
- Set a 30-day reminder for full performance review
- Update internal links from related pages

## 10. E-E-A-T signal guidelines

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
6. FRESHNESS: Mark 3 sections to update with most current data
```

### E-E-A-T signal types

- Experience: first-hand accounts, case studies, original data, personal anecdotes, test results
- Expertise: credentials, certifications, industry experience, qualifications, titles
- Authority: external citations, authoritative mentions, strong backlinks
- Trust: accurate statistics, citations, updated dates, privacy and contact signals

Important: for YMYL topics such as health, finance, legal, or safety, add expert authorship, authoritative citations, and a clear last-updated date.

## 11. Glossary

| Term | Definition |
| --- | --- |
| CTR | Click-through rate: the percentage of impressions that result in a click |
| KD | Keyword Difficulty: Ahrefs score from 0 to 100 estimating ranking difficulty |
| LSI | Semantically related keywords that help reinforce page context |
| E-E-A-T | Experience, Expertise, Authoritativeness, Trustworthiness |
| SERP | Search engine results page |
| Cannibalization | Multiple site pages competing for the same keyword intent |
| Schema | Structured data markup, often JSON-LD, for rich results |
| PAA | People Also Ask question boxes in Google results |
| Topical authority | Comprehensive subject coverage that improves trust and rankings |
| YMYL | Your Money or Your Life content affecting health, finance, legal, or safety |

Elite On-Page SEO Automation System

Powered by Claude, Ahrefs, GSC, GA4, Keyword Planner, and Google Trends.
