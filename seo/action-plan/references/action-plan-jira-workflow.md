# Action Plan Jira Workflow

Detailed workflow, Jira interview rules, task-design standards, scheduling logic, workbook schema, and the master instruction block for using `action-plan` as the post-analysis execution skill.

## Table of contents

- [01. System overview](#01-system-overview)
- [02. Pre-creation interview and Jira field rules](#02-pre-creation-interview-and-jira-field-rules)
- [03. Task design standards](#03-task-design-standards)
- [04. Scheduling rules](#04-scheduling-rules)
- [05. Workbook output standard](#05-workbook-output-standard)
- [06. Master integration instruction](#06-master-integration-instruction)
- [07. Final validation checklist](#07-final-validation-checklist)

## 01. System overview

### What this skill does

This skill converts analysis findings into Jira-ready implementation tasks and a clean `.xlsx` workbook. It is meant for the point after the analysis is done and the user wants execution tasks that can be reviewed, scheduled, and then created in Jira.

### What this skill must not do

- Do not create tasks for Reporting work
- Do not skip the clarifying-question step
- Do not create Jira issues with missing mandatory fields
- Do not stack overlapping tasks on the same time block

## 02. Pre-creation interview and Jira field rules

### Required pre-creation interview

Before building the action plan or creating Jira issues, ask for or confirm all of the following:

- Desired start date in the near future
- Jira space or project
- Assignee
- Priority
- Sprint, or confirmation to use the current sprint
- Parent or epic, if applicable
- Labels or label format
- Whether the user wants workbook only or actual Jira creation
- Whether the `08:00-09:00` meeting blocks the full hour every workday

When the host supports it:

- Use `ask_user_input`
- List the available Jira spaces and let the user choose one

### Mandatory Jira fields

Every Jira issue must have all of these fields:

- `Summary`
- `Description`
- `Start Date`
- `Due Date`
- `Story Points`
- `Sprint`
- `Labels`
- `Parent`, if applicable
- `Priority`
- `Assignee`
- `Project/Space`

### Story points and estimates

- If the user already provides story points or hours, use them
- If not, derive them from the analysis and present them for confirmation before creating Jira issues
- Do not leave story points blank

### Description formatting rule

- Descriptions must be detailed and cleanly written
- Do not include raw escape characters such as `\n`, `\/`, or other raw formatting artifacts
- Use proper Jira fields instead of dumping every detail into the description
- Keep descriptions implementation-focused: scope, context, expected outcome, and constraints

## 03. Task design standards

### Core rules

- Create deliverable-based tasks, not vague edit labels
- Group similar low-level work into one meaningful Jira issue
- Make the summary specific enough to understand the scope immediately
- Put the detail in the description, not in an unreadable summary
- Exclude Reporting work from the plan entirely

### Bad versus good task examples

| Bad task | Why it fails | Better Jira-ready task |
| --- | --- | --- |
| `Update H1 - 1 hr` | Too vague, too small, no scope | `Rewrite titles, meta descriptions, and H1s for 8 priority category pages based on GSC intent gaps, then QA the copy before CMS upload` |
| `Fix technical SEO - 2 hrs` | Mixed scope and weak summary | `Resolve indexability issues on filtered collection URLs by updating crawl directives, validating templates, and confirming the final indexable set` |
| `Add links - 1 hr` | No target set or deliverable | `Map and place contextual internal links from 12 supporting articles to 3 priority money pages, update anchor text, and verify crawl flow` |
| `Do content work - 3 hrs` | Not assignable in Jira | `Expand the dog harness category page with comparison copy, trust signals, and a 4-question FAQ based on competitor and GSC gaps` |

### Task grouping rules

Group work when:

- The same workstream and page set are involved
- One person can complete the work in one flow
- The output is one coherent deliverable

Split work when:

- Different owners are required
- One task would be too large or spans multiple deliverables
- There is a dependency blocker
- The work crosses the requested planning horizon

## 04. Scheduling rules

### Calendar rules

- Timezone: `Asia/Kathmandu`
- Work days: Monday to Friday only
- Work hours: `08:00-17:00`
- Breaks:
  - `10:00-10:15`
  - `12:00-13:00`
  - `15:00-15:15`
- Daily meeting: `08:00-09:00`, but ask the user whether this fully blocks the hour before scheduling around it

### Core scheduling rule

Multiple tasks per day are allowed. The only hard rules are:

- No overlapping task timeframes
- No scheduling outside working hours
- No scheduling during breaks
- No weekend scheduling
- No daily overbooking beyond the confirmed productive windows

### Practical scheduling logic

- Use the earliest available non-overlapping block for each task
- If a task fits in the remaining time of a day, it may share that day with other tasks
- If a task does not fit, continue it on the next available workday
- `Start Date` is the first workday containing scheduled time for that issue
- `Due Date` is the last workday containing scheduled time for that issue
- Keep the schedule sequential with no artificial gaps unless a dependency forces one

### Base schedulable windows

Use these windows by default:

- `10:15-12:00`
- `13:00-15:00`
- `15:15-17:00`

Add any confirmed free time from the morning window only after the user confirms how the `08:00-09:00` meeting behaves.

### Daily capacity rule

- Never exceed `7.25` scheduled task-hours per day
- Also never exceed the sum of the actually confirmed free windows for that day
- If the confirmed free windows total less than `7.25`, use the smaller number

### Monthly planning rule

- If the user asks for a month-long plan, spread tasks across the month with no overlap
- If all work does not fit, schedule the highest-priority items first and move the remainder to backlog

## 05. Workbook output standard

Every final deliverable must be an Excel `.xlsx` workbook.

### Default sheets

- Sheet 1: `Jira Issues`
- Sheet 2: `Schedule`
- Sheet 3: `Summary`, when useful

### `Jira Issues` sheet columns

Use this column order:

1. `Project/Space`
2. `Summary`
3. `Description`
4. `Assignee`
5. `Priority`
6. `Sprint`
7. `Parent`
8. `Labels`
9. `Story Points`
10. `Estimated Hours`
11. `Start Date`
12. `Due Date`
13. `Notes`

### `Schedule` sheet columns

Use this column order:

1. `Date`
2. `Time Frame`
3. `Summary`
4. `Assignee`
5. `Estimated Hours`
6. `Sprint`
7. `Notes`

### Workbook rules

- `Jira Issues` has one row per Jira issue
- `Schedule` has one row per scheduled time block
- Time blocks must not overlap
- The `Summary` used in `Schedule` must match the Jira issue summary
- If a task spans multiple days, keep one Jira issue row and multiple schedule rows

## 06. Master integration instruction

Use the following instruction block to make sure the `action-plan` skill is actually used at the right point in the workflow.

```text
Current Year: 2026

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CORE WORKFLOW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

STEP 1 — URL INPUT -> PRELIMINARY SCAN

When the user provides a site URL:
- Scan the site at a high level
- Identify the business type
- Identify likely competitors

STEP 1.1 — TASK SELECTION
Immediately ask this question using ask_user_input:

Q: What do you want to do for this site? (multi-select)
Options:
- SEO Audit
- On Page SEO
- Keyword Research
- Technical SEO
- Off Page SEO
- Local SEO
- Content Writing
- Reporting
- Action Plan
- All

STEP 2 — SKILL ROUTING
Route each selection to its skill file before executing:

- SEO Audit        -> /mnt/skills/user/seo-audit/SKILL.md
- On Page SEO      -> /mnt/skills/user/on-page-seo/SKILL.md
- Keyword Research -> /mnt/skills/user/keyword-research/SKILL.md
- Technical SEO    -> /mnt/skills/user/technical-seo/SKILL.md
- Off Page SEO     -> /mnt/skills/user/off-page-seo/SKILL.md
- Local SEO        -> /mnt/skills/user/local-seo/SKILL.md
- Content Writing  -> /mnt/skills/user/content-writing/SKILL.md
- Reporting        -> reporting skill
- Action Plan      -> /mnt/skills/user/action-plan/SKILL.md
- All              -> run every non-reporting SEO skill sequentially, then offer Action Plan

If the user selects multiple analysis skills:
- Run each selected skill sequentially
- Deliver one integrated report
- After the report, ask whether to convert the findings into a Jira action plan using /mnt/skills/user/action-plan/SKILL.md

STEP 3 — CROSS-QUESTION BEFORE EXECUTION
Before executing any skill, ask clarifying questions to understand:
- Primary goal
- Target audience
- Known competitors
- Priorities or focus areas

Never assume. Always confirm first.

STEP 4 — ACTION PLAN HANDOFF
After any long analysis task, ask:
"Do you want me to convert these findings into a Jira-ready action plan?"

If yes:
- Route to /mnt/skills/user/action-plan/SKILL.md
- Do not include Reporting items in the Jira task list

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AVAILABLE TOOLS & USAGE RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- Google Search Console -> use freely
- Google Analytics (GA4) -> use freely
- Ahrefs -> ask permission before using
- Gmail -> use freely
- Jira (Atlassian) -> always list available spaces and let the user choose the space or project before creating tasks

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ACTION PLAN + JIRA TASK CREATION RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

IMPORTANT: NEVER CREATE TASKS FOR REPORTING

PRE-CREATION INTERVIEW
Before generating the action plan or creating Jira issues, always ask for:
- Desired start date in the near future
- Jira space or project
- Assignee
- Priority
- Sprint, or confirmation to use the current sprint
- Parent or epic, if applicable
- Labels
- Whether the 08:00-09:00 meeting fully blocks the hour
- Whether the user wants workbook only or actual Jira creation after review

If estimated hours or story points are not provided:
- Derive them from the analysis
- Present them for confirmation before Jira creation

MANDATORY JIRA FIELDS
Every Jira issue must include:
- Summary
- Description
- Start date
- Due date
- Story points
- Sprint
- Labels
- Parent, if applicable
- Priority
- Assignee
- Project/Space

DESCRIPTION RULE
- Descriptions must be detailed and cleanly written
- No raw escape characters
- Use proper Jira fields instead of dumping everything into the description

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WORKING HOURS & CALENDAR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- Timezone: Asia/Kathmandu
- Work days: Monday to Friday only
- Work hours: 08:00 AM - 05:00 PM
- Breaks: 10:00-10:15 AM | 12:00-01:00 PM | 03:00-03:15 PM
- Daily meeting: 08:00-09:00 AM, but confirm whether it blocks the full hour before scheduling

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DATE SCHEDULING RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

MULTIPLE TASKS PER DAY ARE ALLOWED
Tasks may share the same date if:
- Their time frames do not overlap
- They stay inside confirmed working windows
- The day's total scheduled hours do not exceed the confirmed capacity

HARD RULES
- No overlapping task time frames
- No weekend scheduling
- No break-time scheduling
- No overbooking beyond the confirmed productive windows

SCHEDULING LOGIC
- Use the earliest available non-overlapping time block for each task
- Keep tasks sequential with no artificial gaps unless dependencies require a gap
- If a task does not fit in the remaining hours of a day, continue it on the next available workday
- Start date = first day that task has scheduled time
- Due date = last day that task has scheduled time
- If the user wants a month-long plan, spread tasks across the month with no overlap

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OUTPUT FORMAT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Every final action-plan deliverable must be an Excel (.xlsx) workbook with:
- A Jira Issues sheet
- A Schedule sheet
- A Summary sheet when useful

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GENERAL BEHAVIOUR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- ALWAYS ask clarifying questions before acting on any request
- Cross-question the user to confirm intent, scope, and details before creating tasks, running audits, or producing outputs
- Never assume. Never skip the question step
```

## 07. Final validation checklist

- [ ] Was the pre-creation interview completed before task generation?
- [ ] Were Reporting tasks excluded?
- [ ] Does every Jira issue include all mandatory Jira fields?
- [ ] Are descriptions clean and free of raw escape characters?
- [ ] Are tasks grouped into meaningful Jira issues instead of vague micro-tasks?
- [ ] Are multiple tasks per day non-overlapping?
- [ ] Are weekends, breaks, and unavailable meeting windows excluded?
- [ ] Does the workbook contain `.xlsx` output with `Jira Issues` and `Schedule` sheets?
