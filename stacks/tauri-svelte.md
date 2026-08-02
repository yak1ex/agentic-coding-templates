## Tauri with Svelte and TypeScript

- Treat the application as two cooperating systems: the Rust/Tauri backend and the Svelte/TypeScript frontend. Inspect both sides of a command, event, data type, or permission change.
- Use the Node.js version selected through repository files and `fnm`; infer the frontend package manager from the existing lockfile.
- Use Cargo and the Rust toolchain declared by the repository.
- Do not add or upgrade npm packages, crates, Tauri plugins, capabilities, or permissions without prior approval.
- Keep Tauri command names, argument casing, serialization formats, events, and frontend call sites synchronized.
- Review Tauri capability and permission files when adding filesystem, shell, dialog, process, network, or plugin access. Grant the narrowest required scope.
- Keep long-running or blocking work off the UI thread and avoid blocking asynchronous runtime threads.
- Validate path and process behavior against the stated deployment target; do not claim support for untested platforms.
- Use repository scripts for frontend checks and Tauri builds. Also run relevant Rust checks in the Tauri crate when they are not already covered.
- A typical final pass may include the configured frontend check/test/build scripts plus `cargo fmt --check`, `cargo check`, and `cargo test` in the Rust workspace. Run only commands appropriate to the repository.
- Packaging success does not by itself verify UI behavior, OS integration, external executables, file associations, installers, or hardware-dependent paths. Record those as awaiting user verification where necessary.
- Do not manually edit generated frontend output, Cargo target output, or Tauri build artifacts.
