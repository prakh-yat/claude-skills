---
name: off-page-seo
description: Off-page SEO workflow for guest post prospecting, qualification, contact extraction, and outreach email drafting using web search, page fetching, Gmail, and follow-up scheduling. Use when the user wants to find guest post opportunities in a niche, filter low-quality prospects, inspect recent content and editorial standards, extract contact details, draft personalised outreach emails, send selected pitches, or prepare follow-up reminders for guest posting campaigns.
---

# Off-Page SEO

Run structured guest post outreach from prospecting through email drafting. Keep this file focused on workflow rules and open the detailed reference guide only when you need the exact prompt text, qualification rubric, outreach template, or sending rules: [references/guest-post-outreach-automation.md](references/guest-post-outreach-automation.md).

## Core rules

- Execute the full 5-phase workflow in order for end-to-end outreach unless the user asks for a narrower task.
- Do not stop for confirmation between phases unless a required variable is missing or the user wants emails sent.
- Only keep sites scoring 3 out of 5 or better on the qualification rubric.
- Discard any site that charges for guest posts, states links are nofollow-only, shows obvious content-farm signals, or lacks real editorial presence.
- Ground every compliment, topic pitch, and tone match in content actually found on the target site.
- Never invent contact names, post titles, niche coverage, or submission rules.
- If a page blocks fetching, mark it as `manual check required` and continue.
- Never mention `backlink`, `SEO`, `link building`, `domain authority`, or `rankings` in outreach emails.
- Keep outreach emails under 180 words.
- Use the contact person's first name when found; otherwise address the site team by site name.
- Offer Gmail sending and follow-up reminders only after presenting the full results, or when the user explicitly asks to send.

## Required inputs

- Niche or keyword
- Website URL
- Sender name
- One-line credibility statement
- Target countries
- Optional competitor domain
- Whether Gmail sending is desired

## Workflow modes

### Full outreach run

Use all 5 phases when the user wants end-to-end guest post outreach.

### Send selected emails

If the user wants sending, confirm which site numbers to send, show the final drafts first, then send and offer 7-day follow-up reminders.

### Follow-up only

Use the follow-up template when an earlier pitch has gone unanswered for about 7 days.

## 5-phase execution

### Phase 1: Generate search queries

- Generate 12 operator-based Google queries using the keyword.
- Add competitor-related queries if a competitor domain is provided.
- Apply country filters and negative filters to reduce low-quality results.

### Phase 2: Search and qualify prospects

- Search the queries and fetch the top results.
- Score each site against the 5-point rubric.
- Discard weak or disqualified sites immediately.

### Phase 3: Extract contacts and topic fit

- Capture site name, guest post URL, contact person, email or form, recent posts, niche tags, and qualification score.

### Phase 4: Draft personalised outreach

- Reference a real recent post.
- State the user's credibility in one sentence.
- Pitch 2 to 3 specific, benefit-led topics aligned to the site's existing content and gaps.

### Phase 5: Present results

- Show the summary table first.
- Then show each email draft in full.
- End by asking whether to send, schedule follow-ups, or export a summary.

## Output format

Use this structure unless the user asks for something else:

1. Summary table
   Columns: number, site, contact, email or form, qualification score, topics matched, status
2. Draft emails
   One section per site with subject, recipient, and full body
3. Discarded sites
   Include only when useful, with a short rejection reason
4. Action prompt
   Ask whether to send, schedule reminders, or export

## Qualification standard

Score 1 point for each:

- Guest post acceptance page exists
- Niche relevance is direct or adjacent
- Site has recent activity
- Contact route is available
- Editorial standards are visible

Reject sites below 3 out of 5.

## Failure handling

- If search returns too few results, broaden keyword variants and operator patterns.
- If no direct email exists, include the contact form URL and note that the message must be pasted into the form.
- If fetch access is blocked, note `could not access - manual check recommended`.
- If the prospect only accepts paid placements, discard it immediately.
- If the site's content does not match the niche after inspection, discard it and note the reason.
