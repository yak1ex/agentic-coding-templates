# TASKS.md

## Project objective

{{PROJECT_OBJECTIVE}}

## Scope and constraints

- In scope: {{IN_SCOPE}}
- Out of scope: {{OUT_OF_SCOPE}}
- Deployment target: {{DEPLOYMENT_TARGET}}
- Important constraints: {{IMPORTANT_CONSTRAINTS}}

## Current status

{{CURRENT_STATUS_SUMMARY}}

## Active task

- Task: `{{ACTIVE_TASK_ID_OR_NONE}}`
- Current step: {{CURRENT_STEP_OR_NONE}}
- Next verification: {{NEXT_VERIFICATION_OR_NONE}}
- Waiting on: `{{AGENT_USER_EXTERNAL_OR_NONE}}`
- Required action: {{REQUIRED_ACTION_OR_NONE}}

## Tasks

Use stable IDs. Append newly discovered work using the next unused ID. Never reuse an ID or renumber existing tasks without explicit user approval.

### T001 — {{TASK_TITLE}}

- Status: pending
- Objective: {{VERIFIABLE_OUTCOME}}
- Scope:
  - {{INCLUDED_WORK}}
- Acceptance criteria:
  - {{ACCEPTANCE_CRITERION}}
- Implemented:
  - None.
- Verification:
  - Not run.
- Remaining:
  - {{REMAINING_WORK}}
- Notes:
  - {{OPTIONAL_NOTES}}

<!-- Copy the task block above for T002, T003, and later tasks. -->

## Decisions

Record short project decisions that affect future implementation. Use a separate design document when analysis, alternatives, diagrams, or specifications become substantial.

### D001 — {{DECISION_TITLE}}

- Date: {{YYYY-MM-DD}}
- Status: accepted
- Decision: {{DECISION}}
- Rationale: {{RATIONALE}}
- Consequences:
  - {{CONSEQUENCE}}
- Related tasks: `{{TASK_IDS}}`

## Blocked items

Keep the primary task entry authoritative. This section is a compact index for visibility.

- None.

<!-- Example: - `T004`: Waiting for target hardware; required to verify USB reconnect behavior. -->

## Cancelled items

Keep the original task and ID with `Status: cancelled`; record the reason and replacement task where applicable.

- None.

<!-- Example: - `T006`: Cancelled because the feature was superseded by `T009`. -->

## Backlog

Ideas not yet accepted into the mainline implementation plan. Backlog items do not require task IDs until promoted.

- {{BACKLOG_ITEM_OR_NONE}}
