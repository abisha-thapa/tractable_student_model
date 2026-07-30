## ASSISTments

Code and data splits for the ASSISTments experiments (single-skill setting, Q=1).

### Files
- `pc-kt-aaai.ipynb` — full pipeline: the PC model, BKT and DKT baselines, the incremental
  ablation (difficulty, forgetting), and the cold-start (opportunity-stratified) analysis
- `splits/` — the five fixed student-level 80/20 train/test splits
  (`split_run0.csv` … `split_run4.csv`)
- `experiment_config.json` — hyperparameters, dataset MD5 hash, and library/GPU versions

### Dataset
ASSISTments 2012–2013, publicly available. The notebook downloads it automatically.

### Reproducing
Run the notebook top to bottom. It regenerates the per-topic AUC comparison (BKT/DKT/PC),
the incremental ablation, and the cold-start results using the fixed splits in `splits/`.

### Notebook structure
1. Config: hyperparameters, seeds, determinism flags, output paths
2. Load ASSISTments 2012-13, filter to original problems and valid outcomes
3. Six CCSS topic subsets; foundational/advanced cluster assignment; per-split dataset builder
4. PC model (probabilistic circuit) and training
5. Metrics and causal PC evaluation
6. BKT baseline
7. Cold-start analysis (PC vs BKT by opportunity index)
8. DKT baseline
9. Main experiment loop (trains and evaluates all variants per topic/split)
10. Aggregation into result tables
11. Paired significance tests + experiment config dump
12. Per-topic dataset statistics