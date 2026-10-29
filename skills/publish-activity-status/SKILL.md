---
name: publish-activity-status
description: Explicitly prepare, review, and publish a concise coding-project activity update to an existing Notion activity record. Use only when the user requests activity status publication or a dry run.
---

# Publish activity status

## Scope and authority

This is an **explicit-invocation** workflow. Do not publish merely because a task, commit, push, or agent session ended. The repository's `AGENTS.md` and `TASKS.md` remain authoritative for local process and task details; Notion is an activity index, not a replacement task tracker. Never commit or push as part of this skill unless separately authorized.

## Configuration and context

- Obtain the target Notion database from the invocation, an existing local project configuration, or an explicitly confirmed environment default. A database URL or data-source ID is an identifier, **not** an authentication credential; do not embed a personal database URL in this reusable skill.
- Match key: `Activity ID` (text); require exactly one matching page.
- Notion access requires an authorized connector or MCP in the invoking agent environment. Do not assume another environment's connection is available.
- If invoked outside a repository workspace, ask for a repository path or other explicit source context. Do not invent `AGENTS.md` or `TASKS.md`; a Notion-only review is allowed only when the user explicitly requests it.

## Procedure

1. Confirm the user explicitly invoked this skill and whether the request is `dry-run` or `publish`. Default to **dry-run** when the requested mode is unclear.
2. Confirm the source repository/workspace, then read its `AGENTS.md`, `TASKS.md`, and only the relevant implementation/test evidence. Do not assume a clean Git tree or remote synchronization implies verification. Identify the latest relevant task and any `Awaiting user verification` marker.
3. Assemble a candidate with `activity_id`, `status`, `action_owner`, `next_action`, optional `context_url`, and an evidence note. Clearly distinguish verified facts, user reports, and inferences. Never infer `Completed` from a push, merge, or passing automated tests when UI/hardware/platform/subjective verification remains outstanding.
4. Read the Notion database schema and query by exact `Activity ID`. If no page or multiple pages match, **stop** and report the issue. Do not create a page or guess from a similar title.
5. Read the current page and compare `Status`, `Next Action`, `Action Owner`, `Context URL`, and relevant notes. Preserve other properties, manual notes, and unrelated content. If the page contains more recent or conflicting information, stop and request a decision rather than overwrite it.
6. If the proposed fields and material evidence are already present, report **no-op**. Do not append duplicate notes or make cosmetic edits solely to create an update. In **dry-run**, report proposed field-level changes and any conflicts. Perform no Notion writes.
7. In **publish**, present the proposed field-level changes for user approval unless the user has already explicitly approved those exact changes. Then update only approved fields, and append or narrowly edit evidence notes without erasing user content. Do not set `Waiting Since` without a supported start date.
8. Verify the updated record by a read-back or a successful authoritative update response, and report the record URL, changed fields, and remaining user action. If the update fails or cannot be verified, report uncertainty without claiming success.

## Status mapping

- `Pending`: no confirmed implementation in progress or awaiting a future start.
- `In Progress`: work is actively underway; do not infer this from repository activity alone.
- `Awaiting User Verification`: an implementation/result is ready for a user-dependent check, or the user explicitly identifies a pending evaluation. Mark provisional when readiness itself is uncertain.
- `Decision Required`: a user decision is needed before progress.
- `Blocked`: a known obstacle prevents progress; identify blocker and owner.
- `Completed`: all required checks, including user verification where applicable, have been confirmed.
- `Cancelled`: user explicitly cancels the activity.

`Action Owner` must be `User`, `Agent`, `External`, or `None`. Avoid claiming an agent is currently acting unless evidence supports it.

## Output

Report: activity ID and Notion URL; mode (`dry-run` or `publish`); source evidence; current versus proposed field values; conflict/warning list; update result; next-action classification (`No user action`, `Permission`, `Decision`, `User verification`, or `Blocked`).
