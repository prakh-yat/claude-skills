---
name: content-writing
description: SEO content writing workflow for collection pages, product pages, blog posts, service pages, and custom page types. Use when the user wants Claude to interview them first, route to the correct content type, research SERP structure, write conversion-focused SEO copy, generate metadata and schema, suggest internal links, or revise content tone, length, and structure after delivery.
---

# Content Writing

Run SEO content writing as a structured interview and drafting workflow. Keep this file focused on the operating rules and open the full reference prompt only when you need the exact interview text, routing instructions, structure rules, or output blocks: [references/content-writing-master-prompt.md](references/content-writing-master-prompt.md).

## Core rules

- Do not write any content until the interview phases are complete.
- Ask grouped questions, not one question at a time.
- Route the task into the correct content mode before writing:
  - Collection or category page
  - Product page
  - Blog post or article
  - Service page
  - Other, with clarified requirements
- Adjust tone, structure, CTA style, and SEO approach based on the user's answers.
- Use silent research with `web_search` and `web_fetch` before drafting when those tools are available.
- Do not expose the research process unless the user asks.
- Match the requested brand tone while keeping the copy natural and readable.
- Avoid filler, forced keyword repetition, and generic openers.
- After the main content, always include metadata, schema markup, internal link suggestions, and the SEO checklist.
- End by offering revision options.

## Required workflow

### Phase 0: Initial interview

Ask the full initial interview as one numbered list and wait for the user's answers.

### Phase 1: Content-type routing

Select the writing mode from the user's answer:

- `A`: Collection or category page
- `B`: Product page
- `C`: Blog post or article
- `D`: Service page
- `E`: Other

If the user selects `Other`, ask for more context and adapt the closest structure.

### Phase 2: Secondary questions

Ask the secondary grouped questions after routing:

- Brand name
- Word count preference
- Supporting materials or references
- Whether to write the meta title and description
- Whether to generate JSON-LD schema

### Phase 3: Pre-write research

Use these tools when available:

- `web_search`: inspect page-1 results, People Also Ask questions, and competitor patterns
- `web_fetch`: inspect competitor structure and content gaps when a competitor URL is provided

Use the findings silently to improve the content.

### Phase 4: Write the content

Write the full piece using the exact structure required for the chosen content type.

### Phase 5: Offer revisions

After delivery, offer tone changes, length changes, hook rewrites, alternate H1 and meta titles, or the next page in the same style.

## Output requirements

Always include these sections after the main content:

1. `META DATA`
   - Meta title
   - Meta description
   - URL slug suggestion
2. `SCHEMA MARKUP`
   - Relevant JSON-LD block
3. `INTERNAL LINK SUGGESTIONS`
   - 2 to 4 suggested links with anchor text and placement
4. `SEO CHECKLIST`
   - Keyword placement
   - H2 coverage
   - Internal links
   - FAQ schema
   - Image alt text suggestions
   - Final word count

## Writing constraints

- Use proper heading hierarchy
- Keep paragraphs short
- Use bullet lists when scanning matters
- Bold the first 2 to 3 words of key paragraphs
- Prefer active voice
- Avoid stale filler phrases
- Keep keyword usage natural

## Failure handling

- If the user gives incomplete answers, ask only the missing grouped follow-up needed to proceed.
- If research tools are unavailable, continue with best-practice drafting and state the limitation only if it affects accuracy.
- If the requested word count conflicts with the page type, follow the user's preference but note the tradeoff when useful.
