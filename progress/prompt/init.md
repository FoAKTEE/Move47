**central tasks and documents**

* check ref-code/v0.02, all in there, download Katago and please do 
* especially check PROMPT.md and TREE.md

**all should be managed under @Chandra**

**run on GPU no matter what, you may use at most 70% cpu**
* 70% of 256 hardware threads = at most 179 busy threads summed over every
  concurrent worker; each worker is told its thread budget in its prompt

* host facts: this user's non-Slurm processes share one 10-CPU cgroup
  quota (`CPUQuota=1000%` on `user-1012.slice`), which binds before the 70% rule; GPUs open
  only inside Slurm jobs (partition `preempt`, 2 h, preemptible, ≤2 CPUs per GPU, outside the
  slice quota). Effective budget ≈ 10 CPUs + 2 per Slurm GPU job. The "whole CPU budget"
  reference comparison is therefore measured on those 10 CPUs (43.94 sim-s/wall-s at K=10)
* GPU work which enforces the 4-GPU cap


## Git commit policy
* substage commits: one commit per DAG node (or finer), commit tests before/with code
* messages follow `Chandra/_common/contracts/commit_template.md`
  (commit-msg gate already wire); no mention / no coauthor
  of Claude in any case
* never commit build trees, kokkos worktree, or simulation outputs

## Management policy
* under `Chandra`: multiscale memory (this prompt + DAG + design doc
  are the upstream-dependency ledger; update DAG node status as nodes land)
* maximal topological scheduling: deploy
  parallel subagents;
* verification discipline: every claim in commit bodies tagged
  `[SOLID|PRELIMINARY|HOLE|FUTURE]` with a real `verify:` object

* use at most 4 GPU