# Agentic Coding Templates

Reusable operating and task-management templates for coding agents working on small-scale personal development projects.

The repository uses two primary files in each project:

- `AGENTS.md`: stable operating rules, repository conventions, toolchain commands, and verification policy.
- `TASKS.md`: project objective, current state, implementation plan, task evidence, and short decision records.

The templates favor small, reviewable changes; explicit verification; stable task identifiers; minimal process overhead; and human approval for intrusive actions.

## Repository layout

```text
base/
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
examples/
  mutexe/                   Migration example for a small Python/Tk project
  ThumbsContainer/          Migration example for a Tauri/Svelte/Rust project
```

## Recommended use

1. Copy `base/AGENTS.md` and `base/TASKS.md` into the project root.
2. Replace all `{{UPPER_SNAKE_CASE}}` placeholders.
3. Copy the relevant stack appendix into the marked section of `AGENTS.md`.
4. Remove instructions that do not apply to the project.
5. Record the initial plan in `TASKS.md` using stable IDs such as `T001` and `D001`.
6. Keep the instantiated `AGENTS.md` self-contained. Agents should not need this template repository at runtime.

For a multi-stack project, combine only the relevant appendices. For example, a Tauri/Svelte application normally uses `tauri-svelte.md`; it already incorporates the important Rust, TypeScript, and Svelte concerns, so copying all four appendices is usually unnecessary.

## Core policy choices

- Task states are exactly: `pending`, `in progress`, `blocked`, `completed`, and `cancelled`.
- Task IDs are stable and never reused.
- New work is appended; agents do not renumber or substantially reorganize tasks without explicit approval.
- Dependency additions, removals, replacements, and upgrades require prior user approval.
- Agents do not commit unless repository-specific instructions explicitly authorize it.
- Automated or objective work may be completed after relevant checks pass.
- UI, hardware, platform integration, and subjective behavior remain `in progress` until user verification when the agent cannot verify them adequately.

## Design origin

The templates adapt useful principles from the [FerroxLabs `AGENTS.md` template](https://github.com/FerroxLabs/agents-md/) and normalize task-management patterns used in the `mutexe` and `ThumbsContainer` repositories. The resulting wording and structure in this repository are independently organized for small personal projects.
