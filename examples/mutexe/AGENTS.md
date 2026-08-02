# AGENTS.md

Operating instructions for coding agents working in `mutexe`. Read this file and `TASKS.md` before changing the repository.

## 1. Non-negotiable rules

1. Do not fabricate file paths, SoundVolumeView behavior, process state, commands, or verification results.
2. Make only task-related changes; do not perform unrelated cleanup or redesign.
3. Preserve unrelated user changes in the working tree.
4. Do not add, remove, replace, or upgrade dependencies without prior user approval.
5. Do not commit unless the user explicitly requests it for the current work.
6. Update `TASKS.md` with every meaningful implementation step in the same work cycle.
7. Do not bundle or copy `soundvolumeview.exe` into the repository.

## 2. Project context

- Project: `mutexe`
- Objective: Provide a Windows desktop utility that mutes and unmutes individual processes through NirSoft SoundVolumeView.
- Primary language: Python 3
- Framework: `tkinter`
- Runtime and deployment target: Windows desktop; single Python script or packaged executable
- External runtime requirements: `soundvolumeview.exe` must be installed separately and available through `PATH`

## 3. Repository orientation

Before editing:

1. Read `TASKS.md` and identify the affected stable task.
2. Read `app.py`, relevant configuration examples, and any packaging files that the change affects.
3. Inspect `pyproject.toml`, `uv.lock`, and `.python-version` if present before selecting commands.
4. Inspect the working tree and preserve unrelated user changes.
5. State a brief plan and verifiable success criteria for non-trivial work.

Repository layout must be inferred from the checkout. Do not invent missing files or configured quality tools.

## 4. Implementation constraints

- Invoke `soundvolumeview.exe` through the project's common launch helper; do not scatter direct process-launch calls.
- Keep the external executable resolved through `PATH`.
- Preserve Windows process-launch flags and error handling established by the helper.
- Keep code and comments ASCII unless a visible icon or other deliberate UI character requires Unicode.
- Avoid comments that restate obvious code. Document non-obvious reasons and platform constraints.
- Do not add inline lint suppressions such as `# noqa`. Configure a genuinely unwanted rule project-wide only after approval.
- Preserve configuration compatibility unless a task explicitly introduces a migration.

## 5. Dependency policy

Prefer the Python standard library and dependencies already declared by the repository. Prior user approval is required before adding, removing, replacing, or upgrading a dependency.

Before requesting approval, explain the need, alternatives, maintenance impact, and files that would change. After approval, use modern `uv` project commands and update `pyproject.toml` and `uv.lock` together.

Synchronizing already declared dependencies with `uv sync` is allowed.

## 6. Python and uv

- Use the repository's declared Python version.
- Use `uv sync` for environment synchronization.
- Run commands through `uv run`.
- Use `uv add <package>` only after dependency approval.
- Do not use `uv pip install` as the normal way to mutate this managed project.
- Run configured tests and quality checks if they exist.
- At minimum, after changing `app.py`, run:

```text
uv run python -m py_compile app.py
```

If more Python files are changed, syntax-check each changed Python file or use an equivalent repository-wide check.

## 7. Verification and completion

- Read all command output and report failures accurately.
- Objective non-UI changes may be completed after relevant executable checks pass.
- UI state, appearance, live process detection, SoundVolumeView integration, and packaged executable behavior remain `in progress` with `Awaiting user verification` when they cannot be adequately exercised in the agent environment.
- Do not treat a syntax check as proof of Windows runtime behavior.

## 8. Task management

For each meaningful step:

1. Update the affected task in `TASKS.md`.
2. Record implementation and verification facts.
3. Append newly discovered mainline work using the next unused `T` ID.
4. Preserve all existing IDs and do not reorganize mainline tasks without explicit approval.
5. Use exactly one of: `pending`, `in progress`, `blocked`, `completed`, `cancelled`.
6. Review `TASKS.md` for consistency before the final response.

## 9. Git safety

- Do not commit by default.
- Do not stage or discard unrelated changes.
- When the user explicitly requests a commit, include the corresponding `TASKS.md` update and use the repository's established conventional commit style, for example `fix(app): handle missing SoundVolumeView executable`.
- Pushing requires a separate explicit request.

## 10. Final response checklist

- List changed files.
- Report checks actually run and their results.
- State the `TASKS.md` status changes.
- Identify Windows, UI, external-tool, or packaging behavior still awaiting user verification.
