## Python with uv

- Treat `pyproject.toml` and `uv.lock` as the normal project and resolution sources.
- Use the Python version declared by the repository, such as `.python-version` or `requires-python`. Do not silently broaden compatibility claims.
- Synchronize declared dependencies with `uv sync`.
- Run project commands through `uv run`, for example `uv run pytest` or `uv run python -m package`.
- Add a dependency only after approval, using `uv add <package>`; use an appropriate group or optional extra when the project already distinguishes them.
- Remove or upgrade dependencies only after approval, using the corresponding `uv` project command and committing the resulting `pyproject.toml` and `uv.lock` changes together.
- Prefer importable modules and package entry points over path-dependent scripts for non-trivial projects.
- Use `python -m ...` through `uv run` when it avoids interpreter ambiguity.
- Run configured tests, linters, format checks, and type checks. Typical commands may include `uv run pytest`, `uv run ruff check .`, `uv run ruff format --check .`, and `uv run pyright`, but do not assume tools not declared by the repository.
- For a minimal script without configured tests, at least run an appropriate executable or syntax check, such as `uv run python -m py_compile <files>`.
- Do not use `uv pip install` as the normal way to mutate a managed project. It may be used only for an explicitly unmanaged environment or a repository that is not structured as a `uv` project.
