---
name: reporting
description: Monthly SEO reporting workflow for reading uploaded sample reports, matching their design and tone, pulling SEO performance data from GSC, GA4, Ahrefs, and Semrush, writing plain-English insights, and generating a polished PowerPoint report with a client-ready email summary and internal data source log. Use when the user wants a monthly SEO report deck, sample-based PPT styling, month-on-month reporting, executive summaries, slide commentary, or a finished .pptx deliverable.
---

# Reporting

Run monthly SEO reporting as a sample-led slide production workflow. Keep this file focused on execution rules and open the detailed reference guide only when you need the exact phase instructions, slide map, design defaults, QA checklist, or delivery format: [references/monthly-seo-reporting-automated-ppt-generator.md](references/monthly-seo-reporting-automated-ppt-generator.md).

## Core rules

- Read the uploaded sample report files before pulling any metrics.
- Match the sample report's slide order, layout style, branding, colours, typography, and commentary tone as closely as possible.
- Pull data for the current and previous periods, then calculate month-on-month change for every tracked metric.
- Write all client-facing commentary in plain English.
- Avoid SEO jargon in the finished report unless it is translated into simple business language.
- Explain every decline constructively and attach a next action.
- Make every win specific with a real number and business implication.
- Include a visual element on every slide except where the workflow explicitly allows a text summary.
- Deliver a finished `.pptx` file, a client-ready email summary, and an internal data source log.

## Required inputs

- Uploaded sample report file or files
- Client name
- Client website
- Report month
- Reporting period
- Previous period
- Primary goal being tracked
- Currency
- Primary market or country
- Agency or team name

## Tool routing

Use these tools for these areas:

- `Google Search Console`: impressions, clicks, average search position, coverage, and index signals
- `GA4`: sessions, users, engagement, conversions, revenue, channels, and top pages
- `Ahrefs`: links, referring domains, authority trend, and keyword footprint
- `Semrush`: rankings, visibility, and site health
- `web_fetch`: live page checks when needed
- `web_search`: benchmarks and competitor context

## Workflow phases

### Phase 1: Read and analyse the sample report

- Extract colour palette, fonts, logo placement, recurring layouts, slide order, chart types, metrics, and commentary tone.
- Build an internal slide-by-slide map from the uploaded sample.
- Use the sample as the design and tone source of truth.

### Phase 2: Pull all reporting data

- Pull all required metrics from each connected tool for the reporting period and previous period.
- Calculate raw and percentage month-on-month changes.
- Flag large wins, declines, and anomalies automatically.

### Phase 3: Analyse and write insights

- For every section, identify the headline number, trend, likely reason, business implication, and next action.
- Keep all commentary client-friendly and plain English.

### Phase 4: Build the PowerPoint

- Recreate the sample structure and styling.
- Include the required slides, or the sample's exact structure if it overrides the default order.
- Add charts, tables, stat cards, and callouts as needed.

### Phase 5: Design and quality rules

- Match the sample report's visual language.
- If no sample exists, use the fallback reporting palette and typography.
- Keep slides clean, readable, and consistent.

### Phase 6: QA checklist

- Check metrics, date ranges, math, wording, slide completeness, branding, and file integrity before delivery.

## Output structure

Deliver these outputs:

1. PowerPoint report
   Final `.pptx` file named with client and month
2. Client email summary
   Short ready-to-send email with 2 wins, 1 watch item, and next-month focus
3. Data source log
   Plain text record of metrics, tools, and date ranges used

## Failure handling

- If sample reports are missing, use the default visual system defined in the reference guide.
- If a tool does not return a metric, state that clearly and continue without inventing values.
- If revenue or conversion data is not relevant to the business, omit it gracefully and adjust the slide commentary.
- If a metric moves in a counterintuitive direction, call out the anomaly and suggest the likely investigation path.
