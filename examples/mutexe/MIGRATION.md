# mutexe migration notes

- Preserved the Windows/Tkinter/SoundVolumeView constraints and the existing implementation history.
- Replaced the previous three-state task model with the shared five-state model.
- Converted numbered headings to stable IDs `T001` through `T004` without changing their order.
- Moved durable operational rules into `AGENTS.md` and retained implementation evidence in `TASKS.md`.
- Changed future Python environment guidance from `uv venv` plus `uv pip install` to a managed `uv` project workflow.
- Removed automatic commit behavior from the default process; commits now require an explicit request.
- Flagged the historical `browrdr` versus `mutexe` configuration path inconsistency rather than silently changing product behavior.
