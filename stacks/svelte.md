## Svelte and SvelteKit

- Determine whether the repository uses plain Svelte or SvelteKit before applying framework conventions.
- Preserve the existing component, routing, state-management, styling, and server/client-boundary patterns.
- Use scripts from `package.json`; common checks may include `check`, `test`, `lint`, and `build`, but script names are repository-specific.
- Run `svelte-check` through the configured script when present.
- Do not edit generated SvelteKit output, framework caches, or generated type files manually.
- Keep browser-only APIs out of server-side execution paths and protect environment-specific access using established framework patterns.
- Treat accessibility diagnostics as correctness issues unless a repository-specific exception is documented.
- For visual or interaction changes, run available automated checks and keep the task `in progress` with `Awaiting user verification` unless the result can be adequately inspected in the agent environment.
- Do not introduce a component library, state library, CSS framework, or testing framework without approval.
