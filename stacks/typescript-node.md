## TypeScript and Node.js

- Use the Node.js version declared by `.node-version`, `.nvmrc`, `package.json`, or repository documentation. Use `fnm` to select or install that version when needed.
- Infer the package manager from the existing lockfile and configuration:
  - `pnpm-lock.yaml` → `pnpm`
  - `yarn.lock` → `yarn`
  - `bun.lock` or `bun.lockb` → `bun`
  - `package-lock.json` → `npm`
- Do not generate a second lockfile or switch package managers without approval.
- For a greenfield project without a specified package manager, use `npm`.
- Use scripts defined in `package.json` rather than inventing direct tool invocations when a suitable script exists.
- Prefer a frozen or clean lockfile install for verification when supported by the selected package manager.
- Add, remove, replace, or upgrade packages only after approval and update `package.json` and the existing lockfile together.
- Preserve the repository's module system, TypeScript configuration, target environments, and generated-code boundaries.
- Run configured type checks, tests, linting, formatting checks, and production builds. Do not assume script names; inspect `package.json`.
- Do not edit compiled output, generated routes, framework caches, or dependency directories manually.
