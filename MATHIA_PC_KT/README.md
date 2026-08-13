# MATHAia PC KT

Knowledge tracing on MATHia ratio-and-proportion logs with a probabilistic circuit, against BKT and DKT baselines. This folder contains three self-contained notebooks.

## Setup

```bash
pip install -r requirements.txt
```

## Data

The MATHia exports are not included. Put them in `dataset/`, keeping these names:

```
dataset/
  MATHia_2223_deidentified_ratio_proportion_change3_large_sample.csv
  ratio_proportion_change3_all_problems_text_and_metadata.csv
  MATHia_2223_deidentified_ratio_proportion_change4_large_sample.csv
  ratio_proportion_change4_all_problems_text_and_metadata.csv
```

The interaction CSV is one row per student action. The metadata CSV is one row per problem.

## Notebooks

Run in order. 2 and 3 read what 1 writes.

**`1_build_dataset.ipynb`** — interaction exports to `data.pkl` and `problem_info.csv`, per workspace. Filters the interactions worth modeling, derives problem subtypes and per-problem conditional KCs, builds the Q-matrix, assembles response trajectories, writes the per-(student, problem) side table.

**`2_reconstruct_raw.ipynb`** — rebuilds raw MATHia rows for chosen students or schools from `problem_info.csv`, and checks each rebuilt attempt against the columns the side table derived from the originals. Writes a CSV per selection.

**`3_models_and_results.ipynb`** — fits the circuit, the BKT and DKT baselines, and the cross-workspace archetype transfer.

## Path Analysis Graph

A student's sequence of actions in the MATHia can be viewed as a path graph at <https://path-analysis.vercel.app/>.

Notebook 3 lists the students at each end of the archetype log-odds distribution. Rebuild those students' raw interactions with notebook 2, then load the resulting CSV into the site to view their paths. Figure 5 in the paper is produced this way.
