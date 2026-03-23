---
name: local-seo
description: Local SEO audit workflow for Google Business Profile optimisation, citation and NAP consistency checks, local keyword opportunity analysis, service area page planning, and review monitoring using web_fetch and web_search. Use when the user wants a full local SEO audit, competitor GBP benchmarking, citation gap analysis, local keyword research, FAQ and schema generation, review response templates, or a prioritised 30-day action plan for a local business.
---

# Local SEO

Run a full local SEO audit across Google Business Profile, citations, local keyword coverage, and reviews. Keep this file focused on workflow rules and open the detailed operating guide only when you need the exact audit steps, templates, response copy, or final report format: [references/local-seo-master-audit-and-automation.md](references/local-seo-master-audit-and-automation.md).

## Core rules

- Work through all 4 audits in sequence unless the user explicitly asks for only one area.
- Use only `web_search` and `web_fetch` throughout the workflow.
- Do not invent GBP fields, directory listings, rankings, reviews, or NAP details.
- If a listing or directory page cannot be verified, say so explicitly and continue.
- Treat NAP consistency as exact-match work once the canonical website NAP is identified.
- Prioritise fixes that improve local pack visibility, trust, conversion rate, and review health.
- When a finding is actionable, include the exact fix or template needed to implement it.
- Use these severity labels consistently:
  - `Critical`: directly harms visibility, trust, compliance, or conversion
  - `High`: major local ranking or customer-experience issue
  - `Medium`: meaningful optimisation gap
  - `Low`: minor or batchable improvement

## Required inputs

- Business name
- Business website
- Business address
- Phone number
- Business category
- Primary city or region
- Service areas
- Google Business Profile URL if known
- Top 3 competitors
- Primary services

## Tool routing

Use these tools only:

- `web_search`: locate GBP profiles, competitor listings, directories, local pack presence, review pages, local queries, and best-practice references
- `web_fetch`: verify website NAP, inspect page content, confirm schema, audit service area pages, and check whether the site already answers FAQ opportunities

## 4-audit execution

### Audit 1: Google Business Profile

- Find and audit the live GBP listing
- Benchmark competitor GBP profiles
- Audit post freshness and activity
- Generate 4 ready-to-publish GBP posts
- Summarise all GBP findings in one fix table

### Audit 2: Citations and NAP consistency

- Extract canonical NAP from the website
- Audit Tier 1, category-specific, and local directory listings
- Build the NAP inconsistency report
- Identify citation gaps from ranking local directories

### Audit 3: Local keyword research and rankings

- Discover core local search opportunities
- Compare competitor coverage and service-area visibility
- Audit or propose service area pages
- Compile People Also Ask questions and generate FAQ schema answers

### Audit 4: Review monitoring and response automation

- Audit reviews across all visible platforms
- Benchmark competitors on review count, rating, and velocity
- Generate response templates for positive, mixed, negative, and fake reviews
- Generate review request templates and a monitoring schedule

## Output structure

Use this structure unless the user asks for something else:

1. Executive summary
   Include GBP completeness, citation consistency, local pack visibility, review profile, and issue counts
2. Master priority fix list
   Sort by severity and business impact
3. Audit 1 full findings
4. Audit 2 full findings
5. Audit 3 full findings
6. Audit 4 full findings
7. 30-day local SEO action plan

## Expected deliverables

Produce these when the evidence supports them:

- GBP field-by-field audit
- Competitor GBP benchmark table
- 4 GBP posts
- Citation audit table and citation gap list
- Local keyword opportunity table
- Service area page outlines
- FAQPage JSON-LD answers
- Review audit table
- Review response templates
- SMS and email review request templates

## Failure handling

- If the GBP URL is unknown, search by business name plus city and proceed from the best-supported listing.
- If a directory listing cannot be confirmed, mark it as `Can't verify` instead of guessing.
- If service area pages do not exist, generate outlines for the highest-priority locations.
- If review counts or dates are partially visible only, state the limitation and continue with the visible data.
