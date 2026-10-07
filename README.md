# Sales Prediction — Advertising Regression Notebook

> A three-feature regression exercise with a recorded 160/40 train/test split.

[sales_prediction.ipynb](sales_prediction.ipynb) explores the relationship between TV, radio and
newspaper advertising inputs and sales, then fits a linear regression model. It provides pair plots,
summary statistics, held-out metrics and an actual-versus-predicted chart.

## Inspect and reproduce

Read the saved notebook outputs on GitHub, or execute with Python and Jupyter:

```sh
python3 -m venv .venv
.venv/bin/python -m pip install jupyterlab pandas matplotlib seaborn scikit-learn
.venv/bin/python -m jupyter lab sales_prediction.ipynb
```

The matching `Advertising.csv` is not included. Obtain it separately, replace the absolute path in
the `pd.read_csv` cell, and run from a clean kernel. Required columns are `TV`, `Radio`, `Newspaper`
and `Sales`; the displayed `Unnamed: 0` index column is not used as a model feature.
No dependency versions are locked, and dataset provenance/licensing is not documented here.

## Recorded experiment

| Stage | Implementation / saved evidence |
|---|---|
| Dataset | 200 rows shown in summary output |
| Inputs / target | TV, Radio, Newspaper / Sales |
| Split | 160 train, 40 test; `test_size=0.2`, `random_state=42` |
| Model | scikit-learn LinearRegression |
| MSE | 3.1740973540 |
| R² | 0.8994380241 |
| Visual checks | Pair plots and actual-versus-predicted scatter |

Workflow: `CSV → exploration → train/test split → regression fit → held-out metrics → chart`.
Numbers above are historical outputs inspected on **7 October 2026**. Execution was not repeated
because the CSV is absent. The notebook does not define monetary units or establish causal effects
of advertising expenditure.

## Scope and limits

This is a notebook experiment, with no serving API, fitted-model export, automated tests or
cross-validation study. A single split does not measure future campaign performance. The recorded
R² describes that test sample; it is not a guarantee or an advertising-budget recommendation.
