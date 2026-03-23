---
name: seo-audit
description: Full-site SEO audit workflow for both existing and brand-new sites, with interview-first routing, technical, on-page, content, off-page, local, and E-E-A-T checks, plus setup-first auditing for new launches. Use when the user wants Claude to ask audit setup questions first, choose the correct audit mode, inspect connected SEO tools, produce a master issues table, generate schema fixes, prepare a disavow file if needed, and deliver a prioritised 30-60-90 day action plan.
---

# SEO Audit

Run SEO audits as an interview-first workflow that branches into existing-site or new-site auditing. Keep this file focused on routing, tool use, and deliverables. Open the full reference guide only when you need the exact interview script, audit checklists, issue tables, or final output formats: [references/seo-audit-master-prompt-existing-and-new-sites.md](references/seo-audit-master-prompt-existing-and-new-sites.md).

## Core rules

- Do not start any audit until the full interview is complete.
- Ask the initial interview as one grouped message, not one question at a time.
- Route into the correct case before auditing:
  - Existing site
  - Brand new site
- Use the right mindset for the case:
  - Existing site: diagnose current problems and opportunities
  - New site: prevent setup mistakes and create a launch-ready SEO foundation
- Use only the tools that make sense for the selected case.
- Produce all required deliverables at the end, not partial outputs midstream unless the user asks.
- Keep findings specific, actionable, and prioritised by severity, impact, and effort.

## Required workflow

### Phase 0: Initial interview

Ask the complete interview and wait for all answers. Capture:

- Site URL
- Existing versus new status
- Site type
- Primary goal
- Competitors
- Important keywords or topics
- Target market
- Local targeting
- Connected tools for existing sites
- Site age and recent issues for existing sites
- Build status for new sites

### Phase 1: Route to the correct audit mode

#### Existing site audit

Use these tools when available:

- `GSC`
- `GA4`
- `Ahrefs`
- `Semrush`
- `web_fetch`
- `web_search`

Run these audit areas:

- Technical SEO
- On-page SEO
- Content SEO
- Off-page SEO
- Local SEO, if relevant
- E-E-A-T and trust signals

#### New site audit

Use these tools:

- `web_fetch`
- `web_search`

Focus on:

- Indexation and crawl setup
- On-page foundation
- Technical foundation
- Keyword and competitor foundation
- E-E-A-T and trust setup
- Pre-launch and post-launch checklist

## Output deliverables

Always deliver these at the end:

1. Master issues table
   Include markdown table and CSV version
2. Executive summary
   Include health score, top issues, quick wins, strengths, traffic opportunity, and 30-60-90 day plan
3. Schema blocks
   Ready-to-implement JSON-LD for missing or broken schema
4. Disavow file
   Only if toxic links justify it

## Severity and prioritisation

Use these severity labels consistently:

- `Critical`: fix within 48 hours
- `High`: fix within 1 week
- `Medium`: fix within 1 month
- `Low`: fix when time allows

Also assign:

- Impact: `High`, `Medium`, or `Low`
- Effort: `Quick win`, `Low`, `Medium`, `High`, or `Ongoing`

## Failure handling

- If a connected tool is unavailable, say so explicitly and continue with the remaining evidence.
- If an audit area does not apply, such as local SEO for a non-local site, skip it and say why.
- If a site is still in development, treat all findings as setup and prevention tasks rather than live-site failures.
- If evidence is incomplete, avoid guessing and note the limitation.
