# ThumbsContainer migration notes

- Split the original combined `project.md` responsibilities into operational rules (`AGENTS.md`) and project state (`TASKS.md`).
- Preserved the original twenty task streams and mapped them to stable IDs `T001` through `T020`.
- Preserved completed, pending, and in-progress status meaning while adopting the shared five-state vocabulary.
- Kept `T011` as the active task because it is the only source task recorded as in progress.
- Converted durable product and architectural choices into concise decision records.
- Made the Tauri/Rust/Svelte instructions self-contained and added dependency/capability approval boundaries.
- Made user verification explicit for UI, Windows integration, external executables, data-set behavior, and performance claims.
- Did not reproduce every long product requirement in `AGENTS.md`; requirements remain represented through the objective, constraints, task scopes, and decisions in `TASKS.md`.
