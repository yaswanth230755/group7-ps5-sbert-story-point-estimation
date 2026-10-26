# Deliverables scored against the group's selection weights

The weights are those the group used to choose PS-5 (feasibility 20 %, reproducibility 20 %, dataset and split feasibility 15 %, leakage control 10 %, time and compute 10 %, report quality 10 %, viva readiness 10 %, research value 5 %). For each parameter: the evidence in this repository and the remaining risk.

| Parameter (weight) | Evidence | Remaining risk |
|---|---|---|
| Implementation feasibility (20 %) | Complete pipeline on the real TAWOS data (39 projects); 79 tests; GitHub CI green; the notebook runs end to end on Kaggle (about 80 min on a T4) | none known |
| Reproducibility (20 %) | Seeds, configuration hash and data hash stored; three independent GPU runs gave bit-identical metrics, splits and predictions; `python -m spsbert verify` recomputes a project | different GPU or CUDA versions can differ at floating-point noise level (use `--tol 1e-3`) |
| Dataset and split feasibility (15 %) | The real dump was converted (65,427 issues with a story point, 39 projects); 80:20 split and five balanced folds with hard assertions | two guideline project names matched by elimination (labels only) |
| Validation and leakage control (10 %) | Leakage-spy test: the test set is never fitted on or used for selection; early stopping uses a hold-out of the training folds only; duplicate texts removed | random splitting leaks temporal information by design (stated as a limitation) |
| Time and compute (10 %) | Cached embeddings, resumable per-project results, runtime estimate and a guard against unrealistic runs, batches and a cheaper configuration | none for the final run |
| Report quality (10 %) | The report is generated from measured results only: tables, six figures, confidence intervals, Holm-corrected tests, rank test, discussion and limitations | the discussion needs the authors' own interpretation |
| Viva readiness (10 %) | `docs/VIVA_GUIDE.md`, live `predict` and `verify`, the audit output, a notebook that shows every step | members must rehearse |
| Research value (5 %) | Five methods on identical splits answer whether SBERT is effective relative to lexical and trivial baselines | modest by design: within-project, random split |

See also `docs/PS_SELECTION_CHECK.md` (all 12 statements re-scored with the same weights) and `docs/guideline_matrix.csv` (word-by-word assignment compliance).
