## Rust with Cargo

- Treat `Cargo.toml` and `Cargo.lock` as the dependency and resolution sources for applications. Preserve the repository's lockfile policy for libraries and workspaces.
- Use the toolchain declared by `rust-toolchain.toml`, `rust-toolchain`, or repository documentation.
- Add, remove, replace, upgrade, or change crate features only after prior approval.
- Prefer the standard library and crates already present in the workspace.
- Preserve feature gating, target-specific dependencies, workspace inheritance, and minimum-supported-Rust-version policy.
- Use focused tests during iteration, then run the relevant broader checks before finalizing.
- Typical checks are `cargo fmt --check`, `cargo check`, `cargo test`, and configured Clippy commands. Inspect repository configuration before adding flags such as `--all-features`, `--all-targets`, or `-D warnings`.
- Do not claim cross-platform compatibility based only on a host-platform build.
- Avoid `unsafe` unless required by the task and existing design. Document the invariant and test the safe boundary when `unsafe` is introduced or changed.
- Keep recoverable errors explicit at I/O, parsing, process, FFI, and IPC boundaries; do not replace meaningful errors with panics.
