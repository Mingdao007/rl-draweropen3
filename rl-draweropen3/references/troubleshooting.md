# troubleshooting

## CUDA Preflight

If a CUDA run fails unexpectedly, verify the environment first:

```bash
conda run -n data8010 python -c "import torch; print({'cuda_available': torch.cuda.is_available(), 'cuda_version': torch.version.cuda})"
```

The validated homework runners already perform a CUDA readiness check before
launching training jobs.

## `LD_LIBRARY_PATH`

The validated runners prepend the active conda `lib` directory so PyTorch,
Matplotlib, and Stable-Baselines3 do not pick up stale system libraries. If ad
hoc commands fail outside the runner, export the conda `lib` path first.

## IDE Terminal Versus Persistent Sessions

Long runs started from an IDE-integrated terminal can die when the IDE closes.
For long campaigns, prefer tmux:

```bash
tmux new-session -d -s hw2-main 'conda run -n data8010 python run_all_experiments.py --max-parallel 4 --device cuda'
tmux new-session -d -s hw2-part3-extra 'conda run -n data8010 python run_part3_extra_experiments.py --max-parallel 5 --device cuda'
```

Inspect progress:

```bash
tmux capture-pane -t hw2-main -p | tail -n 120
tmux capture-pane -t hw2-part3-extra -p | tail -n 120
```

Attach and detach safely:

```bash
tmux attach -t hw2-main
# then press Ctrl-b d to detach without killing the run
```

## Quick Status Checks

```bash
ps -eo pid,etimes,cmd | grep -E 'run_all_experiments.py|run_part3_extra_experiments.py|train_policy.py' | grep -v grep
watch -n 3 nvidia-smi
```

## Scope Boundary

If the repository does not expose the validated `Assignment_2` entrypoints and
output folders, stop using this skill as a procedural wrapper. It is exact
repo-specific by design.
