# Customization Guide

## 1. Instantiate the base files

Copy `base/AGENTS.md` and `base/TASKS.md` to the root of the target repository. Replace every `{{UPPER_SNAKE_CASE}}` placeholder. Search for `{{` before adopting the files to ensure no accidental placeholders remain.

Delete inapplicable command fields or set them to `N/A`. Concrete absence is better than an invented command.

## 2. Add stack instructions

Copy the relevant appendix into section 11 of the project `AGENTS.md`. Adapt it to the repository rather than treating it as immutable boilerplate.

Recommended combinations:

- Python project: `python-uv.md`
- TypeScript CLI or service: `typescript-node.md`
- Rust CLI or service: `rust-cargo.md`
- Svelte frontend: `typescript-node.md` plus `svelte.md`, deduplicated
- Tauri/Svelte desktop app: normally `tauri-svelte.md` alone, with repository-specific command details

The final project file should be self-contained. Do not require an agent to locate appendices in another repository.

## 3. Initialize TASKS.md

Write a one-paragraph project objective and a concise current-state summary. Convert accepted implementation work into stable mainline tasks:

```markdown
### T001 — Establish project scaffold

- Status: completed
- Objective: Produce a locally buildable application skeleton.
- Scope:
  - Initialize the selected framework and repository layout.
- Acceptance criteria:
  - The development build completes from a clean checkout.
- Implemented:
  - Initialized the application and basic entry points.
- Verification:
  - `...` passed on YYYY-MM-DD.
- Remaining:
  - None.
- Notes:
  - None.
```

A status is evidence-backed:

- `pending`: no implementation started;
- `in progress`: partially implemented or awaiting verification;
- `blocked`: a specific condition prevents progress;
- `completed`: implementation and required verification are complete;
- `cancelled`: intentionally abandoned, with a recorded reason.

## 4. Preserve task history without creating bureaucracy

Use one task for a coherent outcome, not every code edit. Update it after each meaningful step. Append new mainline work with the next unused ID.

Do not renumber tasks to make the list visually tidy. Stable references are more valuable than contiguous numbering.

Keep evidence concise:

- what changed;
- what command or manual procedure verified it;
- what remains;
- why it is blocked or cancelled.

Move lengthy requirements, architecture studies, protocols, schemas, or diagrams to a dedicated document when `TASKS.md` becomes difficult to scan. Link that document from the relevant task or decision.

## 5. Record decisions selectively

A decision record is appropriate when a future agent might otherwise reopen or contradict an accepted choice. Examples include storage format, package manager, supported platform, migration policy, or intentional non-goals.

Do not record routine implementation details as decisions.

## 6. Dependency approval workflow

An agent may inspect and propose a dependency but must not mutate manifests or lockfiles before approval. A useful request contains:

- the problem the dependency solves;
- existing and standard-library alternatives;
- why custom code is less suitable;
- maintenance and operational impact;
- exact files expected to change.

Synchronizing dependencies already declared by a repository is not an addition and does not require separate approval.

## 7. Manual verification

Do not force every task into `completed` merely because compilation passes. For UI, hardware, OS integration, or subjective behavior, use:

```markdown
- Status: in progress
- Verification:
  - Automated checks passed.
  - Awaiting user verification: confirm ...
```

After the user confirms the stated checks, update the task to `completed` and record that confirmation factually.

Keep the `Active task` handoff fields current while work is incomplete:

- `Waiting on: agent` means the agent can continue without user input.
- `Waiting on: user` means the user must grant permission, make a decision, or perform verification.
- `Waiting on: external` means progress depends on a third-party system, event, or prerequisite.
- `Waiting on: none` means there is no active dependency or required action.

Write `Required action: None.` unless a specific party must do something. When user input is required, make the request concrete enough to answer without reconstructing context from the task history.

## 8. Keep AGENTS.md effective

Instruction files lose value when they become long collections of generic advice. Periodically remove rules that do not prevent a plausible repository-specific failure.

Prefer concrete rules such as:

> Always invoke SoundVolumeView through `run_soundvolumeview`; it applies the required Windows process flags.

Avoid vague rules such as:

> Be careful when launching processes.

## 9. Git policy

The base template intentionally disallows commits unless a project explicitly authorizes them. If automatic commits are desired, define:

- when a commit is allowed;
- required verification before committing;
- commit-message convention;
- whether task-file updates must be included in the same commit;
- whether pushing is separately prohibited.
