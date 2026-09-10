# Breast Cancer Detection

This project explores machine-learning models for classifying breast tumors as
malignant or benign using the Wisconsin Diagnostic Breast Cancer dataset. It
also demonstrates two explainability techniques:

- **SHAP**: estimates how each feature contributes to a model prediction.
- **DiCE**: generates counterfactual examples that show how input values could
	change a prediction.

The notebooks are intended for experimentation and education. They are not a
medical diagnostic tool and must not be used to make clinical decisions.

## Contents

| File | Description |
| --- | --- |
| `cancer_dataset.csv` | 569 observations with 30 numeric tumor features, an `id` column, and the `diagnosis` target. |
| `ML_SHAP.ipynb` | Data preparation, model training/evaluation, and SHAP-based explanations. |
| `ML_Dice.ipynb` | Data preparation, model training/evaluation, and DiCE counterfactual explanations. |

## Dataset

The `diagnosis` column is the target:

- `M` = malignant
- `B` = benign

The predictors describe cell-nucleus measurements such as radius, texture,
perimeter, area, smoothness, compactness, concavity, symmetry, and fractal
dimension. Measurements are provided as mean, standard error, and worst-case
values. The `id` column identifies a record and should not be used as a model
feature.

## Setup

Use Python 3.9 or newer and create an isolated environment:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib seaborn scikit-learn shap dice-ml
```

On Windows, activate the environment with:

```powershell
.venv\Scripts\Activate.ps1
```

## Run the notebooks

Start Jupyter from the repository root so the notebooks can find
`cancer_dataset.csv`:

```bash
jupyter notebook
```

Open either notebook and run its cells from top to bottom. The model must be
fit before the SHAP or DiCE explanation cells are run. The notebooks contain
visualizations, classification metrics, confusion matrices, and explanation
plots.

## Typical workflow

1. Load and inspect the CSV data.
2. Encode the diagnosis labels and prepare the feature matrix.
3. Split the data into training and test sets.
4. Train and evaluate scikit-learn classifiers.
5. Inspect model behavior with SHAP or generate counterfactuals with DiCE.

## Reproducibility

Run the notebooks in a clean kernel after installing the dependencies. Results
can vary when a model or train/test split does not specify a random seed.
Generated notebook outputs are environment-dependent, so rerun the cells when
reproducing the analysis.