# rl-draweropen3

A standalone Codex skill repository for reproducing the exact `DATA8010 Homework 2` workflow on the `drawer-open-v3` MetaWorld task.

This repository is intentionally narrow. It is not a generic reinforcement-learning skill and it does not claim to support arbitrary MetaWorld repositories. It is designed for repositories that expose the same `Assignment_2`-style entrypoints and outputs used in the validated homework pipeline.

## What This Skill Reproduces

The canonical path is:

1. inspect the environment
2. archive active artifacts
3. run the canonical 4-run campaign
4. regenerate plots
5. rebuild the Markdown report
6. assemble the final submission bundle

The canonical Part 3 learning-rate ablation is fixed to:

- `3e-4` as the `0.3×` setting
- `1e-3` as the baseline
- `3e-3` as the `3×` setting

The 5-run extension campaign is documented, but it is supplemental and not part of the default public workflow.

## What Ships

- `rl-draweropen3/`: installable Codex skill package
- `rl-draweropen3/agents/openai.yaml`: Codex metadata
- `rl-draweropen3/references/`: workflow, repo map, supplemental branch, and troubleshooting notes
- `LICENSE`: MIT license

## Install

1. Copy `rl-draweropen3/` into `${CODEX_HOME:-$HOME/.codex}/skills/`.
2. Restart Codex or refresh local skills.
3. Invoke the skill as `$rl-draweropen3`.

## Intended Use

Ask Codex to:

- reproduce the `DATA8010 HW2` `drawer-open-v3` workflow
- run the canonical `drawer-open-v3` campaign
- rebuild the report after rerunning the canonical experiments
- rebuild the final submission bundle
- inspect whether a repo matches the expected `Assignment_2` script layout

## Repo Assumptions

This skill expects a repository rooted at `<assignment_root>` that contains:

- `inspect_env.py`
- `archive_active_artifacts.py`
- `run_all_experiments.py`
- `plot_results.py`
- `build_report.py`
- `assemble_final_bundle.py`

It also expects the normal output folders used by the homework workflow:

- `results/`
- `checkpoints/`
- `campaign_logs/`
- `submission/`
- `final_submission_bundle/`

If those files are absent, the skill should fall back instead of pretending to support a broader repo layout.

## Out Of Scope

This public repo does not try to cover:

- generic RL repos
- non-MetaWorld repos
- slide design or presentation polishing
- viewer or video-recording workflows by default
- non-canonical extra experiments unless explicitly requested

## Trigger Examples

- `Use $rl-draweropen3 to run the canonical drawer-open-v3 homework workflow.`
- `Rebuild the DATA8010 HW2 report and final bundle.`
- `Check whether this repo matches the Assignment_2 drawer-open-v3 layout.`
- `Run only the supplemental Part 3 extension branch.`

## Privacy Boundary

This repository contains only the portable skill package and public-facing workflow documentation. It does not include private memory files, local machine paths, personal state, or unrelated private skills.
