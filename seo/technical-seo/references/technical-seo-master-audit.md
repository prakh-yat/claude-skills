# Technical SEO Master Audit Prompt

Use this reference to run a complete technical SEO audit. Fill the variables first, then execute all 4 audits in sequence.

## Table of contents

- [Variables](#variables)
- [Connected tools](#connected-tools)
- [Core prompt](#core-prompt)
- [Audit 1: Site health](#audit-1-site-health)
- [Audit 2: Schema markup and structured data](#audit-2-schema-markup-and-structured-data)
- [Audit 3: Core Web Vitals and page speed](#audit-3-core-web-vitals-and-page-speed)
- [Audit 4: XML sitemap and robots.txt](#audit-4-xml-sitemap-and-robotstxt)
- [Final report](#final-report)

## Variables

Fill these before running:

- Website URL: `[e.g. https://mysite.com]`
- Sitemap URL: `[e.g. https://mysite.com/sitemap.xml]`
- Robots.txt URL: `[e.g. https://mysite.com/robots.txt]`
- Priority pages to audit: `[e.g. homepage, /blog, /pricing - or "crawl automatically"]`
- Business type: `[e.g. SaaS / eCommerce / local business / blog / news site]`
- Target country: `[e.g. US / UK / Global]`

## Connected tools

These tools are expected in the workflow:

- Google Search Console: crawl errors, index coverage, Core Web Vitals field data, sitemaps
- Google Analytics 4: page-level traffic, bounce rate, engagement, top landing pages
- Ahrefs: backlink profile, broken backlinks, DR, organic keywords, top pages
- Semrush: site audit issues, on-page SEO, position tracking, toxic backlinks
- `web_fetch`: raw HTML and HTTP headers from any URL
- `web_search`: best practices, indexing checks, and schema documentation

## Core prompt

```text
You are a Technical SEO specialist. Your job is to perform a full technical audit across 4 areas:
Site Health (crawl errors, broken links, redirects, canonical issues)
Schema Markup & Structured Data
Core Web Vitals & Page Speed
XML Sitemap & Robots.txt

Work through all 4 audits in sequence without stopping. At the end, compile everything into one unified report with a single prioritised fix list sorted by impact.
```

## Audit 1: Site health

Audit crawl errors, broken links, redirects, and canonical issues.

### 1A: GSC index coverage and crawl errors

Tool: Google Search Console

Pull:

- Index Coverage report: total indexed pages, excluded pages, errors, warnings
- URLs with statuses:
  - `Crawled - currently not indexed`
  - `Discovered - not indexed`
  - `Blocked by robots.txt`
  - `Not found (404)`
  - `Redirect error`
- Coverage error breakdown by type:
  - 5xx
  - 404
  - Redirect
  - Soft 404
- Manual actions or security issues
- Last crawl date of the homepage

Flag as `Critical` if:

- More than 5 percent of submitted URLs have errors
- Pages that should be indexed are excluded
- Any manual action exists

### 1B: Semrush site audit issues

Tool: Semrush

Pull:

- Overall site health score
- Errors: list all critical issues with affected URL count
- Warnings: top 10 by affected page count
- Notices: summarise categories only

Specifically surface:

- Broken internal links
- Broken external links
- Redirect chains of 3 or more hops and redirect loops
- Duplicate title tags
- Duplicate meta descriptions
- Missing title tags or meta descriptions
- Title tags longer than 60 chars or shorter than 30 chars
- Thin content under 200 words
- Hreflang errors on multi-language sites
- HTTP pages on HTTPS sites

### 1C: Manual header and canonical check

Tool: `web_fetch`

Fetch the website URL and check:

- Final status code
- Full redirect chain
- `X-Robots-Tag`
- `Content-Type`

Parse the HTML and check:

- `<html lang="">`
- `<title>`
- `<meta name="description">`
- `<link rel="canonical">`
- `<meta name="robots">`
- `<meta name="viewport">`
- Internal links using absolute or relative URLs
- Any `href="javascript:..."` links

Repeat this for up to 5 priority pages.

### 1D: Ahrefs broken backlinks and crawl issues

Tool: Ahrefs

Pull:

- Broken backlinks report
- Top 20 broken backlink URLs with referring domain count
- URLs with 5 or more referring domains
- Best by Links report to confirm top linked pages are indexed and not redirected
- Site Audit crawl errors if available

### 1E: Audit 1 findings summary

Use this table:

```text
| Issue | Type | Severity | Affected URLs | Tool Found | Recommended Fix |
|-------|------|----------|---------------|------------|-----------------|
| 23 broken internal links | Crawl | Critical | /blog/*, /product/* | Semrush | Update or redirect to live URLs |
| Homepage redirects http->https->www (2 hops) | Redirect | High | / | web_fetch | Consolidate to single redirect |
| 14 pages missing meta description | On-page | Medium | Various | Semrush | Write unique descriptions |
```

Severity scale:

- Critical: fix within 1 week
- High: fix within 2 weeks
- Medium: fix in the next sprint
- Low: batch monthly

## Audit 2: Schema markup and structured data

### 2A: Extract existing schema

Tool: `web_fetch`

Fetch the homepage and each priority page. Extract all JSON-LD, Microdata, and RDFa blocks.

For each block, check:

- Is `@type` appropriate for the page type?
- Are required properties present?
- Are deprecated properties used?
- Does the schema match the visible content?
- Is JSON-LD placed in `<head>` or near the top of `<body>`?

### 2B: Validate against Schema.org

Tool: `web_search`

For each found `@type`, search current required and recommended properties.

Search pattern:

```text
schema.org/[TYPE] required properties 2024
```

Cross-check the page implementation against the current requirements.

### 2C: Schema requirements by business type

Based on business type, expect these schema types and flag missing ones.

#### SaaS or software

- `SoftwareApplication` on product pages
- `FAQPage` on FAQ sections
- `Article` or `BlogPosting` on blog posts
- `BreadcrumbList` on inner pages
- `Organization` on the homepage

#### eCommerce

- `Product`
- `Review` or `AggregateRating`
- `BreadcrumbList`
- `Organization`

#### Local business

- `LocalBusiness`
- `Review` or `AggregateRating`
- `FAQPage` if relevant

#### Blog or news

- `Article` or `NewsArticle`
- `Person` for author pages
- `BreadcrumbList`
- `WebSite` with `SearchAction` on the homepage

### 2D: Generate missing schema

For any missing or incomplete required type, generate JSON-LD using real site content only.

Template:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "[TYPE]",
  [PROPERTIES BASED ON TYPE AND PAGE CONTENT]
}
</script>
```

For each generated block:

- State which page it belongs on
- State preferred placement, usually `<head>`
- Note any fields needing manual owner input

### 2E: Audit 2 findings summary

Use this table:

```text
| Page | Schema Found | Missing Schema | Issues | Priority |
|------|--------------|----------------|--------|----------|
| Homepage | Organization | WebSite (SearchAction) | logo URL missing | High |
| /blog/post-1 | none | Article, BreadcrumbList | No schema at all | Critical |
| /pricing | SoftwareApplication | FAQPage | price not declared | High |
```

## Audit 3: Core Web Vitals and page speed

### 3A: GSC Core Web Vitals field data

Tool: Google Search Console

Pull:

- Mobile CWV report: all URL groups in `Poor` and `Needs improvement`
- Desktop CWV report: same

For each failing group, note:

- Metric failing: `LCP`, `INP`, or `CLS`
- Current value versus threshold
- Number of URLs affected

Thresholds:

- `LCP < 2.5s`
- `INP < 200ms`
- `CLS < 0.1`

Flag as `Critical` if:

- More than 15 percent of pages are poor on mobile
- The homepage is poor on either device

### 3B: GA4 page speed by traffic volume

Tool: GA4

Pull:

- Top 20 landing pages by sessions over the last 90 days
- Sessions, bounce rate, and average engagement time for each
- Device category breakdown
- Pages with bounce rate above 70 percent and high traffic

Cross-reference with GSC CWV data to prioritise fixes.

### 3C: Page weight and resource audit

Tool: `web_fetch`

Fetch the homepage and priority pages. Check:

#### Images

- Modern formats such as WebP or AVIF
- Width and height attributes on `<img>`
- Correct lazy loading usage
- `srcset` for responsive images
- Preload for the likely LCP image

#### JavaScript

- Use of `defer` or `async`
- Third-party scripts blocking in `<head>`
- Third-party script count greater than 10

#### CSS

- CSS loaded through `<link>` in `<head>`
- Any `@import` usage
- Inline CSS that should be externalised

#### Fonts

- `font-display: swap`
- Font preloads

#### General

- HTTP/2 or HTTP/3 support
- Any `<meta http-equiv="refresh">`

### 3D: PageSpeed Insights score

Tool: `web_search`

Search for public PageSpeed references:

```text
site:[WEBSITE URL] pagespeed score
PageSpeed Insights [WEBSITE URL]
```

If no reliable public source exists, say so explicitly.

### 3E: Semrush site speed issues

Tool: Semrush

Pull:

- Pages with load time over 3 seconds
- Pages larger than 2 MB
- Pages with more than 80 requests
- Uncompressed resources
- Missing browser caching headers

### 3F: Audit 3 findings summary

Use this table:

```text
| Metric | Current Value | Target | Affected Pages | Device | Priority |
|--------|---------------|--------|----------------|--------|----------|
| LCP | 4.2s | < 2.5s | /blog/* (34 URLs) | Mobile | Critical |
| CLS | 0.18 | < 0.1 | Homepage, /pricing | Both | High |
| INP | 180ms | < 200ms | All pages | Mobile | Good |
| Render-blocking JS | 3 scripts | 0 | All pages | Both | High |
| Images missing width/height | 12 images | 0 | /blog/*, /about | Both | Medium |
| No WebP format | 45 images | 0 | Sitewide | Both | Medium |
```

For every `Critical` or `High` issue, include a specific fix recommendation with code if helpful.

#### Example fix snippets

Lazy loading images correctly:

```html
<!-- Above fold (LCP image) - no lazy load, add preload -->
<link rel="preload" as="image" href="/hero-image.webp">
<img src="/hero-image.webp" width="1200" height="600" alt="...">

<!-- Below fold - add lazy load -->
<img src="/blog-thumb.webp" width="800" height="400" loading="lazy" alt="...">
```

Defer non-critical scripts:

```html
<!-- Before -->
<script src="/analytics.js"></script>

<!-- After -->
<script src="/analytics.js" defer></script>
```

Font display swap:

```css
@font-face {
  font-family: 'MyFont';
  src: url('/fonts/myfont.woff2') format('woff2');
  font-display: swap;
}
```

## Audit 4: XML sitemap and robots.txt

### 4A: Fetch and validate sitemap

Tool: `web_fetch`

Fetch the sitemap URL, or try `/sitemap.xml`.

Check:

- Accessible with 200 status
- Valid XML
- Sitemap index or single sitemap
- Total URLs listed
- `<lastmod>` dates present and recent
- Optional `changefreq` and `priority`
- Any URLs that:
  - return non-200
  - have `noindex`
  - redirect
  - represent duplicate or low-value pages that should be excluded

Spot-check 10 random URLs where possible.

### 4B: GSC sitemap submission status

Tool: Google Search Console

Pull:

- Submitted sitemaps
- Status of each
- Submitted count versus indexed count
- Last read date

Flag as `Critical` if:

- Indexed count is below 50 percent of submitted count
- Any submitted sitemap has errors
- No sitemap is submitted

### 4C: Fetch and validate robots.txt

Tool: `web_fetch`

Fetch the robots URL, or try `/robots.txt`.

Check:

- Accessible status
- `text/plain` content type
- `Sitemap:` directive
- `User-agent: *` rules
- Important pages or directories accidentally disallowed
- Bot-specific rules
- `Crawl-delay` directive

Cross-reference against GSC coverage to identify blocking rules causing exclusions.

### 4D: Ahrefs sitemap and crawlability cross-check

Tool: Ahrefs

Check:

- Crawlability report for blocked URLs
- Top linked internal pages blocked by robots
- Strong-backlink pages disallowed from crawling

### 4E: Audit 4 findings summary

Use this table:

```text
| Issue | Location | Severity | Detail | Recommended Fix |
|-------|----------|----------|--------|-----------------|
| Indexed count 40% of submitted | GSC Sitemaps | Critical | 340 submitted, 136 indexed | Investigate excluded pages in GSC coverage |
| /wp-admin/ rule too broad | robots.txt | High | Blocks /wp-admin/load-styles.php needed for rendering | Tighten disallow rule |
| 12 redirected URLs in sitemap | sitemap.xml | High | Lines 45, 67, 102 | Replace with canonical final URLs |
| No Sitemap: directive in robots.txt | robots.txt | Medium | Bots may not find sitemap | Add Sitemap: https://mysite.com/sitemap.xml |
| lastmod dates all identical | sitemap.xml | Low | All set to 2024-01-01 | Set accurate per-page lastmod dates |
```

Provide corrected code for robots issues when useful:

```txt
User-agent: *
Disallow: /wp-admin/
Allow: /wp-admin/admin-ajax.php

User-agent: GPTBot
Disallow: /

Sitemap: https://[WEBSITE URL]/sitemap.xml
```

## Final report

After all 4 audits, compile one unified report in this structure.

### Executive summary

- Overall site health score from Semrush
- GSC index coverage: indexed versus submitted
- Core Web Vitals summary for mobile
- Total issues by severity
- Estimated SEO impact if all critical issues are fixed

### Master priority fix list

Sort by severity and impact first.

```text
| Priority | Issue | Audit | Tool That Found It | Est. Effort | Est. Impact |
|----------|-------|-------|--------------------|-------------|-------------|
| 1 | [Most impactful critical issue] | Site Health | GSC + Semrush | 2 hrs | High |
```

Effort scale:

- Quick win: under 1 hour
- Low: 1 to 4 hours
- Medium: 1 to 2 days
- High: 3 to 5 days
- Ongoing

Impact scale:

- Low
- Medium
- High
- Critical

### Audit sections

- Audit 1 full findings
- Audit 2 full findings, including generated JSON-LD blocks
- Audit 3 full findings, including fix snippets
- Audit 4 full findings, including corrected robots examples and sitemap recommendations

### 30-day action plan

- Week 1: fix all critical issues
- Week 2: fix all high issues
- Week 3: implement missing schema
- Week 4: page speed optimisation and sitemap cleanup

Use this closing instruction:

```text
Now begin. Start with Audit 1 and work through all 4 audits in sequence. Use the specified tool at each step. Do not stop between audits - deliver the complete unified report at the end.
```
