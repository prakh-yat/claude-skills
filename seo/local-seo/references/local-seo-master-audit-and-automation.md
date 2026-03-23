# Local SEO Master Audit and Automation Prompt

Use this reference to run a complete local SEO audit. Fill the variables first, then execute all 4 audits in sequence.

## Table of contents

- [Variables](#variables)
- [Core prompt](#core-prompt)
- [Audit 1: Google Business Profile](#audit-1-google-business-profile)
- [Audit 2: Local citation building and NAP consistency](#audit-2-local-citation-building-and-nap-consistency)
- [Audit 3: Local keyword research and rankings](#audit-3-local-keyword-research-and-rankings)
- [Audit 4: Review monitoring and response automation](#audit-4-review-monitoring-and-response-automation)
- [Final report](#final-report)

## Variables

Fill these before running:

- Business name: `[e.g. Smith Plumbing Services]`
- Business website: `[e.g. https://smithplumbing.com]`
- Business address: `[e.g. 123 Main St, Austin, TX 78701]`
- Phone number: `[e.g. +1 (512) 555-0123]`
- Business category: `[e.g. Plumber / Dentist / Restaurant / Law Firm]`
- Primary city or region: `[e.g. Austin, TX]`
- Service areas: `[e.g. Austin, Round Rock, Cedar Park, Georgetown]`
- Google Business Profile URL: `[optional]`
- Top 3 competitors: `[e.g. Joe's Plumbing, Austin Pipe Pros, FastFix Plumbing]`
- Primary services: `[e.g. emergency plumbing, drain cleaning, water heater installation]`

## Core prompt

```text
You are a Local SEO specialist. Your job is to run a full local SEO audit and action plan across 4 areas:
Google Business Profile audit and optimisation
Local citation building and NAP consistency
Local keyword research and rankings
Review monitoring and response automation

Work through all 4 audits in sequence without stopping. Use only web_fetch and web_search at every step as specified. Deliver one unified report with a prioritised fix list at the end.
```

## Audit 1: Google Business Profile

Audit, optimise, and benchmark the business profile.

### 1A: Fetch and audit the GBP listing

Tool: `web_search`

Search:

- `[BUSINESS NAME] [PRIMARY CITY]`
- `[BUSINESS NAME] Google Maps`

Extract and audit:

- NAP
- Business name accuracy and keyword stuffing risk
- Address formatting and match to website
- Phone number type and match to website
- Primary and secondary categories
- Description presence and quality
- Hours and special hours
- Attributes and service-business highlights
- Cover photo, logo, and general photo coverage
- Services or products listed
- Website link validity
- Q&A section and unanswered questions

Photo benchmark: flag if fewer than 10 photos are visible.

For Q&A, also search:

```text
[BUSINESS NAME] site:google.com/maps
```

### 1B: Competitor GBP benchmarking

Tool: `web_search`

For each competitor, search:

- `[COMPETITOR NAME] [PRIMARY CITY]`
- `[COMPETITOR NAME] Google Maps`

Capture:

- Review count
- Average rating
- Categories
- Posts activity
- Products or services listed
- Booking button
- Estimated photo count
- Description quality

Use this comparison table:

```text
| Feature | My Business | Competitor 1 | Competitor 2 | Competitor 3 |
|---------|-------------|--------------|--------------|--------------|
| Review count | | | | |
| Avg rating | | | | |
| Photo count | | | | |
| Services listed | | | | |
| Posts active | | | | |
| Booking button | | | | |
| Description length | | | | |
```

List every feature competitors have that the business lacks.

### 1C: GBP posts audit

Tool: `web_search`

Search:

```text
[BUSINESS NAME] Google posts
```

Check:

- Date of the most recent post
- Post types in use
- CTA buttons
- Image usage

Flag as `Critical` if no posts have appeared in the last 30 days.

Generate 4 ready-to-publish GBP posts based on primary services and primary city:

#### Post 1: What's New

```text
[Service name] in [City] - [benefit or USP]

[2-3 sentences describing the service and who it is for.
Include primary city + service keyword naturally.]

Call us: [PHONE NUMBER]
[WEBSITE URL]

[CTA Button: Learn More / Call Now / Book]
```

#### Post 2: Offer

```text
[Seasonal or evergreen offer headline]

[Describe the offer clearly. Include any conditions.]
Valid until: [date]

[CTA Button: Get Offer]
```

#### Post 3: Event or second What's New

```text
[Event name or service update]
[Date/time if event]

[2-3 sentences. Include city name.]

[CTA Button: Learn More]
```

#### Post 4: FAQ-style What's New

```text
[Common customer question about your service]

[Answer in 2-3 sentences. Include service keyword + city.]

[CTA Button: Call Now / Book]
```

### 1D: Audit 1 findings summary

Use this table:

```text
| Field | Current Status | Issue | Priority | Fix |
|-------|----------------|-------|----------|-----|
| Business name | Has keyword stuffing | Against GBP guidelines | Critical | Remove added keywords |
| Photos | 3 photos | Below 10-photo benchmark | High | Upload interior, team, work photos |
| GBP Posts | Last post 45 days ago | Stale | High | Post weekly minimum |
| Services listed | None | Missing service signals | High | Add all services with descriptions |
| Q&A | 3 unanswered questions | Bad UX + missed keywords | Medium | Answer all public questions |
| Holiday hours | Not set | Confuses customers | Medium | Add special hours |
```

## Audit 2: Local citation building and NAP consistency

### 2A: NAP extraction from website

Tool: `web_fetch`

Fetch the business website and extract the exact NAP from:

- Header
- Footer
- About page
- Contact page

Also check:

- Address consistency across pages
- Presence of `LocalBusiness` schema with NAP

This becomes the canonical NAP format.

### 2B: Citation audit across major directories

Tool: `web_search`

Search major directories and note:

- Is the business listed?
- Does the listing match the canonical NAP exactly?
- Any discrepancies in name, address, or phone

Tier 1 searches:

- `[BUSINESS NAME] site:yelp.com`
- `[BUSINESS NAME] site:facebook.com`
- `[BUSINESS NAME] site:yellowpages.com`
- `[BUSINESS NAME] site:bbb.org`
- `[BUSINESS NAME] site:bing.com/maps`
- `[BUSINESS NAME] site:apple.com/maps`
- `[BUSINESS NAME] site:mapquest.com`
- `[BUSINESS NAME] site:foursquare.com`
- `[BUSINESS NAME] site:nextdoor.com`

Category-specific searches should be added based on business category.

For all businesses also check:

- `[BUSINESS NAME] site:chamberofcommerce.com`
- `[BUSINESS NAME] site:manta.com`
- `[BUSINESS NAME] site:superpages.com`
- `[BUSINESS NAME] site:cylex.us.com`

### 2C: Local and regional citation sources

Tool: `web_search`

Search:

- `[PRIMARY CITY] business directory`
- `[PRIMARY CITY] [BUSINESS CATEGORY] directory`
- `[PRIMARY CITY] chamber of commerce directory`
- `best [BUSINESS CATEGORY] [PRIMARY CITY]`

List local directories where the business is not yet present.

### 2D: NAP inconsistency report

Use this table:

```text
| Directory | Listed | Business Name | Address | Phone | NAP Match | Action |
|-----------|--------|---------------|---------|-------|-----------|--------|
| Google Business Profile | Yes | Smith Plumbing | 123 Main St | (512) 555-0123 | Yes | None |
| Yelp | Yes | Smith's Plumbing | 123 Main Street | (512) 555-0123 | No - name differs | Fix name |
| YellowPages | Yes | Smith Plumbing | 123 Main St | (512) 5550123 | No - phone format | Fix phone |
| Angi | No | - | - | - | Not listed | Create listing |
| BBB | Yes | Smith Plumbing Services | 123 Main St | (512) 555-0123 | No - name differs | Fix name |
```

Flag as `Critical` if:

- NAP does not match on major listings
- Duplicate listings exist
- The business is missing from Tier 1 directories

### 2E: New citation opportunities

Tool: `web_search`

Search:

- `best [BUSINESS CATEGORY] [PRIMARY CITY]`
- `[BUSINESS CATEGORY] near me [PRIMARY CITY]`
- `[PRIMARY CITY] [BUSINESS CATEGORY] reviews`

For each ranking directory site, check whether the business is listed. If not, add it to the citation gap list.

## Audit 3: Local keyword research and rankings

### 3A: Core local keyword discovery

Tool: `web_search`

Search combinations such as:

- `[PRIMARY SERVICE] [PRIMARY CITY]`
- `[PRIMARY SERVICE] near me`
- `best [PRIMARY SERVICE] [PRIMARY CITY]`
- `[PRIMARY SERVICE] [SERVICE AREA 1]`
- `[PRIMARY SERVICE] [SERVICE AREA 2]`
- `affordable [PRIMARY SERVICE] [PRIMARY CITY]`
- `emergency [PRIMARY SERVICE] [PRIMARY CITY]`
- `[PRIMARY SERVICE] cost [PRIMARY CITY]`
- `[PRIMARY SERVICE] reviews [PRIMARY CITY]`

For each, note:

- Whether the business appears in the local pack
- Which competitors appear
- Page-1 organic results
- People Also Ask questions
- Featured snippets

### 3B: Competitor keyword gap

Tool: `web_search`

For each competitor, search:

- `site:[COMPETITOR WEBSITE]`
- `[COMPETITOR NAME] [PRIMARY CITY] reviews`
- `[COMPETITOR NAME] [SERVICE AREA]`

Then search service plus service-area combinations to see where competitors appear and the business does not.

Use this table:

```text
| Keyword | Monthly Intent | My Ranking | Competitor 1 | Competitor 2 | Opportunity |
|---------|----------------|-----------|--------------|--------------|-------------|
| plumber austin tx | High | Not ranking | Local Pack #1 | Local Pack #3 | High |
| emergency plumber austin | High | Not ranking | Not ranking | Organic #4 | High |
| drain cleaning round rock | Medium | Not ranking | Not ranking | Not ranking | Quick win |
| water heater installation austin | Medium | Organic #7 | Local Pack #2 | Not ranking | Medium |
```

### 3C: Service area page audit

Tool: `web_fetch`

Check whether the site has location or service-area pages such as:

- `/plumber-round-rock`
- `/plumber-cedar-park`

If pages exist, audit:

- Title tag includes service + city
- H1 includes service + city
- Unique content
- Embedded map
- Local phone or address
- LocalBusiness schema

If pages do not exist, flag as `High` and generate outlines using this template:

```text
URL: /[service]-[city-slug]

Title tag: [Service] in [City], [State] | [Business Name]
Meta description: Looking for a [service] in [City]? [Business Name] serves [City] and surrounding areas. [USP]. Call [phone] for same-day service.

H1: [Service] in [City], [State]

Content structure:
1. Intro paragraph
2. Why choose us
3. Our [City] service area
4. Services we offer in [City]
5. Customer reviews from [City]
6. FAQ section
7. Contact and CTA section
8. LocalBusiness schema in JSON-LD
```

### 3D: People Also Ask and FAQ opportunities

Tool: `web_search` and `web_fetch`

Compile all People Also Ask questions found in 3A.

For each question:

- Check whether the website already answers it
- If not, add it to the FAQ content gap list

Generate answers for the top 10 unanswered questions:

- 40 to 60 words
- Include service keyword and city naturally
- End with a soft CTA

Format as FAQPage JSON-LD:

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Question from PAA]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[40-60 word answer including keyword + city + soft CTA]"
      }
    }
  ]
}
```

### 3E: Audit 3 findings summary

Use this table:

```text
| Keyword Opportunity | Type | Current Position | Priority | Action |
|--------------------|------|-----------------|----------|--------|
| plumber round rock tx | Service area | Not ranking | High | Create /plumber-round-rock page |
| emergency plumber austin | High intent | Not ranking | High | Add to homepage + GBP |
| water heater cost austin | Informational | Not ranking | Medium | Write FAQ or blog post |
| drain cleaning near me | Near-me intent | Not in Local Pack | High | Optimise GBP + citations |
```

## Audit 4: Review monitoring and response automation

### 4A: Current review audit

Tool: `web_search`

Search:

- `"[BUSINESS NAME]" reviews`
- `[BUSINESS NAME] site:google.com/maps`
- `[BUSINESS NAME] site:yelp.com`
- `[BUSINESS NAME] site:facebook.com reviews`
- `[BUSINESS NAME] site:tripadvisor.com`
- `[BUSINESS NAME] site:bbb.org reviews`
- `[BUSINESS NAME] site:trustpilot.com`

For each platform found, record:

- Review count
- Average rating
- Most recent review date
- Oldest visible review date
- Unanswered review count
- Top 3 positive themes
- Top 3 negative themes

Use this table:

```text
| Platform | Review Count | Avg Rating | Most Recent | Unanswered | Sentiment Themes |
|----------|--------------|------------|-------------|------------|------------------|
| Google | 47 | 4.2 stars | 3 days ago | 12 | Fast service / Price too high |
| Yelp | 18 | 3.8 stars | 2 weeks ago | 6 | Friendly staff / Wait times |
| Facebook | 9 | 4.5 stars | 1 month ago | 3 | Quality work |
| BBB | 3 | 4.0 stars | 3 months ago | 0 | Professional |
```

Flag as `Critical` if:

- Google rating is below 4.0
- More than 20 percent of reviews have no response
- Negative reviews appear on page 1 of branded search results
- No new reviews appear in the last 30 days

### 4B: Competitor review benchmarking

Tool: `web_search`

For each competitor, search:

- `[COMPETITOR NAME] reviews [PRIMARY CITY]`
- `[COMPETITOR NAME] site:google.com/maps`

Use this comparison:

```text
| Business | Google Reviews | Avg Rating | Review Velocity |
|----------|----------------|------------|-----------------|
| My Business | 47 | 4.2 stars | about 2/month |
| Competitor 1 | 312 | 4.7 stars | about 15/month |
| Competitor 2 | 89 | 4.1 stars | about 4/month |
| Competitor 3 | 156 | 4.4 stars | about 8/month |
```

If competitors have materially more reviews, estimate the monthly pace needed to close the gap within 12 months.

### 4C: Review response templates

Generate ready-to-use templates for:

- 5-star positive reviews
- 3 to 4 star mixed reviews
- 1 to 2 star legitimate complaints
- Factually incorrect reviews
- Spam or fake reviews

Rules:

- Personalise where possible
- Thank the reviewer by first name if known
- Address the actual feedback
- Include business name and city naturally
- For negative reviews, apologise and move resolution offline
- Never argue defensively

### 4D: Review generation strategy

Tool: `web_search`

Search:

```text
how to ask customers for Google reviews [BUSINESS CATEGORY] best practices 2024
```

Generate:

#### SMS review request template

```text
Hi [Customer First Name], it's [Your Name] from [Business Name].
Thanks for choosing us today for your [service].

If you're happy with the work, we'd really appreciate a quick Google review -
it helps other [City] residents find us: [SHORT GOOGLE REVIEW LINK]

Takes less than a minute. Thanks so much.
```

#### Email review request template

```text
Subject: How did we do, [First Name]?

Hi [First Name],

Thank you for trusting [Business Name] with your [service] today.

We'd love to know how we did - and if you were happy with the service,
a quick Google review would mean a lot to us. It helps other people
in [City] find a reliable [business category] when they need one.

Leave a review here: [GOOGLE REVIEW LINK]

It only takes 60 seconds, and we read every single one.

Thank you again,
[Your Name]
[Business Name]
[Phone Number]
```

#### In-person card script

```text
Hi [First Name], glad we could help today. If you're happy with the work,
we'd really appreciate a quick Google review. It makes a huge difference
for a local business like ours. Just search '[Business Name] [City]' on Google
and you'll see the option to leave a review. Thank you so much.
```

#### Monitoring schedule

- Check Google, Yelp, and Facebook reviews every Monday morning
- Respond to all new reviews within 24 hours, with 48 hours as the maximum
- Escalate all new 1 to 2 star reviews the same day
- Send a review request within 2 hours of service completion

### 4E: Audit 4 findings summary

Use this table:

```text
| Issue | Platform | Severity | Detail | Action |
|-------|----------|----------|--------|--------|
| 12 unanswered reviews | Google | Critical | Some over 60 days old | Respond using templates above |
| Average rating 3.8 | Yelp | High | Below 4.0 threshold | Address recurring complaint themes |
| No reviews in 30 days | Google | High | Review velocity too low | Implement SMS and email review request |
| Competitor has 6x more reviews | Google | High | 47 vs 312 | Need 20+ reviews/month to close gap in 12 months |
| Negative review on page 1 of brand search | Google | Critical | 1-star review ranks for brand search | Respond and generate more positive reviews |
```

## Final report

After all 4 audits, compile a single unified report.

### Executive summary

- GBP completeness score: X/10
- Citation consistency: X percent of checked directories match NAP
- Local pack visibility: ranking or not ranking for X of Y target keywords
- Review profile: total reviews and average rating across platforms
- Total issues by severity

### Master priority fix list

Use this structure:

```text
| # | Issue | Audit | Tool | Est. Effort | Est. Impact |
|---|-------|-------|------|-------------|-------------|
| 1 | Respond to 12 unanswered Google reviews | Reviews | web_search | 1 hr | Critical |
| 2 | Fix NAP inconsistencies on 6 directories | Citations | web_search | 2 hrs | High |
| 3 | Add services list to GBP | GBP | Manual | 30 min | High |
| 4 | Create service area pages for Round Rock, Cedar Park | Keywords | web_fetch | 2 days | High |
| 5 | Publish weekly GBP posts | GBP | Manual | 30 min/week | Medium |
| 6 | Submit to 8 missing Tier 1 directories | Citations | Manual | 2 hrs | Medium |
| 7 | Implement SMS review request after each job | Reviews | Manual | 1 hr setup | High |
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

### 30-day local SEO action plan

- Week 1: respond to unanswered reviews, fix Tier 1 NAP issues, remove GBP violations, upload at least 10 photos
- Week 2: complete GBP services, description, hours, first post, and Q&A
- Week 3: build missing citations, create top service area pages, add FAQPage schema, launch review request workflow
- Week 4: create remaining service area pages, add LocalBusiness schema to location pages, submit pages for indexing, publish more GBP posts, start weekly review monitoring

### Deliverables included

- GBP field-by-field audit with fixes
- Competitor GBP benchmarking table
- 4 ready-to-publish GBP posts
- Citation audit table with NAP discrepancies
- Citation gap list
- Local keyword opportunity table
- Service area page templates
- FAQPage JSON-LD schema with answers
- Review audit across platforms
- Review response templates
- SMS and email review request templates
- 30-day prioritised action plan

Use this closing instruction:

```text
Now begin. Start with Audit 1 and work through all 4 audits in sequence. Use web_fetch and web_search at every step as specified. Do not stop between audits - deliver the complete unified report at the end.
```
