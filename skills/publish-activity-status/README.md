# publish-activity-status

Reusable, explicitly invoked skill for publishing repository activity summaries to an existing Notion record.

## Install

Copy `SKILL.md` to your agent's recognized local skills directory (for example `~/.agents/skills/publish-activity-status/SKILL.md`). Confirm skill discovery in the actual agent session.

## Configuration

Provide the Notion database URL or data-source ID in the invocation or through an explicitly confirmed local configuration. This package does not contain a personal database URL, credentials, or an automatic configuration loader. An authorized Notion tool connection is required.

## Example invocation

> Use `publish-activity-status` for a dry run of activity `git-credential-management` in the current repository. Target the existing `Personal Activities` Notion database [supply its URL or confirmed local default]. Do not write to Notion or modify the repository.

## Pilot fixture

See `examples/ghgcm-t007.md` for the original pilot's expected behavior. The example is not part of the generic skill instructions.
