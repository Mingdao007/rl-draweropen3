---
name: rl-draweropen3
description: |
  Reproduce the exact DATA8010 Homework 2 MetaWorld drawer-open-v3 workflow
  built around the Assignment_2 script layout: inspect the environment, run the
  canonical 4-run campaign, regenerate plots, rebuild the markdown report, and
  assemble the final bundle. Use for requests like drawer-open-v3, DATA8010
  HW2, run the canonical campaign, rebuild the report, or rebuild the final
  bundle.
metadata:
  author: andy
  version: 0.2.0
---

# RL DrawerOpen3

Use this skill only for repositories that expose the validated `Assignment_2`
style workflow around `drawer-open-v3`.

Required entrypoints:

- `inspect_env.py`
- `archive_active_artifacts.py`
- `run_all_experiments.py`
- `plot_results.py`
- `build_report.py`
- `assemble_final_bundle.py`

Do not use this skill for arbitrary RL repos, non-MetaWorld benchmarks, or
repos that do not follow this script layout.

## Default Path

1. Read `references/repo-map.md` to confirm the repository matches the expected
   layout and outputs.
2. Read `references/workflow.md` and follow the canonical path:
   inspect the environment, archive stale artifacts if needed, launch the
   canonical 4-run CUDA campaign, regenerate plots, rebuild the Markdown
   report, then assemble the final submission bundle.
3. For long-running campaigns, prefer the persistent-session guidance in
   `references/troubleshooting.md`.

## Optional Branch

For the supplemental Part 3 extension campaign, read
`references/part3-extra.md`. Treat it as non-canonical and keep the canonical
report and final bundle unchanged unless the user explicitly asks to promote
those extra results.

## Guardrails

- Default to the canonical homework line first.
- Keep examples repo-relative, for example `<assignment_root>`.
- Do not invent new training scripts when the repo already provides stable
  entrypoints.
- If the workspace no longer matches the expected script layout, stop using
  this skill and fall back to normal repo exploration.
