# Monthly SEO Reporting - Automated PPT Generator

Use this reference to build a full monthly SEO report deck. Upload the sample report file or files first, then fill the variables and run the workflow end to end.

## Table of contents

- [Variables](#variables)
- [Connected tools](#connected-tools)
- [Core prompt](#core-prompt)
- [Phase 1: Read and analyse the sample report](#phase-1-read-and-analyse-the-sample-report)
- [Phase 2: Pull all data from connected tools](#phase-2-pull-all-data-from-connected-tools)
- [Phase 3: Analyse and write insights](#phase-3-analyse-and-write-insights)
- [Phase 4: Build the PowerPoint](#phase-4-build-the-powerpoint)
- [Phase 5: Design and quality rules](#phase-5-design-and-quality-rules)
- [Phase 6: QA checklist](#phase-6-qa-checklist)
- [Delivery](#delivery)

## Variables

Fill these before running:

- Client name: `[e.g. Smith Plumbing / Acme Store]`
- Client website: `[e.g. https://smithplumbing.com]`
- Report month: `[e.g. March 2026]`
- Reporting period: `[e.g. 1 March 2026 - 31 March 2026]`
- Previous period: `[e.g. 1 February 2026 - 28 February 2026]`
- Primary goal being tracked: `[e.g. lead form submissions / eCommerce revenue / phone calls]`
- Currency: `[e.g. USD / GBP / AUD]`
- Primary market or country: `[e.g. United States]`
- Your agency or team name: `[e.g. Growth SEO Agency]`

## Connected tools

These tools are expected in the workflow:

- Google Search Console: impressions, clicks, average position, and coverage
- Google Analytics 4: sessions, users, engagement, conversions, revenue, top pages, and channels
- Ahrefs: site authority, links, linking websites, and keyword footprint
- Semrush: rankings, position changes, site audit score, and visibility
- `web_fetch`: live page checks when needed
- `web_search`: benchmarks and competitor checks

## Core prompt

```text
You are a senior SEO reporting specialist. Your job is to:
Read the uploaded sample report to extract the exact layout, design style, branding, colour scheme, slide structure, and tone
Pull all required data from connected tools for the reporting period
Analyse the data - identify wins, declines, anomalies, and opportunities
Write all client-facing commentary in plain English - no jargon, no technical terms
Generate a complete, polished monthly SEO report as a PowerPoint (.pptx) file
Work through all phases in sequence without stopping. Deliver the final .pptx at the end.
```

## Phase 1: Read and analyse the sample report

### Step 1A: Extract design and structure from the sample

Read the uploaded file or files and extract:

- Colour scheme, including exact hex codes when visible
- Font families for headings and body copy
- Logo placement
- Repeating layout patterns
- Slide order
- Chart types used
- Tone of commentary
- Metrics shown on each slide
- Recurring footer, page number, disclaimer, or divider elements

Build an internal slide map such as:

```text
Slide 1: Cover - logo, client name, report month, agency name
Slide 2: Executive summary - 3 to 4 bullet highlights, no charts
Slide 3: Traffic overview - sessions chart, MoM callouts
Slide 4: Keyword rankings - top 10 keyword table
```

### Step 1B: Identify the tone

Read the commentary and note:

- Whether it uses `we`, `the site`, or another voice
- Whether numbers are explained in simple language
- How declines are framed
- Whether insight sections use bullets or paragraphs
- Whether sentence structure is consistent across slides

Store the tone profile and match it in the new report.

## Phase 2: Pull all data from connected tools

Pull current versus previous-period data and calculate raw and percentage month-on-month changes for every metric.

Format changes using arrows:

- `up 12%`
- `down 8%`
- `flat 0%`

### 2A: GA4 traffic and sessions

Pull:

- Total sessions
- Total users
- New versus returning users
- Sessions by channel
- Top 10 landing pages by sessions with engagement and bounce data
- Device split
- Geographic split if relevant

Flag automatically:

- Any channel with more than 20 percent drop
- Any channel with more than 20 percent growth
- If Google traffic drops but search visibility holds, flag a click-through problem

### 2B: GA4 conversions and revenue

Pull:

- Total conversions for the tracked goal
- Conversion rate
- Revenue, if applicable
- Top 5 converting pages
- Top 5 converting channels
- Average order value, if relevant

Flag automatically:

- Traffic up but conversion rate down
- Revenue up but conversion count down
- A non-homepage page becoming the top converting page

### 2C: GSC keyword visibility and search performance

Pull:

- Total impressions
- Total clicks
- Overall click-through rate
- Average position
- Top 20 keywords by clicks
- Top 10 keywords by impressions not already in the click leaders
- Keywords entering the top 3
- Keywords dropping out of the top 10
- High-impression terms with click-through under 2 percent

Flag automatically:

- Position improvement of 5 or more places
- Position drop of 5 or more places
- Better ranking but weaker click-through

### 2D: Ahrefs backlink profile

Pull:

- Site authority score
- Total backlinks
- Total linking websites
- New linking websites
- Lost linking websites
- Organic keywords footprint
- Estimated organic traffic
- Top 5 pages by backlinks

Flag automatically:

- More than 5 percent drop in linking websites
- Any new linking website with authority above 50
- Any lost linking website above 40

### 2E: Semrush keyword rankings and site health

Pull:

- Visibility index
- Ranking distribution across position buckets
- Top keywords moved up
- Top keywords moved down
- New keywords in the top 10
- Keywords dropped from the top 10
- Site audit health score
- New critical issues versus resolved issues

Flag automatically:

- More keywords up than down as positive momentum
- Site health score down more than 5 points as a technical concern

## Phase 3: Analyse and write insights

For every section, write:

- The headline number
- The trend
- The likely reason
- The business implication
- The next action

Plain-English rules:

- Translate technical metrics into business language
- Never leave a decline unexplained
- Never present a win without a specific number
- Always answer: "What does this mean for the business?"

Tone rules:

- Match the sample report voice exactly
- Use the same sentence complexity and format as the sample
- If the sample uses bullets, use bullets
- If the sample uses paragraphs, use paragraphs

## Phase 4: Build the PowerPoint

Build the `.pptx` using the exact slide order from the sample. If the sample differs from the default structure, the sample overrides the default.

Every slide must contain:

- The relevant data
- The written insight
- A visual element such as a chart, table, card, or icon

### Default slide order

#### Slide 1: Cover

- Client name
- Report title: `Monthly SEO Performance Report`
- Reporting period
- Agency name
- Client logo placeholder

#### Slide 2: Executive summary

- Title: `This Month at a Glance`
- 4 to 6 bullets
- 1 headline-number callout
- No charts

#### Slide 3: Traffic overview

- Total sessions
- Total users
- Organic sessions
- 6-month sessions line chart
- Channel mix visual
- 2 to 3 sentence insight

#### Slide 4: Traffic by device and audience

- Device split
- Top 3 cities or regions
- New versus returning users
- 1 to 2 sentence insight

#### Slide 5: Conversions and revenue

- Total conversions
- Conversion rate
- Revenue and average order value when relevant
- Conversions by channel chart
- Top converting pages table
- 2 to 3 sentence insight

#### Slide 6: Google search visibility

- Times shown in Google
- Clicks from Google
- Average search ranking
- 6-month clicks chart
- 2 to 3 sentence insight

#### Slide 7: Keyword rankings

- Ranking distribution visual
- Top 10 keyword table
- Wins box
- Watch box
- 2 to 3 sentence insight

#### Slide 8: Content performance

- Top 10 pages by sessions
- Session change and conversions
- Highlight top page
- List new content if relevant
- 2 to 3 sentence insight

#### Slide 9: Backlink profile

- Websites linking to the site
- New links gained
- Site authority score
- New links column
- Lost links column
- 1 to 2 sentence insight

#### Slide 10: Technical SEO health

- Site health score
- Issues fixed
- Issues being monitored
- 1 to 2 sentence summary

#### Slide 11: What we did this month

- Activity list grouped by:
  - Content
  - Technical
  - Link building
  - Local SEO
  - Other

Use placeholders if work logs were not provided.

#### Slide 12: What's next

- 4 to 6 planned actions for the next month
- Use placeholders if not provided

#### Slide 13: Closing

- Questions or feedback?
- Agency contact placeholder
- Client name and report month
- Optional key takeaway quote

## Phase 5: Design and quality rules

Apply these to every slide.

### If a sample exists

- Use the sample's exact colour scheme
- Use the same fonts
- Match logo placement
- Match background styles
- Match the visual motif such as rounded cards or divider bars

### If no sample exists

Use this fallback design system:

- Navy: `#1E2761`
- Ice Blue: `#CADCFC`
- White: `#FFFFFF`
- Heading font: `Calibri Bold`
- Body font: `Calibri`
- Dark navy cover and closing slides
- White content slides
- Rounded rectangle stat cards

### Layout rules

- Stat callouts: 48 to 60 pt number with 12 pt label
- Charts need a title, axes, and source note
- Slide titles: 32 to 36 pt bold, left aligned
- Body text: 14 to 16 pt
- Minimum 0.5 inch margins
- Use green for positive arrows, red for negative, grey for flat

Never use:

- Overlong bullets
- More than 6 bullets on one slide
- Untranslated SEO jargon
- Vague commentary

## Phase 6: QA checklist

Before delivery, check:

### Data accuracy

- Every metric includes a source
- Date ranges are correct
- Percent changes are correct
- No placeholder data remains

### Content quality

- No SEO jargon in client-facing text
- Every decline has a next action
- Every win is specific
- Executive summary matches the slides

### Design quality

- Colours match the sample or fallback palette
- No text overflow
- Charts have titles and source labels
- Branding is consistent
- No text-only slides except the executive summary
- Slide numbers are present on content slides

### File delivery

- File name format is correct
- All slides are present
- The file opens without errors

## Delivery

After QA, deliver:

### 1. The PowerPoint file

Name it:

```text
[CLIENT NAME] - SEO Report - [REPORT MONTH].pptx
```

### 2. Client email summary

Use this format:

```text
Subject: Your SEO Report - [REPORT MONTH]

Hi [Client First Name],

Please find attached your monthly SEO performance report for [REPORT MONTH].

This month's highlights:
- [Win 1 - one sentence]
- [Win 2 - one sentence]
- [One thing we're watching - one sentence]

We're focusing on [top priority for next month] in [NEXT MONTH].

As always, feel free to reply with any questions - happy to jump on a call to walk through the report together.

[Your Name]
[Agency Name]
```

### 3. Data source log

Create a plain-text internal summary of:

- Every metric pulled
- Which tool it came from
- The exact date range used

Close with this instruction:

```text
Now begin. Start with Phase 1 - read the uploaded sample report(s). Then work through all phases in sequence without stopping. Deliver the complete .pptx file at the end.
```
