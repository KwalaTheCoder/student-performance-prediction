# Real-data evaluation — 2026-11-02

Input: `Student/Student_Performance.csv`. Dataset SHA-256: `93793b00d9026d0b4907df0ca9f88b3696747c7496679d35833bb0fbf9fb57cf`.

Model selection used only training-fold CV. One final holdout was reserved before preprocessing. The full CV leaderboard, dependency versions, seed, feature schema and split sizes are in [experiments/report.json](experiments/report.json).

- Model: **Ridge**
- Training rows: **7982**; holdout rows: **2018**
- Selection metric: `neg_mean_absolute_error`; selected CV score: **-1.606072**
- Dummy baseline CV score on the same folds: **-16.226928**
- Five CV folds; seed 42; tuning: **False**
- Identical raw predictor rows grouped: **True**

| Metric | Holdout value |
|---|---:|
| mae | 1.667983 |
| rmse | 2.084465 |
| r2 | 0.988246 |


## Dataset-specific interpretation

Predicts continuous Performance Index, excluding Performance Index Cat and the label itself from predictors. Units are index points on the supplied 0–100 scale. Duplicate predictor rows are grouped. The result applies to this dataset; provenance and representativeness are unverified.

## Reproduce

Activate an environment with the project's requirements, change to the repository root, and run:

```cmd
python -m mlproject train --data "D:\data\Student\Student_Performance.csv" --output artifacts --folds 5 --seed 42
```

Results were obtained with the dependency versions recorded in the JSON report. Different versions can change results slightly. Negative MAE selection scores are higher-is-better. CV scores are selection estimates and optimistic; the holdout is the final internal result. Hyperparameter tuning is enabled on the smaller datasets and diabetes; for credit, soccer, student and churn the default bounded candidate comparison is used. Scores are not directly comparable across datasets or tasks.

Do not tune against the now-observed holdout or claim improvement over the legacy notebooks: leakage, split policies and preprocessing differ. Raw data, row-level predictions and trained pickle artifacts are not included in this evidence commit.
