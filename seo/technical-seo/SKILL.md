---
name: technical-seo
description: Technical SEO audit workflow for site health, structured data, Core Web Vitals, and sitemap plus robots validation using Google Search Console, GA4, Ahrefs, Semrush, web_fetch, and web_search. Use when the user wants a full technical SEO audit, prioritised fix list, schema review, crawl and index diagnostics, redirect and canonical checks, page speed investigation, sitemap validation, robots.txt analysis, or a 30-day remediation plan for a website.
---

# Technical SEO

Run a full technical SEO audit across crawlability, structured data, performance, and discovery controls. Keep this file focused on audit rules and open the full operating guide only when you need the exact audit steps, issue tables, code snippets, or final report format: [references/technical-seo-master-audit.md](references/technical-seo-master-audit.md).

## Core rules

- Work through all 4 audits in sequence unless the user explicitly requests only one area.
- Use the specified tool for each step whenever it is available.
- Do not invent GSC, GA4, Ahrefs, Semrush, or HTTP findings.
- If a tool is unavailable, say so explicitly and continue with the remaining evidence.
- Focus on issues that affect crawling, indexing, rendering, page experience, and structured data eligibility.
- Consolidate overlapping findings from multiple tools into one final prioritised fix list.
- Use severity labels consistently:
  - `Critical`: directly hurts crawling, indexing, or ranking
  - `High`: significant impact on UX, signals, or discoverability
  - `Medium`: best-practice or supporting issues
  - `Low`: minor or batchable improvements
- When a finding is actionable, include the recommended fix. Include code only when it materially helps implementation.

## Required inputs

- Website URL
- Sitemap URL, or permission to infer `/sitemap.xml`
- Robots.txt URL, or permission to infer `/robots.txt`
- Priority pages to audit, or permission to crawl automatically
- Business type
- Target country

## Tool routing

Use these tools for these areas:

- `Google Search Console`: index coverage, crawl errors, Core Web Vitals field data, sitemap submission status
- `GA4`: page-level traffic, engagement, bounce rate, and landing-page prioritisation
- `Ahrefs`: broken backlinks, DR context, organic pages, crawlability cross-checks
- `Semrush`: site audit findings, page speed issues, duplicates, metadata gaps, and other technical errors
- `web_fetch`: status codes, redirect chains, headers, canonical tags, HTML checks, sitemap fetches, robots.txt fetches, and schema extraction
- `web_search`: schema property validation, best-practice lookup, public PageSpeed references when available

## 4-audit execution

### Audit 1: Site health

- Pull GSC coverage and crawl errors
- Pull Semrush site audit issues
- Run manual `web_fetch` checks on the homepage and priority pages
- Pull Ahrefs broken backlinks and top linked pages
- Consolidate findings into one issue table

### Audit 2: Schema markup and structured data

- Extract JSON-LD, Microdata, and RDFa from the homepage and priority pages
- Validate found types against current Schema.org guidance
- Map expected schema by business type
- Generate missing or incomplete JSON-LD blocks when defensible
- Summarise page-by-page schema findings

### Audit 3: Core Web Vitals and page speed

- Pull mobile and desktop CWV groups from GSC
- Use GA4 to prioritise high-traffic pages with weak performance
- Inspect HTML and headers for images, scripts, CSS, fonts, caching, and protocol issues
- Pull Semrush page speed findings
- Summarise metrics and include code examples for critical or high fixes

### Audit 4: XML sitemap and robots.txt

- Fetch and validate the sitemap
- Pull GSC sitemap submission status
- Fetch and validate robots.txt
- Cross-check crawlability with Ahrefs
- Summarise sitemap and robots issues with corrected examples where needed

## Output structure

Use this format unless the user asks for something else:

1. Executive summary
   Include site health score, coverage summary, CWV summary, total issue counts, and likely SEO impact
2. Master priority fix list
   Sort by impact and severity first, then effort
3. Audit 1 full findings
4. Audit 2 full findings
5. Audit 3 full findings
6. Audit 4 full findings
7. 30-day action plan

## Expected tables

Produce compact tables for:

- Site health findings
- Schema findings
- Core Web Vitals and speed findings
- Sitemap and robots findings
- Master priority fix list

## Failure handling

- If the sitemap or robots URL is missing, try the standard path and report what happened.
- If field data is absent in GSC, state that and rely on available HTML, headers, and audit tools.
- If Schema.org validation cannot be fully verified live, state the assumption and use the best-supported structure from the visible page content.
- If priority pages are not provided, audit the homepage and the most important discoverable templates.
