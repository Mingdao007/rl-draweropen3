# canonical workflow

This skill assumes a repository with the validated `Assignment_2` script layout
and outputs.

## Main Path

From `<assignment_root>`:

1. Inspect the environment:

```bash
conda run -n data8010 python inspect_env.py
```

2. Archive current active artifacts if starting fresh:

```bash
conda run -n data8010 python archive_active_artifacts.py
```

3. Launch the canonical 4-run CUDA campaign:

```bash
conda run -n data8010 python run_all_experiments.py --max-parallel 4 --device cuda
```

4. Regenerate canonical plots:

```bash
conda run -n data8010 python plot_results.py --baseline-lr 1e-3 --report-seed 0
```

5. Rebuild the Markdown report and code package:

```bash
conda run -n data8010 python build_report.py
conda run -n data8010 python package_submission.py
```

6. Rebuild the self-contained delivery folder:

```bash
conda run -n data8010 python assemble_final_bundle.py
```

## Canonical Interpretation

- Main report baseline: dense reward, `lr=1e-3`, `seed=0`
- Part 2: dense `1e-3` vs sparse `1e-3`
- Part 3 mainline: dense `3e-4`, `1e-3`, `3e-3`
- Canonical budget: `500,000` steps per run

In Part 3, the canonical interpretation is:

- `3e-4` is the `0.3×` setting and fails in the canonical rerun
- `1e-3` is the baseline and succeeds
- `3e-3` is the `3×` setting and also succeeds, but not earlier than the baseline

## Expected Outputs

- `results/<run_name>/`
- `checkpoints/<run_name>/`
- `results/plots/`
- `submission/DATA8010_HW2_Report.md`
- `submission/DATA8010_HW2_Code.zip`
- `submission/environment_freeze.txt`
- `final_submission_bundle/`
