# Sales Prediction — Architecture and implementation

This guide follows the tracked implementation. Proposed work is identified separately.

## The problem and the system boundary

Advertising observations provide an approachable way to inspect the relationship between inputs
and Sales. This repository keeps that work in a notebook so preparation, computation and saved
outputs can be read together. Its value is an inspectable experiment, not a deployed prediction
service.

## Processing path

```mermaid
flowchart LR
    N0["Advertising channels"]
    N1["holdout"]
    N2["regression"]
    N3["diagnostics"]
    N0 --> N1
    N1 --> N2
    N2 --> N3
```

## End-to-end behavior

### 1. Supply the input data

The required CSV files are not tracked. Obtain an authorized copy with the expected schema and
replace the author-specific absolute paths before execution.

### 2. Inspect the preparation

The split uses random_state=42 and a 20% holdout. Review the transformations and exclusions before
rerunning; an output cannot be understood separately from its input preparation.

### 3. Run the experiment

The implemented method is LinearRegression. Predictive association is not causal return on
advertising spend. Execute in a fresh kernel to reveal ordering and dependency problems.

### 4. Read the diagnostics

Saved holdout results show R² 0.899438 and mean squared error 3.174097 on 40 observations. The
source does not establish business units. No trained estimator artifact or prediction API is
supplied.

## Design choices and consequences

### Inputs are explicit

TV, Radio, Newspaper.

### Method is inspectable

LinearRegression is the implemented method; no broader modeling capability is inferred.

### Historical evidence is labeled

Saved holdout results show R² 0.899438 and mean squared error 3.174097 on 40 observations. The
source does not establish business units.

## Source entry points

### [sales_prediction.ipynb](../sales_prediction.ipynb)

19 nonempty Python cells are committed, along with any saved outputs.
Cell order and absolute data paths are part of reproducibility; outputs are historical.

## Implementation state

| State | Evidence boundary |
| --- | --- |
| Present | Notebook source and historical saved outputs |
| Required externally | Authorized CSV input and compatible Python packages |
| Not rerun | Data-dependent execution in this documentation pass |
| Not supplied | Deployment service, model registry or automated behavior suite |

“Present” means tracked source or assets exist. It does not mean a production or domain
validation has passed. See [Evaluation](EVALUATION.md) for reproducible checks and limits.
