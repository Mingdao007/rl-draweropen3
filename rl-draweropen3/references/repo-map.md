# repo map

Use this skill only when the repository exposes the same core files:

- `hw2_common.py`: shared defaults, environment helpers, evaluation helpers
- `train_policy.py`: SAC training entrypoint
- `run_all_experiments.py`: canonical 4-run mainline
- `run_part3_extra_experiments.py`: supplemental 5-run branch
- `plot_results.py`: canonical plot regeneration
- `build_report.py`: Markdown report generation
- `build_part3_extra_note.py`: supplemental note generation
- `package_submission.py`: code zip and environment freeze
- `assemble_final_bundle.py`: self-contained final handoff folder

## Result Locations

- `results/`: run metrics and plots
- `checkpoints/`: model checkpoints and final models
- `campaign_logs/`: per-campaign logs
- `submission/`: canonical generated outputs
- `final_submission_bundle/`: final handoff folder with local plot links

## Current Final Handoff Contents

- `DATA8010_HW2_Report.md`
- `plots/` with the report PNGs
- `DATA8010_HW2_Code.zip`
- `environment_freeze.txt`
- `videos/README.md`
- `CONTENTS.md`
