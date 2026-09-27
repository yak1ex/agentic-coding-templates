# Agentic Coding Templates

Reusable operating and task-management templates for coding agents working on small-scale personal development projects.

The repository uses two primary files in each project:

- `AGENTS.md`: stable operating rules, repository conventions, toolchain commands, and verification policy.
- `TASKS.md`: project objective, current state, implementation plan, task evidence, and short decision records.
- `.agentic-template.yml`: machine-readable template provenance used to detect and review upstream changes.

The templates favor small, reviewable changes; explicit verification; stable task identifiers; minimal process overhead; and human approval for intrusive actions.

## Repository layout

```text
base/
  .agentic-template.yml     Template provenance record
  AGENTS.md                 Universal project template
  TASKS.md                  Universal task-management template
stacks/
  python-uv.md              Python projects managed with uv
  typescript-node.md        TypeScript and Node.js projects
  rust-cargo.md             Rust projects managed with Cargo
  svelte.md                 Svelte and SvelteKit projects
  tauri-svelte.md           Tauri applications with Svelte frontends
docs/
  customization-guide.md    How to instantiate and maintain the templates
TEMPLATE_RELEASE            Current date-based template release
examples/
  mutexe/                   Migration example for a small Python/Tk project
  ThumbsContainer/          Migration example for a Tauri/Svelte/Rust project
```

## Recommended use

1. Copy `base/AGENTS.md`, `base/TASKS.md`, and `base/.agentic-template.yml` into the project root.
2. Replace all `{{UPPER_SNAKE_CASE}}` placeholders.
3. Copy the relevant stack appendix into the marked section of `AGENTS.md`.
4. Remove instructions that do not apply to the project.
5. Record the initial ordered plan in `TASKS.md` using stable task IDs such as `T001` and decision IDs such as `D001`.
6. Record the template release, exact Git revision, adoption date, and included components in `.agentic-template.yml`.
7. Keep the instantiated `AGENTS.md` self-contained. Agents should not need this template repository at runtime.

For a multi-stack project, combine only the relevant appendices. For example, a Tauri/Svelte application normally uses `tauri-svelte.md`; it already incorporates the important Rust, TypeScript, and Svelte concerns, so copying all four appendices is usually unnecessary.

## Core policy choices

- Task states are exactly: `pending`, `in progress`, `blocked`, `completed`, and `cancelled`.
- Task and candidate IDs are stable and never reused.
- Task numbering does not imply priority; the ordered `Current plan` determines execution order.
- Newly discovered work is triaged into the current task, another existing task, a new accepted task, a candidate item, or no action before implementation begins.
- `Active work` is a synchronized execution pointer; the referenced task remains the authoritative record.
- New accepted work is appended; agents do not renumber or substantially reorganize tasks without explicit approval.
- Dependency additions, removals, replacements, and upgrades require prior user approval.
- Agents do not commit unless repository-specific instructions explicitly authorize it.
- Automated or objective work may be completed after relevant checks pass.
- UI, hardware, platform integration, and subjective behavior remain `in progress` until user verification when the agent cannot verify them adequately.
- Template adoption records both a readable date-based release and an exact Git revision; later updates are reviewed rather than blindly copied over project customizations.

## Design origin

The templates adapt useful principles from the [FerroxLabs `AGENTS.md` template](https://github.com/FerroxLabs/agents-md/) and normalize task-management patterns used in the `mutexe` and `ThumbsContainer` repositories. The resulting wording and structure in this repository are independently organized for small personal projects.
