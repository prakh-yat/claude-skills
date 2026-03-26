---
name: action-plan
description: Create Jira-ready action plans and `.xlsx` task sheets from SEO analyses, audit findings, and implementation recommendations. Use when the user wants execution tasks after SEO Audit, On Page SEO, Keyword Research, Technical SEO, Off Page SEO, Local SEO, or Content Writing; wants work scheduled across days or a full month; needs Jira fields such as summary, description, assignee, sprint, priority, story points, labels, parent, start date, and due date; or wants non-overlapping task blocks in Asia/Kathmandu business hours. Do not use for Reporting tasks.
---

# Action Plan

Turn completed analysis into Jira-ready tasks and an `.xlsx` action plan. Keep this file focused on operating rules and open the reference manual only when you need the detailed interview flow, task-writing rules, scheduling logic, workbook schema, or the master integration instruction: [references/action-plan-jira-workflow.md](references/action-plan-jira-workflow.md). Use [assets/action-plan-template.xlsx](assets/action-plan-template.xlsx) as the default workbook template.

## Core rules

- Use this skill after analysis is complete or when the user explicitly asks for tasks, a Jira plan, an implementation sheet, or a monthly action plan.
- Never create action-plan tasks for Reporting work.
- Always run the pre-creation interview before generating or creating Jira tasks. Never skip the question step.
- Use `ask_user_input` when the host supports it. Otherwise ask grouped clarifying questions in one message.
- The interview must collect or confirm:
  - Desired start date in the near future
  - Jira space or project, after listing the available spaces
  - Assignee
  - Priority
  - Sprint, or confirmation to use the current sprint
  - Parent or epic, if applicable
  - Label convention
  - Whether the `08:00-09:00` daily meeting fully blocks that hour for scheduling
  - Whether the user wants a workbook only or actual Jira issue creation after review
- If task-level story points or estimated hours are not supplied, derive them from the analysis and present them for confirmation before Jira creation.
- Every Jira issue must include: `Summary`, `Description`, `Start Date`, `Due Date`, `Story Points`, `Sprint`, `Labels`, `Parent` if applicable, `Priority`, `Assignee`, and `Project/Space`.
- Descriptions must be detailed, clean, and written as normal prose. Do not include raw escape characters such as `\n` or `\/`.
- Group related low-level fixes into meaningful tasks. Do not produce vague micro-tasks like `Update H1` unless the scope is truly isolated and justified.
- Multiple tasks may be scheduled on the same workday as long as they do not overlap and the total scheduled time stays within the confirmed productive windows.
- Schedule only on Monday to Friday in `Asia/Kathmandu`.
- Final output must be an Excel `.xlsx` workbook. If `.xlsx` creation is unavailable, say so explicitly before finalizing instead of silently changing the format.

## Required workflow

### Phase 0: Confirm the source analysis

- Confirm which analysis or report the tasks should be built from
- Confirm that Reporting items must be excluded
- Confirm whether the user wants planning only or Jira issue creation after review

### Phase 1: Run the Jira pre-creation interview

- List available Jira spaces and let the user choose the project or space
- Collect the required Jira fields and schedule inputs
- Confirm whether to use the current sprint or a named sprint
- Confirm whether the `08:00-09:00` meeting is fully blocked every workday

### Phase 2: Convert findings into Jira-ready tasks

- Build outcome-based summaries, not vague fix labels
- Write detailed descriptions with clear scope and expected output
- Assign story points, estimated hours, labels, dependencies, and ownership
- Exclude Reporting items from the task list

### Phase 3: Schedule the work

- Place tasks into non-overlapping weekday time blocks
- Allow multiple tasks per day when they fit the confirmed capacity
- Keep dates sequential and avoid unnecessary gaps unless dependencies require them
- Spread work across the requested horizon, including a full month when asked

### Phase 4: Deliver the workbook and optionally create Jira issues

- Produce the `.xlsx` workbook first for review
- If the user confirms creation, create Jira issues using the workbook fields
- Return a short creation summary with issue counts and any skipped items

## Output requirements

Always include:

1. `Jira Issues` sheet
   One row per Jira issue with all required Jira fields.
2. `Schedule` sheet
   One row per scheduled time block with non-overlapping time frames.
3. `Summary` sheet, when helpful
   State the planning horizon, scheduled hours, task count, assumptions, and backlog if anything did not fit.

## Reference map

Open the reference manual only when needed:

- Section 02 for the pre-creation interview and Jira field rules
- Section 03 for task design standards
- Section 04 for scheduling rules
- Section 05 for workbook schema
- Section 06 for the master instruction block
- Section 07 for the final validation checklist

## Failure handling

- If the required interview inputs are missing, ask for them before building Jira issues.
- If the schedule rules and available time windows conflict, ask the user to confirm which window is truly available instead of guessing.
- If the requested work does not fit inside the chosen horizon, schedule the highest-priority tasks first and place the rest in backlog.
- If the tasks look too vague, too small, or too generic, rewrite and regroup them before finalizing the workbook.
