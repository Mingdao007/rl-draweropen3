# part 3 extra branch

This branch is optional and non-canonical. Use it only when the user explicitly
wants the supplemental Part 3 experiments beyond the frozen public report path.

## Current Extra Matrix

The current extra campaign is five dense-reward runs on `seed 0`,
`500,000` steps, `device=cuda`:

- `lr=3e-3`, `batch_size=256`, `warmup=10000`
- `lr=1e-3`, `batch_size=128`, `warmup=10000`
- `lr=1e-3`, `batch_size=512`, `warmup=10000`
- `lr=1e-3`, `batch_size=256`, `warmup=0`
- `lr=1e-3`, `batch_size=256`, `warmup=20000`

Launch it from `<assignment_root>`:

```bash
conda run -n data8010 python run_part3_extra_experiments.py --max-parallel 5 --device cuda
```

After completion, rebuild the supplemental note:

```bash
conda run -n data8010 python build_part3_extra_note.py
```

## Important Boundary

- Do not overwrite `submission/DATA8010_HW2_Report.md`
- Do not overwrite `final_submission_bundle/`
- Treat the output as supplemental until the user explicitly asks to promote it

## Supplemental Outputs

- `submission/PART3_EXTRA_NOTE.md`
- new `results/<run_name>/` and `checkpoints/<run_name>/`
- new `campaign_logs/<timestamp>_part3_extra/`
