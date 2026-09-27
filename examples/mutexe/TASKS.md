# TASKS.md

## Project objective

Develop a Windows desktop utility that mutes and unmutes individual processes by invoking `soundvolumeview.exe`, with configurable static buttons and dynamically managed buttons for watched executables.

## Scope and constraints

- In scope: process-specific mute control, external TOML configuration, process detection, watched-directory discovery, and a compact `tkinter` UI.
- Out of scope: bundling SoundVolumeView and automatic installation of external runtime tools.
- Deployment target: Windows desktop.
- Important constraints: SoundVolumeView is resolved through `PATH`; user-visible and external-tool behavior requires Windows verification.

## Current status

Configuration loading, static process detection, watched executable buttons, and automatic window resizing are implemented. Existing records report Python syntax verification; live Windows behavior should be treated according to the verification evidence recorded per task.

## Current plan

- None. No accepted unfinished work is currently ordered for execution.
- Selection basis: Establish an agreed outcome before beginning further implementation.
- Last reviewed: 2026-09-06

## Active work

- Task: `none`
- Current step: No active implementation step is recorded.
- Waiting on: `none`
- Required action: None.

## Tasks

### T001 — Move target executables and labels to a configuration file

- Status: completed
- Objective: Load static button definitions from a user configuration file instead of hardcoded Python data.
- Scope:
  - Read `%USERPROFILE%/.config/browrdr/config.toml` using a `[[buttons]]` table array.
  - Support `exe` and `short_name` fields.
  - Fail clearly when configuration is missing or invalid.
- Acceptance criteria:
  - The hardcoded button list is removed.
  - Valid configuration creates the expected button definitions.
  - Invalid or missing configuration produces a clear failure.
- Implemented:
  - Added TOML configuration loading with `tomllib` and a `tomli` fallback for older Python.
  - Resolved the configuration path through `%USERPROFILE%`.
  - Removed the hardcoded `BUTTONS` list.
- Verification:
  - A configuration with two button entries was created.
  - `python -m py_compile app.py` passed according to the source task record.
- Remaining:
  - None recorded.
- Notes:
  - The recorded path uses `browrdr`; confirm whether this historical name should be migrated to `mutexe` before changing it.

### T002 — Disable static buttons for processes that are not running

- Status: completed
- Objective: Reflect current process availability and prevent mute commands for absent processes.
- Scope:
  - Detect process names case-insensitively.
  - Update static button state at startup and periodically.
  - Recheck process state before executing an action.
- Acceptance criteria:
  - Buttons are disabled while their target process is absent.
  - Buttons become available when the process starts.
  - No SoundVolumeView action is issued for an absent process.
- Implemented:
  - Added process enumeration with `psutil`.
  - Added startup and five-second polling checks.
  - Added disabled styling and status messaging.
- Verification:
  - `uv run python -m py_compile app.py` passed according to the source task record.
- Remaining:
  - None recorded.
- Notes:
  - The historical dependency addition predates the approval policy in this template.

### T003 — Add ephemeral buttons for watched executables

- Status: completed
- Objective: Discover running executables under configured directories and manage corresponding buttons dynamically.
- Scope:
  - Expand environment variables in watched directory configuration.
  - Add buttons for newly discovered processes and remove them after termination.
  - Generate short labels from executable paths.
  - Initially mute newly discovered targets when needed.
- Acceptance criteria:
  - Matching running executables create one corresponding ephemeral button.
  - Terminated processes remove their ephemeral buttons.
  - Static and ephemeral state remain independently managed.
- Implemented:
  - Added watched-directory scanning through process executable paths.
  - Added generated short names, dynamic button creation/removal, and separate state dictionaries.
  - Changed button layout to support dynamic entries.
- Verification:
  - `python -m py_compile app.py` passed according to the source task record.
  - A configuration example with `watched_dirs` was created under the `mutexe` configuration path.
- Remaining:
  - None recorded.
- Notes:
  - Live process discovery and mute behavior are Windows-dependent; the original task marks the feature completed based on its development process.

### T004 — Resize the window for ephemeral button changes

- Status: completed
- Objective: Keep all visible buttons accessible as ephemeral buttons are added or removed.
- Scope:
  - Recalculate required dimensions after initial creation and dynamic changes.
  - Preserve minimum initial dimensions.
- Acceptance criteria:
  - The window grows and shrinks to fit visible buttons.
  - The configured minimum dimensions are respected.
- Implemented:
  - Added `update_window_size()` based on the button container's requested dimensions.
  - Invoked resizing after initial creation and dynamic add/remove operations.
- Verification:
  - `python -m py_compile app.py` passed according to the source task record.
- Remaining:
  - None recorded.
- Notes:
  - Visual behavior is best reconfirmed manually on Windows when this area is next changed.

## Decisions

### D001 — Keep SoundVolumeView external

- Date: 2026-08-02
- Status: accepted
- Decision: Resolve `soundvolumeview.exe` through `PATH`; do not bundle it with the project.
- Rationale: The user installs NirSoft SoundVolumeView separately, and the project should not redistribute or maintain a built-in copy.
- Consequences:
  - Runtime startup and errors must handle a missing executable clearly.
  - Packaging verification must use an environment where SoundVolumeView is installed.
- Related tasks: `T001`, `T002`, `T003`

### D002 — Use uv project workflow for future Python dependency changes

- Date: 2026-08-02
- Status: accepted
- Decision: Use `uv sync`, `uv run`, and approved `uv add` operations rather than `uv pip install` for managed project changes.
- Rationale: Project-level dependency declarations and lockfile updates are reproducible and easier for agents and the user to review.
- Consequences:
  - A `pyproject.toml` and `uv.lock` should remain authoritative when present.
  - Future dependency mutations require prior approval.
- Related tasks: None.

## Blocked items

- None.

## Cancelled items

- None.

## Candidate items

- None.
